# RL_geNNerator
Just the best<br>

# Алгоритмы работы RL системы 

## Варианты:

### 1) алгоритм генерации нейросети послойно 

- агент получается на вход в качестве состояния среды список последних метрик за последние N обучений
Обучение представляет из себя создание нейросети+ обучение N эпох с отслеживанием метрик
Как результат обучения агент получает лучшие значения метрик

По результатам предыдущих обучений агент принимает решение о том, как слой добавить в конце предыдущей нейросети

### 2) алгоритм генерации нейросети полностью

Входные данные такие же как и в пункт 1
Отличие заключается лишь в том, что агент сразу простраивает всю нейросетевую архитектуру вместо того, чтобы добавлять новый слой в конец

При таком подходе можно добавить в качестве награды уменьшение нейросети количество слоев ( оптимизация архитектур)

## СТРУКТУРА КЛАССА СРЕДЫ (observation):
### Init - объявление переменных 
- обязательные параметры 
* Action space
* Observation space
### Reset - очистить все изменения в среде
### Step - шаг обновления среды
В него передаёт action от агента
В нем генерируется новая наблюдение для агента и награда
### Render - метод, который генерирует графическую часть

## ОБЪЯСНЕНИЕ РАБОТЫ ШАГА (STEP):
получаем на вход action
### 1) если мы генерируем послойно:
Мы преобразовываем действие агента в новый слой, добавляем его в конец текущей архитектуры
Строим нейросеть заново с учётом добавленного слоя
Проводим обучение полученной модели, трассируя метрики
После чего, на основании результатов обучения вычисляется награда 
Полученные метрики добавляются в конец массива из последних результатов обучений 
И этот список передаёт как наблюдение агенту вместе с наградой

### 2) если мы генерируем архитектуру полностью
Мы преобразовываем action от агента в нейросетевую архитектуру
Проводим обучение полученной модели
И возвращаем тоже самое что в пункте 1, только от агента мы получаем нейросетевую архитектуру целиком

# Структура репозитория
branch template:
<pre>
     | ------------->  <span style="color: red"> name </span>
     | <span style="color: green">
     |                 /* description
     |                 */
     |</span> 

</pre>
# Repo tree
<pre>

<span style="color: red">main </span>|
     | ------------->  <span style="color: red"> FullNNGeneration </span>----------------> <span style="color: blue"> </span>
     |<span style="color: green">                                                          | /* Здесь разработка кастомной среды 
     |                 /* В этой ветке хранятся чистовые скрипты                           |
     |                   для реализованного алгоритма генерации всей нейросети             |
     |                   агентом сразу (а не послойно)                                     |
     |                 */                                                                  | */
     |</span>  
     |
     |
     |
     |
     |
     | ------------->  <span style="color: red"> fft_detector </span>
     | <span style="color: green">
     |                 /* this script scan 2.38-2.52 GHz spectrum
     |                    It can be usefull for drone detection by spectrum
     |                    fft_detector.grc, fft_detector.py, required files
     |                 */
     |</span> 
     |
     |
     |
     |
     |
     |
     | ------------->  <span style="color: red"> xml2yml </span>
     | <span style="color: green">
     |                 /* there is python script for converting xml to yml
     |                 */
     |</span> 
     |
     |
     |
     |
     |
     |
     | ------------->  <span style="color: red"> guides_and_docs </span>
     | <span style="color: green">
     |                 /* there is some guides and documentation 
     |                 */
     |</span> 

</pre>
