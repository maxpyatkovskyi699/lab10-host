# Lab10 - Django Deployment

Невеликий Django-проєкт, підготовлений для запуску локально та деплою на Railway з використанням PostgreSQL.

## Встановлення

Клонувати репозиторій:

```bash
git clone https://github.com/maxpyatkovskyi699/lab10-host.git
cd lab10-host
```

Встановити залежності:

```bash
pip install -r requirements.txt
```

## Налаштування змінних середовища

Створити файл `.env` у корені проєкту:

```env
SECRET_KEY=your_secret_key
DEBUG=True
ALLOWED_HOSTS=127.0.0.1,localhost
DATABASE_URL=postgres://user:password@localhost:5432/dbname
```

## Запуск проєкту

Виконати міграції:

```bash
python manage.py makemigrations
python manage.py migrate
```

Запустити сервер:

```bash
python manage.py runserver 8000
```

Після запуску застосунок буде доступний за адресою:

```
http://127.0.0.1:8000
```

## Деплой на Railway

1. Завантажити проєкт на GitHub.
2. Створити новий проєкт у Railway.
3. Підключити GitHub-репозиторій.
4. Додати PostgreSQL.
5. Налаштувати змінні середовища (`SECRET_KEY`, `DEBUG`, `ALLOWED_HOSTS`, `DATABASE_URL`).
6. Вставити у Custom Start Command:
```bash
python manage.py migrate && python manage.py collectstatic --noinput && gunicorn mysite.wsgi --bind 0.0.0.0:$PORT
```
7. Виконати міграції:

```bash
python manage.py migrate
```

8. Зібрати статичні файли:

```bash
python manage.py collectstatic --noinput
```

9. Запустити застосунок через:

```bash
gunicorn mysite.wsgi
```

## Примітка

Наразі онлайн-версія проєкту недоступна через статус **TRIAL EXPIRED** на Railway. Код проєкту, конфігурація та налаштування деплою залишаються в репозиторії.
