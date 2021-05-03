# О проекте

Описание бинарных форматов игр  **Дальнобойщики 1**, **Дальнобойщики 2** (версия 8) и **Дальнобойщики 3**.

#### Прогресс по всем форматам
| b3D | MSK | PLM | RMP | TXR | RES | TECH | RAW | WAY | WMD |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | 
| >50% | 100% | 100% | 100% | 100% | 100% | >85% | 100% | 95% | 5% |

####  Дополнительные ссылки
* [Группа ВК](https://vk.com/rnr_mods)
* <a href="https://discord.gg/cmmmd53Wsy"><img src="https://img.shields.io/badge/discord-join-7289DA.svg?logo=discord&longCache=true&style=flat" /></a>
## Форматы файлов

    Описание форматов файлов сделано в виде шаблонов для программы 010Editor и Kaitai Struct. 
    
    Шаблоны в формате .bt хранят структуры в стиле языка C, если открыть файл в 010Editor и применить шаблон, то программа отобразит дерево структур файла, в котором удобно изменять значения хранимых переменных и совершать другие манипуляции. 

    Файлы .ksy содержат описание формата в виде yaml документа. Данный файл можно преобразовать/скомпилировать в готовой код для чтения для большого числа языков или отобразить формат в графическом виде.

#### Дальнобойщики 1 (1998)

| № | Формат | Шаблон (010 Editor) | Kaitai | Описание |
| :-- | :------- | :-- |  :-- | :-- |
|  **1**  |  .b3D**  |   [b3D.bt](https://github.com/AlexKimov/reRNR/RNRFileFormats/tree/master/formats/templates/B3D.bt) | | 3D объекты и объекты игровой логики (модели коллизий, порталы, объекты освещения и т.п.) |
|  **2**  | .MSK |  [MSK.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/MSK.bt) | | 8 битные файлы масок, хранятся в архиве .RMP | 
|  **3**  | .PLM |  [PLM.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/PLM.bt) | | Палитра, хранится в архиве RMP | 
|  **4**  | .RMP* | [RES.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/RES.bt) |  | Архив ресурсов (звуки, текстуры) | 
| **5**  | .TXR | [TXR.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/TXR.bt) | [ard_truck_2_txr.ksy](https://github.com/reRNR/RNRFileFormats/blob/master/formats/ksy/hard_truck_2_txr.ksy) | Текстура | 

    * Формат аналогичен формату RES из второй части игры (Дальнобойщики 2)
    ** Формат аналогичен формату b3D из второй части игры (Дальнобойщики 2), ну или наоборот

#### Дальнобойщики 2 (версия 8)

| № | Формат | Шаблон (010 Editor) | О формате |
| :-- | :------- | :-- | :-- |
|  **1**  |  .b3D  |   [b3D.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/B3D.bt) | 3D объекты и объекты игровой логики (модели коллизий, порталы, объекты освещения и т.п.) |
|  **2**  | .MSK |  [MSK.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/MSK.bt) | 8/16 битные файлы масок, хранятся в архиве .RES | 
|  **3**  | .PLM |  [PLM.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/PLM.bt) | Палитра, хранится в архиве .RES | 
|  **4**  | .RAW |   |  Карты высот | 
|  **5**  | .RES |  [RES.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/RES.bt) | Архив ресурсов (звуки, текстуры) | 
|  **6**  | .TECH | [TECH.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/TECH.bt)  | Параметры транспортных средств | 
|  **7**  | .TXR |  [TXR.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/TXR.bt) |  Текстура | 
|  **8**  | .WAY | [WAY.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/WAY.bt) | Пути для транспорта под управлением ИИ | 

#### Дальнобойщики 3 (2009)
| № | Формат | Прогресс  | Шаблон |  Описание   |
| :-- | :------- | :-- | :-- | :-- |
|  **1**  |  .WMD  |     | [WMD.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/WDB.bt) | 3D объекты и объекты игровой логики (модели коллизий, порталы, объекты освещения и т.п.) |

## Спасибо
Юрий Гладышенко

* * * 
# About
Hard Truck 1 (1998), Hard Truck 2 King of the Road 1.3 and RignRoll (2010) games file formats.

#### Hard Truck 1 (1998)

| № | Format/Ext  | Template (010 Editor) |  Description   |
| :-- | :------- | :-- | :-- | 
|  **1**  |  .b3D**  | [b3D.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/B3D.bt) | Game logic and 3D objects |
|  **2**  | .RMP* |  [RES.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/RES.bt) | Resource archive: sounds, textures | 
|  **3**  | .PLM | [PLM.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/PLM.bt) |   Palette | 
|  **4**  | .MSK |  [MSK.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/MSK.bt) |    Texture Masks, 8-bit with palette | 
|  **5**  | .TXR |  [TXR.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/TXR.bt) |    Texture file |

    *  almost the same as RES format from Hard Truck 2
    **  b3D format from Hard Truck 2 has the same structure, but there are some differences

#### Hard Truck 2 King of the Road (2002)
| № | Format/Ext |  Template (010 Editor) |  Description   |
| :-- | :------- |  :-- | :-- |
|  **1**  | .b3D | [b3D.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/B3D.bt) | Game logic and 3D objects |
|  **2**  | .MSK |  [MSK.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/MSK.bt) |    Mask files stored in .RES | 
|  **3**  | .PLM |  [PLM.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/PLM.bt) |    Palette file in .RES | 
|  **4**  | .RAW  |   [RAW.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/RAW.bt) |  Heightmaps | 
|  **5**  | .RES   | [RES.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/RES.bt) | Resource archive: sounds, textures | 
|  **6**  | .TECH  |  [TECH.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/TECH.bt) |   Vehicle params | 
|  **7**  | .TXR |  [TXR.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/TXR.bt) |   Texture file |
|  **8**  | .WAY  | [WAY.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/WAY.bt) | AI waypoints | 

#### RignRoll (2009)
| № | Format/Ext |  Template (010 Editor) |  Description   |
| :-- | :------- |  :-- | :-- |
|  **1**  |  .WMD  |  [WMD.bt](https://github.com/reRNR/RNRFileFormats/tree/master/formats/templates/WDB.bt) | Game logic and 3D objects |
