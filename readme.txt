Веб-сервис комплексной лингвистической оценки текстов для авторов образовательного контента**

Приложение помогает авторам образовательного контента оценить качество, читаемость и тональность своих текстов с использованием лингвистических метрик.

Стек технологий

Backend: Django 5.1
Database: PostgreSQL / SQLite
Data Processing: Pandas
Visualization: Matplotlib
Frontend: Bootstrap 5
Server: PythonAnywhere

 Установка и запуск
 Требования
- Python 3.10+
- Git

Локальная установка
bash
git clone <repository-url>
cd textinsight_edu

python -m venv venv
source venv/bin/activate  # На Windows: venv\Scripts\Activate.ps1

pip install -r requirements.txt

cp .env.example .env
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```


## Функциональность

- ✅ Регистрация и управление пользователями
- ✅ Загрузка текстов (50-50000 символов)
- ✅ Расчет метрик читаемости (Flesch-Kincaid Index)
- ✅ Анализ тональности текста
- ✅ Подсчет слов и среднюю длину слова
- ✅ История анализов с сохранением результатов
- ✅ Административная панель Django
- ✅ Bootstrap 5 интерфейс

## Структура проекта

textinsight_edu/
├── config/           # Основные настройки Django
├── accounts/         # Управление пользователями
├── documents/        # Управление документами
├── analysis/         # Лингвистический анализ
├── templates/        # HTML шаблоны
├── static/           # CSS, JS, изображения
├── manage.py         # Django команды
└── requirements.txt  # Зависимости


## Деплой на PythonAnywhere

Приложение развернуто на: **https://fydj.pythonanywhere.com**

 Инструкции деплоя

1. Клонировать репозиторий
2. Установить зависимости в виртуальное окружение
3. Настроить .env` с production значениями
4. Собрать статические файлы: `python manage.py collectstatic`
5. Применить миграции: `python manage.py migrate`
6. Настроить WSGI в PythonAnywhere

Подробнее: см. [DEPLOYMENT.md](DEPLOYMENT.md)

 API Routes

GET /documents/` — Список документов
POST /documents/create/` — Загрузка текста
GET /documents/<id>/` — Результаты анализа
DELETE /documents/<id>/delete/` — Удаление документа
GET /admin/` — Административная панель

## Технические детали

Метрики анализа:
  - Flesch-Kincaid Grade Level
  - Средняя длина слова
  - Количество слов в тексте
  - Анализ тональности (положительные/отрицательные слова)

- *Безопасность:
  - Все секреты в `.env` файле
  - CSRF защита
  - Обязательная аутентификация
  - ORM защита от SQL инъекций