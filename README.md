# Аналитика обучения
В проекте были проанализированы данные курсов, которые проходили студенты в нескольких семестрах на обучающей платформе. Его задачи:
- определить, сколько студентов успешно сдали только один курс
- определить курсы и экзамены в рамках курса, которые обладают самой низкой и самой высокой завершаемостью*.
- определить по каждому предмету средний срок сдачи экзаменов (под сдачей понимаем последнее успешное прохождение экзамена студентом).
- выявить самые популярные предметы по количеству регистраций на них. А также предметы с самым большим оттоком.
- выявить семестр с самой низкой завершаемостью курсов и самыми долгими средними сроками сдачи курсов.
- построить адаптированные RFM-кластеры студентов, чтобы качественно оценить аудиторию.
### Технический стек
Python - pandas, numpy, seaborn, scipy.stat, matplotlib

### Данные
Я анализировала следующие данные: 
общая информация о курсах - список предметов и модулей реализации, продолжительность модулей в днях
общая информация о тестах - идентификационный номер теста, предмет и модуль, тип теста (оценка преподавателя, тестирование и экзамен), вес теста в %
оценки студентов, полученных во время прохождения курса - id студента, номер теста, оценка и дата сдачи 
регистрации студентов на курсы - id студента, предмет и модуль, дата регистрации, дата отмены регистрации

### Этапы работы
- Провела предварительный анализ (EDA) и предобработку данных - какие данные предоставлены для анализа, проверка на пропуски, преобразование в нужные типы данных, отбор данных 
- Определила количество студентов, успешно завершивших курс - отобрала курсы с экзаменами, по каждому курсу подгрузила из другого датасета данные о студентах, оставила записи о студентах, которые сдали только 1 экзамен
- Выявила курсы с самым высоким и низким показателем прохождения курса студентом - отобрала студентов, у которых не было перезачетов, добавила переменную "экзамен сдан" - да,нет на основе полученных студентами баллов; рассчитала количество успешных сдач на каждом курсе и количество всех попыток сдать экзамен по курсу; рассчитала для каждого курса долю студентов, успешно прошедших курс
- Определила среднее время сдачи экзамена
- Определила самые популярные курсы для регистрации и курсы с самым большим оттоком - рассчитала, сколько всего студентов регистрировалось на каждый курс и вывела 3 лидирующие курса по количеству регистраций; исключила повторые регистрации и рассчитала процент оттока по формуле [студенты, отозвавшие регистрации] / [все зарегистрированные студенты] * 100; 
- Провела RFM-анализ, сегментировала студентов на несколько групп по успеваемости и проценту завершаемости курсов - создала отдельный датасет для работы, загрузила в него данных о студентах и  R - среднее время сдачи одного экзамена, F - завершаемость курсов, M - среднее количество баллов, получаемое за экзамен. Определила границы метрик recency, frequency и monetary для каждого RFM-сегмента. Получилось 20 сегментов, на основе перекрестных таблиц выделила более крупные 5 кластеров и описала каждый из них. 

### Результаты
- С помощью RFM-фнализа разделила аудиторию студентов на пять групп - "отличники", "хорошисты", "троечники", "не сдавшие", "пересдающие". Рассчитала размер и долю каждой группы 

|Segment	|quantity_students	|perc_students|
|---|---|----|
|Good	|1549	|31.24|
|Satisfactory|	1496	|30.17|
|Great	|1319	|26.60|
|Failure| 567	| 11.43|
|Retake	|28	|0.56|
- Самыми многочисленными группами студентов являются "Хорошисты" (31%) и "Троечники" (30%)
- "Отличники" - чуть больше четверти от всех студентов (26%). Мы можем предположить, что учебные курсы предъявляют студентам достижимые требования и их можно отнести к "средней сложности" - материал курса требует усилия со стороны студентов (при достаточно легкой программе процентная доля "отличников" и "хорошистов" была бы значительно выше)
- Только 11% студентов не смогли справиться с освоением курсов - возможно, они недооценили свои имеющиеся навыки и знания, и их не хватило для успешного завершения курса. Или было недостаточно мотивации для окончания, студенты разочаровались. Мы не можем точно сказать, что влияет на завершение/незавершение курсов из-за отсутствия дополнительных данных
