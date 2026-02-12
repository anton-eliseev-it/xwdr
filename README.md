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
