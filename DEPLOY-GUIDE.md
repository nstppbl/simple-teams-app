# Руководство по деплою простого приложения

## Вариант 1: GitHub Pages (Самый простой)

### Шаг 1: Создай репозиторий на GitHub

1. Зайди на https://github.com
2. Создай новый репозиторий (например, `timesheets-teams-app`)
3. Загрузи файлы из `simple-teams-app/`

### Шаг 2: Включи GitHub Pages

1. В репозитории: **Settings** → **Pages**
2. **Source:** выбери `main` branch
3. **Folder:** выбери `/root`
4. Нажми **Save**

### Шаг 3: Получи URL

URL будет: `https://YOUR-USERNAME.github.io/timesheets-teams-app/`

### Шаг 4: Обнови manifest.json

Замени `YOUR-URL-HERE` на GitHub Pages URL:

```json
"contentUrl": "https://YOUR-USERNAME.github.io/timesheets-teams-app/index.html",
"websiteUrl": "https://YOUR-USERNAME.github.io/timesheets-teams-app/index.html",
"validDomains": [
  "YOUR-USERNAME.github.io",
  "*.login.microsoftonline.com",
  "res.cdn.office.net"
]
```

### Шаг 5: Загрузи в Teams

Следуй инструкциям из `README.md`

---

## Вариант 2: Netlify (Очень просто)

### Шаг 1: Зарегистрируйся на Netlify

1. Зайди на https://netlify.com
2. Зарегистрируйся (можно через GitHub)

### Шаг 2: Загрузи файлы

1. Перетащи папку `simple-teams-app` в Netlify
2. Или подключи GitHub репозиторий

### Шаг 3: Получи URL

Netlify даст тебе URL: `https://random-name-123.netlify.app`

### Шаг 4: Обнови manifest.json

Замени `YOUR-URL-HERE` на Netlify URL

### Шаг 5: Загрузи в Teams

Следуй инструкциям из `README.md`

---

## Вариант 3: Azure Static Web Apps

### Шаг 1: Создай Azure Static Web App

1. Зайди в Azure Portal
2. **Create a resource** → **Static Web App**
3. Заполни:
   - **Name:** timesheets-app
   - **Resource group:** создай новый
   - **Plan:** Free
   - **Source:** GitHub (или другой)
4. Нажми **Create**

### Шаг 2: Получи URL

URL будет: `https://timesheets-app.azurestaticapps.net`

### Шаг 3: Обнови manifest.json

Замени `YOUR-URL-HERE` на Azure URL

### Шаг 4: Загрузи в Teams

Следуй инструкциям из `README.md`

---

## Вариант 4: Свой веб-сервер

Если у тебя есть свой веб-сервер:

1. Загрузи файлы из `simple-teams-app/` на сервер
2. Убедись, что используется HTTPS
3. Обнови `manifest.json` с твоим URL
4. Загрузи в Teams

---

## Быстрый тест: ngrok (локально)

Если хочешь протестировать локально:

### Шаг 1: Установи ngrok

Скачай: https://ngrok.com/download

### Шаг 2: Запусти локальный сервер

```bash
# Python
python -m http.server 8000

# Или Node.js
npx http-server -p 8000
```

### Шаг 3: Запусти ngrok

```bash
ngrok http 8000
```

Скопируй HTTPS URL (например, `https://abc123.ngrok.io`)

### Шаг 4: Обнови manifest.json

```json
"contentUrl": "https://abc123.ngrok.io/index.html",
"websiteUrl": "https://abc123.ngrok.io/index.html",
"validDomains": [
  "abc123.ngrok.io",
  "*.login.microsoftonline.com",
  "res.cdn.office.net"
]
```

### Шаг 5: Загрузи в Teams

⚠️ **Важно:** ngrok URL меняется при каждом перезапуске. Для продакшена используй постоянный хостинг.

---

## Рекомендация

Для начала используй **GitHub Pages** или **Netlify** - это бесплатно и очень просто.

Для продакшена лучше использовать **Azure Static Web Apps** - это интегрируется с Microsoft экосистемой.

