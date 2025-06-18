# A-Vision

A-Vision — это Telegram-бот для описания изображений и видео для незрячих/слабовидящих пользователей, а также расшифровки аудио в текст.

## 🚀 Быстрый старт

### Локальный запуск

1. **Клонируйте репозиторий:**
```bash
git clone https://github.com/your-username/a_vision.git
cd a_vision
```

2. **Установите зависимости:**
```bash
pip install -r requirements.txt
```

3. **Создайте файл `.env`:**
```env
BOT_TOKEN=your_telegram_bot_token
GOOGLE_API_KEY=your_google_api_key
```

4. **Запустите бота:**
```bash
python main.py
```

### Настройка Telegram бота

1. Создайте бота через [@BotFather](https://t.me/BotFather)
2. Получите токен бота
3. Настройте вебхук (для продакшена):
```bash
curl -X POST "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/setWebhook" \
     -H "Content-Type: application/json" \
     -d '{"url": "https://your-domain.com/<YOUR_BOT_TOKEN>"}'
```

## 🌐 Бесплатный деплой на Vercel

### Шаг 1: Подготовка

1. **Форкните репозиторий** на GitHub
2. **Создайте аккаунт** на [Vercel](https://vercel.com)

### Шаг 2: Настройка переменных окружения

1. Перейдите в [Google AI Studio](https://aistudio.google.com/apikey)
2. Создайте API ключ для Gemini
3. В настройках проекта на Vercel добавьте переменные:
   - `BOT_TOKEN` - токен вашего Telegram бота
   - `GOOGLE_API_KEY` - API ключ Google Gemini

### Шаг 3: Деплой

1. **Подключите GitHub репозиторий** к Vercel
2. **Настройте проект:**
   - Framework Preset: `Other`
   - Build Command: `python main.py`
   - Output Directory: оставьте пустым
   - Install Command: `pip install -r requirements.txt`

3. **Нажмите Deploy**

### Шаг 4: Настройка вебхука

После успешного деплоя:

1. Получите URL вашего приложения (например: `https://your-app.vercel.app`)
2. Установите вебхук:
```bash
curl -X POST "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/setWebhook" \
     -H "Content-Type: application/json" \
     -d '{"url": "https://your-app.vercel.app/<YOUR_BOT_TOKEN>"}'
```

3. Проверьте статус вебхука:
```bash
curl "https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getWebhookInfo"
```

## 📁 Структура проекта

```
A-Vision/
├── config.py              # Конфигурация и настройки
├── main.py                # Основной файл приложения
├── requirements.txt       # Зависимости Python
├── vercel.json           # Конфигурация для Vercel
├── handlers/
│   ├── commands.py       # Обработчики команд
│   └── media.py          # Обработчики медиа
├── services/
│   └── gemini.py         # Сервис для работы с Gemini AI
└── utils/
    └── logger.py         # Настройки логирования
```

## ⚙️ Настройка

### Изменение промптов

В файле `config.py` можно настроить:

```python
MEDIA_PROMPT = "Ваш промпт для описания изображений/видео"
VOICE_PROMPT = "Ваш промпт для транскрипции аудио"
BOT_USERNAME = "Название вашего бота"
```

### Модель AI

По умолчанию используется бесплатная модель от Google `gemini-2.5-flash`. Можно изменить в `config.py`:

```python
GEMINI_MODEL = "gemini-1.5-flash"  # или другая модель
```

## 🔧 Команды бота

- `/start` - Активировать бота в чате
- `/help` - Показать справку
- `/stop` - Деактивировать бота

## 📝 Логирование

Логи сохраняются в файл `bot.log` и выводятся в консоль. Для продакшена на Vercel логи доступны в панели управления.

## 🚨 Устранение неполадок

### Бот не отвечает

1. Проверьте правильность токена в переменных окружения
2. Убедитесь, что вебхук установлен корректно
3. Проверьте логи в панели Vercel

### Ошибки API

1. Проверьте правильность Google API ключа
2. Убедитесь, что у вас есть доступ к Gemini API
3. Проверьте лимиты API

### Проблемы с деплоем

1. Убедитесь, что все зависимости указаны в `requirements.txt`
2. Проверьте, что `vercel.json` настроен корректно
3. Проверьте логи сборки в Vercel

## 📄 Лицензия

MIT License - см. файл [LICENSE](LICENSE) для деталей.

**A-Vision** — часть **A.Cloud** 🌟
