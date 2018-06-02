# Описание формата b3D

###### Date: 2018.05 | Version: 0.01

**Глоссарий**

    integer
    float  	
	string
    array	
 
**-TODO-**
    
## Оглавление

**1.**  [Введение](#введение)

**2.**  [Общая структура формата](#общая-структура-формата)

**3.**  [Секции](#секции)

&nbsp;&nbsp;**3.1** [Заголовок файла](#header) 

&nbsp;&nbsp;**3.2** [Список материалов](#список-материалов) 

&nbsp;&nbsp;**3.3** [Блоки данных](#блоки-данных)

## 1. Введение
Этот документ описывает структуру формата файла **b3D**, используемого в игре Дальнобойщики 2 (Второе издание) **версия 8**. 

Все переменные в секциях описаны в порядке их следования в файле.

## 2. Общая структура формата
Формат **b3D** разделен на 3 основные секции (см [Табл. 1](#Таблица-1-Структура).  

#### Таблица 1. Общая Структура

| №     | Секция                   | Ссылки    | 
| :---- | :------------------------ | :------------- |   
| **1** | Заголовок файла                  |  См. [Таблица 2](#Структура-заголовка-файла)   |
| **2** | Список материалов                |  См. [Таблица 3]() |  
|    | Идентификатор начала секции         |  См. [Таблица 6]()                | 
| **3** | Блоки данных | См. [Таблица 5]() |  См. [Таблица 5]()
|    | Идентификатор конца секции          |  См. [Таблица 6]()                 | 

## 3. Секции

### 3.1 Заголовок файла

Файл начинается с сигнатуры из четырех символов "b3d.". Далее располагается таблица размеров секций файла. Все значения размеров в таблице уменьшены в 4 раза, это возможно поскольку все переменные хранящиеся в формате кратны 4ем. Короче, захотели разработчики - сделали. Также присутствует неизвестная константа 6.

##### Таблица 2. Структура заголовка файла
| Тип данных   | Описание                                  | Значение         |
| :------ | :------------------------------------------- | :------------ |
| string  | Сигнатура файла                             | "b3d." |
| integer  | [ Размер файла в байтах ] / 4                            |  |
| integer  | Неизвестная константа                            | 6 |
| integer  | [ Размер секции со списком материалов (1ая секция) ] / 4   |  |
| integer  | [ Размер первых двух секций (1ая и 2ая) в байтах ] / 4  |  |
| integer  | [ Размер секции с блоками данных (третья секция) в байтах ] / 4  |  |
	
### 3.2 Список материалов

##### Таблица 3. Общая структура секции списка материалов
| № | Тип данных   | Описание                               |
| :-- | :------ | :------------------------------------------- | 
| 1   | integer |  Количество материалов                                 |
| 2   | array |  Список названий материалов                 |

##### Таблица 4. Формат элемента списка материалов 
| Размер       | Тип данных   | Описание                               |
| :-----       | :------      | :------------------------------------------ | 
|  32 байта    | string       |  Имя материала                  |

### 3.3 Блоки данных

#### 3.3.1 Структура

##### Таблица 5. Общая структура блока данных
| №  | Описание                                     | Ссылки    | 
| :- | :------------------------------------------- | :------ |
|    | Идентификатор начала блока                   | См. [Таблица 6]()   |
|  1 | Заголовок блока                              | См. [Таблица 7]()   |
|  2 | Параметры                                    | См. [3.3.2]()   | 
|  3 | Вложенные блоки данных                       | См. [Таблица 9]()  |
|    | Идентификатор конца блока                    | См. [Таблица 6]()  |

##### Таблица 6. Идентификаторы
| №  | Описание                                     | Значение в десятичной форме      |
| :- | :------------------------------------------- | :------------ |
|  1 |     Начало секции с блоками данных           |   111         | 
|  2 |     Конец секции с блоками данных            |   222         | 
|  3 |     Начало одного блока                      |   333         | 
|  4 |     ???                                      |   444         | 
|  4 |     Конец одного блока                       |   555         | 

##### Таблица 7. Заголовок блока данных
| №   | Тип данных     | Описание                            |
| :-- | :----------- | :------------------------------------ | 
| 1   |  string      |  Название блока                       |
| 2   |  integer     |   Тип блока                           |

##### Таблица 8. Типы блоков
| Номер блока | Описание                               | Параметры |
| :-- |  :---------------------------------------- | :---------- |
| 0    | Пустой блок                               | См. [Таблица 10]()   | 
| 1    | Связывает два блока.  | См. [Таблица 11]()   |
| 2    |                               |    |
| 4    | Групповой блок.                              |    |
| 5    | Групповой блок. Содержит вложенные блоки для отображения объектов, сквозь которые транспорт проехать не может: строения, внешняя и внутренняя модели транспорта, некоторые другие, а также модели коллизий этих и других объектов. |    |
| 7    |                                |    |
| 8    |                               |    |
| 9    |                               |    |
| 10    |                               |    |
| 12    |                               |    |
| 13    |                               |    |
| 14    |                               |    |
| 18    | Связывает два блока.                              |    |
| 19    | Групповой блок. Содержит вложенные блоки для отображения объектов, по которым транспорт может перемещаться: дороги, стоянки, поверхность земли, холмы и скалы.                          |    |
| 20    |                               |    |
| 21    |                               |    |
| 23    |                               |    |
| 24    | Содержит матрицу трансформации объектов.  |    |
| 25    |                               |    |
| 28    |                               |    |
| 29    |                               |    |
| 30    |                               |    |
| 33    |                               |    |
| 35    | Полигоны                              |    |
| 36    |                               |    |
| 37    | Индексы                              |    |
| 39    |                               |    |
| 40    |                               |    |

##### Таблица 9. Вложенные блоки
| № | Тип данных   | Описание                               | Ссылка |
| :-- | :------ | :------------------------------------------- | :--  |
| 1   | integer |  Количество блоков                                 |  |
| 2   | array |  Блоки                 | См. [Таблица 5]()  |

#### 3.3.2 Параметры блоков

**Блок 0**

Самый первый блок в файле. Данный тип блок не хранит в себе вложенных блоков. 

 ##### Таблица 10. Блок 0 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |   0      |
| 2   | float   | Неизвестная переменная                     |   0      |
| 3   | float   | Неизвестная переменная                     |   0      |
| 4   | float   | Неизвестная переменная                     |   0      |
| 5   | float   | Неизвестная переменная                     |   0      |
| 6   | float   | Неизвестная переменная                     |   0      |
| 7   | float   | Неизвестная переменная                     |   0      |
| 8   | float   | Неизвестная переменная                     |   0      |
| 9   | float   | Неизвестная переменная                     |   0      |
| 10  | float   | Неизвестная переменная                     |   1      |
| 11  | float   | Неизвестная переменная                     |   0      |

**Блок 1**

Присутствует только в файле "Common.d3D" в единственном количестве. Данный тип блок не хранит в себе вложенных блоков. 

 ##### Таблица 11. Блок 1 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   |  string      |  Название                             | Observer |
| 2   |  string      |  Название                             | db:room_db_012 |

**Блок 2**

Присутствует только в файлах "Trucks.d3D" ($$$Group_1381_truck), "ce.d3D" (room_ce01), "dq.d3D" (lep12).

 ##### Таблица 12. Блок 2 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |          |
| 2   | float   | Неизвестная переменная                     |          |
| 3   | float   | Неизвестная переменная                     |          |
| 4   | float   | Неизвестная переменная                     |          |
| 5   | float   | Неизвестная переменная                     |          |
| 6   | float   | Неизвестная переменная                     |          |
| 7   | float   | Неизвестная переменная                     |          |
| 8   | float   | Неизвестная переменная                     |          |
| Вложенные блоки                                                       |
| 9   | integer | Количество блоков                          |          |
| 10   | array   | Блоки                                     |          | 
 
 **Блок 4**
 
##### Таблица. Блок 4 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |          |
| 2   | float   | Неизвестная переменная                     |          |
| 3   | float   | Неизвестная переменная                     |          |
| 4   | float   | Неизвестная переменная                     |          |
| 1   |  string      |  Название                                        |
| 2   |  string      |  Название                                        |
| Вложенные блоки                                                       |
| 6   | integer | Количество блоков                          |          |
| 7   | array   | Блоки                                      |          |
 
##### Таблица. Блок 5 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |          |
| 2   | float   | Неизвестная переменная                     |          |
| 3   | float   | Неизвестная переменная                     |          |
| 4   | float   | Неизвестная переменная                     |          |
| 5   | string  | Название блока/объекта                     |          |
| Вложенные блоки                                                       |
| 6   | integer | Количество блоков                          |          |
| 7   | array   | Блоки                                      |          |
 
 ##### Таблица. Блок 7 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |          |
| 2   | float   | Неизвестная переменная                     |          |
| 3   | float   | Неизвестная переменная                     |          |
| 4   | float   | Неизвестная переменная                     |          |
| 5   | string  | Название блока/объекта                     |          |
| 6   | integer | Количество                                 |          |
| 7   | array   |                                            |          |
| Вложенные блоки                                                       |
| 6   | integer | Количество блоков                          |          |
| 7   | array   | Блоки                                      |          |

 ##### Таблица. Блок 9 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |          |
| 2   | float   | Неизвестная переменная                     |          |
| 3   | float   | Неизвестная переменная                     |          |
| 4   | float   | Неизвестная переменная                     |          |
| 5   | float   | Неизвестная переменная                     |          |
| 6   | float   | Неизвестная переменная                     |          |
| 7   | float   | Неизвестная переменная                     |          |
| 8   | float   | Неизвестная переменная                     |          |
| Вложенные блоки                                                       |
| 9   | integer | Количество блоков                          |          |
| 10   | array   | Блоки                                     |          | 

 ##### Таблица. Блок 10 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |          |
| 2   | float   | Неизвестная переменная                     |          |
| 3   | float   | Неизвестная переменная                     |          |
| 4   | float   | Неизвестная переменная                     |          |
| 5   | float   | Неизвестная переменная                     |          |
| 6   | float   | Неизвестная переменная                     |          |
| 7   | float   | Неизвестная переменная                     |          |
| 8   | float   | Неизвестная переменная                     |          |
| Вложенные блоки                                                       |
| 9   | integer | Количество блоков                          |          |
| 10   | array   | Блоки                                     |          | 

 ##### Таблица. Блок 12 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | float   | Неизвестная переменная                     |          |
| 2   | float   | Неизвестная переменная                     |          |
| 3   | float   | Неизвестная переменная                     |          |
| 4   | float   | Неизвестная переменная                     |          |
| 5   | float   | Неизвестная переменная                     |          |
| 6   | float   | Неизвестная переменная                     |          |
| 7   | float   | Неизвестная переменная                     |          |
| 8   | float   | Неизвестная переменная                     |          |
| 9   | integer   | Неизвестная переменная                   |          |
| 10   | integer   | Неизвестная переменная                  |          |
| Вложенные блоки                                                       |
| 11   | integer | Количество блоков                         |          |
| 12   | array   | Блоки                                     |          | 

 ##### Таблица. Блок 13 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | integer   | Неизвестная переменная                     |          |
| 2   | integer   | Неизвестная переменная                     |          |
| 3   | integer   | Неизвестная переменная                     |          |
| 4   | integer   | Неизвестная переменная                     |          |
| 5   | integer   | Неизвестная переменная                     |          |
| 6   | integer   | Неизвестная переменная                     |          |
| 7   | integer   | Количество                                 |          |
| 8   | array     |                                            |          |

 ##### Таблица. Блок 14 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | integer   | Неизвестная переменная                     |          |
| 2   | integer   | Неизвестная переменная                     |          |
| 3   | integer   | Неизвестная переменная                     |          |
| 4   | integer   | Неизвестная переменная                     |          |
| 5   | integer   | Неизвестная переменная                     |          |
| 6   | integer   | Неизвестная переменная                     |          |
| 7   | float   | Неизвестная переменная                       |          |
| 8   | float   | Неизвестная переменная                       |          |
| 9   | float   | Неизвестная переменная                       |          |
| 10   | float   | Неизвестная переменная                      |          |
| 11   | float   | Неизвестная переменная                      |          |
                     
 ##### Таблица. Блок 18 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | integer   | Неизвестная переменная                     |          |
| 2   | integer   | Неизвестная переменная                     |          |
| 3   | integer   | Неизвестная переменная                     |          |
| 4   | integer   | Неизвестная переменная                     |          |
| 5   | string  | Название блока/объекта                     |          |
| 5   | string  | Название блока/объекта                     |          |
					 
 ##### Таблица. Блок 19 
| № | Тип данных   | Описание                                |
| :-- | :----------- | :------------------------------------ |  
| Вложенные блоки                                            |
| 14   | integer | Количество блоков                         |  
| 15   | array | Блоки                                       |  

 ##### Таблица. Блок 21 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | integer   | Неизвестная переменная                     |          |
| 2   | integer   | Неизвестная переменная                     |          |
| 3   | integer   | Неизвестная переменная                     |          |
| 4   | integer   | Неизвестная переменная                     |          |
| 3   | integer   | Неизвестная переменная                     |          |
| 4   | integer   | Неизвестная переменная                     |          |
| Вложенные блоки                                               |
| 14   | integer | Количество блоков                         |  |
| 15   | array | Блоки                                       |  |

 ##### Таблица. Блок 24
| № | Тип данных   | Описание                                | Значение |
| :-- | :---- | :------------------------------------ | :---    |
| X                                                             | 	
| 1   | float | X                                            |  |
| 2   | float | y                                            |  |
| 3   | float | z                                            |  |
| Y 	                                                        |	
| 4   | float | X                                            |  |
| 5   | float | y                                            |  |
| 6   | float | z                                            |  |
| Z                                                             |		
| 7   | float | X                                            |  |
| 8   | float | y                                            |  |
| 9   | float | z                                            |  |
| Позиция                                                       |	
| 10   | float | X                                           |  |
| 11   | float | y                                           |  |
| 12   | float | z                                           |  |
| 13   | integer |  Неизвестная переменная                   | 0, 1  |
| Вложенные блоки                                               |
| 14   | integer | Количество блоков                         |  |
| 15   | array | Блоки                                       |  |

 ##### Таблица. Блок 25 
| № | Тип данных     | Описание                              | Значение |
| :-- | :----------- | :------------------------------------ | :---     |  
| 1   | integer   | Неизвестная переменная                     |          |
| 2   | integer   | Неизвестная переменная                     |          |
| 3   | integer   | Неизвестная переменная                     |          |
| 4   | string   | Неизвестная переменная                     |          |
| 5   | integer   | Неизвестная переменная                     |          |
| 6   | integer   | Неизвестная переменная                     |          |
| 7   | float   | Неизвестная переменная                       |          |
| 8   | float   | Неизвестная переменная                       |          |
| 9   | float   | Неизвестная переменная                       |          |
| 10   | float   | Неизвестная переменная                      |          |
| 11   | float   | Неизвестная переменная                      |          |
| 12   | float   | Неизвестная переменная                       |          |
| 13   | float   | Неизвестная переменная                       |          |
| 14   | float   | Неизвестная переменная                      |          |
| 15   | float   | Неизвестная переменная                      |          |

 ##### Таблица. Блок 35
| № | Тип данных   | Описание                                |
| :-- | :----------- | :------------------------------------ |  
| 1   |              |                                       |

 ##### Таблица. Блок 37
| № | Тип данных   | Описание                                |
| :-- | :----------- | :------------------------------------ |  
| 1   |              |                                       |

#### 3.3.3 Группировка блоков

#### 3.3.4 Типы объектов