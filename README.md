# Secure Login Audit Starter

نظام تسجيل دخول آمن مبني باستخدام Laravel + Docker، مزود بميزات متقدمة مثل تسجيل محاولات الدخول، حماية ضد الهجمات، عرض سجلات الدخول للمشرف، حماية الجلسات، والمزيد.

---

## Features

- ✅ تسجيل محاولات الدخول الناجحة والفاشلة مع IP و User-Agent ووقت الدخول.
- 🚨 تنبيه عند رصد محاولات brute-force.
- 👮 صفحة خاصة للمشرف لعرض جميع سجلات الدخول (Audit Logs).
- 🔐 حماية الجلسات وتخزينها في قاعدة البيانات.
- 🛡️ حماية مدمجة ضد CSRF و XSS.
- 🐳 جاهز للعمل باستخدام Docker.
-  Laravel Breeze (Auth Scaffolding) سريع وخفيف.

---

## Installation (Manual Setup)

> **متطلبات التشغيل يدويًا:**
> - PHP 8.2+
> - Composer
> - MySQL
> - Node.js + npm

### 1. Clone الريبو

```bash
git clone https://github.com/Solimansorks/secure-login-audit-starter.git
cd secure-login-audit-starter
```

### 2. إعداد Laravel

```bash
composer install
cp .env.example .env
php artisan key:generate
```

### 3. إعداد قاعدة البيانات

- أنشئ قاعدة بيانات جديدة باسم: `secure_login`
- حدّث بيانات الاتصال داخل ملف `.env`

```env
DB_DATABASE=secure_login
DB_USERNAME=root
DB_PASSWORD=your_password
```

### 4. Run migrations

```bash
php artisan migrate
```

### 5. إعداد الواجهة

```bash
npm install
npm run dev
```

### 6. شغل التطبيق

```bash
php artisan serve
```

افتح: `http://localhost:8000`

---

## Using Docker (بدون إعداد محلي)

> **المتطلبات الوحيدة:**  
> - [Docker](https://www.docker.com/)  
> - [Docker Compose](https://docs.docker.com/compose/)

### 1. شغل المشروع داخل Docker

```bash
docker compose up -d --build
```

### 2. الدخول للحاوية (Container)

```bash
docker exec -it secure_laravel_app bash
```

### 3. داخل الحاوية، شغل:

```bash
composer install
php artisan migrate
npm install
npm run build
```

### 4. افتح في المتصفح:

```
http://localhost:8001
```

---

##  Security Features

| الميزة                        | التفاصيل |
|------------------------------|----------|
| تسجيل محاولات الدخول         | يتم تسجيل كل محاولة مع IP و Agent والنجاح أو الفشل |
| تنبيه اختراق محتمل          | يتم تسجيل الإنذارات عند تكرار محاولات فشل متعددة |
| حماية الجلسات               | الجلسات مخزنة في قاعدة البيانات |
| حماية CSRF                  | مفعّلة تلقائيًا في Laravel |
| حماية XSS                   | مفعّلة افتراضيًا داخل Blade |

---

##  Admin Routes

| الصفحة         | الرابط              | ملاحظات                     |
|----------------|---------------------|------------------------------|
| لوحة التحكم     | `/dashboard`         | تتطلب تسجيل دخول             |
| سجل الدخول     | `/audit-logs`        | تتطلب صلاحية المشرف         |
| إعدادات الحساب | `/profile`           | تعديل معلومات المستخدم      |

---

##  Folder Structure

```txt
secure-login-audit-starter/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   └── Middleware/
│   ├── Models/
│   └── Providers/
├── database/
│   ├── migrations/
│   └── seeders/
├── public/
├── resources/
│   ├── views/
│   └── js/
├── routes/
│   ├── web.php
│   └── auth.php
├── docker-compose.yml
├── Dockerfile
└── .env
```

---

##  Developer

- 👤 **Mohamed Soliman**
-  GitHub: [@Solimansorks](https://github.com/Solimansorks)

---

##  License

هذا المشروع مفتوح المصدر ومتاح بموجب رخصة [MIT License](LICENSE).
