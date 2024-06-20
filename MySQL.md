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
```bash
mysql -u root -p
```

### คำสั่งสำหรับแสดงข้อมูล User

```sql
SELECT User, Host FROM mysql.user;
```

### คำสั่งสำหรับสร้าง User

```sql
CREATE USER 'user-name'@'localhost' IDENTIFIED BY 'password-key';
```

### คำสั่งสำหรับลบ User

```sql
DROP USER 'user-name'@'localhost';
```

### คำสั่งสำหรับการให้สิทธิ์การเข้าถึง Database ทั้งหมดกับ User

```sql
GRANT ALL PRIVILEGES ON * . * TO 'user-name'@'localhost';
FLUSH PRIVILEGES;
```

### คำสั่งสำหรับแสดงสิทธิ์การเข้าถึง Database ที่ User นั้นได้รับ

```sql
SHOW GRANTS FOR 'user-name'@'localhost';
```

### คำสั่งสำหรับลบสิทธิ์การเข้าถึง Database ของ User นั้น

```sql
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'user-name'@'localhost';
```

## คำสั่งโดยทั่วไป

### คำสั่งออกจาก MySQL

```bash
exit;
```

### คำสั่งแสดง Database ทั้งหมด

```bash
SHOW DATABASES
```

### คำสั่งสร้าง Database

```bash
CREATE DATABASE database-name;
```

### คำสั่งลบ Database

```bash
DROP DATABASE database-name;
```

### คำสั่งเลือก Database ที่ต้องการใช้งาน

```bash
USE database-name;
```