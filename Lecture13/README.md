sudo mysql -u root -p
:wq

1. Створення бази даних: Створіть базу даних з назвою SchoolDB:
CREATE DATABASE SchoolDB;

USE SchoolDB;

2. Таблиця Institutions: Створіть таблицю Institutions, яка зберігатиме інформацію про школи та дитячі садочки:
CREATE TABLE Institutions (
institution_id INT PRIMARY KEY AUTO_INCREMENT,
institution_name VARCHAR(100),
institution_type ENUM('School', 'Kindergarten'),
address VARCHAR(255)
);

3. Таблиця Classes:
CREATE TABLE Classes (
class_id INT PRIMARY KEY AUTO_INCREMENT,
class_name VARCHAR(100),
institution_id INT,
direction ENUM('Mathematics', 'Biology and Chemistry', 'Language Studies'),
FOREIGN KEY (institution_id) REFERENCES Institutions(institution_id)
);

4. Таблиця Children:
CREATE TABLE Children (
child_id INT PRIMARY KEY AUTO_INCREMENT,
first_name VARCHAR(50),
last_name VARCHAR(50),
birth_date DATE,
year_of_entry INT,
age INT,
institution_id INT,
class_id INT,
FOREIGN KEY (institution_id) REFERENCES Institutions(institution_id),
FOREIGN KEY (class_id) REFERENCES Classes(class_id)
);

5. Таблиця Parents:
CREATE TABLE Parents (
parent_id INT PRIMARY KEY AUTO_INCREMENT,
first_name VARCHAR(50),
last_name VARCHAR(50),
child_id INT,
tuition_fee DECIMAL(10, 2),
FOREIGN KEY (child_id) REFERENCES Children(child_id)
);

6. Операції з даними:
INSERT INTO Institutions (institution_name, institution_type, address)
VALUES
('Zelenyi Licei', 'School', '123 Shkilna St, Zelenyi'),
('Mali Zirkachky', 'Kindergarten', '456 Dytiachyi Shliakh, Zelenyi'),
('Rivniy Akademiia', 'School', '789 Rivnenska Blvd, Rivne');

INSERT INTO Classes (class_name, institution_id, direction)
VALUES
('Matematyka 101', 1, 'Matematyka'),
('Biologiia i Khimiia', 1, 'Biologiia i Khimiia'),
('Mova i Literatyra 201', 3, 'Movni Doslidzhennia');

INSERT INTO Children (first_name, last_name, birth_date, year_of_entry, age, institution_id, class_id)
VALUES
('Ivan', 'Kozak', '2015-03-12', 2021, 9, 1, 1),
('Olha', 'Tkachenko', '2016-07-22', 2022, 8, 2, 2),
('Dmytro', 'Petrenko', '2014-11-30', 2020, 10, 3, 3); 

INSERT INTO Parents (first_name, last_name, child_id, tuition_fee)
VALUES
('Mykola', 'Kozak', 1, 1500.00),  
('Svitlana', 'Tkachenko', 2, 1200.50), 
('Volodymyr', 'Petrenko', 3, 2000.00); 

7.1. Отримайте список всіх дітей разом із закладом, в якому вони навчаються, та напрямом навчання в класі
SELECT
c.first_name AS child_first_name,
c.last_name AS child_last_name,
i.institution_name AS institution,
cl.class_name AS class_name,
cl.direction AS class_direction
FROM
Children c
JOIN
Institutions i ON c.institution_id = i.institution_id
JOIN
Classes cl ON c.class_id = cl.class_id;
![Image1](images/childInfo.png)

7.2. Отримайте інформацію про батьків і їхніх дітей разом із вартістю навчання
SELECT
p.first_name AS parent_first_name,
p.last_name AS parent_last_name,
c.first_name AS child_first_name,
c.last_name AS child_last_name,
p.tuition_fee AS tuition_fee
FROM
Parents p
JOIN
Children c ON p.child_id = c.child_id;
![Image2](images/parAndChildr.png)

7.3. Отримайте список всіх закладів з адресами та кількістю дітей, які навчаються в кожному закладі
SELECT
i.institution_name AS institution,
i.address AS address,
COUNT(c.child_id) AS number_of_children
FROM
Institutions i
LEFT JOIN
Children c ON i.institution_id = c.institution_id
GROUP BY
i.institution_id, i.institution_name, i.address;
![Image3](images/ChildrenNumber.png)

8. Зробіть бекап бази та застосуйте його для нової бази даних і перевірте, що цілісність даних не порушено
sudo mysqldump -u root -p SchoolDB > SchoolDB_backup.sql
![Image4](images/Terminal 2024-12-06 17.19.43.png)

mysqldump -u root -p SchoolDB > /home/vagrant/SchoolDB_backup.sql

CREATE DATABASE SchoolDB_New;

mysql -u root -p SchoolDB_New < /home/vagrant/SchoolDB_backup.sql

USE SchoolDB_New;
SHOW TABLES;

![Image4](images/Terminal 2024-12-06 18.17.10.png)
- Бачимо, що ті ж самі таблиці, що і в початковій базі, присутні в новій

(P.S. Спочатку в мене не вийшло зробити бекап під sudo, потім я налаштувала юзера з паролем, і тоді під цим юзером вдалося)