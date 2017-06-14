Create a list of students showing first and last names only.

mysql> select first_name,last_name
    -> from student;
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Eric       | Ephram    |
| Greg       | Gould     |
| Adam       | Ant       |
| Howard     | Hess      |
| Charles    | Caldwell  |
| James      | Joyce     |
| Doug       | Dumas     |
| Kevin      | Kraft     |
| Frank      | Fountain  |
| Brian      | Biggs     |
+------------+-----------+
10 rows in set (0.00 sec)




Create a list of students with all the columns but only if the student has less than 8 years experience

mysql> select *
    -> from student
    -> where years_of_experience < 8;
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          1 | Eric       | Ephram    |                   2 | 2016-03-31 |
|          2 | Greg       | Gould     |                   6 | 2016-09-30 |
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
|          4 | Howard     | Hess      |                   1 | 2016-02-28 |
|          5 | Charles    | Caldwell  |                   7 | 2016-05-07 |
|          8 | Kevin      | Kraft     |                   3 | 2016-04-15 |
|         10 | Brian      | Biggs     |                   4 | 2015-12-25 |
+------------+------------+-----------+---------------------+------------+
7 rows in set (0.00 sec)



Create a list of students showing the lastname, startdate, and id columns only and sorted by last_name in ascending sequence

mysql> select last_name,start_date,student_id
    -> from student
    -> order by last_name;
+-----------+------------+------------+
| last_name | start_date | student_id |
+-----------+------------+------------+
| Ant       | 2016-06-02 |          3 |
| Biggs     | 2015-12-25 |         10 |
| Caldwell  | 2016-05-07 |          5 |
| Dumas     | 2016-07-04 |          7 |
| Ephram    | 2016-03-31 |          1 |
| Fountain  | 2016-01-31 |          9 |
| Gould     | 2016-09-30 |          2 |
| Hess      | 2016-02-28 |          4 |
| Joyce     | 2016-08-27 |          6 |
| Kraft     | 2016-04-15 |          8 |
+-----------+------------+------------+
10 rows in set (0.00 sec)



Create a list of students showing all columns but only if the student first name is Adam, James, or Frank and sort them in last_name descending sequence.

mysql> select *
    -> from student
    -> where first_name in ('adam','james','frank')
    -> order by last_name desc;
+------------+------------+-----------+---------------------+------------+
| student_id | first_name | last_name | years_of_experience | start_date |
+------------+------------+-----------+---------------------+------------+
|          6 | James      | Joyce     |                   9 | 2016-08-27 |
|          9 | Frank      | Fountain  |                   8 | 2016-01-31 |
|          3 | Adam       | Ant       |                   5 | 2016-06-02 |
+------------+------------+-----------+---------------------+------------+
3 rows in set (0.00 sec)



Create a list of students showing firstname, lastname and startdate where the startdate is between Jan 1, 2016 and June 30, 2016 and order the list by descending start_date sequence.

mysql> select first_name, last_name, start_date
    -> from student
    -> where start_date between '2016-01-01' and '2016-06-30'
    -> order by start_date desc;
+------------+-----------+------------+
| first_name | last_name | start_date |
+------------+-----------+------------+
| Adam       | Ant       | 2016-06-02 |
| Charles    | Caldwell  | 2016-05-07 |
| Kevin      | Kraft     | 2016-04-15 |
| Eric       | Ephram    | 2016-03-31 |
| Howard     | Hess      | 2016-02-28 |
| Frank      | Fountain  | 2016-01-31 |
+------------+-----------+------------+
6 rows in set (0.00 sec)



assignmennt table stuff

mysql> describe assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| grade          | varchar(30)      | YES  |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)


mysql> alter table assignment drop column grade;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
4 rows in set (0.01 sec)


mysql> alter table assignment add column grade_id int;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11)          | YES  |     | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)



grade

mysql> CREATE TABLE `grade` (
    ->   grade_id int(11) unsigned NOT NULL AUTO_INCREMENT,
    ->   grade varchar(30) DEFAULT NULL,
    ->   PRIMARY KEY (grade_id)
    ->   );
Query OK, 0 rows affected (0.02 sec)

mysql> describe grade
    -> ;
+----------+------------------+------+-----+---------+----------------+
| Field    | Type             | Null | Key | Default | Extra          |
+----------+------------------+------+-----+---------+----------------+
| grade_id | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| grade    | varchar(30)      | YES  |     | NULL    |                |
+----------+------------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)


mysql> alter table assignment drop column grade_id;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql>


adding foreign Key

mysql> ALTER TABLE assignment ADD CONSTRAINT fk_assignment
    -> FOREIGN KEY ( grade_id ) REFERENCES grade ( grade_id ) ON DELETE CASCADE ON UPDATE RESTRICT;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> describe assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11) unsigned | NO   | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> explain assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11)          | NO   |     | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11) unsigned | NO   | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> select * from assignment;
+---------------+------------+----------------+----------+----------+
| assignment_id | student_id | assignment_nbr | class_id | grade_id |
+---------------+------------+----------------+----------+----------+
|             1 |         10 |             20 |        1 |        1 |
|             2 |          9 |             10 |        1 |        2 |
|             3 |          8 |             19 |        1 |        5 |
|             4 |          7 |             18 |        1 |        3 |
|             5 |          6 |             18 |        1 |        4 |
|             6 |          5 |             18 |        1 |        2 |
+---------------+------------+----------------+----------+----------+
6 rows in set (0.00 sec)

mysql>


mysql> explain grade;
+----------+------------------+------+-----+---------+----------------+
| Field    | Type             | Null | Key | Default | Extra          |
+----------+------------------+------+-----+---------+----------------+
| grade_id | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| grade    | varchar(30)      | YES  |     | NULL    |                |
+----------+------------------+------+-----+---------+----------------+
2 rows in set (0.00 sec)

mysql>


mysql> select * from grade;
+----------+-----------------------------+
| grade_id | grade                       |
+----------+-----------------------------+
|        1 | Incomplete                  |
|        2 | Complete and unsatisfactory |
|        3 | Complete and statisfactory  |
|        4 | Exceeds expectations        |
|        5 | Not Graded                  |
+----------+-----------------------------+
5 rows in set (0.00 sec)



mysql> ALTER TABLE assignment ADD FOREIGN KEY
    -> (student_id) REFERENCES student(student_id);
Query OK, 6 rows affected (0.02 sec)
Records: 6  Duplicates: 0  Warnings: 0


mysql> describe assignment;
+----------------+------------------+------+-----+---------+----------------+
| Field          | Type             | Null | Key | Default | Extra          |
+----------------+------------------+------+-----+---------+----------------+
| assignment_id  | int(11) unsigned | NO   | PRI | NULL    | auto_increment |
| student_id     | int(11) unsigned | NO   | MUL | NULL    |                |
| assignment_nbr | int(11)          | NO   |     | NULL    |                |
| class_id       | int(11)          | YES  |     | NULL    |                |
| grade_id       | int(11) unsigned | NO   | MUL | NULL    |                |
+----------------+------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)
