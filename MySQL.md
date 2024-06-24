# MySQL

> ตัวช่วยสำหรับการเขียนภาษา SQL ที่ใช้ใน MySQL Database

## ตำแหน่ง Path ของ MySQL Database ในระบบปฏิบัติการต่างๆ
OS | Locations 
----- | ----- |
Mac | /usr/local/mysql/bin |
Windows | /Program Files/MySQL/**MySQL version**/bin |
Xampp | /xampp/mysql/bin |

## คำสั่งที่เกี่ยวข้องกับการจัดการ User

### คำสั่ง Login เข้าใช้งาน MySQL

```bat
mysql -u username -p
```

### คำสั่ง Login เข้าใช้งาน MySQL `กรณีที่อยู่คนละเครื่อง`

```bat
mysql -h hostname -u username -p
```

### คำสั่งสำหรับแสดงข้อมูล User

```sql
SELECT User, Host FROM mysql.user;
```

### คำสั่งสำหรับสร้าง User

```sql
CREATE USER 'username'@'hostname' IDENTIFIED BY 'passwordkey';
```

### คำสั่งสำหรับลบ User

```sql
DROP USER 'username'@'hostname';
```

### คำสั่งสำหรับการให้สิทธิ์การเข้าถึง Database ทั้งหมดกับ User

```sql
GRANT ALL PRIVILEGES ON * . * TO 'username'@'hostname';

FLUSH PRIVILEGES;
```

### คำสั่งสำหรับแสดงสิทธิ์การเข้าถึง Database ที่ User นั้นได้รับ

```sql
SHOW GRANTS FOR 'username'@'hostname';
```

### คำสั่งสำหรับลบสิทธิ์การเข้าถึง Database ของ User นั้น

```sql
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'username'@'hostname';
```

### คำสั่งสำหรับแก้ไข Host ของ User ที่ต้องการ

```sql
UPDATE mysql.user SET Host='newhostname' WHERE Host='oldhostname' AND User='username';
```

### คำสั่งสำหรับแก้ไข Username ของ User ที่ต้องการ

```sql
RENAME USER 'oldusername'@'localhost' TO 'newusername'@'hostname';
```

### คำสั่งแสดงข้อมูลการตรวจสอบการตั้ง Password `กรณีติด ERROR 1819(HY000)`

```sql
SHOW VARIABLES LIKE 'validate_password%';
```

### คำสั่งแสดงข้อมูล Version ของ MySQL 

* กรณีที่ต้องการใช้ `คำสั่งใช้งานบน Ubuntu`

```sh
sudo mysqladmin -p -u username version
```

* กรณีที่ต้องการใช้ `คำสั่งใช้งานบน Windows`

```bat
mysql -V
```

* กรณีที่ต้องการใช้ `คำสั่งใช้งานบน MySQL`

```sql
STATUS;
```

```sql
SHOW VARIABLES LIKE ‘%version%’;
```

## คำสั่งทั่วไป

### คำสั่งออกจาก MySQL

```sql
exit
```

```sql
\q
```

### คำสั่งแสดง Database ทั้งหมด

```sql
SHOW DATABASES;
```

### คำสั่งสร้าง Database

```sql
CREATE DATABASE databasename;
```

### คำสั่งลบ Database

```sql
DROP DATABASE databasename;
```

### คำสั่งเลือก Database ที่ต้องการใช้งาน

```sql
USE databasename;
```

### คำสั่งแสดง Table ทั้งหมด

```sql
SHOW TABLES;
```

### คำสั่งแสดงโครงสร้างภายใน Table นั้น

```sql
SHOW COLUMNS FROM tablename;
```

### คำสั่งสร้าง Table

```sql
CREATE TABLE tablename (
    id INT AUTO_INCREMENT,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    email VARCHAR(50),
    password VARCHAR(20),
    location VARCHAR(100),
    dept VARCHAR(100),
    is_admin TINYINT(1),
    register_date DATETIME,
    PRIMARY KEY(id)
);
```

### คำสั่งเปลี่ยนแปลงชื่อ Table

```sql
ALTER TABLE oldtablename RENAME newtablename;
```

### คำสั่งลบ Table

```sql
DROP TABLE tablename;
```

### คำสั่งเพิ่ม Column ใน Table นั้น

```sql
ALTER TABLE tablename ADD COLUMN columnname columntype;
```

### คำสั่งเปลี่ยนแปลงชื่อ Column ใน Table นั้น

```sql
ALTER TABLE tablename CHANGE oldcolumnname newcolumnname columntype;
```

### คำสั่งเปลี่ยนแปลงประเภทของ Column ใน Table นั้น

```sql
ALTER TABLE tablename MODIFY columnname newcolumntype;
```

### คำสั่งลบ Column ใน Table นั้น

```sql
ALTER TABLE tablename DROP COLUMN columnname;
```

### คำสั่งเพิ่มข้อมูลลง Column ใน Table นั้น

* กรณีเพิ่มข้อมูล `แบบ Record เดียว`

```sql
INSERT INTO tablename VALUES (value1, value2);
```

```sql
INSERT INTO tablename(columnname1, columnname2) VALUES (value1, value2);
```

* กรณีเพิ่มข้อมูล `แบบหลายๆ Record`

```sql
INSERT INTO tablename VALUES (value1, value2), (value3, value4);
```

```sql
INSERT INTO tablename(columnname1, columnname2) VALUES (value11, value12), (value21, value22);
```

### คำสั่งเปลี่ยนแปลงข้อมูล Column ใน Table นั้น

* กรณีเปลี่ยนแปลงข้อมูล `แบบไม่ระบุ Column อ้างอิง`

```sql
UPDATE tablename SET columnname1=xxx;
```

```sql
UPDATE tablename SET columnname1=xxx, columnname2=xxx;
```

* กรณีเปลี่ยนแปลงข้อมูล `แบบระบุ Column อ้างอิง`

```sql
UPDATE tablename SET columnname1=xxx WHERE columnname2=xxx;
```

```sql
UPDATE tablename SET columnname11=xxx, columnname12=xxx WHERE columnname21=xxx;
```

### คำสั่งลบข้อมูล Column ใน Table นั้น

* กรณีลบข้อมูล `โดยลบข้อมูล Column ทั้งหมดใน Table นั้น`

```sql
DELETE FROM tablename;
```

* กรณีลบข้อมูล `โดยลบเฉพาะข้อมูล Column ที่ต้องการใน Table นั้น`

```sql
DELETE FROM tablename WHERE columnname=xxx;
```

### คำสั่งแสดงข้อมูล Column ใน Table นั้น

* กรณีแสดงข้อมูล Column `โดยแสดงข้อมูลทุก Column ใน Table นั้น`

```sql
SELECT * FROM tablename;
```

* กรณีแสดงข้อมูล Column `โดยแสดงข้อมูล Column ที่ต้องการใน Table นั้น`

```sql
SELECT columnname FROM tablename;
```

```sql
SELECT columnname1, columnname2 FROM tablename;
```

```sql
SELECT tablename1 columnname1, tablename2 columnname2 FROM tablename1, tablename2;
```

* กรณีแสดงข้อมูล Column `ในกรณีอื่นๆ` โดยจะระบุหรือไม่ก็ได้ ขึ้นอยู่กับความต้องการ เช่น
    * `WHERE` ตามด้วยเงื่อนไขที่ต้องการเพื่อ ระบุว่าจะดึงข้อมูลออกมาจากตำแหน่งใด
    * `GROUP BY` ตามด้วยชื่อ Column เพื่อระบุ Column ที่ต้องการแบ่งกลุ่ม Record
    * `HAVING` ตามหลัง `GROUP BY` พร้อมระบุเงื่อนไขเพื่อกำหนดรูปแบบการแบ่งกลุ่ม Record ใน Column นั้น
    * `ORDER BY` ตามด้วยชื่อ Column เพื่อระบุ Column ที่ต้องการเรียงข้อมูลจากน้อยไปมาก และจะใส่ `DESC` ตามหลัง `ORDER BY` ต่อเมื่อต้องการเรียงข้อมูลจากมากไปน้อย
    * `LIMIT` ตามด้วยเลขช่วงที่ต้องการเพื่อกำหนดช่วงของจำนวน Record ใน Column ที่ต้องการแสดงผล

```sql
SELECT columnname1 FROM tablename WHERE columnname2=xxx GROUP BY columnname3 HAVING groupbycondition ORDER BY columnname4 LIMIT limitrange;
```

```sql
SELECT columnname1 FROM tablename WHERE columnname2=xxx GROUP BY columnname3 HAVING groupbycondition ORDER BY columnname4 DESC LIMIT startrange, endrange;
```

### คำสั่งตั้งชื่อ Column ใน Table นั้น

```sql
SELECT columnname AS editcolumnname FROM tablename;
```

```sql
SELECT columnname1 AS editcolumnname1, columnname2 AS editcolumnname2 FROM tablename;
```

### คำสั่งกำหนดเงื่อนไขแสดงข้อมูลของ Column ใน Table นั้น

```sql
SELECT columnname1 FROM tablename WHERE columnname2=xxx;
```

### คำสั่งแสดงข้อมูลที่ซ้ำกันของ Column ใน Table นั้น ให้รวบเป็น Record เดียว

```sql
SELECT DISTINCT columnname FROM tablename;
```

### คำสั่งแสดงจำนวนข้อมูลของ Column ใน Table นั้น ที่ถูกเรียกขึ้น

```sql
SELECT COUNT(columnname) FROM tablename;
```

### คำสั่งแสดงการจัดกลุ่มข้อมูลของ Column ใน Table นั้น

```sql
SELECT columnname1 FROM tablename GROUP BY columnname2;
```

### คำสั่งแสดงการเรียงข้อมูลของ Column ใน Table นั้น

* กรณีแสดงข้อมูล Column `เรียงจากน้อยไปมาก หรือ A-Z`

```sql
SELECT columnname1 FROM tablename ORDER BY columnname2;
```

* กรณีแสดงข้อมูล Column `เรียงจากมากไปน้อย หรือ Z-A`

```sql
SELECT columnname1 FROM tablename ORDER BY columnname2 DESC;
```

```sql
SELECT columnname11 FROM tablename ORDER BY columnname21 DESC, columnname22 DESC;
```

```sql
SELECT columnname11 FROM tablename ORDER BY columnname21 DESC, columnname22;
```

### คำสั่งแสดงการกำหนดจำนวน Record ในการแสดงผลลัพธ์ของ Column ใน Table นั้น

* กรณีแสดง Record `แบบระบุจำนวน Record ที่ต้องการให้แสดง`

```sql
SELECT columnname1 FROM tablename LIMIT limitrange;
```

* กรณีแสดง Record `แบบระบุช่วงของ Record ที่ต้องการให้แสดง (โดยนับตำแหน่งที่ 0 เป็นตำแหน่งแรก)`

```sql
SELECT columnname1 FROM tablename LIMIT startrange, endrange;
```

> Update ข้อมูลล่าสุด : 24/06/2024 เวลา 11.36 น.