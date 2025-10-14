# Использовать базовый образ python:3.9-slim
FROM python:3.9-slim

# Установить рабочую директорию /app
WORKDIR /app

# Установить системные пакеты: curl и vim
RUN apt-get update && apt-get install -y curl vim && rm -rf /var/lib/apt/lists/*

# Скопировать requirements.txt и установить Python пакеты
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Скопировать файл app.py в контейнер
COPY app.py .

# Создать пользователя appuser с UID 1000
RUN adduser --uid 1000 --disabled-password --gecos "" appuser

# Переключиться на пользователя appuser
USER appuser

# Открыть порт 5000
EXPOSE 5000

# Установить переменную окружения FLASK_ENV=production
ENV FLASK_ENV=production

# Запустить приложение командой python app.py
CMD ["python", "app.py"]