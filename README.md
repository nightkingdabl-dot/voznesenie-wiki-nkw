# Вознесение Wiki — Cloudflare Workers + D1

Готовая версия для Cloudflare Workers Builds. Все проектные файлы лежат **прямо в корне репозитория**, без папок.

## Что исправлено
- Добавлен `.assetsignore`, поэтому `node_modules/workerd` больше не загружается как сайт и ошибка `Asset too large` не возникает.
- `workers_dev = true` включён, поэтому Worker получает адрес вида `https://voznesenie-wiki.<ВАШ-SUBDOMAIN>.workers.dev` после первого деплоя.
- Поиск по названию, описанию, тексту и тегам.
- Теги статей.
- Категории и подкатегории.
- Регистрация/вход по желанию.
- Админка: создание/редактирование/удаление статей, категории, пользователи, выдача админских прав, блокировка.
- Адаптивный дизайн для телефона.
- Cloudflare D1 для постоянного хранения.

## 1. D1
Cloudflare → Workers & Pages → D1 → Create database.

Имя: `voznesenie-wiki-db`

В SQL Console выполни **весь** файл `schema.sql`.

## 2. Database ID
Открой D1 → созданную базу → скопируй Database ID.

В `wrangler.toml` замени:
`REPLACE_WITH_YOUR_D1_DATABASE_ID`
на настоящий ID.

## 3. GitHub
Загрузи все файлы из этого ZIP прямо в корень репозитория. Папки создавать не нужно.

## 4. Cloudflare Workers Builds
Подключи GitHub-репозиторий через Workers & Pages → Create application → Import a repository.

Настройки:
- Build command: `npm install`
- Deploy command: `npx wrangler deploy`
- Version command: **пусто** (для production)
- Root directory: `/`

Cloudflare Builds автоматически выполнит deploy после push.

## 5. Адрес сайта
После успешного деплоя Cloudflare выдаст URL на странице Worker.

Так как `workers_dev = true`, адрес будет иметь вид:
`https://voznesenie-wiki.<ВАШ-SUBDOMAIN>.workers.dev`

Точный `<ВАШ-SUBDOMAIN>` зависит от аккаунта Cloudflare, поэтому заранее придумать полный URL нельзя.

Если хочешь свой адрес вроде `wiki.example.com`, после деплоя открой Worker → Settings → Domains & Routes → Add Custom Domain.

## 6. Первый администратор
Логин: `NIGHT_KING`
Пароль: `vozn_04`

После первого запуска обязательно поменяй пароль перед публичным использованием.
