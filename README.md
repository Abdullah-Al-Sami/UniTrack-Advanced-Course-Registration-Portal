````markdown
# UniTrack — Advanced Course Registration Portal

**UniTrack** is a database-driven web application for managing university course enrollments and academic administration. Built with **HTML, CSS, Bootstrap, PHP, and MySQL**, UniTrack streamlines student registration, course management, departmental coordination, notices, and secure user authentication while providing a responsive, user-friendly interface for both students and administrators.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Repository Contents](#repository-contents)
- [Prerequisites](#prerequisites)
- [Local Installation (XAMPP / Windows)](#local-installation-xampp--windows)
- [Alternative Installation (Linux)](#alternative-installation-linux)
- [Database Import & SQL Notes](#database-import--sql-notes)
- [Configuration (DB / App)](#configuration-db--app)
- [Running the App Locally](#running-the-app-locally)
- [Deployment (cPanel / Shared Host)](#deployment-cpanel--shared-host)
- [Git & GitHub — Step-by-step (fixes included)](#git--github---step-by-step-fixes-included)
- [Recommended .gitignore](#recommended-gitignore)
- [Security Checklist](#security-checklist)
- [Troubleshooting](#troubleshooting)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)
- [License & Contact](#license--contact)

---

## Project Overview
UniTrack implements the full lifecycle of online course registration: session/semester management, department & course setup, student enrollment, news/notice board, enrollment history, admin and student authentication, user logs, and profile management. It is intended for academic use and designed to be simple to deploy on Apache/PHP + MySQL environments.

## Key Features
- Admin panel: manage courses, departments, sessions, semesters, students, and notices
- Student panel: login, view courses, enroll, view enrollment history, change password, pin verification
- Enrollment invoice / printable receipts
- User login history and activity logs
- Responsive UI using Bootstrap
- SQL dump for initial data (sample departments, courses, and students)

## Tech Stack
- Front-end: HTML5, CSS3, Bootstrap, JavaScript (vanilla)
- Back-end: PHP (compatible with PHP 7.4+ / 8.x)
- Database: MySQL / MariaDB
- Web Server: Apache (XAMPP, WAMP, LAMP, or cPanel)

## Repository Contents (short)
- `index.php`, `admin/`, `includes/`, `assets/`, `pictures/`, `studentphoto/`
- `onlinecourse.sql` — database dump
- `ER.jpg` — ER diagram
- `Documentation/` — project report and screenshots

> ⚠️ **Important:** The repository may contain test data (student reg numbers, photos, pincode files). Before publishing publicly, remove or sanitize any sensitive/personal data.

---

## Prerequisites
- XAMPP/WAMP (Windows) or LAMP stack (Linux) with Apache, PHP, MySQL
- phpMyAdmin (for importing `onlinecourse.sql`) or MySQL client
- Git and a GitHub account
- Basic command-line familiarity (PowerShell / Bash)

---

## Local Installation (XAMPP / Windows)
```powershell
git clone https://github.com/Abdullah-Al-Sami/UniTrack-Advanced-Course-Registration-Portal.git
cd "UniTrack-Advanced-Course-Registration-Portal"
Copy-Item -Path ".\*" -Destination "C:\xampp\htdocs\UniTrack" -Recurse
````

1. Start Apache & MySQL in XAMPP.
2. Create a new database `onlinecourse` in phpMyAdmin.
3. Import `onlinecourse.sql`.
4. Update DB credentials in `includes/config.php`.
5. Run the app at `http://localhost/UniTrack`.

---

## Alternative Installation (Linux)

```bash
sudo apt update
sudo apt install apache2 php php-mysql mysql-server
sudo systemctl enable --now apache2 mysql
sudo cp -R /path/to/UniTrack /var/www/html/unitrack
sudo chown -R www-data:www-data /var/www/html/unitrack
sudo chmod -R 755 /var/www/html/unitrack
```

---

## Database Import & SQL Notes

```bash
mysql -u root -p onlinecourse < onlinecourse.sql
```

If import fails, check for smart quotes (`‘` `’`) and replace with standard quotes (`'`).

---

## Configuration (DB / App)

```php
<?php
$DB_HOST = 'localhost';
$DB_USER = 'root';
$DB_PASS = '';
$DB_NAME = 'onlinecourse';

$conn = new mysqli($DB_HOST, $DB_USER, $DB_PASS, $DB_NAME);
if ($conn->connect_error) {
    die('Connection failed: ' . $conn->connect_error);
}
?>
```

---

## Running the App Locally

* Start Apache & MySQL
* Visit `http://localhost/UniTrack`

Default login (sample data):

```
Admin: admin / admin
Student: 213002039 / 420612
```

---

## Deployment (cPanel / Shared Host)

1. Upload project via File Manager or FTP.
2. Create MySQL DB & user in cPanel.
3. Import `onlinecourse.sql`.
4. Update DB credentials.

---

## Git & GitHub — Step-by-step (fixes included)

```powershell
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/Abdullah-Al-Sami/UniTrack-Advanced-Course-Registration-Portal.git
git push -u origin main
```

Fix common errors:

* `nothing added to commit but untracked files present` → run `git add .`
* `src refspec main does not match any` → no commit yet; commit and rename branch

---

## Recommended .gitignore

```
.DS_Store
Thumbs.db
.idea/
.vscode/
node_modules/
vendor/
studentphoto/
onlinecourse.sql
id passes.txt
.env
```

---

## Security Checklist

* Remove personal/sensitive data.
* Use prepared statements for SQL queries.
* Replace MD5 with bcrypt.
* Validate/sanitize user input.
* Disable directory listing.
* Use HTTPS in production.

---

## Troubleshooting

* **SQL import error:** ensure UTF-8 encoding.
* **PHP errors:** check `error_log`.
* **Git push errors:** ensure `git branch -M main` before pushing.

---

## Future Improvements

* Add result management & billing module.
* Role-based access control.
* REST API support.
* Two-factor authentication for admin.

---

## Contributing

1. Fork this repo.
2. Create feature branch: `git checkout -b feature/new-feature`
3. Commit & push: `git push origin feature/new-feature`
4. Submit Pull Request.

---

## License & Contact

Project for academic/demo use.

**Author:** Md. Abdullah Al Sami
**GitHub:** [Abdullah-Al-Sami](https://github.com/Abdullah-Al-Sami)

```
```
