# mirakurun + EPGStation for PX-S1UD

多分動く

# ENV

## 環境1
- Raspberry Pi 3B+
- PLEX PX-S1UD V2
- NTTCommunications ACR390NTTCom

## 環境2
- Raspberry Pi 4
- VASTDTV VT20
- SCM Microsystems, Inc. SCR331-LC1 / SCR3310 SmartCard Reader

# 立ち上げ
```
$ cat /etc/os-release
PRETTY_NAME="Raspbian GNU/Linux 12 (bookworm)"
NAME="Raspbian GNU/Linux"
VERSION_ID="12"
VERSION="12 (bookworm)"
VERSION_CODENAME=bookworm
ID=raspbian
ID_LIKE=debian
HOME_URL="http://www.raspbian.org/"
SUPPORT_URL="http://www.raspbian.org/RaspbianForums"
BUG_REPORT_URL="http://www.raspbian.org/RaspbianBugs"
$ uname -a
Linux raspberrypi 6.1.0-rpi7-rpi-v8 #1 SMP PREEMPT Debian 1:6.1.63-1+rpt1 (2023-11-24) aarch64 GNU/Linux
$ getconf LONG_BIT
32
```

## 1. docker, docker compose
ref. https://docs.docker.com/engine/install/raspberry-pi-os/
- ユーザをdocker グループに追加するのを忘れないように
- systemdで自動起動するように設定する

## 2. install firmware 
```
wget http://plex-net.co.jp/plex/px-s1ud/PX-S1UD_driver_Ver.1.0.1.zip
unzip PX-S1UD_driver_Ver.1.0.1.zip
sudo cp PX-S1UD_driver_Ver.1.0.1/x64/amd64/isdbt_rio.inp /lib/firmware/
sudo reboot
```

## 3. git clone 
```
git clone https://github.com/ma1750/mirakurun_epgstation_px-s1ud.git
cd mirakurun_epgstation_px-s1ud/
```

## 4. init mirakurun
```
docker compose run --rm -e SETUP=true mirakurun
```

## 5. run & fun
```
docker compose up -d
```
