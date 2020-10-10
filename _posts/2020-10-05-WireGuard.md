---
layout: post
title: WireGuard
feature-img: "assets/img/wireguard/banner.jpg"
tags: [Wireguard, VPN, SubSpace]
---

Notes on setting up WireGuard and SubSpace.  


## WireGuard
### WireGuard Server

Considering a Debian 9 (Stretch) server.

Adding unstable repo :
```bash
echo "deb http://deb.debian.org/debian/ unstable main" > /etc/apt/sources.list.d/unstable-wireguard.list
printf 'Package: *\nPin: release a=unstable\nPin-Priority: 150\n' > /etc/apt/preferences.d/limit-unstable
```
Installing
```bash
apt update
apt install wireguard-dkms wireguard-tools
```
Generating public key
```bash
sudo umask 077
sudo wg genkey 
cat privatekey | wg pubkey > publickey
```

Creating the interface in /etc/wireguard/wg0.conf
```bash
[Interface]
PrivateKey = <Serv Private Key>
Address = 10.0.0.1/24
ListenPort = 51820
PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o ens18 -j MASQUERADE; ip6tables -A FORWARD -i wg0 -j ACCEPT; ip6tables -t nat -A POSTROUTING -o ens18 -j MASQUERADE
PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o ens18 -j MASQUERADE; ip6tables -D FORWARD -i wg0 -j ACCEPT; ip6tables -t nat -D POSTROUTING -o ens18 -j MASQUERADE
SaveConfig = true

[Peer]
PublicKey = <Serv Pub Key>
AllowedIPs = 10.0.0.2/24
```

And restart
```bash
wg-quick down wg0 && wg-quick up wg0
```

### WireGuard Client
On windows, download the client [here](https://www.wireguard.com/install/)  

Click on "Add empty tunnel" or CTRL + N and complete as follow :
```bash
[Interface]
PrivateKey = <Client Private Key>
Address = 10.0.0.2/24
DNS = 1.1.1.1, 8.8.8.8

[Peer]
PublicKey = <Server Public Key>
AllowedIPs = 0.0.0.0/0
Endpoint = <Server IP or URL>:51820
```
If you want the option "Block untunneled traffic" to appear you have to specify 
```bash
AllowedIPs = 0.0.0.0/0
```
Note that the client Public and Private key are created with each empty tunnel. 
You ll need those values for the server config.  
  
Ref :  
https://www.linode.com/docs/networking/vpn/set-up-wireguard-vpn-on-debian/  
https://golb.hplar.ch/2019/07/wireguard-windows.html
## SubSpace
### SubSpace Docker