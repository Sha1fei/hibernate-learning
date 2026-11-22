# Hibernate Learning

Заметки по изучению Hibernate ORM.

## Содержание

1.  [Hibernate Core](./01-hibernate-core) (основы ORM: маппинг Java-объектов на таблицы и управление персистентностью) — SessionFactory, Session, Configuration, persistence.xml
2.  [Маппинг сущностей](./02-entity-mapping) (описание соответствия между Java-классами и таблицами БД) — `@Entity`, `@Table`, `@Column`, `@Enumerated`, `@Temporal`, `@Lob`
3.  [Первичные ключи](./03-primary-keys) (стратегии генерации уникальных идентификаторов сущностей) — `@Id`, `@GeneratedValue`, IDENTITY, SEQUENCE, TABLE, UUID
4.  [Связи между сущностями](./04-relationships) (моделирование отношений между таблицами через объектные ссылки) — `@OneToOne`, `@OneToMany`, `@ManyToOne`, `@ManyToMany`, каскады, `mappedBy`
5.  [Жизненный цикл сущности](./05-entity-lifecycle) (понимание состояний объекта и переходов между ними) — transient, persistent, detached, removed, `persist()`, `merge()`, `flush()`
6.  [HQL запросы](./06-hql-queries) (объектно-ориентированный язык запросов Hibernate) — HQL, JPQL, именованные запросы, параметры, `@Query`
7.  [Criteria API](./07-criteria-api) (программное построение типобезопасных запросов без строковых выражений) — CriteriaBuilder, CriteriaQuery, Predicate, Specification
8.  [Стратегии загрузки](./08-fetching-strategies) (управление моментом и способом загрузки связанных данных) — LAZY, EAGER, N+1 проблема, `JOIN FETCH`, `@BatchSize`, `@EntityGraph`
9.  [Кэширование](./09-caching) (многоуровневое кэширование для снижения нагрузки на БД) — L1 Cache, L2 Cache, Query Cache, EhCache, Redis
10. [Наследование](./10-inheritance) (маппинг иерархий классов на таблицы БД) — SINGLE_TABLE, JOINED, TABLE_PER_CLASS, `@MappedSuperclass`, `@DiscriminatorColumn`
11. [Транзакции и блокировки](./11-transactions) (управление параллельным доступом и целостностью данных) — optimistic locking, pessimistic locking, `@Version`, isolation levels
12. [Hibernate Validator](./12-hibernate-validator) (валидация данных сущностей по аннотациям Bean Validation) — `@NotNull`, `@Size`, кастомные валидаторы, группы валидации
13. [Производительность](./13-performance) (оптимизация запросов, батчинг и профилирование) — batch insert/update, `@DynamicUpdate`, `StatelessSession`, статистика, slow queries
14. [Генерация схемы](./14-schema-generation) (автоматическое создание и обновление структуры БД) — `hbm2ddl.auto`, Flyway, Liquibase, `@Index`, `@UniqueConstraint`
15. [Интеграция со Spring](./15-spring-integration) (использование Hibernate через Spring Data JPA) — `LocalContainerEntityManagerFactoryBean`, `JpaRepository`, `@PersistenceContext`
