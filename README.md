# ARP Poisoning Lab

A Python-based Windows network lab script that demonstrates ARP cache poisoning behavior for educational and defensive security purposes. The project detects the local gateway and your machine's network information, resolves MAC addresses, and repeatedly sends crafted ARP replies to poison the gateway ARP cache in a controlled local-network scenario.

This project is intended for:
- learning how ARP spoofing works,
- testing network behavior in a controlled lab environment,
- understanding how ARP poisoning can be detected and mitigated.

Important: Use only on networks you own or have explicit authorization to test. Unauthorized use may be illegal and unethical.

## Features

- Detects local IP and default gateway using Windows networking commands
- Resolves the gateway's MAC address through ARP data and fallback checks
- Identifies the local machine's MAC address
- Sends targeted ARP replies to poison the gateway cache
- Optionally restores ARP entries when the script is interrupted
- Uses multithreaded packet injection to continuously maintain the poisoned state

## Project Structure

- `wifi-poisoning` — main Python script that performs the ARP poisoning demonstration

## Requirements

- Windows-based environment
- Python 3
- Scapy
- Administrator privileges (typically required for network packet injection)

Install dependencies:

```bash
pip install scapy
```

## Usage

Run the script from a terminal:

```bash
python wifi-poisoning
```

Follow the prompts:

- Confirm the detected gateway and local IP
- Allow the script to activate the poisoning routine
- Press `Ctrl+C` to stop the attack and restore ARP entries

## How It Works

The script:
1. Detects the local machine IP and default gateway.
2. Resolves MAC addresses using `arp`, `ipconfig`, and Scapy-based ARP queries.
3. Builds crafted ARP reply packets with the machine's MAC address as the attacker identity.
4. Sends these packets repeatedly to poison the target ARP cache.
5. Restores correct ARP mappings when the process exits.

## Security Notes

ARP poisoning is a classic network attack method used to intercept or manipulate traffic on a local network. In production environments, this behavior is generally considered malicious unless used strictly in a legitimate security testing context.

The script is best suited for:
- personal lab environments,
- classroom demonstrations,
- cybersecurity training,
- defensive research and detection experiments.

## Legal and Ethical Use

Only use this project in:
- your own lab network,
- a test environment you explicitly control,
- an authorized security assessment with written permission.

Do not use it on public, third-party, or unauthorized networks.

## Disclaimer

This project is provided for educational and authorized security research purposes only. The author is not responsible for misuse, damage, or illegal activity performed with this code.

## License

This project currently does not include a license file. If you plan to share or distribute it publicly, consider adding an appropriate license such as MIT or GPL.
