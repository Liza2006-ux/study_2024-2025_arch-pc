---
## Front matter
Обработка данных и визуализация
Волчкова Елизавета 
НКАбд-01-24

Предобработка данных и их изучения.

3. Проверьте данные на пропуски и дубликаты.
4. Вычислите сводную (описательную) статистику о данных датафреймов (таблиц) и выведите ее.
5. Если в некоторых столбцах нужно изменить данные, измените их и аргументируйте зачем их стоит
изменить (например, дата должна иметь тип данных datetime64, а не object).


https://www.db-fiddle.com/f/u5ekzMZFW7dq2D2Nz8FgTn/11
Выполнение проекта.
Есть таблица оператора, который может подобрать тур по России или по Европе. 
Связь с таблицами Россия и Европа у оператора идёт по столбцу город ("City"). 
Доступ к подробной информации таблиц у оператора идёт через "Tour" Rus или Eur.
![Rus](https://github.com/user-attachments/assets/42810454-1e42-42c2-8f2f-495e41190b84)


![Eur — копия](https://github.com/user-attachments/assets/5825504c-dca9-4e5a-8ea4-f0a9aef53227)


![table](https://github.com/user-attachments/assets/88af8763-228b-49aa-bb9e-412fd3a2ef99)





CREATE TABLE `Operator` (
    `Country`	VARCHAR(512),
    `City`	VARCHAR(512),
    `Tour`	VARCHAR(512)
);

INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Turkey', 'Istanbul', 'Eur ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Turkey', 'Izmir', 'Eur ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Turkey', 'Izmir', 'Eur ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Turkey', 'Istanbul', 'Eur ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('USA', 'New York', 'Eur ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('USA', 'Chicago', 'Eur ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Russia', 'Kaliningrad', 'Rus ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Russia', 'Kaliningrad', 'Rus ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Russia', 'Kazan', 'Rus ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Russia', 'Kazan', 'Rus ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Russia', 'Sochi', 'Rus ');
INSERT INTO `Operator` (`Country`, `City`, `Tour`) VALUES ('Russia', 'Sochi', 'Rus ');


CREATE TABLE `Rus` (
    `Rating`	INT,
    `City`	VARCHAR(512),
    `Days`	INT,
    `Pople`	INT,
    `Avia`	VARCHAR(512),
    `Sea`	VARCHAR(512),
    `Price`	INT,
    `Sold`	INT
);

INSERT INTO `Rus` (`Rating`, `City`, `Days`, `Pople`, `Avia`, `Sea`, `Price`, `Sold`) VALUES ('5', 'Kaliningrad', '7', '1', 'y', 'n', '500', '50 ');
INSERT INTO `Rus` (`Rating`, `City`, `Days`, `Pople`, `Avia`, `Sea`, `Price`, `Sold`) VALUES ('5', 'Kaliningrad', '14', '2', 'y', 'n', '350', '75 ');
INSERT INTO `Rus` (`Rating`, `City`, `Days`, `Pople`, `Avia`, `Sea`, `Price`, `Sold`) VALUES ('5', 'Kazan', '7', '3', 'y', 'n', '600', '100 ');
INSERT INTO `Rus` (`Rating`, `City`, `Days`, `Pople`, `Avia`, `Sea`, `Price`, `Sold`) VALUES ('5', 'Kazan', '14', '2', 'n', 'n', '700', '125 ');
INSERT INTO `Rus` (`Rating`, `City`, `Days`, `Pople`, `Avia`, `Sea`, `Price`, `Sold`) VALUES ('4', 'Sochi', '7', '2', 'y', 'y', '600', '150 ');
INSERT INTO `Rus` (`Rating`, `City`, `Days`, `Pople`, `Avia`, `Sea`, `Price`, `Sold`) VALUES ('5', 'Sochi', '14', '2', 'n', 'y', '500', '175 ');



CREATE TABLE `Eur` (
    `Rating`	INT,
    `City`	VARCHAR(512),
    `Days`	INT,
    `People`	INT,
    `Avia`	VARCHAR(512),
    `Viza`	VARCHAR(512),
    `Sea`	VARCHAR(512),
    `Price`	INT,
    `Sold`	INT
);

INSERT INTO `Eur` (`Rating`, `City`, `Days`, `People`, `Avia`, `Viza`, `Sea`, `Price`, `Sold`) VALUES ('5', 'Istanbul', '7', '1', 'y', 'n', 'y', '500', '20 ');
INSERT INTO `Eur` (`Rating`, `City`, `Days`, `People`, `Avia`, `Viza`, `Sea`, `Price`, `Sold`) VALUES ('4', 'Izmir', '7', '2', 'y', 'n', 'y', '750', '30 ');
INSERT INTO `Eur` (`Rating`, `City`, `Days`, `People`, `Avia`, `Viza`, `Sea`, `Price`, `Sold`) VALUES ('3', 'Izmir', '7', '3', 'y', 'n', 'y', '1000', '40 ');
INSERT INTO `Eur` (`Rating`, `City`, `Days`, `People`, `Avia`, `Viza`, `Sea`, `Price`, `Sold`) VALUES ('2', 'Istanbul', '14', '3', 'y', 'n', 'y', '1800', '50 ');
INSERT INTO `Eur` (`Rating`, `City`, `Days`, `People`, `Avia`, `Viza`, `Sea`, `Price`, `Sold`) VALUES ('5', 'New York', '7', '2', 'y', 'y', 'n', '800', '60 ');
INSERT INTO `Eur` (`Rating`, `City`, `Days`, `People`, `Avia`, `Viza`, `Sea`, `Price`, `Sold`) VALUES ('5', 'Chicago', '14', '2', 'y', 'y', 'n', '1500', '70 ');


![table](https://github.com/user-attachments/assets/b038cadd-2344-4d2e-a7e4-428ecf555f02)


1 Пример запроса для получения информации о турах по России и Европе, доступных оператору

SELECT 
    O.OperatorName,
    O.City AS OperatorCity,
    'Russia' AS Region,
    R.TourName,
    R.Price
FROM 
    Operator O
JOIN 
    TourRus R
ON 
    O.City = R.City

UNION ALL
SELECT 
    O.OperatorName,
    O.City AS OperatorCity,
    'Europe' AS Region,
    E.TourName,
    E.Price
FROM 
    Operator O
JOIN 
    TourEur E
ON 
    O.City = E.City;




   2
   -- Пример запроса к таблице Operator, где необходимо вывести вообще все туры из Tour = Rus и Tour = Eur, на одного (где People = 1) и дешевле 750 (где Price < 750)

SELECT 
    O.Country,
    O.City,
    O.Tour,
    R.Rating,
    R.City AS TourCity,
    R.Days,
    R.People,
    R.Avia,
    R.Sea,
    R.Price,
    R.Sold
FROM 
    Operator O
JOIN 
    Rus R
ON 
    O.City = R.City
WHERE 
    O.Tour = 'Rus' 
    AND R.People = 1 
    AND R.Price < 750

UNION ALL

SELECT 
    O.Country,
    O.City,
    O.Tour,
    E.Rating,
    E.City AS TourCity,
    E.Days,
    E.People,
    E.Avia,
    E.Viza,
    E.Sea,
    E.Price,
    E.Sold
FROM 
    Operator O
JOIN 
    Eur E
ON 
    O.City = E.City
WHERE 
    O.Tour = 'Eur' 
    AND E.People = 1 
    AND E.Price < 750;




    3
 Пример запроса к таблице Operator, где необходимо вывести вообще все туры из Tour = Rus и Tour = Eur, где будет море (Sea = y), но без перелета (Avia = n)

SELECT 
    O.Country,
    O.City,
    O.Tour,
    R.Rating,
    R.City AS TourCity,
    R.Days,
    R.People,
    R.Avia,
    R.Sea,
    R.Price,
    R.Sold
FROM 
    Operator O
JOIN 
    Rus R
ON 
    O.City = R.City
WHERE 
    O.Tour = 'Rus' 
    AND R.Sea = 'y' 
    AND R.Avia = 'n'

UNION ALL

SELECT 
    O.Country,
    O.City,
    O.Tour,
    E.Rating,
    E.City AS TourCity,
    E.Days,
    E.People,
    E.Avia,
    E.Viza,
    E.Sea,
    E.Price,
    E.Sold
FROM 
    Operator O
JOIN 
    Eur E
ON 
    O.City = E.City
WHERE 
    O.Tour = 'Eur' 
    AND E.Sea = 'y' 
    AND E.Avia = 'n';



    4
 Пример запроса к таблице Operator, где необходимо вывести вообще все туры из Tour = Rus и Tour = Eur, чтобы отдохнуть где угодно на 14 дней (Days = 14), только не в Чикаго (City != Chicago)

SELECT o.Country, o.City, o.Tour
FROM Operator o
JOIN Rus r ON o.City = r.City AND o.Tour = 'Rus'
JOIN Eur e ON o.City = e.City AND o.Tour = 'Eur'
WHERE (r.Days = 14 OR e.Days = 14)
  AND o.City != 'Chicago';
![4пример](https://github.com/user-attachments/assets/6cbe7684-e832-40b1-94d8-91ac0f1cd035)



5
 Пример запроса к таблице Operator, где необходимо вывести вообще все туры из Tour = Rus, но не Tour != Eur, на 7 дней (Days = 7), где продаж от 140 (Sold >= 140)

SELECT o.Country, o.City, o.Tour
FROM Operator o
JOIN Rus r ON o.City = r.City AND o.Tour = 'Rus'
LEFT JOIN Eur e ON o.City = e.City AND o.Tour = 'Eur'
WHERE r.Days = 7
  AND r.Sold >= 140
  AND e.City IS NULL;


6
Надо написать запрос к Operator, чтобы вывести вообще все туры кроме России (Tour != Rus, Tour = Eur) без визы (Viza = 'n') и цена от 500 (Price > 500)


Eur -создание таблицы
![5406633673089999788](https://github.com/user-attachments/assets/bcd07661-4862-45e0-b086-ea93d75a4e60)

Rus - создание таблицы
    
![5406633673089999789](https://github.com/user-attachments/assets/dd5575f4-3df3-4bbe-b555-012c742822b4)


Проверила данные на пропуски и дубликаты.
![distinct](https://github.com/user-attachments/assets/ff87c095-281d-460d-b9b7-dd59ba95674b)

SELECT DISTINCT o.Country, o.City, o.Tour
FROM Operator o
JOIN Rus r ON o.City = r.City AND o.Tour = 'Rus'
JOIN Eur e ON o.City = e.City AND o.Tour = 'Eur'
WHERE o.Country IS NOT NULL
  AND o.City IS NOT NULL
  AND o.Tour IS NOT NULL
  AND r.Rating IS NOT NULL
  AND r.Days IS NOT NULL
  AND r.People IS NOT NULL
  AND r.Avia IS NOT NULL
  AND r.Sea IS NOT NULL
  AND r.Price IS NOT NULL
  AND r.Sold IS NOT NULL
  AND e.Rating IS NOT NULL
  AND e.Days IS NOT NULL
  AND e.People IS NOT NULL
  AND e.Avia IS NOT NULL
  AND e.Viza IS NOT NULL
  AND e.Sea IS NOT NULL
  AND e.Price IS NOT NULL
  AND e.Sold IS NOT NULL;
