from pathlib import Path
import html, re, json, shutil, zipfile

src = Path("/mnt/data/document (8).txt")
lines = src.read_text(encoding="utf-8-sig").splitlines()

# Exact source ranges from the uploaded document.
ranges = {
    "rules": (1, 706),
    "criminal": (707, 777),
    "constitution": (778, len(lines)),
}

rules_headings = {
    1:"Повага, антибулінг та особистий простір",
    18:"ПДР — Правила дорожнього руху",
    173:"Використання читів та багів",
    184:"Службові обов’язки",
    224:"Рейди",
    235:"Non-RP поведінка",
    239:"RP-процес",
    292:"Green zone",
    333:"Поширення ворожої пропаганди",
    345:"Тимчасове привласнення території",
    397:"Партнерські шлюби / ДАРШ",
    442:"Зброя",
    479:"Безпека та OOC-поведінка",
    498:"КПП та блокпости",
    524:"Правоохоронні органи",
    596:"Майно",
    612:"Корупція",
    632:"Продаж контрабанди",
    640:"Суд",
    656:"Зовнішній вигляд",
    675:"Проведення мирних мітингів/протестів",
    684:"ТАКСІ",
    701:"Порушення Конституції сервера",
}
criminal_headings = {
    707:"Розділ №1 (Пограбування)",
    728:"Розділ №2 (Завдання шкоди здоров'ю)",
    752:"Розділ №3 (Майно)",
    762:"Розділ №4 (Правила дорожнього руху)",
    766:"Розділ №5 (Додаткові статті)",
}
constitution_headings = {
    778:"1. Основні положення",
    790:"2. Засновник та Власник Сервера",
    802:"3. Органи законної влади",
    816:"4. Суд",
    832:"5. Права та обов'язки",
    843:"6. Зміни та редагування",
    851:"7. Підприємництво та праця",
    863:"8. Відповідальність, компенсації і статус новачків",
    885:"9. Мерія",
    896:"10. Затримані та арештовані",
    909:"11. Журналістика, преса та контентмейкерство",
}

def inject_breaks(text):
    # Preserve original wording but visually separate concatenated sanctions.
    text = re.sub(r"(Покарання\s*[-–:])", r"\n\1", text)
    text = re.sub(r"(Автоматичне покарання\s*[-–:])", r"\n\1", text)
    return text.strip()

def render_inline(text):
    esc = html.escape(inject_breaks(text))
    parts = esc.split("\n")
    chunks=[]
    for part in parts:
        st=part.strip()
        if not st: continue
        if re.match(r"^(Покарання|Автоматичне покарання|Покарання за|Покарання для)", st, re.I):
            chunks.append(f'<div class="penalty">{st}</div>')
        elif st.startswith("→"):
            chunks.append(f'<div class="example-line">{st}</div>')
        elif st.startswith(("Стаття ", "1.", "2.", "3.", "4.", "5.", "6.", "7.", "8.", "9.", "10.", "11.")) and len(st)<220:
            chunks.append(f'<div class="article-title">{st}</div>')
        else:
            chunks.append(f'<p>{st}</p>')
    return "".join(chunks)

def sectionize(start, end, heading_map):
    boundary = sorted(heading_map)
    sections=[]
    for idx, hline in enumerate(boundary):
        s = max(start, hline)
        e = (boundary[idx+1]-1) if idx+1 < len(boundary) else end
        title = heading_map[hline]
        raw = [x for x in lines[s-1:e] if x.strip()]
        # Remove duplicated exact heading from body.
        body = raw[1:] if raw and raw[0].strip() == title else raw
        sections.append((title, body))
    return sections

all_sections = {
    "rules": sectionize(1,706,rules_headings),
    "criminal": sectionize(707,777,criminal_headings),
    "constitution": sectionize(778,len(lines),constitution_headings),
}

def count_articles(sections):
    return sum(1 for _, body in sections for x in body if re.match(r"^Стаття\s", x.strip()))

stats = {k: {"lines": sum(1 for i in range(r[0]-1,r[1]) if lines[i].strip()),
             "sections": len(all_sections[k]), "articles": count_articles(all_sections[k])}
         for k,r in ranges.items()}

def render_sections(sections):
    out=[]
    for n,(title,body) in enumerate(sections,1):
        cards=[]
        current=[]
        def flush():
            nonlocal current
            if current:
                cards.append('<article class="rule-card">'+''.join(current)+'</article>')
                current=[]
        for raw in body:
            st=raw.strip()
            if not st: continue
            if st.startswith("Стаття "):
                flush()
                current.append(f'<div class="article-title">{html.escape(st)}</div>')
            elif "Покарання" in st or st.startswith("Автоматичне покарання"):
                current.append(render_inline(st))
            elif st in ["Приклад порушення","Правильний приклад","Приклад правильного позначення території",
                        "СУДОВИЙ БОТ","ПЕРЕЙТИ ДО БОТА","ПЕРЕГЛЯНУТИ ЦІНИ","ОТРИМАТИ ЛІЦЕНЗІЮ"]:
                current.append(f'<div class="label-chip">{html.escape(st)}</div>')
            elif st.startswith("→"):
                current.append(f'<div class="example-line">{html.escape(st)}</div>')
            else:
                if current:
                    current.append(f'<p>{html.escape(st)}</p>')
                else:
                    cards.append(f'<div class="text-row">{html.escape(st)}</div>')
        flush()
        out.append(f'''
        <section class="chapter" id="sec-{n}">
          <div class="chapter-head">
            <div class="chapter-index">{n:02d}</div>
            <div><div class="kicker">РОЗДІЛ</div><h2>{html.escape(title)}</h2></div>
          </div>
          <div class="chapter-body">{''.join(cards)}</div>
        </section>''')
    return ''.join(out)

page_defs = {
    "rules": ("Правила", "RP-правила, ПДР, службові правила та інші положення сервера.", "📋", "Правила сервера"),
    "criminal": ("Кримінальний кодекс", "ККС — статті, склади правопорушень та покарання.", "⚖️", "ККС"),
    "constitution": ("Конституція", "Права, обов’язки, суд, влада та порядок змін Конституції.", "🏛️", "Конституція"),
}

outdir = Path("/mnt/data/kks_lawbook_v2")
if outdir.exists(): shutil.rmtree(outdir)
outdir.mkdir(parents=True)

css = r"""
:root{--bg:#070a10;--panel:#0e141f;--panel2:#121a28;--line:#243246;--text:#f6f8fb;--muted:#93a1b7;--accent:#f4bd4e;--blue:#6e92ff;--danger:#ff7484;--good:#7bdcb5}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;background:radial-gradient(900px 500px at 90% -10%,rgba(244,189,78,.12),transparent 60%),radial-gradient(800px 500px at 0% 15%,rgba(110,146,255,.10),transparent 60%),var(--bg);color:var(--text);font-family:Inter,system-ui,-apple-system,Segoe UI,Arial,sans-serif}
a{color:inherit;text-decoration:none}.app{min-height:100vh}.topbar{position:sticky;top:0;z-index:20;backdrop-filter:blur(18px);background:rgba(7,10,16,.82);border-bottom:1px solid rgba(255,255,255,.08)}
.topbar-in{width:min(1440px,100%);margin:auto;padding:14px 20px;display:flex;align-items:center;gap:18px}.logo{font-weight:1000;letter-spacing:.08em}.logo span{color:var(--accent)}.nav{display:flex;gap:8px;margin-left:auto;flex-wrap:wrap}.nav a{padding:9px 12px;border:1px solid transparent;border-radius:11px;color:#b7c2d2;font-size:13px;font-weight:800}.nav a:hover,.nav a.active{background:rgba(255,255,255,.05);border-color:var(--line);color:#fff}.source{font-size:11px;color:var(--muted)}
.wrap{width:min(1180px,100%);margin:auto;padding:0 18px}.hero{padding:52px 0 28px}.badge{display:inline-flex;gap:8px;align-items:center;padding:7px 10px;border:1px solid rgba(244,189,78,.25);border-radius:999px;color:var(--accent);font-size:10px;font-weight:950;letter-spacing:.15em}.hero h1{font-size:clamp(40px,7vw,76px);line-height:.95;letter-spacing:-.055em;max-width:1000px;margin:14px 0}.hero p{color:var(--muted);max-width:780px;font-size:17px}.stats{display:flex;gap:10px;flex-wrap:wrap;margin:24px 0}.stat{padding:10px 12px;border:1px solid var(--line);border-radius:12px;background:rgba(14,20,31,.72);color:#c7d0de;font-size:12px}.stat b{color:#fff}.layout{display:grid;grid-template-columns:260px 1fr;gap:18px;align-items:start}.side{position:sticky;top:85px;max-height:calc(100vh - 105px);overflow:auto;padding:14px;border:1px solid var(--line);border-radius:18px;background:rgba(14,20,31,.76)}.side-title{font-size:10px;color:var(--muted);font-weight:950;letter-spacing:.16em;margin:2px 4px 10px}.side a{display:block;padding:9px 10px;border-radius:9px;color:#aeb9ca;font-size:12px}.side a:hover{background:rgba(255,255,255,.05);color:#fff}.chapter{margin-bottom:16px;border:1px solid var(--line);border-radius:20px;background:rgba(14,20,31,.80);overflow:visible;box-shadow:0 18px 55px rgba(0,0,0,.20)}.chapter-head{display:flex;gap:14px;align-items:center;padding:19px 20px;border-bottom:1px solid var(--line);background:linear-gradient(135deg,rgba(110,146,255,.08),transparent)}.chapter-index{width:38px;height:38px;display:grid;place-items:center;border-radius:11px;border:1px solid rgba(244,189,78,.25);color:var(--accent);font-weight:1000;font-size:12px}.kicker{font-size:9px;letter-spacing:.16em;color:#718098;font-weight:950}.chapter h2{margin:2px 0 0;font-size:21px;line-height:1.2}.chapter-body{padding:16px 18px}.text-row{padding:7px 4px;color:#d7dfeb;line-height:1.75}.rule-card{margin:10px 0;padding:15px 16px;border:1px solid rgba(255,255,255,.07);border-left:3px solid var(--blue);border-radius:14px;background:linear-gradient(135deg,rgba(255,255,255,.035),rgba(255,255,255,.015));height:auto;min-height:0;overflow:visible}.rule-card p{margin:7px 0;color:#d0d8e5;line-height:1.78;white-space:normal;overflow:visible;max-height:none}.article-title{font-size:16px;line-height:1.45;font-weight:950;color:#fff;margin-bottom:7px;white-space:normal;overflow:visible}.penalty{margin-top:10px;padding:10px 12px;border-radius:10px;border:1px solid rgba(255,116,132,.23);background:rgba(255,116,132,.075);color:#ffb2bd;font-weight:850;line-height:1.65;white-space:normal}.example-line{margin-top:8px;padding:9px 11px;border-radius:10px;background:rgba(110,146,255,.08);border:1px solid rgba(110,146,255,.18);color:#bcd0ff;font-weight:750}.label-chip{display:inline-block;margin-top:7px;padding:5px 8px;border-radius:999px;background:rgba(255,255,255,.05);border:1px solid var(--line);font-size:10px;color:#9eabc0;font-weight:900}.searchbar{display:flex;gap:10px;position:sticky;top:76px;z-index:10;padding:12px 0;background:linear-gradient(var(--bg) 70%,transparent)}.searchbar input{flex:1;padding:13px 14px;border-radius:13px;background:#0b111b;border:1px solid var(--line);color:#fff;font-size:14px}.searchbar input:focus{outline:none;border-color:var(--accent)}.searchinfo{padding:12px 0;color:var(--muted);font-size:12px}.hide{display:none!important}.footer{padding:44px 0 70px;text-align:center;color:#6f7d92;font-size:11px}@media(max-width:900px){.layout{grid-template-columns:1fr}.side{position:relative;top:auto;max-height:none;display:flex;gap:7px;overflow:auto}.side-title{display:none}.side a{white-space:nowrap}.source{display:none}}@media(max-width:620px){.nav{width:100%;margin-left:0}.topbar-in{flex-wrap:wrap}.hero{padding-top:34px}.chapter-head{padding:15px}.chapter-body{padding:13px}.rule-card{padding:13px}.searchbar{top:117px}.hero p{font-size:15px}}
"""

js = r"""
const input=document.querySelector('#search');
const chapters=[...document.querySelectorAll('.chapter')];
const count=document.querySelector('#resultCount');
function apply(){
  const q=(input?.value||'').trim().toLowerCase();
  let visible=0;
  chapters.forEach(c=>{
    const ok=!q || c.innerText.toLowerCase().includes(q);
    c.classList.toggle('hide',!ok);
    if(ok) visible++;
  });
  if(count) count.textContent=`Показано розділів: ${visible} із ${chapters.length}`;
}
input?.addEventListener('input',apply);apply();
document.querySelectorAll('.side a').forEach(a=>a.addEventListener('click',()=>setTimeout(()=>{},0)));
"""

def page_html(key):
    title, desc, icon, navname = page_defs[key]
    active = key
    side = "".join(f'<a href="#sec-{i}">{html.escape(title)}</a>' for i,(title,_) in enumerate(all_sections[key],1))
    return f"""<!doctype html><html lang="uk"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>ККС LAWBOOK — {html.escape(title)}</title><link rel="stylesheet" href="style.css"></head><body><div class="app">
<header class="topbar"><div class="topbar-in"><a class="logo" href="index.html">ККС <span>LAWBOOK</span></a>
<nav class="nav"><a class="{active=='rules' and 'active' or ''}" href="rules.html">📋 Правила</a><a class="{active=='constitution' and 'active' or ''}" href="constitution.html">🏛️ Конституція</a><a class="{active=='criminal' and 'active' or ''}" href="criminal.html">⚖️ Кримінальний кодекс</a></nav><div class="source">SOURCE: document (8).txt</div></div></header>
<main class="wrap"><section class="hero"><div class="badge">{icon} {html.escape(navname.upper())}</div><h1>{html.escape(title)}</h1><p>{html.escape(desc)} Текст взято без заміни змісту з наданого документа.</p>
<div class="stats"><div class="stat">Розділів: <b>{stats[key]['sections']}</b></div><div class="stat">Статей: <b>{stats[key]['articles']}</b></div><div class="stat">Рядків джерела: <b>{stats[key]['lines']}</b></div></div></section>
<div class="searchbar"><input id="search" placeholder="Пошук по цьому розділу..."></div><div id="resultCount" class="searchinfo"></div>
<div class="layout"><aside class="side"><div class="side-title">НАВІГАЦІЯ</div>{side}</aside><section>{render_sections(all_sections[key])}</section></div></main>
<footer class="footer">ККС LAWBOOK • Окремі сторінки • Весь вміст сформований із наданого файлу</footer></div><script src="script.js"></script></body></html>"""

for key in page_defs:
    (outdir/f"{key}.html").write_text(page_html(key),encoding="utf-8")

index = """<!doctype html><html lang="uk"><head><meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1"><title>ККС LAWBOOK</title><link rel="stylesheet" href="style.css">
<style>.cards{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}.home-card{padding:23px;border:1px solid var(--line);border-radius:20px;background:rgba(14,20,31,.8)}.home-card .ico{font-size:28px}.home-card h2{margin:9px 0 4px}.home-card p{color:var(--muted);font-size:13px}.go{display:inline-block;margin-top:9px;color:var(--accent);font-weight:900;font-size:12px}@media(max-width:820px){.cards{grid-template-columns:1fr}}</style></head>
<body><div class="app"><header class="topbar"><div class="topbar-in"><a class="logo" href="index.html">ККС <span>LAWBOOK</span></a><nav class="nav"><a href="rules.html">📋 Правила</a><a href="constitution.html">🏛️ Конституція</a><a href="criminal.html">⚖️ Кримінальний кодекс</a></nav><div class="source">RP SERVER</div></div></header>
<main class="wrap"><section class="hero"><div class="badge">ОФІЦІЙНИЙ ДОВІДНИК</div><h1>Правила сервера — по поличках.</h1><p>Три повноцінні сторінки: правила, Конституція та Кримінальний кодекс. Дані структуровані з твого документа без вигадування відсутніх статей.</p></section>
<div class="cards">
<div class="home-card"><div class="ico">📋</div><h2>Правила</h2><p>{stats['rules']['sections']} розділів • {stats['rules']['articles']} статей • {stats['rules']['lines']} рядків джерела</p><a class="go" href="rules.html">Відкрити →</a></div>
<div class="home-card"><div class="ico">🏛️</div><h2>Конституція</h2><p>{stats['constitution']['sections']} розділів • {stats['constitution']['articles']} статей • {stats['constitution']['lines']} рядків джерела</p><a class="go" href="constitution.html">Відкрити →</a></div>
<div class="home-card"><div class="ico">⚖️</div><h2>Кримінальний кодекс</h2><p>{stats['criminal']['sections']} розділів • {stats['criminal']['articles']} статей • {stats['criminal']['lines']} рядків джерела</p><a class="go" href="criminal.html">Відкрити →</a></div>
</div>
<footer class="footer">ККС LAWBOOK • Створено на основі document (8).txt</footer></main></div></body></html>"""
(outdir/"index.html").write_text(index,encoding="utf-8")
(outdir/"style.css").write_text(css,encoding="utf-8")
(outdir/"script.js").write_text(js,encoding="utf-8")

zip_path = Path("/mnt/data/kks_lawbook_v2.zip")
with zipfile.ZipFile(zip_path,"w",zipfile.ZIP_DEFLATED) as z:
    for f in outdir.iterdir():
        z.write(f, f.name)

print("Готово:", zip_path)
print(stats)
