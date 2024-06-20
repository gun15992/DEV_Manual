# Laravel 

> การสร้าง Project และเขียนคำสั่งของ Laravel ในที่นี้จะใช้กับระบบปฏิบัติการ Windows เท่านั้น

## ขั้นตอนการติดตั้ง Laravel

### คำสั่งสร้าง Project

* เข้าไปที่ Command Prompt (CMD) แล้ว cd เข้าไปที่ Path ของ Folder ที่ต้องการสร้าง Project จากนั้นพิมพ์คำสั่ง 

```bash
composer create-project laravel/laravel project-name
```

* หรือ สามารถสร้าง Project โดย Install ในรูปแบบ Global โดยพิมพ์คำสั่ง

```bash
composer global require laravel/installer
 
laravel new project-name
```

### คำสั่งเริ่มการทำงาน Project

* ในการเริ่มการการทำงาน Project ทุกครั้ง ให้ cd เข้าไปที่ Folder ที่ตั้งเป็นชื่อ Project จากนั้นหากต้องการเริ่มการทำงาน Project ที่เราสร้างขึ้นเพื่อดูผลลัพธ์การทำงาน สามารถทำได้โดยพิมพ์คำสั่ง

```bash
cd project-name
 
php artisan serve
```

## การแสดงรายละเอียดโดยรวมของ Laravel

### คำสั่งแสดงรายละเอียดโดยรวม

* ในการเเสดงข้อมูลรายละเอียดโดยรวมของ Laravel สามารถทำได้โดยพิมพ์คำสั่ง

```bash
php artisan about
```