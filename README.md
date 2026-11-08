# Практикум Python ЛР15–18

Поточний етап — **ЛР15**, варіант **8**, ситуація **Музейний фонд**.
Створено початковий Django-проєкт `config` і порожній застосунок `monitoring`.
Моделей Device, паспортів, міток, вимірювань і предметних маршрутів ще немає:
вони додаються в наступних лабораторних цього самого проєкту.

## Профіль 8 для наступних робіт

- Пристрої: «Фонд тканини» (`V08-A`), «Фонд дерево» (`V08-B`),
  «Вестибюль» (`V08-C`).
- Пошук: `q=Фонд`; температурний поріг: `21 °C`.
- План: три пристрої, два паспорти, три мітки та десять вимірювань із UTC.
- Додатковий критерій: показувати розмах `max − min`; якщо вимірювань немає —
  «немає даних», а не нуль.
- Повний початковий профіль з методички збережено в `profile08.json`.
  Температури надалі слід перетворювати через `Decimal`.

## Перевірене середовище

Python **3.12.14**, Django **6.1.2**. Повні фактичні версії та результати
перевірок містяться в `docs/verification.json` і `docs/protocol.txt`.
`requirements.txt` — прямі залежності з наданого комплекту;
`requirements-lock.txt` — повний перевірений список версій.

## Запуск у Windows

Відкрийте термінал у папці з `manage.py`. Потрібний погоджений Python 3.12–3.14;
для точного відтворення перевіреного середовища використано Python 3.12.14.
Активація середовища та зміна політики PowerShell не потрібні.

```powershell
py -3.12 -m venv .venv
.venv\Scripts\python.exe -m pip install -r requirements-lock.txt
.venv\Scripts\python.exe -m pip check
.venv\Scripts\python.exe -VV
.venv\Scripts\python.exe -m django --version
.venv\Scripts\python.exe -c "import sqlite3, ctypes; print(sqlite3.sqlite_version)"
.venv\Scripts\python.exe manage.py migrate
.venv\Scripts\python.exe manage.py check
.venv\Scripts\python.exe manage.py runserver 127.0.0.1:8000
```

Відкрийте `http://127.0.0.1:8000/` — очікується 200, початкова сторінка Django.
`http://127.0.0.1:8000/missing/` — 404. Зупинка сервера — Ctrl+C.
Сервер не відкривається на зовнішню адресу.

Для Linux/macOS створіть `.venv` тим самим підтримуваним інтерпретатором,
а в командах використовуйте `.venv/bin/python` замість Windows-шляху.

## Порівняння Flask

Після зупинки Django запустіть готовий короткий приклад із методички:

```powershell
.venv\Scripts\python.exe -m flask --app framework_examples.flask_app run --host 127.0.0.1 --port 5000
```

`/` повертає HTML, `/devices/1` — JSON. Дані порівняльного прикладу
синтетичні та зберігаються в пам’яті, без предметних Django-моделей.
FastAPI/HTTPX2/Uvicorn залишені в requirements відповідно до комплекту,
але окремий FastAPI-проєкт для ЛР15 не створювався.

## Що перевірено

Початкові міграції, `check`, `pip check`, sqlite3 та ctypes; фактичні HTTP GET
до Django і Flask; відтворення з вихідних файлів і lock-файла в іншому
порожньому каталозі та новому віртуальному середовищі.
HTTP-метод, статус і Content-Type зафіксовано в `docs/verification.json`.
Словник усіх наявних налаштувань — `docs/settings_dictionary.md`.

## Локальні налаштування

`LANGUAGE_CODE='uk'`, `TIME_ZONE='Europe/Kyiv'`, SQLite,
`ALLOWED_HOSTS=['127.0.0.1', 'localhost']`, `DEBUG=True` лише для навчання.
Реальний SECRET_KEY у вихідних файлах не зберігається: береться з
`DJANGO_SECRET_KEY` або генерується для локального процесу.
Без постійного ключа між перезапусками сесії не зберігаються; для початкової
ЛР15 це не заважає перевіркам. Це не конфігурація публічного розгортання.

## Git і GitHub

До репозиторію належать `config/`, `monitoring/`, `framework_examples/`, `docs/`,
`manage.py`, обидва requirements, `.gitignore`, README та `profile08.json`.
Не додавайте `.venv`, `db.sqlite3`, `.env`, кеші, паролі або токени.
`.gitignore` уже містить відповідні правила.

GitHub-репозиторій: https://github.com/LitruzZz/course-monitoring-python-2026

Вихідні файли потрібно завантажити в цей створений репозиторій перед здачею.
Публічність визначає викладач; приватному репозиторію потрібний доступ викладача.
