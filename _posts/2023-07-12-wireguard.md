---
title: 'Настройка wireguard'
tags: 
    - wireguard
categories:
    - VPN
    - server
sources:
    - https://www.wireguard.com/install/
    - https://www.digitalocean.com/community/tutorials/how-to-set-up-wireguard-on-ubuntu-20-04
    - https://gist.github.com/chrisswanda/88ade75fc463dcf964c6411d1e9b20f4
---

### Настройка сервера

* устанавливаем wireguard
* генерируем приватный ключ для сервера
```
wg genkey | sudo tee /etc/wireguard/private.key
sudo chmod go= /etc/wireguard/private.key
```
* генерируем публичный ключ на основе приватного
```
sudo cat /etc/wireguard/private.key | wg pubkey | sudo tee /etc/wireguard/public.key
```
* создаем конфигурацию `/etc/wireguard/wg0.conf`
```
[Interface]
PrivateKey = <content of /etc/wireguard/private.key>
Address = 10.8.0.1/24, fd0d:86fa:c3bc::1/64
ListenPort = <anyport>
SaveConfig = true
```
* разрешаем перенаправления в сети настройками в `/etc/sysctl.conf`
```
net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1
```
* ищем сетевой интерфейс по умолчанию
```
ip route list default
```
* добваляем в конфигурацию `/etc/wireguard/wg0.conf` маршруты
```
PostUp = iptables -t nat -I POSTROUTING -o <интерфейс> -j MASQUERADE
PostUp = ip6tables -t nat -I POSTROUTING -o <интерфейс> -j MASQUERADE
PreDown = iptables -t nat -D POSTROUTING -o <интерфейс> -j MASQUERADE
PreDown = ip6tables -t nat -D POSTROUTING -o <интерфейс> -j MASQUERADE
```
* добавляем в конфигурацию `/etc/wireguard/wg0.conf` разрешения для файервола
```
PostUp = ufw route allow in on wg0 out on <интерфейс>
PreDown = ufw route delete allow in on wg0 out on <интерфейс>
```
* разрешаем в файерволе порт на которым слушает сервер (прописан `/etc/wireguard/wg0.conf`)
```
sudo ufw allow <anyport>/udp
```
* запускаем сервер
```
sudo systemctl start wg-quick@wg0.service
```

### Настройка для клиентов

* на сервере генерируем пары ключей под каждого клиента
```
wg genkey | tee /etc/wireguard/client1private.key | wg pubkey > /etc/wireguard/client1public.key
```
* отдаем кленту приватный ключ
* добавляем клиента в конфигурацию сервера
```
wg set wg0 peer <content of /etc/wireguard/client1public.key> allowed-ips 10.0.0.x/32
```
