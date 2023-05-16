# Телеком

**Заказчик**

Оператор связи «ТелеДом» 

**Задача**

Обучить модель, которая будет предсказывать, разорвёт ли абонент договор. 
Качество модели на тестовых данных на метрике AUC-ROC не менее 0.85

**Данные**

Персональные данные о некоторых клиентах, информацию об их тарифах и услугах.

**Используемые библиотеки**

- Pandas,
- Numpy,
- Matplotlib,
- Sqlalchemy, 
- Seaborn,
- Datetime,
- Math,
- Torch,
- Pipeline,
- Phik

**Выводы**

- Результат достигнут AUC-ROC больше 0.85 на тесте.
- Модель без настроенного порога находит чуть больше половины клиентов которые уйдут, но и лишних флаеров почти не рассылает fp довольно низкое.
- При необходимости в зависимости от бизнес задачи, можно поиграть балансом  Precision и Rcall.
- Как и предполагалось до моделирования Type вносит самый большой вклад, далее TotalCharges,	InternetService, MonthlyCharges, они впринцепе связаны.
- ContractDuration и AdditionalServices в тоже кое-что внесли и не зря были добавлены, AdditionalServices может заменить все оставшиеся бинарные сервисы кроме TechSupport это довольно важный параметры, клиенты TechSupport с нами остаются дольше.

**Рекомендации**

1. Направления по улучшению модели, связаны с выбранной бизнес стратегией (баланс между затратами и результатом), а именно застает порога можно поднять значения TP (Recall) но с ним же возрастет и FP, что может привести к повышению затрат на бонусы, а некоторых случаях и к оттоку клиентов.
2. Рекомендации бизнесу следующие:
- Сосредоточиться на переводе клиентов на схему оплаты раз в 1–2 года (сложно уйти когда все оплачено) а т.к мат. ожидание по длительности контракта 300 дней, это неплохой способ улучшить этот показатель, скидки бонусы доп опции (в качестве доп опции может быть техподдержка).
- Пересмотреть ценовую политику в предоставлении других услуг fiber optic дешевле у конкурентов, клиенты уходят, и остается только телефон и dsl (не очень актуальные технологии).
- Личные данные клиентов особо не влияют на их приверженность (не стоит сосредотачиваться на их сборе и хранении), всех интересует цена.