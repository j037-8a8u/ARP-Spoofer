# ARP Spoofer

##  Disclaimer

This project is intended **strictly for educational purposes and authorized lab environments only**.
Do **NOT** use this tool on networks you do not own or have explicit permission to test.

---

##  Overview

This is a simple Python-based ARP spoofing script that performs a **Man-in-the-Middle (MITM)** attack by poisoning the ARP tables of a target machine and the router.

It continuously sends spoofed ARP responses to:

* Trick the **target** into thinking the attacker is the router
* Trick the **router** into thinking the attacker is the target

---

##  Features

* ARP spoofing between target and router
* Automatic MAC address resolution
* Continuous packet sending with live counter
* Exit with ARP table restoration
* Command-line argument support

---

##  Tech Stack

* Python 3
* `scapy` (packet crafting & network interaction)
* `argparse` (CLI arguments)
* `subprocess` (enabling IP forwarding)

---

##  Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/arp-spoofer.git
cd arp-spoofer
```

### 2. Install dependencies

```bash
pip install scapy
```

### 3. Run as root (required)

```bash
sudo python3 arp_spoofer.py -t <target_ip> -r <router_ip>
```

---

## ⚙️ Usage

```bash
sudo python3 arp_spoofer.py -t 192.168.1.5 -r 192.168.1.1
```

### Arguments:

| Flag             | Description       |
| ---------------- | ----------------- |
| `-t`, `--target` | Target IP address |
| `-r`, `--router` | Router/Gateway IP |

---

##  Example Output

```
[+] Sent 120 packets
```

Press `CTRL + C` to stop:

```
[-] Detected Ctrl + C  -->  Quitting
[+] ARP Tables restored
```

---

##  How It Works

1. Retrieves MAC addresses using ARP requests
2. Sends forged ARP replies:

   * Target → Attacker is router
   * Router → Attacker is target
3. Enables IP forwarding for packet relay
4. Continuously maintains spoofed state
5. Restores ARP tables on exit

---

##  Requirements & Notes

* Must be run with **root privileges**
* Works only on **local networks (LAN)**
* Ensure IP forwarding is enabled:

  ```bash
  echo 1 > /proc/sys/net/ipv4/ip_forward
  ```

---

##  Ethical Use

Only use this tool in:

* Personal labs (e.g., VMware, VirtualBox)
* Capture-the-flag environments
* Authorized penetration testing scenarios

---

---
