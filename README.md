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
