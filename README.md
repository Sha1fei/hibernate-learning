# Hibernate Learning

Углублённое практическое руководство по Hibernate 6 / JPA. От базового маппинга до внутреннего устройства (Persistence Context, ActionQueue), оптимизации запросов, аудита (Envers), мультитенантности и перехватчиков.

## Содержание

1.  [Hibernate Core](./01-hibernate-core) (архитектура сессий, реестры сервисов и диалекты SQL) — `SessionFactory`, `Session`, `StandardServiceRegistry`, `PhysicalNamingStrategy`, `Dialect`
2.  [Маппинг сущностей](./02-entity-mapping) (полное моделирование таблиц, JSON-типов, формул и компонентов) — `@Entity`, `@Table`, `@SecondaryTable`, `@Embedded`, JSON в Hibernate 6 (`@JdbcTypeCode`), `@Formula`
3.  [Первичные ключи и оптимизаторы](./03-primary-keys) (генерация ID, составные ключи и пуловые оптимизаторы) — `IDENTITY`, `SEQUENCE`, `pooled-lo`, `@EmbeddedId`, `@IdClass`, `@NaturalId`, UUID, TSID
4.  [Связи между сущностями](./04-relationships) (моделирование ассоциаций без утечек и циклических ссылок) — `@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany`, каскады, `orphanRemoval`, методы синхронизации
5.  [Жизненный цикл и FlushMode](./05-entity-lifecycle) (состояния сущности, режимы сброса изменений и грязная проверка) — transient, managed, detached, removed, `flush()`, `FlushModeType` (AUTO, COMMIT), Dirty Checking
6.  [HQL и JPQL запросы](./06-hql-queries) (объектные запросы, оконные функции, CTE и DTO-проекции) — HQL, `JOIN FETCH`, DTO через `SELECT NEW`, оконные функции Hibernate 6, массовые обновления (Bulk Operations)
7.  [Criteria API и Metamodel](./07-criteria-api) (типобезопасные запросы, генерация метамодели и спецификации) — `CriteriaBuilder`, `CriteriaQuery`, каноническая метамодель (`User_`), `CriteriaUpdate`, `Specification`
8.  [Стратегии загрузки и проблема N+1](./08-fetching-strategies) (ликвидация лишних SQL-запросов и управление графами) — `LAZY`, `EAGER`, N+1 проблема, `JOIN FETCH`, `@EntityGraph`, `@BatchSize`, `MultipleBagFetchException`
9.  [Кэширование (L1, L2, Query Cache)](./09-caching) (многоуровневое кэширование, инвалидация и провайдеры) — кэш первого уровня, кэш второго уровня, Query Cache, стратегии параллелизма (READ_WRITE), Redis, Ehcache
10. [Наследование в ORM](./10-inheritance) (стратегии маппинга иерархий классов и полиморфные выборки) — `SINGLE_TABLE`, `JOINED`, `TABLE_PER_CLASS`, `@MappedSuperclass`, `@DiscriminatorColumn`, полиморфные запросы
11. [Транзакции и блокировки](./11-transactions) (управление конкурентным доступом и предотвращение аномалий) — `@Version`, Optimistic Locking, Pessimistic Locking (`PESSIMISTIC_WRITE`), Deadlock, уровни изоляции
12. [Hibernate Validator](./12-hibernate-validator) (декларативная валидация данных сущностей на уровне приложения) — встроенные ограничения, кастомные валидаторы, валидация на уровне класса, группы проверок
13. [Производительность и батчинг](./13-performance) (высоконагруженная оптимизация JDBC и профилирование) — JDBC batching (`batch_size`), `order_inserts`, `StatelessSession`, `@DynamicUpdate`, StatementInspector, HikariCP
14. [Генерация схемы и миграции](./14-schema-generation) (управление DDL, индексами и интеграция с инструментами миграций) — `hbm2ddl.auto`, `@Index`, `@UniqueConstraint`, экспорт DDL в файл, связка с Flyway/Liquibase
15. [Интеграция со Spring Data JPA](./15-spring-integration) (работа Hibernate под управлением Spring Boot) — `JpaRepository`, `@PersistenceContext`, Open Session in View (OSIV антипаттерн), read-only оптимизация
16. [Hibernate Envers (Аудит данных)](./16-hibernate-envers) (автоматическое версионирование и история изменений таблиц) — `@Audited`, `_AUD` таблицы, `AuditReader`, `@RevisionEntity`, отслеживание изменённых колонок
17. [Интерцепторы и события](./17-interceptors-and-events) (перехват низкоуровневых операций сохранения и обновления) — `Interceptor`, `PreInsertEventListener`, `PostUpdateEventListener`, `Integrator`
18. [Кастомные типы и конвертеры](./18-custom-types-and-converters) (хранение сложных объектов и JPA конвертеры) — `@Converter`, `AttributeConverter`, `UserType`, `CompositeUserType`, маппинг нестандартных типов СУБД
19. [Мультитенантность (Multi-Tenancy)](./19-multi-tenancy) (изоляция данных разных клиентов в одном приложении) — подходы (Database, Schema, Discriminator/Row-level), `MultiTenantConnectionProvider`, `CurrentTenantIdentifierResolver`
20. [Инструментирование байт-кода](./20-bytecode-enhancement) (Bytecode Enhancement на этапе сборки проекта) — lazy loading одиночных скалярных полей (CLOB/BLOB), dirty tracking без снапшотов памяти, maven/gradle плагины
21. [Внутренняя архитектура Hibernate](./21-internal-architecture) (что происходит под капотом Session и PersistenceContext) — `PersistenceContext`, `ActionQueue`, `EntityEntry`, двунаправленный snapshot, порядок выполнения SQL операций
22. [Мягкое удаление и фильтры](./22-soft-delete-and-filters) (Soft Delete и динамическая фильтрация записей) — `@SoftDelete` (Hibernate 6.4+), `@SQLDelete`, `@SQLRestriction`, `@FilterDef`, `@Filter`
