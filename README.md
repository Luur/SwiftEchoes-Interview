# SwiftEchoes-Interview
The knowledge base for interview preparation.

Кожна тема скаладється з двох частин, інформаці і запитання. Інформація це набір загальних та корисних тез, які можуть допомогти вам відповісти на загальні питання по цій темі (Приклад, що таке комбайн, що ти по ньому знаєш). Частина запитань, це набір конкретних запитань, які можна зустріти на співбесідах. 


## Table of contents
* [General](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [AADS](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [OOP](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [SOLID](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Architectures](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Design patterns](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Frameworks](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
    * [SwiftUI](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
    * [Combine](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
        * [Info](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
        * [Questions](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
    * [UKit](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
        * [HitTesting and ResponderChain](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Memory Management](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Runloop](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Classes & Structs](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Collections](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Concurrency](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Dispatch method](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Generics](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Initialization](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Persistance](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Debug](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Closures](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Enums](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)
* [Git](https://github.com/Luur/SwiftEchoes-Interview#hard-skills)


## General
## AADS
## OOP
## SOLID
## Architectures
## Design patterns
## Frameworks
### SwiftUI
#### Info
SwiftUI provides views, controls, and layout structures for declaring your app’s user interface and tools to manage the flow of data. Стоїть на трьох китах:

* Opaque type https://habr.com/ru/company/otus/blog/542080/
Один з "типів" типів (є абстрактинй тип (протоколи), конкретний(наші дефолтні типи), загальний(дженерік) і непрозорий).
Реалізовується за допомогою ключового слова some, працює він як реверснутий дженерік, тобто ми не ззвоні вказуєм який тип має бути, а тип визначається з середині і приховується на зовні, хоча повертається конкретний (це відрізнає його від протокола).
Дає нам можливість використовувати протокол з асосіейтед тайпом як тип повернення (без непрозорого типу у нас би була помилка компіляції, що такий тип мож використовувати тільки з дженеріком).
Якщо в середені метода є умови, то може повертатися тільки один тип (з протоколом такого б не було, там можна або один або інший або третій, головне щоб вони реалізовували протокол)

* result builders https://habr.com/ru/company/otus/blog/555848/ https://www.hackingwithswift.com/swift/5.4/result-builders
Построители результатов (result builders) в Swift позволяют получать результирующее значение из последовательности компонентов — выставленных друг за другом «строительных блоков». Описывающий объединение неких частей в окончательный результат.
Дає наможливість писати код деклеративно і на виході отримувати одне значення як результат (у випадки з вюбілдер це буде TypelView де аргументи це перелік елементів шо ми додали, макс 10),
Дає нам можливість використовувати іф елс в свіфтюай,
Замежами свіфтюай можна використовувати щоб зручніше писати констрейнти, або стрінги.
Щоб самому створити резлтбілдер, треба використати пропертів врапер @resultbuilder а також реалізувати потрібні методи білдблок, білдайзе(щоб можна убло іф елс писати), білдарей, білдлуп ітд)

* датафлов проперті врпери
    * стейт(це для велью типів коли власником є конкретне вю)
    * стейтобджект(це для референс типів, які мусять реалізовувати ObservableObject, коли власником є конкретне вю. Стейтобджекта не було в першій версії світюай і замість нього використовували обзерведобджект, але тоді появлявся баг, що при апдейті юая цей обєкт теж перестворювався)
    * байндінг(щоб передавати стейт на інші вюшки і щоб вони могли його міняти) Обновлення по байдінгу працює в дві сторони, міняємо значення якоїсь проперті то апдейтиться юай, міняємо це за допомогою юая то абдейтиться і пропертя
    * обзервердобджект (це для референс типів, які мусять реалізовувати ObservableObject, коли власником є не конкретне вю, а цей обєкт передають у в конретне вю звідкись)
    * енвайронментобджект (можна добавляти до вю за допомогою модифікатора і тоді всі сабвюшки цього вю теж будуть мати до нього доступ)
    * енвайронмент це похоже до енваронментобджекта, може шеритися між свюхами, але це ківелю пари які відповідальні за настройки (дісміс, опенурл ітд)
    * паблішед(це з комбайна) якщо маємо клас який реалізовує ObservableObject, то щоб юай реагував на зміни пропертів цього класу, проперті мають мати паблішед проперті врапер
        
### Combine
#### Info
The Combine framework provides a declarative Swift API for processing values over time. Потоки даних які приходять звідусіль: таймери доторки, жести ітд.

Завдяки комбайн Деякі інструменти які ми використовували можна замінити на Combine (Делегати, колбеки, таргетекшени, нотіфікейшни цент обсервери)

Асинхронний код тепер виглядає як синхронний.

Від імперативного програмування відрізняється тим шо при зміні наприклад таблиці нам не треба робити релоад вю, а якшо пропертя це сума двох інших пропертей, то при зміні цих пропертей, сума перерахується сама. 

Уявимо у нас є нотіфікешн центр який робить пост і обсервер який цей нотіфікешн ловить, в комбайні це паблішер який відправляє, а сабскрайбер це той хто ловить, між ними є оператори,

паблішер і сабскрайбер є протоколами, пабліше в собі має аутпут і ерор, а сабскрайбер має інпут і еррор, аутпут і інпут мають бути одного типу, також тип помилки теж має бути одинаковий. При використанні паболішерів, якшо не треба помилки то використовувати Never, якшо треба можна використати setFailureType.

Pulisher неможе бути використаний напиряму бо це протокол, треьба використовувати AnyPublisher  і модифікатор eraseToAnyPublisher для тайп кастінга

Пайплайн працює настпуний чином: підписуємся на паблішера - паблішер створює підписку і відправлає його сабскрайберу - сабскрайбер просить дані - паблоішер їх відправляє - паблішер закриває підписку

Байндінгів для uikit нема окрім тих які робить комюніті.
    
Приклади паблішерів:
* Just (самий простий, повертає результат 1 раз і закінчується)
* Future (нагадує знайоми нам Result, має фейлер і саксес)
* Fail (зразу зипняє пайплайн з помилкою)
* Empty (не публікує ніяких значень, як EmptyView в SwiftUI)
* Defered (отложений паблішер, викликається незразу)
* Sequence (відправляє елементи масиву почерзі)
    
Також є така штука як Subject, який теж відноситься до паблішерів, (воно похоже @Published проперті врапера?)
    
Приклади сабскрайбера:
* onReceive (з СвіфтЮАЙ)
* asign (для обновлення властивостей обєкта, але тип помилки має завжди бути Never)
* sink (буває 2 типів: reciveValue або reciveCompletion i reciveValue)
    
Оператори:
* для мапінга (scan (накопичує дані і публікує коли вони змінюються, для прикладу юзер вводить текст, то це пабліше буде видвати a/ab/abc ітк), map, flatMap і також їхні варіанти з try якшо є можливість викиду помилки)
* для фільтрування (filter, compactMap, replaceEmpty, replaceError, removeDuplicates, collect і їхні варіанти з try)
* метчінг критерія (allSatisfy, contains, containsWhere коли треба кастомні умови)
* для масива (first last drop, prefix, output)
* обєднання (combineLatest, merge, zip)
* відловлення помилок (catch, retry, mapError, asrtNoFailure)
* для контрою часу (debounce, delay, timeout, thottle, measureInterval)
* debuging (breakpoint, pring, handleEvent)
#### Questions
### UKit
#### HitTesting and ResponderChain
## Memory management
## Runloop
## Classes & Structs
## Collections
## Concurrency
## Dispatch method
## Generics
### Info
Щоб мати можливість створити якусь функціональність не привязючись до конкретного типу, позволяє забрати багато дублікації коду, позволяє зробити таку штуку шо метод може примаймати два аргумента будь якого типу, але цей тип є однаковим для двох аргументів. Ми можемо використовувати протоколи для обмеження дженеріків
### Questions
* що таке ключове слово where? яка різниця між "дженері:протоко" і "дженерік where"
    <details><summary>Answer</summary>
        Відповідь: дає нам можливість уточняти асошіейтед тип
    </details>
* Яка диспечирізація в дженеріка
    <details><summary>Answer</summary>
        Пошукати про це інфу, вона міняєтьс якщо дженерік в іншому модулі. вроді вона статична, а якщо дженерів іншому модулі, чи якомусь фреймворку то вона міняється на динамічну, бло непонятно шо буде в середині.
    </details>
## Initialization
### Info
https://docs.swift.org/swift-book/LanguageGuide/Initialization.html
### Questions
* Що таке конвіньєнс конструктор, що зними відбувається при наслідуванні
    <details><summary>Answer</summary>
        Відповдь: це конструктор для зручності, він в середині мусить викликати інший ініціалізатор цього класу
    </details>
* Приклад реквєд ініт
    <details><summary>Answer</summary>
        Відповідь: ініт віз кодер в вюконтролері, або коли реалізовуємо протокол з конструктором в середині
    </details>
* чому коли ми обявляємо свій конструктор нас заствляє реалізувати реквєрд конструктор
    <details><summary>Answer</summary>
        Відповідь: клас наслідує конструктори свого батька до того моменту поки не обявляє свої конструктори
    </details>
* Чому для класу свіфт не може згенерувати нам конструктор, як робить це зі структурою
    <details><summary>Answer</summary>
        https://www.hackingwithswift.com/quick-start/understanding-swift/why-dont-swift-classes-have-a-memberwise-initializer
    </details>
* три типи конструкторів
    <details><summary>Answer</summary>
        Відповідь: рекваєрд, конвініент, дезігнейтед
    </details>
* який ланцюг ініціалізації обєкта, чи може конвініанс викликати супер?
    <details><summary>Answer</summary>
        Відповідь: конвініанс має виклакти в собі або інший конвініас, або дезігнейте, дезігнейтед має виклаккти супер якшо було наслідування
    </details>
* як не втрати в структурі згенерований конструктор, якшо хоч додати кастомний?
    <details><summary>Answer</summary>
        Відповідь: перенести кастомний в екстеншн
    </details>
## Persistance
### Questions
* Кешування, які є способи кешування
* які є опції для стореджу і персістенс
    <details><summary>Answer</summary>
        є колекції, юзердефолтс, кічейн, запис в фаіл, кордата чи реалм
    </details>
* Як зберегти обєкт в юзердефолтс
    <details><summary>Answer</summary>
        треба щоб він реалізовував протокол Codable
    </details>
## Debug
### Questions
* які інструменти є дебагінга
    <details><summary>Answer</summary>
        інструменти, брейкпоінти, асерти, перкондішн, прінти, вю ієархія
    </details>
* Які основні тулзи Instruments, для яких задач їх використовувати
* Як емолювати поганий інтернет
    <details><summary>Answer</summary>
        (Network Link Conditioner) та ще інші способи, найти в неті, дрисати
    </details>
## Closures
### Questions
* що таке трейлінг кложура
    <details><summary>Answer</summary>
        https://www.hackingwithswift.com/sixty/6/5/trailing-closure-syntax
    </details>
* чи може функція мати кложуру як тип повертання
    <details><summary>Answer</summary>
        може https://www.hackingwithswift.com/sixty/6/10/returning-closures-from-functions
    </details>
* Що стається коли кепчер ліст ловить велью значення
    <details><summary>Answer</summary>
        Відповді, створює копію яка не змінюється, а якшо захоплює клас, то він уже захоплює це по ссилці і там по іншому працює
    </details>
* escaping, nonescaping, autoclosures, кепчурліст і як він працює, якими кложури є по дефолту(нонескейрінг, хоча спочатку були ескайпінг) чому так? чому поміняли?
    <details><summary>Answer</summary>
        https://www.hackingwithswift.com/example-code/language/what-is-the-autoclosure-attribute на решту іну треба найти
    </details>
## Enums
### Questions
* Як реалізувати rawValue в енама який має асосіетед вельюс?
    <details><summary>Answer</summary>
        Потрібно самому реалізувати конструктор init?(rawValue: RawValue) і компютед пропертю var rawValue: RawValue
    </details>
* Як зберегти енам в юзер дефолтс?
    <details><summary>Answer</summary>
        Якщо енам має асосіейтед вельюс, то потрібно щоб він реалізовував протокол Codable і тоді зберігати його як Data чи Dictionary. Якщо енам немає асосіейтед вельюс то просто зберігати його рав дата.
    </details>
* Чому всякі константи типу кольорів, чи подібні речі краще мати як енам ніж структуру?
    <details><summary>Answer</summary>
        The advantage of using a case-less enumeration is that it can't accidentally be instantiated and works as a pure namespace.
    </details>
* Реалізацією чого є енам з кейсами some i none?
    <details><summary>Answer</summary>
        Це раеалізація Optional
    </details>
## Git
### Questions
* Що таке git bisect, для чого він використовується?
    <details><summary>Answer</summary>
        Бінарний пошук по комітах щоб знайти той в якому баг
    </details>
* Ситуація: я працював в гілці А, з неї створив гілку Б, як змерджити з мастер тільки зміни гілки Б?
