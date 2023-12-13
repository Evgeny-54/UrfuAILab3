# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил(а):
- Жевакин Евгений Дмитриевич
- РИ221120
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
-  Предложите вариант изменения найденных переменных для 10 уровней в игре. Визуализируйте изменение уровня сложности в таблице.
- Задание 2.
- Создайте 10 сцен на Unity с изменяющимся уровнем сложности.
- Задание 3
- Решение в 80+ баллов должно заполнять google-таблицу данными из Python. В Python данные также должны быть визуализированы.
- Выводы.
- ✨Magic ✨

## Цель работы
разработать оптимальный баланс для десяти уровней игры Dragon Picker

## Задание 1
Предложите вариант изменения найденных переменных для 10 уровней в игре. Визуализируйте изменение уровня сложности в таблице.

### Решение задачи 1

Мы предлагаем менять только переменные: период сбрасывания и скорость перемещения дракона

<picture>

 <img alt="table.png" src="https://github.com/Evgeny-54/UrfuAILab3/blob/main/table.png">
</picture>

[Ссылка на таблицу](https://docs.google.com/spreadsheets/d/1AlahhKJT6tQesSFKg86LYb-bF0ZYSNrAWfgxTqexxpc/edit#gid=0)






## Задание 2
Создайте 10 сцен на Unity с изменяющимся уровнем сложности.

### Решение задачи 2

Созданные сцены в Unity можно найти в папке _Scenes этого репозитория

<picture>

 <img alt="Unity.png" src="https://github.com/Evgeny-54/UrfuAILab3/blob/main/Unity.png">
</picture>


## Задание 3
Решение в 80+ баллов должно заполнять google-таблицу данными из Python. В Python данные также должны быть визуализированы.

### Решение задачи 3

Заполняем таблицу данными. Далее строим графики изменения уровня сложности, скорости и периода  сбрасывания с помощью билиотеки "matplotlib", которую надо предварительно установить.

<picture>

 <img alt="sh.png" src="https://github.com/Evgeny-54/UrfuAILab3/blob/main/sh.png">
</picture>



```py
%matplotlib inline

import gspread
import numpy as np
import matplotlib.pyplot as plt
gc = gspread.service_account(filename='taxi-334215-2d8d3f211c81.json')
sh = gc.open("unityAI3")
row = ['B','C','D','E','F','G','H','I','J','K']

speed = [4.00, 4.00,5.00,5.00,6.00,6.00,7.00,7.00,8.00,9.00]
time = [2.00,1.00,2.00,1.00,1.00,0.90,0.90,0.70,0.70,0.50]

i = 0

while i < len(speed):
    sh.sheet1.update((row[i] + str(3)), int(speed[i]))
    i+=1
i = 0
while i < len(time):
    sh.sheet1.update((row[i] + str(3)), int(time[i]))
    i+=1

levels = []

i = 0
while i < len(speed):
    levels.append(speed[i]/time[i])
    i+=1

x = [1,2,3,4,5,6,7,8,9,10]

plt.subplot(211)
print("График изменения уровня сложности")
plt.plot (x, levels,'ro')
plt.subplot(212)
print("График изменения скорости и периода сбрасывания")
plt.plot (x, speed)
plt.plot (x, time)
```


## Выводы

В ходе выполнения данной лабароторной работы, научился настраивать баланс уровней в игре. Заполять google таблицу и визуализировать данные в upiter


