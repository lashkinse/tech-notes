# Настройка DNS-серверов

Для изменения DNS-сервера через командную строку выполните настройку файла `/etc/network/interfaces`. Он должен выглядеть примерно так:

```
# The primary network interface
auto ens3
iface ens3 inet static
        address 192.168.0.1/24
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 1.1.1.1
```

Если у вас есть более одного DNS-сервера, добавьте пробел между каждым:

```
dns-nameservers X.X.X.X Y.Y.Y.Y Z.Z.Z.Z
```

После внесения изменений обновите настройки с помощью следующей команды:

```
sudo ip link set eth0 down && sudo ip link set eth0 up
```
