# Вознесение Wiki — Cloudflare Workers + D1

Эта версия специально исправляет ошибку `Asset too large`: Worker не использует `[assets]` и не загружает `node_modules`. HTML/CSS/JS встроены в Worker.

## Cloudflare Workers Builds
- Build command: оставить пустым (или `echo Build complete`)
- Deploy command: `npx wrangler deploy`
- Version command: пусто
- Root directory: `/`

D1 уже прописан: `dc1695af-9944-4a5d-901b-7280f540bb93`. Схема таблиц создаётся Worker автоматически при первом запросе.

Имя Worker: `voznesenie-wiki-nk`. После успешного deploy Cloudflare покажет адрес `https://voznesenie-wiki-nk.<account-subdomain>.workers.dev`.

Первый 
