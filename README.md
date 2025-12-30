# ARP Sniffer

A Python-based Man-in-the-Middle (MITM) attack tool that performs ARP spoofing and network packet capture for educational and authorized security testing purposes.

## ⚠️ Warning

This tool performs ARP spoofing and network packet interception. **Use only on networks you own or have explicit permission to test.** Unauthorized network access is illegal.

## Features

- **ARP Spoofing**: Intercepts traffic between a target client and gateway
- **Packet Sniffing**: Captures and saves network packets to PCAP format
- **Network Discovery**: Automatically scans the network to discover connected devices
- **Gateway Detection**: Identifies the network gateway and active clients
- **IP Forwarding**: Enables IP forwarding to maintain network connectivity during the attack

## Requirements

- Python 3.x
- Linux/Unix-based system (uses `sysctl`, `route` commands)
- `scapy` library
- Root/sudo privileges

## Installation

```bash
pip install scapy
```

## Usage

Run the script with elevated privileges:

```bash
sudo python3 packet_sniffer.py
```

### How it Works

1. Enables IP forwarding to route packets between target and gateway
2. Performs ARP scan on the specified IP range (default: 192.168.1.0/24)
3. Displays all detected devices on the network
4. Allows selection of target client
5. Starts ARP spoofing to intercept traffic
6. Captures and saves packets to `packets.pcap`

### Configuration

Edit the IP range in the script:

```python
ipRange = "192.168.1.0/24"  # Change this to your network
```

## Output

- `packets.pcap`: Captured network packets in PCAP format (viewable with Wireshark)

## Disclaimer

This tool is provided for **educational purposes and authorized security testing only**. Users are responsible for ensuring they have proper authorization before running this tool on any network.

## Author

Created for network security research and educational purposes.
