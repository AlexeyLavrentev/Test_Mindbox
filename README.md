1. Deployment

Создан манифест для Deployment, который учитывает требования к отказоустойчивости и ресурсам.

Replicas: 4 — Нагрузочный тест показал, что 4 пода справляются с пиковой нагрузкой.

Pod Anti-Affinity — Поды распределяются по разным нодам для повышения отказоустойчивости.

Node Affinity — Поды распределяются по трем зонам.

Readiness и Liveness Probes — Учитывают время инициализации приложения (5-10 секунд).

Resource Requests и Limits — Установлены минимальные запросы и лимиты для CPU и памяти.

2. Service

Создан манифест для Service, который обеспечивает доступ к приложению внутри кластера.

Type: ClusterIP — Для внутреннего доступа.

3. Horizontal Pod Autoscaler (HPA)

Для минимизации потребления ресурсов в ночное время добавлен HPA.

Min Replicas: 2 — Минимальное количество подов ночью.

Max Replicas: 4 — Максимальное количество подов днем.

CPU Utilization: 50% — Масштабирование на основе использования CPU.

Принятые решения:

Отказоустойчивость:

Использование Pod Anti-Affinity и Node Affinity для распределения подов по нодам и зонам.

RollingUpdate Strategy для минимизации простоев при обновлении.

Ресурсы:

Установлены минимальные запросы и лимиты для CPU и памяти.

Использование HPA для автоматического масштабирования в зависимости от нагрузки.

Инициализация приложения:

Настроены readiness и liveness probes с учетом времени инициализации.

Минимизация потребления ресурсов:

HPA уменьшает количество подов ночью, когда нагрузка минимальна.
