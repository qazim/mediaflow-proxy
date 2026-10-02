# Используем официальный образ Python как базу
FROM python:3.11-slim

# Устанавливаем рабочую директорию
WORKDIR /app

# Устанавливаем системные зависимости, если они нужны
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    && rm -rf /var/lib/apt/lists/*

# Клонируем наш форк репозитория
# ВАЖНО: замените YourUsername/YourRepoName на данные вашего форка!
RUN git clone https://github.com/YourUsername/YourRepoName.git .

# Устанавливаем Python-зависимости
RUN pip install --no-cache-dir -r requirements.txt

# Открываем порт, который будет использовать Render
EXPOSE 8000

# Команда для запуска прокси-сервера
# Render автоматически передаст переменную окружения PORT
CMD ["uvicorn", "mediaflow_proxy.main:app", "--host", "0.0.0.0", "--port", "8000"]
