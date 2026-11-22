## Criteria API и Metamodel
-   ```CriteriaBuilder``` (фабрика для построения программных типобезопасных запросов) - создание предикатов, условий, агрегаций, математических выражений и выражений сортировки
-   ```CriteriaQuery<T>``` (объект структуры запроса, собираемый через методы Java) - методы `.select()`, `.distinct()`, `.where()`, `.groupBy()`, `.having()`, `.orderBy()`
-   ```Root<T> & Path<T>``` (определение корня выборки и путей навигации по графу свойств) - `Root<User> user = cq.from(User.class); Path<String> email = user.get(User_.email);`
-   ```Каноническая статическая метамодель (JPA Static Metamodel)``` (генерация типобезопасных классов-зеркал через annotation processor) - генерирует классы вида `User_.name`, устраняя опечатки в строковых именах колонок при рефакторинге
-   ```Predicate (условия фильтрации WHERE)``` (композиция логических выражений AND/OR) - `cb.and(cb.equal(root.get(User_.active), true), cb.greaterThan(root.get(User_.age), 18))`
-   ```CriteriaUpdate<T> & CriteriaDelete<T>``` (программное выполнение массовых DML-операций) - безопасная сборка запросов `UPDATE` и `DELETE` без склеивания строк
-   ```JPA Tuple (TupleQuery)``` (выборка произвольного набора разнородных колонок без создания отдельного класса) - `CriteriaQuery<Tuple> q = cb.createTupleQuery()`; извлечение по алиасам или индексам
-   ```Spring Data Specification<T>``` (шаблон проектирования для переиспользуемых динамических фильтров) - `(root, query, cb) -> cb.equal(root.get("status"), status)`; легко объединяются через `.and()` и `.or()`
-   ```Подзапросы (Subquery) в Criteria API``` (построение вложенных SELECT для проверок EXISTS, IN, ANY) - `Subquery<Long> subquery = cq.subquery(Long.class)`
