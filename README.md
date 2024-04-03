## Документация к функциям библиотеки робота МОШ (MoshLib).
### Шпаргалка по функциям
##### Функции конфигурации
- `setDistL(sensor);`, `setDistR(sensor);`, `setDistF(sensor);`: установка левого/правого/переднего датчика по умолчанию (Доступны: ir0, ir1, us)
- `setLineReg(regulator)`: установка регулятора движения по линии по умолчанию (Доступны: RELAY_L, RELAY_R, RELAY_LR, PROP)
##### Функции простого передвижения
- ДОПИШУ ПОЗЖЕ (Саша)


### Функции конфигурации

**Указывает тип левого датчика расстояния по умолчанию**
```c++
setDistL(sensor);
```
- **Параметры**:
  - `sensor`: Доступные варианты датчиков: ir0, ir1, us
- **Пример использования**:
  -  `setDistL(ir1);`: установка первого инфрокрасного датчика по умолчанию

```c++
setDistR(sensor);
```
**Указывает тип правого датчика расстояния по умолчанию**
- **Параметры**:
  - `sensor`: Доступные варианты датчиков: ir0, ir1, us
- **Пример использования**:
  -  `setDistR(ir1);`: установка первого инфрокрасного датчика по умолчанию

```c++
setDistF(sensor);
```
**Указывает тип переднего датчика расстояния по умолчанию**
- **Парамтеры**:
  - `sensor`: Доступные варианты датчиков: ir0, ir1, us
- **Пример использования**:
  -  `setDistF(ir1);`: установка первого инфрокрасного датчика по умолчанию

```c++
setLineReg(regulator);
```
**Устанавливает регулятор движения по линии по умолчанию**
- **Параметры**:
  - `regulator`: Доступные варианты регуляторов: RELAY_L, RELAY_R, RELAY_LR, PROP
- **Пример использования**:
  -  `setLineReg(PROP);`: установка пропорционального регулятора движения по линии по умолчанию

### Функции простого передвижения

```c++
goTime(runtime, speed_left, speed_right);
```
**Движение с заданной скоростью на определенное время**
- **Параметры**:
  - `runtime`: Время работы в мс.
  - `speed_left`: Скорость левого мотора.
  - `speed_right`: Скорость правого мотора.

```c++
goTime(uint32_t runtime, int8_t speed = DEFAULT_SPEED_TICK);
```
**Вариант функции `goTime`, где используется одна скорость для обоих моторов**
- **Параметры**:
  - `runtime`: Время работы в тиках.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

```c++
goHold(uint32_t timeout = HOLD_STOP_TIMEOUT);
```
**Удерживает моторы в текущем положении на заданное время**
- **Параметры**:
  - `timeout`: Время удержания (по умолчанию `HOLD_STOP_TIMEOUT`).

```c++
goTick(int32_t ticks, uint8_t speed = DEFAULT_SPEED_PWM);
```
**Движение на заданное количество тиков**
- **Параметры**:
  - `ticks`: Количество тиков.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
goDist(int32_t distance_mm, int16_t speed_PWM = DEFAULT_SPEED_PWM);
```
**Прямолинейное синхронное движение на заданное расстояние**
- **Параметры**:
  - `distance_mm`: Заданное расстояние в миллиметрах.
  - `speed_PWM`: Скорость движения (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
goCross(uint8_t crosses = 1, bool found_line = false, int16_t speed_PWMDIR = DEFAULT_SPEED_PWM);
```
**Синхронное движение до перекрестка**
- **Параметры**:
  - `crosses`: Количество перекрестков (по умолчанию `1`).
  - `found_line`: Состояние найденной линии (по умолчанию `false`).
  - `speed_PWMDIR`: Скорость движения (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
turnAngle(int16_t a, int16_t speed = DEFAULT_SPEED_PWM);
```
**Поворот вокруг центра на заданный угол**
- **Параметры**:
  - `a`: Угол поворота (значения меньше нуля означают поворот против часовой стрелки).
  - `speed`: Скорость поворота (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
alignLine(uint32_t duration = PARAMS::ALIGN_DURATION);
```
**Выравнивание робота по линии**
- **Параметры**:
  - `duration`: Время выравнивания (по умолчанию `PARAMS::ALIGN_DURATION`).

```c++
turnLineL(int8_t crosses = 1, int16_t speed = DEFAULT_SPEED_PWM);
```
**Поворот вокруг центра влево, пересекая линии**
- **Параметры**:
  - `crosses`: Количество линий (по умолчанию `1`).
  - `speed`: Скорость поворота (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
turnLineR(int8_t crosses = 1, int16_t speed = DEFAULT_SPEED_PWM);
```
**Поворот вокруг центра вправо по перекресткам**
- **Параметры**:
  - `crosses`: Количество линий (по умолчанию `1`).
  - `speed`: Скорость поворота (по умолчанию `DEFAULT_SPEED_PWM`).

### Функции движения до-по-вдоль стены
```c++
wallFront(mosh::hardware::DistanceSensor& sensor, uint8_t distance, uint8_t speed = DEFAULT_SPEED_PWM);
```
**Прямолинейное синхронное движение до стены**
- **Параметры**:
  - `sensor`: Ссылка на датчик расстояния.
  - `distance`: Целевое расстояние до стены.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
wallFront(uint8_t distance, uint8_t speed = DEFAULT_SPEED_PWM);
```
**Вариант функции `wallFront`, где используется передний датчик расстояния**
- **Параметры**:
  - `distance`: Целевое расстояние до стены.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
wallBack(mosh::hardware::DistanceSensor& sensor, uint8_t distance, int16_t speed = DEFAULT_SPEED_PWM);
```
**Прямолинейное синхронное движение назад от стены**
- **Параметры**:
  - `sensor`: Ссылка на датчик расстояния.
  - `distance`: Расстояние, на котором должна находиться стена.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
wallBack(uint8_t distance, uint8_t speed = DEFAULT_SPEED_PWM);
```
**Вариант функции `wallBack`, где используется передний датчик расстояния**
- **Параметры**:
  - `distance`: Расстояние, на котором должна находиться стена.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_PWM`).

```c++
wallTimeL(uint8_t distance, uint32_t runtime, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение вдоль стены по левому датчику**
- **Параметры**:
  - `distance`: Целевое расстояние в сантиметрах.
  - `runtime`: Время движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

```c++
wallTimeR(uint8_t distance, uint32_t runtime, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение вдоль стены по правому датчику**
- **Параметры**:
  - `distance`: Целевое расстояние в сантиметрах.
  - `runtime`: Время движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

### Функции движения по линии
```c++
lineTime(uint32_t runtime, uint8_t speed = DEFAULT_SPEED);
```
**Движение по линии с регулятором по умолчанию**
- **Параметры**:
  - `runtime`: Время движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED`).

```c++
lineTimeL(uint32_t runtime, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение по линии по левому датчику**
- **Параметры**:
  - `runtime`: Время движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

```c++
lineTimeR(uint32_t runtime, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение по линии по правому датчику**
- **Параметры**:
  - `runtime`: Время движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

```c++
lineTimeLR(uint32_t runtime, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение по линии по двум датчикам**
- **Параметры**:
  - `runtime`: Время движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

```c++
lineTimeP(uint32_t runtime, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение по линии по P-регулятору**
- **Параметры**:
  - `runtime`: Время движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

```c++
lineCrossP(uint8_t crosses = 1, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение по линии до перекрестка P-регулятором**
- **Параметры**:
  - `crosses`: На каком перекрёстке остановиться.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).

```c++
lineDistP(int32_t distance, uint8_t speed = DEFAULT_SPEED_TICK);
```
**Движение по линии на расстояние P-регулятором**
- **Параметры**:
  - `distance`: Расстояние движения.
  - `speed`: Скорость движения (по умолчанию `DEFAULT_SPEED_TICK`).





# MoshLib

TODO обновить

## Библиотека Arduino для мобильного робота

* Управление оборудованием:
  * Моторы:
    * [x] Контроль ШИМ-Направление;
    * [x] Вращение с постоянной скоростью;
    * [x] Удержание позиции;
    * [ ] Управление ускорением;

  * УЗ-датчик:
    * [x] Определение расстояния (см);
    * [ ] Фильтр;

  * ИК-датчик:
    * [x] Определение расстояния (см);
    * [ ] Фильтр;

  * Датчик линии:
    * [x] Калибровка значений на линии и на поле;
    * [x] Логический режим, определение уровня чувствительности;
    * [x] Аналоговый режим;

  * Кнопка:
    * [ ] Поведение определяется внешней библиотекой;
    * [ ];

  * Серво:
    * [ ] Поведение определяется внешней библиотекой;
    * [ ];

  * Дисплей:
    * [ ] Поведение определяется внешней библиотекой;
    * [ ];

* Функционал:
  * Конфигурирование робота:
    * [x] Установка положений датчиков; `setDistL setDistR setDistF`
    * [ ] Установка алгоритма движения по линии по умолчанию;
    * [ ] Установка скорости движения по умолчанию;
    * [ ] Крайние углы захвата, задание скорости;
    * [ ] Крайние углы толкателя, задание скорости;

  * Управление:
    * [ ] Блокирующее ожидание нажатия кнопки;
    * [ ] Синхронное движение моторов;
    * [ ];

  * // TODO имя:
    * [ ] Захват;
    * [ ] Толкатель;

  * Простые движения:
    * [x] По времени `-Time-`;
    * [x] По тикам; `-Ticks-`
    * [x] Удержание позиции;
    * [ ];

  * Поворот:
    * [x] На угол по энкодерам; `turnAngle`
    * [ ] Поворот до линии (Направо, налево); `turnLine`
    * [ ] Выравнивание по линии `linePos`
  
  * Прямолинейное движение:
    * [x] На расстояние мм по энкодерам; `goDist`
    * [x] На время; `goTime`
    * [x] Вперёд до стены -> мм; `wallFront`
    * [x] Назад от стены -> мм; `wallBack`
    * [ ] До чёрной линии -> мм; `goCross`
    * [ ] До белой линии -> мм; `goTolineW`
    * [ ] Чтение штрихкода (определение массива длин полос данной длины); `readBars`
    * [ ] Чтение штрихкода (определение количества полос); `readBars`
    * [ ] Прямо и выравнивание по перпендикулярным линиям;
  
  * Движение вдоль стены:
    * Вид движения:
      * [x] По одному датчику (Левый или Правый); `wallL* wallR*`
      * [ ] По двум датчикам (удержание позиции по середине); `wall*`

    * Остановка:
      * [x] По времени; `*Time`
      * [ ] По расстоянию; `*Dist`
      * [ ] Пока не пропадёт из зоны видимости;
      * [ ] До фиксации линии; `*Line`
  
  * Движение по линии:
    * Реализованные регуляторы:
      * [x] Релейный по одному датчику (Левый или Правый); `line*L line*R`
      * [x] Релейный по двум датчикам; `line*LR`
      * [x] Пропорциональный; `line*P`
      * [ ] Пропорционально-Дифференциальный; `line*PD`

    * Остановка:
      * [x] По времени; `*TIme*`
      * [ ] До объекта -> мм; `*Wall`
      * [ ] По пройденому расстоянию; `*Dist*`
      * [ ] По число пройденных перекрёстков -> мм `*Cross*`

* TODO:

* BL;

* Заменить полиморфизм на указатели функций.
