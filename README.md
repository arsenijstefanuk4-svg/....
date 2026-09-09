<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Повний збірник правил — UKRAINE RP | Emergency Hamburg</title>
    <style>
        * { box-sizing: border-box; }
        body { font-family: 'Segoe UI', Arial, sans-serif; background-color: #121212; color: #e0e0e0; margin: 0; padding: 20px; }
        .container { max-width: 1000px; margin: 0 auto; }
        h1 { text-align: center; color: #0057b7; margin-bottom: 5px; }
        .subtitle { text-align: center; color: #ffd700; margin-bottom: 25px; font-size: 16px; }
        .controls { display: flex; gap: 10px; margin-bottom: 20px; }
        #searchBar { flex: 1; padding: 12px; border-radius: 6px; border: 1px solid #333; background-color: #1e1e1e; color: #fff; font-size: 16px; }
        #toggleBtn { padding: 12px 20px; border-radius: 6px; border: none; background-color: #0057b7; color: #fff; font-size: 16px; cursor: pointer; font-weight: bold; transition: 0.2s; }
        #toggleBtn:hover { background-color: #00428c; }
        .accordion { background-color: #1e1e1e; color: #fff; cursor: pointer; padding: 16px 20px; width: 100%; border: none; text-align: left; outline: none; font-size: 18px; transition: 0.3s; border-radius: 6px; margin-top: 10px; font-weight: bold; display: flex; justify-content: space-between; align-items: center; border-left: 5px solid #0057b7; }
        .active, .accordion:hover { background-color: #2a2a2a; border-left: 5px solid #ffd700; }
        .accordion::after { content: '\02795'; font-size: 12px; }
        .active::after { content: "\2796"; }
        .panel { padding: 0 20px; background-color: #181818; max-height: 0; overflow: hidden; transition: max-height 0.3s ease-out; border-radius: 0 0 6px 6px; }
        .panel h3 { color: #ffd700; margin-top: 20px; border-bottom: 1px solid #333; padding-bottom: 5px; }
        .panel ul { list-style-type: none; padding-left: 0; margin: 15px 0; }
        .panel li { padding: 10px 0; border-bottom: 1px solid #282828; line-height: 1.5; }
        .panel li:last-child { border-bottom: none; }
        .badge { background-color: #d9534f; color: #fff; padding: 3px 8px; border-radius: 4px; font-size: 13px; font-weight: bold; margin-left: 8px; display: inline-block; }
        .badge-warn { background-color: #f0ad4e; color: #fff; padding: 3px 8px; border-radius: 4px; font-size: 13px; font-weight: bold; margin-left: 8px; display: inline-block; }
        .badge-info { background-color: #5bc0de; color: #fff; padding: 3px 8px; border-radius: 4px; font-size: 13px; font-weight: bold; margin-left: 8px; display: inline-block; }
    </style>
</head>
<body>

<div class="container">
    <h1>UKRAINE RP | Emergency Hamburg</h1>
    <div class="subtitle">Повна Конституція, Загальні Правила (1-23), Кримінальний Кодекс та Службові Регламенти</div>

    <div class="controls">
        <input type="text" id="searchBar" placeholder="Введіть правило, статтю чи покарання для пошуку..." onkeyup="filterRules()">
        <button id="toggleBtn" onclick="toggleAll()">Розгорнути все</button>
    </div>

    <!-- 1. ПОАВГА ТА АНТИБУЛІНГ -->
    <button class="accordion">1. Повага, антибулінг та особистий простір</button>
    <div class="panel">
        <ul>
            <li><b>1.1. Токсичність та образи:</b> Заборонено використання нецензурної лексики, образи гравців у надмірній формі або провокації на конфлікт. <span class="badge-info">Mute 30-60 хв</span></li>
            <li><b>1.2. Булінг та цькування:</b> Заборонено цілеспрямоване переслідування чи цькування конкретного гравця/групи осіб. <span class="badge">Mute 120 хв / Ban 3 дні</span></li>
            <li><b>1.3. Дискримінація:</b> Заборонено будь-які прояви сексизму, расизму, націоналізму чи дискримінації за будь-якими ознаками. <span class="badge">Ban 7-14 днів</span></li>
            <li><b>1.4. Образа родичів:</b> Згадка або пряма/прихована образа батьків чи родичів у негативному контексті. <span class="badge">Ban 7-30 днів</span></li>
        </ul>
    </div>

    <!-- 2. ПДР -->
    <button class="accordion">2. Правила дорожнього руху (ПДР)</button>
    <div class="panel">
        <ul>
            <li><b>2.1. Рух по смугах:</b> Виїзд на зустрічну смугу руху без увімкнених спецсигналів або обґрунтованої RP-причини. <span class="badge-info">Штраф 5,000₴ / Деморган 15 хв</span></li>
            <li><b>2.2. NRD (NonRP Drive):</b> Водіння по тротуарах, залізничних коліях, горах чи полях на непідготовленому транспорті. <span class="badge-info">Деморган 30 хв</span></li>
            <li><b>2.3. VDM / DB (Vehicle Deathmatch):</b> Умисний таран інших авто, наїзд на пішоходів або вбивство за допомогою ТЗ. <span class="badge">Деморган 60-120 хв</span></li>
            <li><b>2.4. Перевищення швидкості:</b> Рух зі швидкістю понад 120 км/год у межах населеного пункту. <span class="badge-info">Штраф 3,000₴ - 10,000₴</span></li>
            <li><b>2.5. Створення аварійної ситуації:</b> Різке гальмування, підрізання чи блокування смуг руху. <span class="badge-info">Штраф / Деморган 20 хв</span></li>
        </ul>
    </div>

    <!-- 3. ЧИТИ ТА БАГИ -->
    <button class="accordion">3. Використання читів та багів</button>
    <div class="panel">
        <ul>
            <li><b>3.1. Сторонній софт (Чити):</b> Використання будь-яких сторонніх програм, скриптів чи модифікацій, що надають перевагу у грі. <span class="badge">Пермабан (Бан назавжди) + ЧС</span></li>
            <li><b>3.2. Багоюз:</b> Використання помилок та недоробок текстур/функціоналу гри задля вигоди чи шкоди іншим. <span class="badge">Деморган 120 хв / Ban 7 днів</span></li>
            <li><b>3.3. Приховування багів:</b> Неповідомлення адміністрації про знайдені критичні баги. <span class="badge-warn">Warn / Ban 3 дні</span></li>
        </ul>
    </div>

    <!-- 4. СЛУЖБОВІ ОБОВ'ЯЗКИ -->
    <button class="accordion">4. Службові обов'язки держструктур</button>
    <div class="panel">
        <ul>
            <li><b>4.1. Прогул зміни:</b> Перебування у робочій формі під час виконання власних справ чи фарму грошей. <span class="badge-warn">Догана / Звільнення</span></li>
            <li><b>4.2. Невиконання наказів:</b> Ігнорування законних розпоряджень вищого керівництва організації. <span class="badge-warn">Догана / Warn</span></li>
            <li><b>4.3. Використання спецзасобів/зброї не за призначенням:</b> Безпідставне застосування кайданків, тайзера або зброї. <span class="badge">Деморган 60 хв / Warn</span></li>
        </ul>
    </div>

    <!-- 5. РЕЙДИ -->
    <button class="accordion">5. Правила проведення рейдів</button>
    <div class="panel">
        <ul>
            <li><b>5.1. Санкція на рейд:</b> Проведення рейдів об'єктів/територій банд без затвердженого судового ордера чи дозволу Прокуратури. <span class="badge-warn">Warn лідеру / Скасування ситуації</span></li>
            <li><b>5.2. Кількісний склад:</b> Виїзд на рейд у кількості менше ніж 4 працівники спецпідрозділів. <span class="badge">Деморган 60 хв</span></li>
            <li><b>5.3. Правило RK під час рейду:</b> Повернення на місце проведення рейду після смерті. <span class="badge">Деморган 90 хв</span></li>
        </ul>
    </div>

    <!-- 6. NON-RP ПОВЕДІНКА -->
    <button class="accordion">6. Non-RP поведінка (НонРП)</button>
    <div class="panel">
        <ul>
            <li><b>6.1. Non-RP дії:</b> Дії, що суперечать реалістичній поведінці та здоровому глузду. <span class="badge-info">Деморган 30-60 хв</span></li>
            <li><b>6.2. PG (PowerGaming):</b> Зображення з себе "супергероя" (наприклад, вихід 1 в 3 або напад з кулаками на озброєну людину). <span class="badge">Деморган 60 хв</span></li>
            <li><b>6.3. RK (Revenge Kill):</b> Вбивство або спроба вбити гравця, який вас перед цим убив (повернення протягом 15 хв). <span class="badge">Деморган 60 хв</span></li>
            <li><b>6.4. FearRP:</b> Відсутність страху за життя свого персонажа при дулі пістолета чи прямому нападі. <span class="badge">Деморган 45 хв</span></li>
            <li><b>6.5. Leave from RP (Ухід від RP):</b> Вихід з гри, перехід у Зелену Зону або афк під час арешту/перестрілки. <span class="badge">Warn / Ban 3 дні</span></li>
        </ul>
    </div>

    <!-- 7. GREEN ZONE -->
    <button class="accordion">7. Green Zone (Зелена Зона)</button>
    <div class="panel">
        <ul>
            <li><b>7.1. Стрільба в ЗЗ (Shoot in GZ):</b> Відкриття вогню з будь-якої зброї на території спавнів, лікарень, мерії, автосалонів. <span class="badge">Деморган 90 хв / Warn</span></li>
            <li><b>7.2. Кримінал у ЗЗ:</b> Проведення грабунків, викрадень чи нанесення шкоди на території ЗЗ. <span class="badge">Warn</span></li>
            <li><b>7.3. Сховування в ЗЗ:</b> Втеча від переслідування чи перестрілки на територію Зеленої Зони. <span class="badge">Деморган 60 хв / Warn</span></li>
        </ul>
    </div>

    <!-- 8. ВОРОЖА ПРОПАГАНДА -->
    <button class="accordion">8. Поширення ворожої пропаганди</button>
    <div class="panel">
        <ul>
            <li><b>8.1. Ворожа символіка:</b> Використання символів агресії, гербів, прапорів чи текстів окупантів. <span class="badge">Пермабан</span></li>
            <li><b>8.2. Висловлювання та розпалювання:</b> Публічна висловлена підтримка дій держави-агресора у голосовому чи текстовому чатах. <span class="badge">Пермабан + ЧС</span></li>
        </ul>
    </div>

    <!-- 9. ТИМЧАСОВЕ ПРИВЛАСНЕННЯ ТЕРИТОРІЇ -->
    <button class="accordion">9. Тимчасове привласнення території</button>
    <div class="panel">
        <ul>
            <li><b>9.1. Незаконне перекриття:</b> Блокування доріг, мостів чи районів без погодженої RP-ситуації. <span class="badge">Деморган 45 хв</span></li>
            <li><b>9.2. Часові рамки:</b> Захоплення території злочинними угрупованнями не може тривати понад 45 хвилин без виклику сил поліції. <span class="badge-warn">Warn</span></li>
        </ul>
    </div>

    <!-- 10. ПАРТНЕРСЬКІ ШЛЮБИ -->
    <button class="accordion">10. Партнерські шлюби (ДАРШ)</button>
    <div class="panel">
        <ul>
            <li><b>10.1. Реєстрація:</b> Усі шлюби повинні фіксуватися офіційно через орган ДАРШ та подачу заявки.</li>
            <li><b>10.2. Фейкові шлюби:</b> Укладання шлюбів з метою абузу ігрових систем майна чи передачі валюти. <span class="badge">Анулювання + Штраф</span></li>
        </ul>
    </div>

    <!-- 11. ЗБРОЯ -->
    <button class="accordion">11. Правила поводження зі зброєю</button>
    <div class="panel">
        <ul>
            <li><b>11.1. Відкрите носіння:</b> Перебування у людних місцях з оголеною зброєю без наявності ліцензії чи загрози життю. <span class="badge-info">Конфіскація + Штраф</span></li>
            <li><b>11.2. DM (DeathMatch):</b> Вбивство чи нанесення шкоди без будь-якої діалогової чи ігрової RP-причини. <span class="badge">Деморган 60-120 хв</span></li>
            <li><b>11.3. Mass DM:</b> Умисне вбивство 3 і більше гравців без RP-причини. <span class="badge">Ban 3-7 днів</span></li>
        </ul>
    </div>

    <!-- 12. БЕЗПЕКА ТА OOC -->
    <button class="accordion">12. Безпека та OOC-поведінка</button>
    <div class="panel">
        <ul>
            <li><b>12.1. MG (MetaGaming):</b> Використання інформації з OOC (Discord, чати, стріми) у IC-грі. <span class="badge-info">Mute 30 хв / Деморган 30 хв</span></li>
            <li><b>12.2. Перенос конфліктів:</b> Перенесення особистих образ з діскорду в ігровий процес персонажа. <span class="badge">Mute 60 хв</span></li>
        </ul>
    </div>

    <!-- 13. КПП ТА БЛОКПОСТИ -->
    <button class="accordion">13. КПП та блокпости</button>
    <div class="panel">
        <ul>
            <li><b>13.1. Легітимність блокпоста:</b> Блокпости дозволено виставляти лише за наявності старшого офіцера та спецтехніки. <span class="badge-warn">Догана</span></li>
            <li><b>13.2. Таран КПП:</b> Прорив через шлагбаум чи перекриття блокпоста на швидкості. <span class="badge">Деморган 60 хв</span></li>
        </ul>
    </div>

    <!-- 14. ПРАВООХОРОННІ ОРГАНИ -->
    <button class="accordion">14. Поведінка з правоохоронцями</button>
    <div class="panel">
        <ul>
            <li><b>14.1. Непідкорення:</b> Відмова показати документи або виконати законну вимогу вийти з авто. <span class="badge-info">Арешт (1-2 зірки)</span></li>
            <li><b>14.2. Провакація поліції:</b> Навмисне підрізання, сигнали чи образи держслужбовців ради погоні. <span class="badge">Деморган 40 хв</span></li>
        </ul>
    </div>

    <!-- 15. МАЙНО -->
    <button class="accordion">15. Передача та купівля майна</button>
    <div class="panel">
        <ul>
            <li><b>15.1. Non-RP Обман:</b> Обман гравців при продажу авто, предметів чи послуг. <span class="badge">Ban 14-30 днів + Вилучення</span></li>
            <li><b>15.2. Продаж за реальні гроші (RMT):</b> Спроба або продаж ігрових цінностей за реальні гроші. <span class="badge">Пермабан з обнуленням</span></li>
        </ul>
    </div>

    <!-- 16. КОРУПЦІЯ -->
    <button class="accordion">16. Корупційна діяльність</button>
    <div class="panel">
        <ul>
            <li><b>16.1. Покривання злочинців:</b> Випущення з-під варти або видалення зі списку розшуку без RP-розслідування. <span class="badge-warn">Warn / Звільнення</span></li>
            <li><b>16.2. Ліміт хабаря:</b> Сума хабаря не може перевищувати 20,000₴ за одну ситуацію. <span class="badge">Деморган 60 хв</span></li>
        </ul>
    </div>

    <!-- 17. ПРОДАЖ КОНТРАБАНДИ -->
    <button class="accordion">17. Продаж контрабанди</button>
    <div class="panel">
        <ul>
            <li><b>17.1. Торгівля на спавні:</b> Продаж зброї чи нелегалу на центральних вулицях/спавнах. <span class="badge">Деморган 60 хв</span></li>
            <li><b>17.2. Конфіскація:</b> У разі затримання вся контрабанда повністю вилучається співробітниками НПС чи СБС.</li>
        </ul>
    </div>

    <!-- 18. СУД -->
    <button class="accordion">18. Судова система</button>
    <div class="panel">
        <ul>
            <li><b>18.1. Неявка на засідання:</b> Прогул судового слухання відповідачем чи позивачем без поважної причини. <span class="badge-info">Програш справи + Штраф</span></li>
            <li><b>18.2. Неповага до суду:</b> Перебивання, лайка або неадекватна поведінка у залі засідань. <span class="badge">Арешт за неувагу / Штраф</span></li>
        </ul>
    </div>

    <!-- 19. ЗОВНІШНІЙ ВИГЛЯД -->
    <button class="accordion">19. Зовнішній вигляд персонажа</button>
    <div class="panel">
        <ul>
            <li><b>19.1. Non-RP Скіни:</b> Використання неетичних, гігантських або невидимих скінів та аксесуарів. <span class="badge-info">Kick / Деморган 15 хв</span></li>
            <li><b>19.2. Форма держслужбовців:</b> Носіння цивільними особами одягу, що повністю копіює форму поліції чи ДСНС. <span class="badge-info">Арешт / Штраф</span></li>
        </ul>
    </div>

    <!-- 20. ОЗУ -->
    <button class="accordion">20. Правила ОЗУ (Банди/Картелі)</button>
    <div class="panel">
        <ul>
            <li><b>20.1. Союз угруповань:</b> Укладання союзів між понад 2 бандами для масового терору міста. <span class="badge-warn">Догана лідерам</span></li>
            <li><b>20.2. Напад на інкасаторів:</b> Напад дозволений лише за наявності мінімум 3 осіб у масках та зі зброєю. <span class="badge">Деморган 60 хв</span></li>
        </ul>
    </div>

    <!-- 21. МІТИНГИ ТА ПРОТЕСТИ -->
    <button class="accordion">21. Мирні мітинги та протести</button>
    <div class="panel">
        <ul>
            <li><b>21.1. Узгодження:</b> Будь-який мітинг повинен мати організатора та бути узгоджений за 2 години з Мерією. <span class="badge">Розгін силами КОРД</span></li>
            <li><b>21.2. Збройний протест:</b> Використання вогнепальної зброї під час мирного мітингу автоматично переводить його у статус масових заворушень. <span class="badge">Арешт</span></li>
        </ul>
    </div>

    <!-- 22. ТАКСІ -->
    <button class="accordion">22. Правила служби ТАКСІ</button>
    <div class="panel">
        <ul>
            <li><b>22.1. Відмова від виклику:</b> Безпідставне скидання прийнятого замовлення. <span class="badge-info">Штраф компанії</span></li>
            <li><b>22.2. Пограбування таксистів:</b> Заборонено грабувати гравців, які працюють на роботі Таксі. <span class="badge">Деморган 60 хв</span></li>
        </ul>
    </div>

    <!-- 23. КОНСТИТУЦІЯ СЕРВЕРА -->
    <button class="accordion">23. Порушення Конституції сервера</button>
    <div class="panel">
        <ul>
            <li><b>Стаття 1. Права людини:</b> Кожен гравець має право на недоторканність особистості, захист у суді та захист від свавілля держслужбовців.</li>
            <li><b>Стаття 2. Рівність перед законом:</b> Жоден гравець, незалежно від донат-статусу чи посади, не має імунітету від правил. <span class="badge">Звільнення / Ban</span></li>
            <li><b>Стаття 3. Презумпція невинуватості:</b> Гравець вважається невинуватим, доки його провина не буде доведена фото/відео доказами.</li>
        </ul>
    </div>

    <!-- КРИМІНАЛЬНИЙ КОДЕКС (КК) -->
    <button class="accordion">⚖️ КРИМІНАЛЬНИЙ КОДЕКС СЕРВЕРА (КК)</button>
    <div class="panel">
        <ul>
            <li><b>Стаття 1.1. Крадіжка:</b> Таємне викрадення чужого майна. <span class="badge-info">Штраф 10,000₴ / 1 рік в'язниці</span></li>
            <li><b>Стаття 1.2. Грабіж / Розбій:</b> Відкрите викрадення майна із застосуванням зброї чи погроз. <span class="badge">3 роки в'язниці</span></li>
            <li><b>Стаття 2.1. Легкі тілесні ушкодження:</b> Побиття кулаками без застосування зброї. <span class="badge-info">Штраф 5,000₴ / 1 рік в'язниці</span></li>
            <li><b>Стаття 2.2. Важкі тілесні / Замах на вбивство:</b> Нанесення поранень з вогнепальної/холодної зброї. <span class="badge">3 роки в'язниці</span></li>
            <li><b>Стаття 2.3. Вбивство службової особи:</b> Умисне позбавлення життя поліцейського, медика чи держслужбовця. <span class="badge">5 років в'язниці (Максимум)</span></li>
            <li><b>Стаття 3.1. Угон авто:</b> Незаконне заволодіння чужим транспортним засобом. <span class="badge-info">2 роки в'язниці</span></li>
            <li><b>Стаття 3.2. Пошкодження держмайна:</b> Умисний таран службових авто чи погрома будівель. <span class="badge-info">Штраф 15,000₴ / 2 роки в'язниці</span></li>
            <li><b>Стаття 4.1. Втеча від поліції:</b> Ігнорування вимог про зупинку ТЗ під час погоні. <span class="badge">2 роки в'язниці + Позбавлення прав</span></li>
            <li><b>Стаття 5.1. Нелегальна зброя:</b> Носіння зброї без ліцензії або носіння автоматичної зброї. <span class="badge">Конфіскація + 2 роки в'язниці</span></li>
            <li><b>Стаття 5.2. Проникнення на закриту територію:</b> Перебування на території ДБР, СБС чи парковки поліції без дозволу. <span class="badge">2 роки в'язниці</span></li>
        </ul>
    </div>

    <!-- РЕГЛАМЕНТ АДМІНІСТРАЦІЇ -->
    <button class="accordion">🛡️ РЕГЛАМЕНТ АДМІНІСТРАЦІЇ СЕРВЕРА</button>
    <div class="panel">
        <h3>Загальні положення</h3>
        <p>Адміністрація відповідає за дотримання порядку та підтримку RP-атмосфери. Всі дії мають бути об'єктивними, обґрунтованими та відповідати високим стандартам поведінки.</p>
        <ul>
            <li><b>1.1 - 1.2. RP-Процес:</b> Адміністратор повинен залишатися в рамках своєї ролі та не втручатися в ігровий процес без необхідності.</li>
            <li><b>2.1 - 2.2. Знання правил:</b> Зобов'язаний відмінно знати правила сервера та стежити за їх дотриманням.</li>
            <li><b>3.1 - 3.2. Доказова база:</b> Будь-яке покарання має мати фіксацію (скріншот/відео). При видачі бана обов'язково вказувати чітку причину.</li>
            <li><b>4.1 - 4.2. Заборона блатів:</b> Суворо заборонено видавати гроші, зброю чи переваги друзям або звичайним гравцям.</li>
            <li><b>5.1 - 5.2. Рівність:</b> Усі гравці рівні перед правилами незалежно від статусу чи знайомств.</li>
            <li><b>8.1 - 8.4. Команди:</b> Використання команд `/slay`, `/freeze`, `/kick`, `/ban` заради розваги — кагається зняттям з посади.</li>
            <li><b>12.1 - 12.3. За заборону нелегалу:</b> Адміністраторам заборонено перебувати у бандах чи брати участь у злочинній діяльності.</li>
        </ul>
    </div>

    <!-- НАЦІОНАЛЬНА ПОЛІЦІЯ (НПС) -->
    <button class="accordion">🚔 РЕГЛАМЕНТ НАЦІОНАЛЬНОЇ ПОЛІЦІЇ (НПС)</button>
    <div class="panel">
        <h3>Основні вимоги до поліцейського:</h3>
        <ul>
            <li>Спілкування з громадянами ведеться **виключно українською мовою**.</li>
            <li>Пред'явлення службового посвідчення на першу вимогу громадянина.</li>
            <li>Заборонено видавати штрафи або затримувати людей без наявності відеофіксації порушення.</li>
            <li>Патрулювання здійснюється екіпажем мінімум з 2 співробітників.</li>
        </ul>
        <h3>Спеціалізація підрозділів:</h3>
        <ul>
            <li><b>Patrol Police:</b> Первинний виїзд на виклики, пограбування кас/магазинів, реагування на стрільбу та затримання дрібних порушників.</li>
            <li><b>Traffic Police:</b> Контроль дотримання ПДР, швидкісні переслідування, виписування штрафів та оформлення ДТП.</li>
            <li><b>Undercover Police:</b> Таємне стеження, робота під прикриттям, збір доказів проти нелегального продажу зброї.</li>
            <li><b>КОРД / SEK:</b> Штурм будівель, затримання особливо небезпечних злочинців, звільнення заручників.</li>
        </ul>
    </div>
</div>

<script>
    var acc = document.getElementsByClassName("accordion");
    var isExpanded = false;

    for (var i = 0; i < acc.length; i++) {
        acc[i].addEventListener("click", function() {
            this.classList.toggle("active");
            var panel = this.nextElementSibling;
            if (panel.style.maxHeight) {
                panel.style.maxHeight = null;
            } else {
                panel.style.maxHeight = panel.scrollHeight + "px";
            }
        });
    }

    function toggleAll() {
        isExpanded = !isExpanded;
        var btn = document.getElementById("toggleBtn");
        btn.innerText = isExpanded ? "Згорнути все" : "Розгорнути все";

        for (var i = 0; i < acc.length; i++) {
            var panel = acc[i].nextElementSibling;
            if (isExpanded) {
                acc[i].classList.add("active");
                panel.style.maxHeight = panel.scrollHeight + "px";
            } else {
                acc[i].classList.remove("active");
                panel.style.maxHeight = null;
            }
        }
    }

    function filterRules() {
        var input = document.getElementById("searchBar").value.toLowerCase();
        var accordions = document.getElementsByClassName("accordion");

        for (var i = 0; i < accordions.length; i++) {
            var panel = accordions[i].nextElementSibling;
            var items = panel.querySelectorAll("li, p");
            var hasMatch = false;

            for (var j = 0; j < items.length; j++) {
                var text = items[j].innerText.toLowerCase();
                if (text.includes(input)) {
                    items[j].style.display = "";
                    hasMatch = true;
                } else if (input !== "") {
                    items[j].style.display = "none";
                } else {
                    items[j].style.display = "";
                }
            }

            if (hasMatch || input === "") {
                accordions[i].style.display = "";
                if (input !== "") {
                    accordions[i].classList.add("active");
                    panel.style.maxHeight = panel.scrollHeight + "px";
                }
            } else {
                accordions[i].style.display = "none";
                panel.style.maxHeight = null;
            }
        }
    }
</script>

</body>
</html>
