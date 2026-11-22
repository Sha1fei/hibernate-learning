## Интерцепторы и события
-   ```EmptyInterceptor / Interceptor``` (перехват жизненного цикла сущностей на уровне сессии или приложения) - методы: `onSave`, `onFlushDirty`, `onDelete`, `preFlush`, `postFlush`
-   ```PreInsertEventListener & PreUpdateEventListener``` (низкоуровневая подписка на события до формирования SQL) - интеграция через `EventListenerRegistry`; позволяет валидировать или модифицировать массив состояния `state[]`
-   ```PostInsertEventListener & PostDeleteEventListener``` (асинхронная отправка событий во внешние системы после записи) - идеальное место для отправки сообщений в Kafka или RabbitMQ после фиксации изменений
-   ```Integrator (Регистрация слушателей при старте)``` (программное подключение кастомных слушателей в SessionFactory) - реализация `org.hibernate.integrator.spi.Integrator` через ServiceLoader
-   ```Модификация состояния в onFlushDirty vs геттеры/сеттеры``` (правильный способ изменения полей в перехватчике) - изменение напрямую через массив `currentState[]` предотвращает рекурсивный вызов dirty checking
-   ```StatementInspector``` (перехват и модификация сгенерированного SQL текста перед выполнением) - добавление кастомных хинтов оптимизатора СУБД (например, `/*+ INDEX(...) */`)
