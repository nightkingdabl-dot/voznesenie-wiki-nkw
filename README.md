# Вознесение Wiki — Cloudflare Workers + D1

Готовая мобильная Wiki без обязательного входа. Статьи, категории, подкатегории, теги, поиск и админка хранятся в Cloudflare D1.

## Cloudflare Workers Builds

- Build command: `npm install`
- Deploy command: `npx wrangler deploy`
- Version command: оставить пустым
- Root directory: `/`

Wrangler уже настроен на Worker `voznesenie-wiki-nk` и D1 database ID:
`dc1695af-9944-4a5d-901b-7280f540bb93`

### Почему больше не будет ошибки 144 MiB

Статические assets остаются в корне проекта (папок внутри ZIP нет), но Wrangler получает `assets.include` и публикует только `index.html`, `style.css` и `app.js`. Поэтому `node_modules/workerd/bin/workerd` не считается публичным asset.

## Первый администратор


После запуска рекомендуется сменить пароль/создать отдельную учётную запись администратора.

## D1

В базе должна быть применена схема из `schema.sql`. Если таблицы ещё не созданы, выполни содержимое `schema.sql` в D1 Console.

## Адрес сайта

`workers_dev = true`, поэтому после успешного deploy Cloudflare выдаст `workers.dev` адрес для Worker `voznesenie-wiki-nk`. Также можно привязать свой домен в Workers & Pages → Worker → Settings → Domains & Routes.
