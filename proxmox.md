# proxmox.

### Установка.

* Качаем образ: [ISO Images](https://www.proxmox.com/en/downloads/category/iso-images-pve).
* Делаем загрузочную флешку: [balenaEtcher](https://www.balena.io/etcher/).

После установки proxmox доступен по SSH и по web-интерфейсу на порту 8006.

Логин root, пароль &mdash; указанный при установке.

### Папки.

* `/var/lib/vz/template/iso/` &mdash; образы гостевых систем.

### Подключить репозиторий Яндекс.

Отредактировать список репозиториев: `nano /etc/apt/sources.list`
```
deb http://mirror.yandex.ru/debian bullseye main
deb http://mirror.yandex.ru/debian bullseye-updates main
deb http://mirror.yandex.ru/debian-security bullseye-security main
```

### Пробросить диск в виртуальную машину.

ls -l /dev/disk/by-id/

qm set 100 -scsi1 /dev/disk/by-id/ata-ST4000DX001-1CE168_Z300ZGBC

qm set 100 -scsi2 /dev/disk/by-id/usb-ST320005_42AS_98765432100C-0:0

### Разное.

Выключить виртуальную машину из консоли: `qm stop 100`

### Подключить жёсткий диск.

Посмотреть диски `lsblk` и UUID `blkid`

Отредактировать список автоматически монтируемых дисков: `nano /etc/fstab`

Пример:
```
UUID=1a192a26-3a0a-4bc6-8b4c-c4c01f8a1208 /mnt/public ext4 nodev,noexec 0 2
```

Смонтировать диски, указанные в fstab: `mount -a`

### Права на папки.

Посмотреть права: `ls -l /mnt/public`

Смена владельца: `chown -R root:root /mnt/public`

Дать права:
```
chmod -R a-x /mnt/public
chmod -R a+rwX /mnt/public
```

### Управление правами ACL (Access Control List).

Установка: `apt install acl`

Посмотреть права ACL: `getfacl /mnt/public`

Удалить права ACL: `setfacl -b /mnt/public/APP`
