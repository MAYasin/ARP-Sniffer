# ARP Sniffer

A Python-based Man-in-the-Middle (MITM) utility designed to perform ARP spoofing and network packet capture. This tool is built for network security researchers and students to understand how ARP protocol vulnerabilities can be exploited.

> [!WARNING]
> **Legal Disclaimer:** This tool is for **educational and authorized security testing only**. Performing ARP spoofing on a network without explicit permission is illegal and unethical.

## 🚀 Features

* **Automated Discovery:** Scans the local network to identify active hosts and their MAC addresses.
* **ARP Spoofing:** Efficiently poisons the ARP cache of both the target and the gateway.
* **Live Sniffing:** Captures real-time traffic and exports it to a standard `.pcap` file.
* **Automatic IP Forwarding:** Configures your system to route packets so the victim does not lose internet connectivity.
* **Clean Exit:** Automatically restores the ARP tables of the target and gateway upon termination.

## 📋 Requirements

* **OS:** Linux/Unix (required for `sysctl` and packet routing).
* **Privileges:** Root/Sudo access is mandatory to manipulate network interfaces.
* **Dependencies:**
* Python 3.x
* `scapy`

## 🛠️ Installation

1. **Clone the repository:**

```bash
git clone https://github.com/MAYasin/MITMA-Script.git
cd MITMA-Script
```


2. **Install dependencies:**

```bash
pip install scapy
```

## 📖 Usage

1. **Set your network range:** Open `packet_sniffer.py` and modify the `ipRange` variable to match your local subnet (e.g., `192.168.1.0/24`).

2. **Run the tool:**

```bash
sudo python3 packet_sniffer.py

```

3. **Follow the prompts:**

* Select your target from the discovered devices list.
* The tool will begin poisoning and sniffing.
* Press `Ctrl+C` to stop the attack and gracefully restore the network.


## 🔍 How It Works

1. **Network Recon:** Uses Scapy's `ARP` function to broadcast requests and map the IP/MAC addresses on the network.
2. **IP Forwarding:** Executes a system command (`sysctl -w net.ipv4.ip_forward=1`) to act as a router.
3. **The Attack:** Sends continuous unsolicited ARP responses to the victim (claiming to be the gateway) and to the gateway (claiming to be the victim).
4. **Logging:** All intercepted packets are written to `packets.pcap` for later analysis in **Wireshark**.
5. **Recovery:** Upon exit, the script sends "correct" ARP packets to re-map the target and gateway to their legitimate hardware addresses.

## 📁 Output

| File | Description |
| --- | --- |
| `packets.pcap` | Standard packet capture file containing all intercepted traffic. |

## 📺 Demo

Check out the tool in action here:
**[Watch the Demonstration](https://youtu.be/pLeYtnbKcBI)**

---

**Author:** [MAYasin](https://github.com/MAYasin)
*Created for network security research and educational purposes.*
