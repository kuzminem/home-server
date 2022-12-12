# Open Media Vault.

### Подключить репозиторий Яндекс.

Отредактировать список репозиториев: `nano /etc/apt/sources.list`
```
deb http://mirror.yandex.ru/debian bullseye main
deb http://mirror.yandex.ru/debian bullseye-updates main
deb http://mirror.yandex.ru/debian-security bullseye-security main
```
Закомментить единственную строку в `nano /etc/apt/sources.list.d/openmediavault-kernel-backports.list`

Установить extras: `wget -O - https://github.com/OpenMediaVault-Plugin-Developers/packages/raw/master/install | bash`

System - omv-extras
* Settings - [ ] Backports
* apt clean

Выключить vault.
Удалить cdrom, отредактировать прорядок загрузки.
Включить.

Установить плагин miniDLNA.

Обновиться.

### Создать шару.

Storage - File Systems

Storage - Shared Folders

Services - SMB/CIFS

### Portainer.

System - omv-extras
* Portainer - Install
