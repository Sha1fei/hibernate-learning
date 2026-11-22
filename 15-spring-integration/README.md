## Интеграция со Spring Data JPA
-   ```spring-boot-starter-data-jpa``` (автоконфигурация Hibernate и JPA в инфраструктуре Spring) - автоматически поднимает `HikariDataSource`, `LocalContainerEntityManagerFactoryBean` и `JpaTransactionManager`
-   ```@PersistenceContext & EntityManager``` (внедрение потокобезопасного прокси EntityManager в сервисы и компоненты) - делегирует операции реальной сессии, привязанной к текущему потоку транзакции
-   ```Проблема Open Session in View (OSIV / spring.jpa.open-in-view)``` (антипаттерн удержания сессии открытой до конца HTTP запроса) - включен в Spring Boot по умолчанию; приводит к удержанию соединений пула во время рендеринга и скрытым запросам в контроллерах; рекомендуется отключать (`false`)
-   ```@Transactional(readOnly = true) оптимизация``` (оптимизация транзакций на чтение) - переводит сессию Hibernate в `FlushModeType.MANUAL`, отключая создание snapshot'ов памяти и Dirty Checking
-   ```JpaRepository & CrudRepository``` (автоматическая кодогенерация CRUD методов и пагинации) - генерация SQL по конвенциям имен методов (`findByEmailAndStatus`); пагинация через `Pageable` и `Page<T>`
-   ```@Modifying(clearAutomatically = true, flushAutomatically = true)``` (корректное выполнение кастомных UPDATE/DELETE в репозитории) - автоматически синхронизирует и очищает Persistence Context, предотвращая рассинхрон с кэшем первого уровня
-   ```Spring Data JPA Auditing (@EnableJpaAuditing)``` (автоматическое заполнение полей аудита) - аннотации `@CreatedDate`, `@LastModifiedDate`, `@CreatedBy`, `@LastModifiedBy` в связке с `AuditorAware`
