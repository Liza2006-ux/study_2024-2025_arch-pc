---
## Front matter
Обработка данных и визуализация
Волчкова Елизавета 
НКАбд-01-24

Предобработка данных и их изучения.
1. Выведите по 5 строк с каждой таблицы.
2. Введите информацию о каждой таблицы и изучите их (возможно есть какие-то странности. Опишите
полученные данные.
3. Проверьте данные на пропуски и дубликаты.
4. Вычислите сводную (описательную) статистику о данных датафреймов (таблиц) и выведите ее.
5. Если в некоторых столбцах нужно изменить данные, измените их и аргументируйте зачем их стоит
изменить (например, дата должна иметь тип данных datetime64, а не object).


https://www.db-fiddle.com/f/u5ekzMZFW7dq2D2Nz8FgTn/11
Выполнение проекта
Таблица по турам в Европу и по России,  в которой преведены страны по Европе и города, города по России, 
Есть таблица оператора, который может подобрать тур по России или по Европе. 
Связь с таблицами Россия и Европа у оператора идёт по столбцу город ("City"). 
Доступ к подробной информации таблиц у оператора идёт через "Tour" Rus или Eur

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




 Пример запроса для получения информации о турах по России и Европе, доступных оператору
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


Проверила данные на пропуски и дубликаты.

Вопросы:
1.
