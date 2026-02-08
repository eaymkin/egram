# ⚡ Быстрый деплой (5 минут)

Самая быстрая инструкция для деплоя на Render.

## 1️⃣ Подготовка (1 мин)

```bash
# Перейдите в папку проекта
cd "c:\Users\eaymk_mvlkdvh\Новая папка (2)"

# Инициализируйте Git
git init
git add .
git commit -m "Initial commit"
```

## 2️⃣ GitHub (1 мин)

1. Создайте репозиторий на https://github.com/new
2. Загрузите код:
```bash
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git
git push -u origin main
```

## 3️⃣ Backend на Render (2 мин)

1. Откройте https://dashboard.render.com
2. New + → Web Service
3. Подключите GitHub репозиторий
4. Настройки:
   - Root Directory: `backend`
   - Build Command: `./build.sh`
   - Start Command: `gunicorn config.wsgi:application`
5. Add Database → PostgreSQL
6. Environment Variables:
   ```
   SECRET_KEY = [Generate]
   DEBUG = False
   ALLOWED_HOSTS = YOUR_SERVICE_NAME.onrender.com
   ```
7. Create Web Service

⏱️ Ждите 5-10 минут...

## 4️⃣ Frontend на Render (1 мин)

1. New + → Static Site
2. Подключите тот же репозиторий
3. Настройки:
   - Root Directory: `frontend`
   - Build Command: `npm install && npm run build`
   - Publish Directory: `build`
4. Environment Variable:
   ```
   REACT_APP_API_URL = https://YOUR_BACKEND_URL.onrender.com/api
   ```
5. Create Static Site

⏱️ Ждите 3-5 минут...

## 5️⃣ Финальные настройки (30 сек)

1. Вернитесь к Backend сервису
2. Environment → Добавьте:
   ```
   FRONTEND_URL = https://YOUR_FRONTEND_URL.onrender.com
   ```
3. Save Changes (автоматически редеплоится)

## ✅ Готово!

Ваше приложение онлайн!

- **Frontend**: https://YOUR_FRONTEND_URL.onrender.com
- **Backend API**: https://YOUR_BACKEND_URL.onrender.com/api
- **Admin**: https://YOUR_BACKEND_URL.onrender.com/admin

### Создание суперпользователя

Backend → Shell:
```bash
cd backend
python manage.py createsuperuser
```

---

**Проблемы?** См. полную инструкцию в [DEPLOYMENT.md](DEPLOYMENT.md)
