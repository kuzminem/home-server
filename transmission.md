# Transmission.

### Сборка докер-контейнера Transmission для [Open Media Vault](omv.md).

Файл [docker-compose.yml](transmission/docker-compose.yml).

В папке с файлом выполнить команду `docker compose create`

Файл [settings.json](transmission/settings.json) скопировать в папку `\\VAULT\public\Transmission\Config`.

Интересует два параметра:
-t --auth или -T --no-auth
--incomplete-dir или --no-incomplete-dir
