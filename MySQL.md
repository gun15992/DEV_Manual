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
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password-key';
```

### คำสั่งสำหรับลบ User

```sql
DROP USER 'username'@'localhost';
```

### คำสั่งสำหรับการให้สิทธิ์การเข้าถึง Database ทั้งหมดกับ User

```sql
GRANT ALL PRIVILEGES ON * . * TO 'username'@'localhost';
FLUSH PRIVILEGES;
```

### คำสั่งสำหรับแสดงสิทธิ์การเข้าถึง Database ที่ User นั้นได้รับ

```sql
SHOW GRANTS FOR 'username'@'localhost';
```

### คำสั่งสำหรับลบสิทธิ์การเข้าถึง Database ของ User นั้น

```sql
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'username'@'localhost';
```

### คำสั่งสำหรับแก้ไข Host ของ User ที่ต้องการ

```sql
UPDATE mysql.user SET Host='newhost' WHERE Host='oldhost' AND User='username';
```

### คำสั่งสำหรับแก้ไข Username ของ User ที่ต้องการ

```sql
RENAME USER 'oldusername'@'localhost' TO 'newusername'@'localhost';
```

### คำสั่งแสดงข้อมูลการตรวจสอบการตั้ง Password `กรณีติด ERROR 1819(HY000) เกี่ยวกับการตั้ง Password ไม่ปลอดภัย`

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

หรือ

```sql
SHOW VARIABLES LIKE ‘%version%’;
```

## คำสั่งทั่วไป

### คำสั่งออกจาก MySQL

```sql
exit;
```

### คำสั่งแสดง Database ทั้งหมด

```sql
SHOW DATABASES;
```

### คำสั่งสร้าง Database

```sql
CREATE DATABASE database-name;
```

### คำสั่งลบ Database

```sql
DROP DATABASE database-name;
```

### คำสั่งเลือก Database ที่ต้องการใช้งาน

```sql
USE database-name;
```

### คำสั่งแสดง Table

```sql
SHOW TABLES;
```

### คำสั่งสร้าง Table

```sql
CREATE TABLE table-name (
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

### คำสั่งลบ Table

```sql
DROP TABLE table-name;
```

### คำสั่งเพิ่มข้อมูลลงใน Table `แบบ Record เดียว`

```sql
INSERT INTO users (
    first_name, 
    last_name, email, 
    password, 
    location, 
    dept, is_admin, 
    register_date
) values ('Brad', 'Traversy', 'brad@gmail.com', '123456','Massachusetts', 'development', 1, now());
```