# Laravel React Starter Kit


Opinionated Laravel + Inertia/React starter with Vite and FrankenPHP-ready defaults.

## Required environment

Set these in `.env` (or your host):
- `APP_NAME` – display name
- `APP_ENV` – `local` or `production` (defaults to `production` if unset; the example `.env` sets `local`)
- `APP_KEY` – run `php artisan key:generate` once to set
- `APP_URL` – e.g. `http://localhost:8000` (Laravel falls back to `http://localhost`; set this explicitly so URL generation in CLI/emails uses the right host)
- `DB_CONNECTION`: `sqlite`
- `DB_DATABASE`: 
- `FILESYSTEM_DISK` – usually `public`; source path and URL are defined in `config/filesystems.php` (`storage/app/public` → `/storage` via `php artisan storage:link`)
- `SESSION_DRIVER` – `file`, `database`, etc.
- `QUEUE_CONNECTION` – `database` by default

## Local development

```bash
cp .env.example .env
composer install
npm install
php artisan key:generate
php artisan migrate
php artisan storage:link
npm run dev    # Vite
php artisan serve
```

Queues/log tail used in this repo’s dev script: `php artisan queue:listen` and `php artisan pail --timeout=0`.

## Production / devpu.sh commands

- Build: `composer install --no-dev --optimize-autoloader --no-interaction --no-progress && npm ci && npm run build`
- Pre-deploy: `php artisan migrate --force && php artisan storage:link && php artisan config:cache && php artisan route:cache && php artisan view:cache`
- Start: `frankenphp run --config /etc/caddy/Caddyfile --adapter caddyfile`
- Optional: `php artisan queue:work --sleep=3 --tries=3 --max-time=3600` and `php artisan schedule:work`

## File uploads

- Uses the `public` disk; files are stored under `storage/app/public/...` and served via `/storage/...` after `php artisan storage:link`.
- Profile avatar uploads are saved to `avatars/` with a public URL computed by the model accessor.

## Testing

```bash
php artisan test
```
