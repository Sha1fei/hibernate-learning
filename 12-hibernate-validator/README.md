## Hibernate Validator
-   ```Встроенные ограничения Bean Validation (JSR 380)``` (базовая валидация свойств сущностей) - `@NotNull`, `@NotBlank`, `@NotEmpty`, `@Size`, `@Min`, `@Max`, `@Email`, `@Positive`, `@Past`, `@Future`
-   ```Кастомные аннотации валидации (@Constraint)``` (создание собственных бизнес-правил валидации) - аннотация с `@Constraint(validatedBy = CheckInnValidator.class)` и класс, реализующий `ConstraintValidator<CheckInn, String>`
-   ```Кросс-полевая валидация на уровне класса (Class-level constraint)``` (проверка согласованности нескольких полей объекта) - валидатор вешается на сам класс сущности (например, `startDate < endDate` или «пароль совпадает с подтверждением»)
-   ```Группы проверок (Validation Groups)``` (разные правила валидации для разных сценариев) - интерфейсы-маркеры `OnCreate`, `OnUpdate`; аннотация `@NotNull(groups = OnCreate.class)`; в контроллере `@Validated(OnCreate.class)`
-   ```Group Sequence (@GroupSequence)``` (управление строгим порядком выполнения валидаций) - не выполнять тяжелые проверки в БД, если упали базовые дешевые проверки формата
-   ```Интеграция с жизненным циклом Hibernate (Pre-persist / Pre-update)``` (автоматическая валидация сущностей перед сохранением в БД) - Hibernate Validator автоматически вызывается перед операциями записи, выбрасывая `ConstraintViolationException`
-   ```Локализация сообщений об ошибках (ValidationMessages.properties)``` (кастомизация текстов ошибок под язык пользователя) - шаблоны сообщений с интерполяцией параметров: `{min}`, `{max}`
