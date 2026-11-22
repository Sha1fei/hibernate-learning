## Внутренняя архитектура Hibernate
-   ```PersistenceContext (Персистентный контекст)``` (центральное хранилище состояния сессии в памяти) - хранит ссылки на все управляемые сущности, их загруженные снимки (snapshots) и прокси-объекты
-   ```EntityEntry & Status (MANAGED, READ_ONLY, DELETED)``` (мета-информация об объекте внутри PersistenceContext) - хранит статус, версию, сгенерированный ID и флаги валидности для каждой сущности
-   ```ActionQueue (Очередь отложенных действий)``` (строгий упорядоченный список SQL команд, выполняемых при flush) - Hibernate накапливает действия и гарантирует детерминированный порядок их отправки в СУБД
-   ```Порядок выполнения операций в ActionQueue при flush``` (стандартная последовательность отправки DML) - 1. EntityInsertAction → 2. EntityUpdateAction → 3. CollectionRemoveAction → 4. CollectionUpdateAction → 5. EntityDeleteAction
-   ```Двунаправленный Snapshot (Loaded State)``` (массив оригинальных значений полей при чтении из БД) - массив `Object[]`, с которым сравнивается текущее состояние объекта при выполнении алгоритма Dirty Checking
-   ```StatefulPersistenceContext vs StatelessSession``` (сравнение потребления ресурсов и возможностей) - Stateful хранит полный граф связей и историю, Stateless выполняет прямые вызовы JDBC без буферизации
