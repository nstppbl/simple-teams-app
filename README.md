# Простое веб-приложение для Teams

## Что это?

Простое HTML приложение, которое работает в Teams как Tab. Не требует VS Code или сложной настройки.

---

## Как использовать

### Вариант 1: Локальный хостинг (для тестирования)

#### Шаг 1: Размести файлы на веб-сервере

Нужно разместить `index.html` на веб-сервере, чтобы Teams мог его открыть.

**Варианты:**
- GitHub Pages (бесплатно)
- Netlify (бесплатно)
- Azure Static Web Apps (бесплатно)
- Свой веб-сервер

#### Шаг 2: Обнови manifest.json

Открой `manifest.json` и замени `YOUR-URL-HERE` на твой реальный URL:

```json
"contentUrl": "https://your-app.azurestaticapps.net/index.html",
"websiteUrl": "https://your-app.azurestaticapps.net/index.html",
"validDomains": [
  "your-app.azurestaticapps.net",
  "*.login.microsoftonline.com",
  "res.cdn.office.net"
]
```

#### Шаг 3: Создай иконки (опционально)

Создай два файла:
- `icon-color.png` (192x192 пикселей)
- `icon-outline.png` (32x32 пикселей)

Или используй любые PNG файлы с этими именами.

#### Шаг 4: Создай ZIP файл

1. Выбери все файлы в папке `simple-teams-app`:
   - `manifest.json`
   - `index.html`
   - `icon-color.png` (если есть)
   - `icon-outline.png` (если есть)
2. Создай ZIP архив
3. Назови его `timesheets-app.zip`

#### Шаг 5: Загрузи в Teams

1. Открой Microsoft Teams
2. Нажми на **Apps** (в левом меню)
3. Нажми **Upload custom app**
4. Выбери `timesheets-app.zip`
5. Нажми **Add**
6. Нажми **Add to personal apps**

#### Шаг 6: Открой приложение

1. В левом меню Teams найди **Timesheets**
2. Нажми на него
3. Должно открыться приветственное окно!

---

### Вариант 2: Быстрый тест через ngrok (локально)

Если хочешь протестировать локально без деплоя:

#### Шаг 1: Установи ngrok

1. Скачай ngrok: https://ngrok.com/download
2. Распакуй в папку

#### Шаг 2: Запусти локальный сервер

```bash
# Python 3
python -m http.server 8000

# Или Node.js
npx http-server -p 8000
```

#### Шаг 3: Создай tunnel

```bash
ngrok http 8000
```

Скопируй URL (например, `https://abc123.ngrok.io`)

#### Шаг 4: Обнови manifest.json

Замени `YOUR-URL-HERE` на ngrok URL

#### Шаг 5: Загрузи в Teams

Следуй шагам из Варианта 1 (шаги 4-6)

---

## Структура файлов

```
simple-teams-app/
├── index.html          # Главная страница
├── manifest.json       # Конфигурация Teams App
├── icon-color.png      # Иконка (цветная)
├── icon-outline.png    # Иконка (контур)
└── README.md          # Эта инструкция
```

---

## Что дальше?

После того как базовое приложение работает:

1. Добавь форму таймшитов
2. Подключи Dataverse API
3. Добавь дашборды
4. Настрой экспорт в Excel

---

## Troubleshooting

### Ошибка: "App not loading"

- Проверь, что `index.html` доступен по URL из manifest.json
- Проверь, что URL использует HTTPS (Teams требует HTTPS)
- Проверь консоль браузера (F12) на ошибки

### Ошибка: "Invalid manifest"

- Проверь, что `manifest.json` валидный JSON
- Проверь, что все обязательные поля заполнены
- Используй валидатор: https://developer.microsoft.com/microsoft-teams/platform/tools/manifest-editor

### Ошибка: "Teams SDK not found"

- Проверь, что `index.html` загружает TeamsJS SDK
- Проверь интернет-соединение
- Проверь, что `res.cdn.office.net` в `validDomains`

---

## Полезные ссылки

- [Teams App Manifest Schema](https://learn.microsoft.com/microsoftteams/platform/resources/schema/manifest-schema)
- [TeamsJS SDK Documentation](https://learn.microsoft.com/microsoftteams/platform/tabs/how-to/using-teams-client-sdk)
- [Teams App Validation Tool](https://developer.microsoft.com/microsoft-teams/platform/tools/manifest-editor)

