# Установка и настройка BIND9

## Установка:

```bash
sudo apt update
sudo apt install bind9
```

Если необходимо, разрешите BIND9 работать через брандмауэр:

```bash
sudo ufw allow Bind9
```

## Настройка:

Отредактируйте файл настройки – named.conf.options:

```bash
sudo nano /etc/bind/named.conf.options
```

Внесите следующие изменения в файл:

```bash
options {
    directory "/var/cache/bind";
    listen-on { any; };
    forwarders {
        8.8.8.8;
        8.8.4.4;
        77.88.8.8;
        77.88.8.1;
        208.67.222.222;
        208.67.220.220;
    };
    recursion yes;
    allow-recursion { any; };
    allow-query { any; };
    dnssec-validation auto;
    auth-nxdomain no;
    listen-on-v6 { none; };
};
```

Перезапустите службу BIND9, чтобы применить изменения:

```bash
sudo systemctl restart bind9
```

## Проверка работоспособности:

После завершения процесса установки необходимо проверить работу BIND9:

```bash
nslookup google.com 127.0.0.1
```

Ответ должен быть похожим на следующий:

```
Server: 127.0.0.1
Address: 127.0.0.1#53
```

```
Non-authoritative answer:
Name: google.com
Address: 64.233.164.138
...
```

Теперь BIND9 должен быть правильно настроен и готов к использованию.
