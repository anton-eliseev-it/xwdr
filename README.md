# FORWARD -- ALL SERVERS
```
nano /etc/sysctl.conf
```
net.ipv4.ip_forward=1

```
sysctl -p
```
# WG-R --- WG-N
```
cd /etc/wireguard
```
```
systemctl start wg-quick@wg0
```
```
systemctl enable wg-quick@wg0
```
```
systemctl status wg-quick@wg0
```
# Config xray
```
sudo apt install curl unzip -y
```
```
bash -c "$(curl -L https://github.com/XTLS/Xray-install/raw/main/install-release.sh)" @ install
```
```
xray --version
```
```
cd /usr/local/etc/xray/
```
```
nano config.json
```
```
systemctl restart xray
```
```
systemctl enable xray
```
```
systemctl status xray
```
# KEYS -- UUID -- XRAY
```
xray uuid
```
```
xray x25519
```
# LINK FOR CLIENTS
```
vless://YOUR_UUID@SERVER1_PUBLIC_IP:443?type=tcp&security=reality&pbk=YOUR_PUBLIC_KEY&fp=chrome&spx=/&sni=www.microsoft.com&sid=b1&flow=xtls-rprx-vision#MyXrayServer
```
# DON'T FORGET SHORTID (sid)

# COMMENTS
 •  YOUR_UUID: UUID.
 •  SERVER1_PUBLIC_IP: Публичный IP Server1.
 •  YOUR_PUBLIC_KEY: Public key из xray x25519.
 •  sni=www.microsoft.com (http://www.microsoft.com/): (http://www.microsoft.com/) Должен совпадать с serverNames.
 •  sid=b1: Твой shortId.
 •  fp=chrome: Fingerprint для uTLS (можно firefox, safari и т.д.).

# Example
примеры шортайди

•  01
•  ab
•  b1
•  12
•  ffee
•  a1b2
•  123456
•  deadbeef
•  cafe1234

# FOR NEW CLIENTS
```
"clients": [
  {
    "id": "старый_UUID_который_уже_есть",
    "flow": "xtls-rprx-vision"
  },
  {
    "id": "новый_UUID_для_нового_устройства",   // сгенерируй: xray uuid
    "flow": "xtls-rprx-vision",
    "email": "phone-new"                         // опционально, для логов
  }
]
```
