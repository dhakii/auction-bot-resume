# Бот-Аукционер для Telegram

Telegram-бот для проведения художественных аукционов с автоматическим управлением ставками, заявками и уведомлениями.

## 🌟 Основные возможности

### Для участников:
- 📝 Регистрация с уникальным номером
- 🎨 Подача заявок на аукционы
- 💰 Участие в торгах
- 🔔 Уведомления о ставках и результатах
- 📊 Просмотр своих ставок

### Для администраторов:
- 🛎️ Создание аукционов
- 📨 Просмотр и обработка заявок
- 📢 Рассылка сообщений
- 📈 Статистика
- 🔄 Переиздание аукционов
- ↩️ Отмена ставок
- 👤 Информация о пользователях

### Автоматизация:
- ⏰ Автоматическое завершение аукционов
- 🎯 Уведомления победителям и авторам
- 🧹 Очистка старых данных
- 🔄 Интеграция с VK (опционально)

## 🚀 Быстрый старт

### Требования:
- Python 3.10+
- SQLite3
- Telegram Bot Token

### Установка:

```bash
# 1. Клонировать репозиторий
git clone https://github.com/YOUR_USERNAME/auction-bot.git
cd auction-bot/tgbot

# 2. Создать виртуальное окружение
python -m venv venv

# 3. Активировать виртуальное окружение
# Windows:
.\venv\Scripts\activate
# Linux/Mac:
source venv/bin/activate

# 4. Установить зависимости
pip install -r requirements.txt

# 5. Создать .env файл
cp .env.example .env
# Отредактировать .env и добавить свои данные

# 6. Запустить бота
python bot_withdb.py
```

## ⚙️ Конфигурация

Создайте файл `.env` в директории `tgbot/`:

```env
API_TOKEN=your_telegram_bot_token
AUCTION_CHAT_ID=-1001234567890
CONTACT_INFO=По всем вопросам пишите в сообщения группы
DEFAULT_AUTHOR_CONTACT=@YourUsername
DB_PATH=auction_bot.db
POST_TAGS=#торги #аукцион #искусство
ADMIN_USERNAMES=admin1,admin2
```

## 📁 Структура проекта

```
tgbot/
├── main.py                      # Точка входа
├── bot_withdb.py               # Альтернативная точка входа
├── config.py                   # Конфигурация
├── database.py                 # Работа с БД
├── states.py                   # FSM состояния
├── keyboards.py                # Клавиатуры
├── validators.py               # Валидация данных
├── utils.py                    # Утилиты
├── handlers_basic.py           # Базовые обработчики
├── handlers_admin.py           # Админ-функции
├── handlers_auctions.py        # Аукционы
├── handlers_proposals.py       # Заявки
├── handlers_watcher.py         # Мониторинг аукционов
├── handlers_notifications.py  # Уведомления
├── handlers_vk.py             # VK интеграция
├── vk_reposter_client.py      # VK клиент
├── requirements.txt           # Зависимости
└── .env                       # Конфигурация (не в git)
```

## 🗄️ База данных

Бот использует SQLite с автоматической инициализацией:

- **users** - пользователи и их номера
- **auctions** - аукционы
- **bids** - ставки
- **proposals** - заявки на аукционы

### Миграция

Для безопасного обновления БД:

```bash
python migrate_safely.py
```

Подробнее: [MIGRATION_ANALYSIS.md](MIGRATION_ANALYSIS.md)

## 📚 Документация

- [CHANGELOG.md](CHANGELOG.md) - История изменений
- [TEST_GUIDE.md](TEST_GUIDE.md) - Руководство по тестированию
- [UPGRADE_GUIDE.md](UPGRADE_GUIDE.md) - Инструкция по обновлению
- [CODE_AUDIT_REPORT.md](CODE_AUDIT_REPORT.md) - Аудит кода
- [MIGRATION_ANALYSIS.md](MIGRATION_ANALYSIS.md) - Анализ миграции БД

## 🔧 Разработка

### Тайминги аукционов

- **Длительность аукциона:** до 21:00 МСК следующего дня после первой ставки
- **Автозавершение без ставок:** 7 дней после публикации

### Добавление новых функций

1. Создайте обработчики в соответствующем `handlers_*.py`
2. Зарегистрируйте в `main.py`
3. Добавьте состояния в `states.py` (если нужно)
4. Обновите клавиатуры в `keyboards.py`

## 🛡️ Безопасность

- ✅ Проверка регистрации пользователей
- ✅ Проверка членства в группе
- ✅ Проверка прав администратора
- ✅ Rate limiting (10 действий в минуту)
- ✅ Валидация всех входных данных
- ✅ Защита от SQL injection

## 📊 Производительность

- Время ответа: 100-500ms
- Поддержка множественных одновременных пользователей
- Автоматическая очистка старых данных (60 дней)
- Оптимизированные запросы с индексами


## 🤝 Вклад в проект

1. Fork репозитория
2. Создайте ветку для фичи (`git checkout -b feature/AmazingFeature`)
3. Commit изменений (`git commit -m 'Add some AmazingFeature'`)
4. Push в ветку (`git push origin feature/AmazingFeature`)
5. Откройте Pull Request

## 📝 Лицензия

Этот проект является частной разработкой.

## 👥 Авторы

- Разработка и поддержка: [@Marinakhakimov](https://t.me/Marinakhakimov)

## 📞 Поддержка

По всем вопросам обращайтесь:
- Telegram: [@Marinakhakimov](https://t.me/Marinakhakimov)
- Issues: [GitHub Issues](https://github.com/YOUR_USERNAME/auction-bot/issues)

## 🙏 Благодарности

- [aiogram](https://github.com/aiogram/aiogram) - Telegram Bot framework
- [aiosqlite](https://github.com/omnilib/aiosqlite) - Async SQLite
- [python-dotenv](https://github.com/theskumar/python-dotenv) - Environment variables

---

**Версия:** 2.0  
**Последнее обновление:** 13.10.2025  
**Статус:** ✅ Готов к продакшену