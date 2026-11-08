# Налаштування settings.py

## BASE_DIR

Поточне значення: `Path(__file__).resolve().parent.parent`.

Кореневий каталог проєкту; база для шляхів до локальних файлів.

## SECRET_KEY

Поточне значення: `DJANGO_SECRET_KEY або новий випадковий ключ процесу; значення не наводиться`.

Ключ підпису. Значення береться з DJANGO_SECRET_KEY або генерується локально; реальний ключ у репозиторій і звіт не записується.

## DEBUG

Поточне значення: `True`.

Докладні діагностичні сторінки лише під час локального розроблення.

## ALLOWED_HOSTS

Поточне значення: `['127.0.0.1', 'localhost']`.

Дозволені імена хостів HTTP-запиту; лише loopback і localhost.

## INSTALLED_APPS

Поточне значення: `['django.contrib.admin', 'django.contrib.auth', 'django.contrib.contenttypes', 'django.contrib.sessions', 'django.contrib.messages', 'django.contrib.staticfiles']`.

Шість стандартних застосунків: адміністрування, автентифікація, типи вмісту, сесії, повідомлення та статичні файли. monitoring створений, але за вимогою ЛР15 ще не підключений.

## MIDDLEWARE

Поточне значення: `['django.middleware.security.SecurityMiddleware', 'django.contrib.sessions.middleware.SessionMiddleware', 'django.middleware.common.CommonMiddleware', 'django.middleware.csrf.CsrfViewMiddleware', 'django.contrib.auth.middleware.AuthenticationMiddleware', 'django.contrib.messages.middleware.MessageMiddleware', 'django.middleware.clickjacking.XFrameOptionsMiddleware']`.

Послідовність проміжних обробників запиту й відповіді: безпека, сесії, загальні HTTP-правила, CSRF, користувач, повідомлення, захист від clickjacking.

## ROOT_URLCONF

Поточне значення: `'config.urls'`.

Модуль кореневої маршрутизації; зараз лише стандартний admin/.

## TEMPLATES

Поточне значення: `[{'BACKEND': 'django.template.backends.django.DjangoTemplates', 'DIRS': [], 'APP_DIRS': True, 'OPTIONS': {'context_processors': ['django.template.context_processors.request', 'django.contrib.auth.context_processors.auth', 'django.contrib.messages.context_processors.messages']}}]`.

DjangoTemplates; окремих каталогів немає, шаблони застосунків дозволені. Контекстні процесори передають запит, користувача/дозволи й повідомлення.

## WSGI_APPLICATION

Поточне значення: `'config.wsgi.application'`.

Точка входу для WSGI-сумісного сервера; ASGI окремо оголошено в config/asgi.py.

## DATABASES

Поточне значення: `{'default': {'ENGINE': 'django.db.backends.sqlite3', 'NAME': BASE_DIR / 'db.sqlite3'}}`.

SQLite-файл db.sqlite3 в BASE_DIR. База створюється міграціями та не входить до Git/ZIP.

## AUTH_PASSWORD_VALIDATORS

Поточне значення: `[{'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator'}, {'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator'}, {'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator'}, {'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator'}]`.

Стандартні перевірки пароля: схожість із даними користувача, мінімальна довжина, поширений пароль і пароль лише з цифр. Паролів у коді немає.

## LANGUAGE_CODE

Поточне значення: `'uk'`.

Українська локалізація інтерфейсів Django.

## TIME_ZONE

Поточне значення: `'Europe/Kyiv'`.

Часовий пояс проєкту — Київ.

## USE_I18N

Поточне значення: `True`.

Увімкнена система перекладів і локалізації.

## USE_TZ

Поточне значення: `True`.

Увімкнена робота з часовими поясами; майбутні вимірювання матимуть часову зону.

## STATIC_URL

Поточне значення: `'static/'`.

URL-префікс статичних ресурсів CSS/JS/зображень.

## MAILERS

Поточне значення: `{'default': {'BACKEND': 'django.core.mail.backends.console.EmailBackend'}}`.

Стандартний поштовий механізм цього згенерованого проєкту виводить листи в консоль; зовнішній поштовий сервіс не налаштовано.
