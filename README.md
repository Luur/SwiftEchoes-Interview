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


## General
## AADS
## OOP
## SOLID
## Architectures
## Design patterns
## Frameworks
### SwiftUI
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
## Initialization
## Persistance
## Debug
## Closures
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
