# Laravel Demo for /dev/push

Small Laravel + Inertia/React demo app used to verify /dev/push presets and runners.
For the full starter kit docs, see:

```
https://github.com/laravel/laravel
```

## Deploy on /dev/push (quick steps)

1) Create a new project and select the **Laravel** preset. It should auto-detect the Laravel preset with Node support (e.g., "FrankenPHP (PHP 8.3) + Node 22").
2) Create a database (see [storage](https://devpu.sh/docs/basics/storage/)), for example `demo-laravel-db`.
3) Set env vars in the project:
   - `APP_KEY` (generate a valid Laravel key)
   - `DB_CONNECTION=sqlite`
   - `DB_DATABASE=/data/database/demo-laravel-db/db.sqlite`
4) Deploy.
