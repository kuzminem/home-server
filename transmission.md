# Transmission.

### Сборка докер-контейнера Transmission для [Open Media Vault](omv.md).

Файл docker-compose.yml.
```
version: "2.1"
services:
  transmission:
    image: lscr.io/linuxserver/transmission:latest
    container_name: transmission
    hostname: transmission
    network_mode: host
    restart: unless-stopped
    environment:
      - PUID=998
      - PGID=100
      - TZ=Europe/Moscow
    volumes:
      - /srv/dev-disk-by-uuid-1a192a26-3a0a-4bc6-8b4c-c4c01f8a1208/Transmission:/downloads
      - /srv/dev-disk-by-uuid-1a192a26-3a0a-4bc6-8b4c-c4c01f8a1208/Transmission/watch:/watch
      - /srv/dev-disk-by-uuid-1a192a26-3a0a-4bc6-8b4c-c4c01f8a1208/Transmission/settings:/config
```
В папке с файлом выполнить команду `docker compose create`

### Настройка.

Web-интерфейс доступен по порту 9091.

При запуске контейнера в папке Transmission будут созданы папки:
1. complete &mdash; в эту папку будут перемещаться скачанные торренты из папки incomplete.
2. incomplete &mdash; в этой папке размещаются файлы в процессе скачивания.
3. settings &mdash; в этой папке находится файл settings.json.
4. watch &mdash; transmission проверяет содержимое этой папки на наличие торрент-файлов и начинает их закачку. Если в файле settings.json изменить параметр "trash-original-torrent-files" на true, то торрент-файлы из папки watch будут автоматически удаляться.
