# Аналитика обучения
В проекте были проанализированы данные курсов, которые проходили студенты в нескольких семестрах 
### Стек
Python - pandas, numpy, seaborn, scipy.stat

### Данные
Я анализировала следующие данные: 
общая информация о курсах - список предметов и модулей реализации, продолжительность модулей в днях
общая информация о тестах - идентификационный номер теста, предмет и модуль, тип теста (оценка преподавателя, тестирование и экзамен), вес теста в %
оценки студентов, полученных во время прохождения курса - id студента, номер теста, оценка и дата сдачи 
регистрации студентов на курсы - id студента, предмет и модуль, дата регистрации, дата отмены регистрации

### Задачи, которые я решила в ходе проекта
- Провела предварительный анализ (EDA) и предобработку данных.
- Определила студентов, успешно завершивших курс
- Выявила курсы с самым высоким и низким показателем прохождения курса студентом
- Определила среднее время сдачи экзамена
- Определила самые популярные курсы для регистрации
- Провела RFM-анализ, сегментировала студентов на несколько групп по успеваемости и завершаемости курсов
