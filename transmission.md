# Transmission.

### Сборка докер-контейнера Transmission для [Open Media Vault](omv.md).

Файл [docker-compose.yml](transmission/docker-compose.yml).

В папке с файлом выполнить команду `docker compose create`

### Настройка.

Web-интерфейс доступен по порту 9091.

При запуске контейнера в папке \\VAULT\public\Transmission будут созданы папки:
1. complete - в эту папку будут перемещаться скачанные торренты из папки incomplete.
2. incomplete - в этой папке размещаются файлы в процессе скачивания.
3. settings - в этой папке находится файл settings.json.
4. watch - transmission проверяет содержимое этой папки на наличие торрент-файлов и начинает их закачку. Если в файле settings.json изменить параметр "trash-original-torrent-files" на true, то торрент-файлы из папки watch будут автоматически удаляться.

Бороться с папками complete / incomplete бессмысленно.
