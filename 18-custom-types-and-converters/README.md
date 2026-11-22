## Кастомные типы и конвертеры
-   ```@Converter & AttributeConverter<X, Y> (JPA стандарт)``` (преобразование Java типов в типы базы данных и обратно) - `convertToDatabaseColumn()` и `convertToEntityAttribute()`; идеально для шифрования данных на лету
-   ```@Converter(autoApply = true)``` (автоматическое применение конвертера ко всем полям соответствующего типа во всем проекте) - избавляет от необходимости указывать `@Convert` на каждом свойстве
-   ```UserType<T> (Низкоуровневый кастомный тип Hibernate)``` (расширенное управление сохранением сложных объектов) - методы `nullSafeGet()`, `nullSafeSet()`, `deepCopy()`, `isMutable()`, `disassemble()`, `assemble()`
-   ```CompositeUserType (Маппинг составного Java-объекта на несколько колонок БД)``` (создание переиспользуемых Value Objects) - например класс `MonetaryAmount` (поля `amount: BigDecimal` и `currency: Currency`)
-   ```TypeContributor (Регистрация глобальных типов в Hibernate 6)``` (добавление поддержки нестандартных типов СУБД на уровне SessionFactory) - интеграция типов PostgreSQL: `inet`, `uuid[]`, `hstore`
-   ```Шифрование конфиденциальных полей (PII) через AttributeConverter``` (прозрачное симметричное шифрование номеров карт и паспортов в БД) - AES шифрование при записи и расшифровка при чтении
