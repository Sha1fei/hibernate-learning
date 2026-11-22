## Наследование
-   ```@Inheritance(strategy = InheritanceType.SINGLE_TABLE)``` (все классы иерархии в одной таблице с колонкой-дискриминатором) - по умолчанию; одна таблица с `dtype` колонкой; быстрые запросы; много NULL в колонках подклассов
-   ```@DiscriminatorColumn(name = "type", discriminatorType = DiscriminatorType.STRING)``` (настройка колонки-дискриминатора для различения типов) - `@DiscriminatorValue("ADMIN")` — значение для конкретного подкласса; по умолчанию — имя класса
-   ```@Inheritance(strategy = InheritanceType.JOINED)``` (каждый класс в отдельной таблице, связанные через FK) - нормализованная схема; нет NULL колонок; JOIN при каждом запросе — медленнее для глубоких иерархий
-   ```@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)``` (каждый конкретный класс в своей таблице со всеми полями) - нет JOIN; дублирование колонок родителя; полиморфные запросы используют UNION — медленно
-   ```@MappedSuperclass``` (общий базовый класс с полями, не являющийся сущностью) - не создаёт таблицу; не участвует в полиморфных запросах; удобно для `id`, `createdAt`, `updatedAt`
-   ```Полиморфные запросы``` (запросы к базовому классу, возвращающие все подтипы) - `FROM Payment p` — возвращает `CreditCardPayment`, `BankTransferPayment` и т.д.; работает с SINGLE_TABLE и JOINED
-   ```@DiscriminatorFormula``` (вычисляемый дискриминатор через SQL-выражение) - Hibernate-специфичная аннотация; `@DiscriminatorFormula("CASE WHEN card_number IS NOT NULL THEN 'CARD' ELSE 'BANK' END")`
