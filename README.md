# ukrainian_law_data_analysis
Робота присвячена аналізу динаміки законотворчого процесу в Україні з використанням статистичних методів. Головною метою дослідження є розгляд етапів проходження законопроєктів та встановлення факторів, що впливають на динаміку.

Конкретні завдання дослідження: визначення тривалості проходження законопроєктів крізь усі стадії законодавчого процесу; вивчення чинників, що впливають на тривалість законотворчого процесу; аналіз результатів та виявлення основних недоліків законотворчого процесу в Україні. 

Актуальність цієї теми зумовлена необхідністю вдосконалення законотворчого процесу в Україні. За даними VoxUkraine, лише 16,8 % від усіх зареєстрованих законопроєктів успішно проходить усі етапи законодавчого процесу і стають законами.
Для порівняння, у Польщі ця цифра становить 63,2 %, а у Великобританії — 77,2 %. Такий розрив у статистиці вказує на наявність проблем та важливість підвищення ефективності роботи законотворчої сторони України.

Для обробки даних використовуються методи тематичного моделювання, такі як TF-IDF, LDA.  Для аналізу зібраних даних використовуються статистичні методи, такі як кореляційний аналіз, перевірка гіпотез, групування даних та інші. Ці методи дозволяють виявити залежності, провести статистичну оцінку та розрахунки.
Робота складається з чотирьох частин.

У першому розділі наведено загальну характеристику законотворчої системи України. Розподілено процес на основні етапи та схарактеризовано кожен з них. Встановлено можливі недоліки та проблемні місця для подальшого їх глибшого аналізу.

У другому розділі наведено опис методології, основні принципи роботи, недоліки та переваги обраних інструментів. Надано короткий опис статистичних інструментів.
Третій розділ присвячено практичній частині роботи: описано дані, їх обробку та проміжні результати.

Четвертий розділ описує інтерпретацію отриманих результатів. Наведено аналіз можливих чинників та статистичні висновки щодо результатів. Сформовані рекомендації задля пришвидшення прийняття законопроєктів.

## Робота з даними
Для роботи над дослідженням було зібрано набір даних у форматі json, що включає в себе всю доступну інформацію про 9 скликання Верховної Ради. Багаторівневу структуру документу було зчитано та сформовано менші датафрейми з потрібною інформацією.

Робота з даними була виконана на мові Python з використанням бібліотек, таких як pandas, numpy та matplotlib.

Для обробки текстових даних необхідно виконати передпроцесинг. Для цього за допомогою функції preprocess_first дані було очищено від стоп-слів, пунктуації та нумерації. Надалі для стемінгу даних було використано стемер "tree_stem", який був розроблений за допомогою методів машинного навчання. 

Запропонований алгоритм не використовує пошук у словнику, при цьому має досить малу розмірність. Він працює швидше у 24 рази за підхід лематизації і перевершує інші алгоритми стемінгу за швидкістю також.
Після всіх етапів підготовки отримали такий текст:

![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/e48acdcb-d42f-4509-84d7-8302ed2c9ec1)

## Аналіз динаміки проходженння законопроєкту

### Загальна інформація

За час роботи 9 скликання Верховної Ради України всього було зареєстровано 8677 законопроєктів у період із грудня 2019 року до квітня 2023 року. З них пройшли весь етап від реєстрації до підписання закону 923 законопроєкти, що становить 10,64 % від усієї маси.

Середній час проходження законопроєктом усіх стадій до поточної — 140 днів, а для успішного отримання статусу «Закон підписано» — 204 дні, тобто в середньому в Україні закон приймають майже 30 тижнів. Згідно з Регламентом, приблизні терміни ухвалення мають становити 80 днів. Фактичний же час проходження перевищує його у 2,5 рази.
### Залежність від галузі
Розглянемо середній час проходження залежно від галузі (‘rubric’) законопроєкту. Маємо такі варіанти: 'Галузевий розвиток', 'Економічна політика', 'Правова політика', 'Установчі повноваження', 'Двосторонні міжнародні угоди', 'Державне будівництво', 'Соціальна політика', 'Організаційні питання', 'Безпека й оборона', 'Гуманітарна політика', 'Інші (заяви, звернення ВРУ)', 'Багатосторонні міжнародні угоди', 'Міжнародні угоди'. Для зручності об’єднаємо в одну категорію 'Двосторонні міжнародні угоди', 'Багатосторонні міжнародні угоди' та 'Міжнародні угоди’.

Найшвидше приймалися закони пов’язані з безпекою та обороною — середній час 104 дні, при цьому найдовше набувала чинності саме соціальна політика — у середньому 287 днів.

 ![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/8032a6f6-ea9f-40d3-befa-de87463d59c2)

Розглянемо ближче кожну галузь. Розрахуємо середню тривалість кожного етапу проходження залежно від теми політики.
 
![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/f0f5caa7-9f65-48b3-8135-2fa1b4ac3d4f)

Чітко видно, що «Установчі повноваження» та категорія «Інші» проходять ВРУ миттєво та підписуються Президентом у середньому за 4 дні, так само як і «Організаційні питання». Розгляд у парламенті в цілому відрізняється несуттєво від категорії до категорії, середній час — 154 дні, розгляд у комітеті триває 138 днів.
Принагідно, що всі етапи проходження соціальної політики на порядок довші за інші галузі, та найчастіше ветуються Президентом. Рішення парламенту займає близько 188 днів, розгляд у комітеті — 184, а розгляд після ветування — 101.

Також зазначу, що підпис Президента не перевищує дозволених 15 днів, хоча наближається максимально близько — 14 днів у середньому.
### Аналіз ухвалених та відхилених 
Розглянемо тільки законопроєкти, що вже стали законами. Для них тривалість проходження розподіляється таким чином.

 ![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/e9d7fc11-4ec5-4ac1-93e5-0091c08407e8)

55 % законопроєктів розглядаються протягом 4 місяців від дати подання, найбільша кількість була ухвалена в період від 30 до 60 днів — 137 актів.
Усього за період від 1 до 500 днів прийнято лише 89 % законів, 99 % потрапляють у часовий період до 1000 днів, що становить 2.7 роки.
Спираючись на ці дані, можемо зробити висновок, що випадково обраний законопроєкт має більшу ймовірність подолати бюрократичний процес за 6 місяців та з найбільше часу проведе саме на слуханнях Верховної Ради.

Розглянемо законопроєкти, що завершили свій шлях або негативно (остаточне відхилення) або позитивно (схвалення). Наскільки різниться їхня тривалість?
 
![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/0d1ac6cb-9210-4dfc-852f-f95357b7cf6a)

Результати t-тесту для даного прикладу є наступними:

— t-статистика: 5.64

— p-значення: 0.000000018

Щоби проаналізувати ці результати, спочатку потрібно встановити нульову гіпотезу й альтернативну гіпотезу.

Нульова гіпотеза (H0): Середні значення тривалості розгляду для відхиленої групи та прийнятої групи рівні.

Альтернативна гіпотеза (H1): Середні значення тривалості розгляду для відхиленої групи та прийнятої групи відрізняються.

p-значення 0.000000018 дозволяє відхилити нульову гіпотезу, що середні часи розгляду обох груп не відрізняються, на рівні значущості 0.05.

Отже, можна вважати, що є статистично значимі докази того, що середні значення тривалості розгляду для відхиленої групи та прийнятої групи відрізняються, прийняття законопроєкту проходить значно швидше за відхилення.

У групі прийнятих законопроєктів ми бачимо, що близько 50 % законопроєктів проходять розгляд і приймаються менше ніж за 127 днів. Крім того, 75 % прийнятих законопроєктів проходять розгляд і приймаються менше ніж за 288.5 днів.

З іншого боку, у групі відхилених законопроєктів значення медіани — 176 днів — показує, що половина відхилених проходять розгляд і відхиляються швидше, ніж цей період. Крім того, 75 % відхилених законопроєктів проходять розгляд і відхиляються швидше 369 днів.

Отже, зазначені відсоткові значення показують, що прийняті законопроєкти мають більшу швидкість проходження розгляду та прийняття в порівнянні з відхиленими законопроєктами. Відхилені законопроєкти потребують більшого часу для розгляду та вирішення їх долі.

Зважаючи на те, що прийняті мають значно меншу тривалість проходження, можна зосередити зусилля на виявленні причин відхилення та шляхів покращення ефективності процесу розгляду.

### Залежність від ініціаторів

Розглянемо залежність швидкості проходження законопроєкту від його ініціатора. Загальна кількість ініціаторів — 671, куди входять народні депутати України, представники Кабінету Міністрів та зовнішні особистості. Найбільше законів у ВР ініціюються саме Кабінетом Міністрів України, а саме Прем’єр-міністром України (Шмигаль Денис) — 657 за період 9 скликання. У середньому він ініціював один закон кожні 2.1 дні в період з липня 2019 року й до квітня 2023, якщо відкинути вихідні.
Наступний по кількості законопроєктів (650) — Мазурашу Георгій Георгійович. Представник партії «Слуга народу» та член Комітету Верховної Ради України з питань молоді і спорту. До слова, є активним противником законів про мову, вступу України в НАТО та розширення прав ЛГБТ-спільноти.

Найбільш ініціативними є члени партії «Слуга народу», а Президент України зареєстрував 244 законопроєкти.

Розглянемо ефективність законодавців як відношення успішно прийнятих законопроєктів до їх загальної кількості. Найбільш ефективним законодавцем виявився Президент України — 64 % прийнятих законопроєктів. Відкинемо законодавців, що ініціювали менше 50 проєктів для більш ефективного результату експерименту та відсортуємо по ефективності.

Серед п’яти найменш ефективних депутатів усі, окрім Євтушка Сергія — представники партії «ОПЗЖ». Солод Юрій Васильович був достроково позбавлений мандатів через державну зраду.

 ![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/40398bd6-99d0-4ccd-b9ef-1135027cbdfc)

 5 найменш ефективних депутатів



Розгляньмо 5 найбільш ефективних законотворців:
 ![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/01ff78a1-40f0-4171-96d6-6824b7d678c8)

Президент України має найвищу ефективність як ініціатор законопроєктів, адже 61 % з них проходять усі стадії і приймаються. 
Цей відрив від інших учасників списку може свідчити про більший вплив президента на перебіг законодавчого процесу, ніж передбачено в терміні «парламентсько-президентська республіка», якою є Україна.

За визначенням, у такій республіці влада розподіляється між єдиним законодавчим органом — парламентом, та президентом, що здійснює лише виконавчу владу.
Проте, у даному випадку висока ефективність президента в ініціюванні та прийнятті законопроєктів може вказувати на те, що він має більший вплив на законодавчий процес, ніж це визначено системою. Це може бути пов’язано з його авторитетом, політичним впливом або іншими факторами, які дозволяють йому успішно проводити свої законопроекти через усі стадії законодавчого процесу.

Усі інші топ-5 ініціаторів є у свою чергу представниками партії «Слуга народу», яка переважає кількісно усі інші.

Проаналізуємо топ-30 найактивніших законодавців, їхню ефективність та середній час проходження законопроєктів.

![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/48f78d6b-81d3-42f4-b79b-ff220c498141)


Показник кореляції R = 0.34, що не є недостатнім, аби знайти статистично важливу залежність між цими двома факторами. Примітно, що середній час проходження законопроєктів від Прем’єр-міністра Шмигаля значно більший за інших. При цьому середній час проходження для Зеленського є доволі низьким — 112 днів.

### Ефективність комітетів
Після ініціації законопроєкт одразу потравляє на розгляд до комітетів, де над ним проводиться основна робота. На цьому етапі швидкість проходження залежить конкретно від комітету ВРУ, які наділені частиною законодавчої влади. Кожен комітет різниться за кількістю особового складу, гендерним розподілом та середнім віком учасників.
Нижче представлені п’ять найбільш ефективних комітетів ВРУ. 

![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/2cb3a826-8fa3-4bae-a1ae-8d3b9adfa4f0)

 Із значним відривом попереду йде комітет з питань євроінтеграції – 76% відсотків прийнятих законопроєктів. Другим після лідера є комітет з питань зовнішньої політки – 39%. Також середній час проходження є відносно невеликим. Що ж відрізняє ці комітети від інших? 
 
Примітно, що обидва комітети очолюють молоді депутатки, Гопко Ганна (закордонні справи) та Іванна Климпуш-Цинцадзе (євроінтеграція). Ще одна характерна риса – гендерна рівність. У складі обох комітетів приблизно однакова частка чоловіків та жінок.

Погляньмо тепер на п’ять найменш успішних комітетів.

![image](https://github.com/dosshhhik/ukrainian_law_data_analysis/assets/97986491/3929c71b-2dc7-4bf3-907a-cbaf11217cab)

Їх усіх очолюють представники партії «Слуга народу»,  та  голови усіх комітетів є чоловіками (окрім Третьякової Галини – голови Комітету з питань соціальної політики та захисту прав ветеранів). 
 
## ВИСНОВКИ
У ході роботи було проаналізовано основні етапи законотворчості в Україні та виявлено такі закономірності:
-	Розгляд у головному комітеті займає значно більше часу, ніж прописані в Регламенті 30 днів.
-	Галузь законопроєкту впливає на тривалість проходження розгляду, в основному на рішення Президента.
-	Доля 60% законопроєктів буде вирішена в перші 6 місяців від реєстрації.
-	Найбільш ефективний ініціатор – Президент України.
-	Найменш ініціативними депутатами є представники фракції «ОПЗЖ»
-	Найефективніші комітети очолюють жінки.
Ці висновки підтверджують наявність таких проблем, як велика кількість «сирих» законопроєктів, що  мають мало шансів на успішне проходження, низькоякісна комунікація між комітетами ВРУ, депутатами та КМУ, що призводить до застою законопроєктів. Також варто звернути увагу на монобільшість провладної фракції, представники якої є головами більшості комітетів та можуть просувати свої інтереси. Важливо підняти питання нерівномірного гендерного та вікового розподілу представників законотворчої системи.
Шляхи для покращення:
-	Перенести основну роботу (розробку та пропрацювання ідей) над законопроєктом на передреєстраційний етап, підвищити контроль реєстрації законопроєктів, аби не пропускати неякісні. Це пришвидшить роботу комітетів та знизить відсоток проєктів, які змушені відхилити через недостатнє 
-	Підсилити координацію між представниками кожного з етапів проходження. Наприклад, зобов’язати ініціаторів консультуватися з представниками КМУ перед подачею проєкту.

Доповнити дослідження можна глибшим аналізом чинників, що впливають на роботу депутатів – вік, стать, фракція, освіта, професія до ВРУ і так далі. Також виявити зв’язки між депутатами, їхнє спільне сприяння чи заповільнення проходження законотворчого процесу. 



