# Использование resolvconf для постоянных резолверов в resolv.conf

## Установка:

```bash
sudo nano apt install resolvconf
sudo nano systemctl enable --now resolvconf.service
```

## Настройка:

Отредактируйте файл настройки – /etc/resolvconf/resolv.conf.d/head:

```bash
sudo nano /etc/resolvconf/resolv.conf.d/head
```

Он должен выглядеть примерно так:

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Обновить /etc/resolv.conf можно командой:

```bash
sudo resolvconf -u
```
