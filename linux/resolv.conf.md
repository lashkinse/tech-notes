# Использование resolvconf для постоянных резолверов в resolv.conf

## Установка:

```bash
sudo nano apt install resolvconf
sudo nano systemctl enable --now resolvconf.service
```

## Настройка:

Отредактируйте файл настройки – `/etc/resolvconf/resolv.conf.d/head`:

```bash
sudo nano /etc/resolvconf/resolv.conf.d/head
```

Пример содержимого файла:

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Обновить /etc/resolv.conf можно с помощью команды:

```bash
sudo resolvconf -u
```

Теперь ваш resolv.conf будет постоянно содержать указанные вами DNS-серверы после каждого перезапуска системы.
