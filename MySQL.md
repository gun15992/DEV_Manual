# MySQL

> ตัวช่วยสำหรับการเขียนภาษา SQL ที่ใช้ใน MySQL Database

## ตำแหน่ง Path ของ MySQL ในระบบปฏิบัติการต่างๆ
OS | Locations 
----- | ----- |
Mac | /usr/local/mysql/bin |
Windows | /Program Files/MySQL/**MySQL version**/bin |
Xampp | /xampp/mysql/bin |

## คำสั่ง Login
```bash
mysql -u root -p
```

## ตำสั่งสำหรับ Show Users

```sql
SELECT User, Host FROM mysql.user;
```

## ตำสั่งสำหรับ Create User

```sql
CREATE USER 'someuser'@'localhost' IDENTIFIED BY 'somepassword';
```