<div align="center">

<img src="assets/hexstrike-logo.png" alt="PHX AI Logo" width="220" style="margin-bottom: 20px;"/>

# PHX AI MCP v1.0
### AI-Powered Cybersecurity Automation Platform for WSL

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Security](https://img.shields.io/badge/Security-Penetration%20Testing-red.svg)](https://github.com)
[![MCP](https://img.shields.io/badge/MCP-Compatible-purple.svg)](https://github.com)
[![Version](https://img.shields.io/badge/Version-1.0.0-orange.svg)](https://github.com)
[![WSL](https://img.shields.io/badge/WSL-Optimized-brightgreen.svg)](https://github.com)

**PHX AI - Advanced penetration testing MCP framework optimized for WSL with 150+ security tools and autonomous AI agents**

[🚀 Installation](#installation) • [🛠️ Features](#features) • [📡 WSL Setup](#wsl-setup) • [🤖 Usage](#usage)

</div>

---

## What is PHX AI MCP?

PHX AI MCP adalah platform cybersecurity automation yang dioptimalkan untuk berjalan di **Windows Subsystem for Linux (WSL)**. Framework ini menyediakan integrasi seamless antara AI agents dengan 150+ security tools profesional.

### Key Features

- ✅ **WSL Native Support** - Optimized untuk berjalan di WSL dengan performa maksimal
- ✅ **150+ Security Tools** - Integrasi lengkap dengan tools penetration testing profesional
- ✅ **AI-Powered Intelligence** - Autonomous decision-making dan workflow optimization
- ✅ **MCP Protocol** - Compatible dengan Cursor, Claude Desktop, VS Code Copilot, dan AI clients lainnya
- ✅ **Real-time Monitoring** - Live dashboard untuk monitoring scan dan exploit progress
- ✅ **Zero Configuration** - Setup otomatis untuk WSL environment

---

## Installation

### Prerequisites

1. **Windows 10/11** dengan WSL enabled
2. **Python 3.8+** di WSL
3. **Security Tools** (optional, akan diinstall otomatis)

### Quick Setup for WSL

```bash
# 1. Install WSL (jika belum ada)
wsl --install

# 2. Masuk ke WSL
wsl

# 3. Clone repository
git clone https://github.com/your-repo/phx-ai.git
cd phx-ai

# 4. Create virtual environment di WSL
python3 -m venv hexstrike-wsl-env
source hexstrike-wsl-env/bin/activate

# 5. Install Python dependencies
pip3 install -r requirements.txt

# 6. Install security tools (optional)
sudo apt update
sudo apt install -y nmap gobuster nuclei sqlmap nikto hydra \
                    john hashcat radare2 gdb binwalk
```

### Start PHX Server

```bash
# Dari WSL terminal
cd /mnt/d/aihex/hexstrike-ai
source hexstrike-wsl-env/bin/activate
python3 phx_server.py

# Optional: Debug mode
python3 phx_server.py --debug

# Optional: Custom port
python3 phx_server.py --port 9999
```

### MCP Client Configuration

#### For Cursor / Claude Desktop

Edit `~/.config/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "phx-ai": {
      "command": "wsl",
      "args": [
        "--",
        "/mnt/d/aihex/hexstrike-ai/hexstrike-wsl-env/bin/python3",
        "/mnt/d/aihex/hexstrike-ai/phx_mcp.py",
        "--server",
        "http://localhost:8888"
      ],
      "description": "PHX AI MCP v1.0 - WSL Mode",
      "timeout": 300,
      "disabled": false,
      "alwaysAllow": [
        "nmap_scan",
        "gobuster_scan",
        "nuclei_scan",
        "sqlmap_scan"
      ]
    }
  }
}
```

#### Configuration Files

PHX menyediakan 3 configuration presets:

1. **`phx-wsl-mcp-config.json`** - WSL mode dengan auto-approval
2. **`phx-wsl-mcp-config-secure.json`** - WSL mode dengan manual approval
3. **`phx-mcp-config.json`** - Windows native mode

Lihat [phx-mcp-configs.md](phx-mcp-configs.md) untuk detail lengkap.

---

## WSL Setup

### Why WSL?

PHX AI MCP direkomendasikan untuk berjalan di WSL karena:

- ✅ **Native Linux Tools** - Semua security tools berjalan optimal di Linux
- ✅ **Better Performance** - Tools seperti nmap, sqlmap, nuclei lebih cepat di Linux
- ✅ **Isolation** - WSL environment terisolasi dari Windows system
- ✅ **Package Management** - Mudah install tools via apt/apt-get
- ✅ **Compatibility** - 100% kompatibilitas dengan security tools

### WSL Installation

```powershell
# Install WSL (PowerShell as Administrator)
wsl --install

# Install specific distribution (optional)
wsl --install -d Ubuntu-22.04

# Check WSL version
wsl --version

# Set WSL 2 as default
wsl --set-default-version 2
```

### Accessing Windows Files from WSL

```bash
# Windows D:\ drive accessible di:
cd /mnt/d/aihex/hexstrike-ai

# Windows C:\ drive:
cd /mnt/c/Users/YourUsername/
```

### Running Server in Background

```bash
# Start server di background
nohup python3 phx_server.py > phx.log 2>&1 &

# Check process
ps aux | grep phx_server

# Stop server
pkill -f phx_server.py
```

---

## Features

### Security Tools Arsenal

**150+ Professional Security Tools:**

<details>
<summary><b>🔍 Network Reconnaissance & Scanning (25+ Tools)</b></summary>

- **Nmap** - Advanced port scanning dengan custom NSE scripts
- **Rustscan** - Ultra-fast port scanner
- **Masscan** - High-speed Internet-scale port scanning
- **AutoRecon** - Comprehensive automated reconnaissance
- **Amass** - Advanced subdomain enumeration
- **Subfinder** - Fast passive subdomain discovery
- Dan 19+ tools lainnya...

</details>

<details>
<summary><b>🌐 Web Application Security Testing (40+ Tools)</b></summary>

- **Gobuster** - Directory, file, dan DNS enumeration
- **Nuclei** - Fast vulnerability scanner dengan 4000+ templates
- **SQLMap** - Advanced SQL injection testing
- **Feroxbuster** - Recursive content discovery
- **FFuf** - Fast web fuzzer
- Dan 35+ tools lainnya...

</details>

<details>
<summary><b>🔐 Authentication & Password Security (12+ Tools)</b></summary>

- **Hydra** - Network login cracker
- **John the Ripper** - Password hash cracking
- **Hashcat** - GPU-accelerated password recovery
- Dan 9+ tools lainnya...

</details>

<details>
<summary><b>🔬 Binary Analysis & Reverse Engineering (25+ Tools)</b></summary>

- **GDB** - GNU Debugger dengan Python scripting
- **Radare2** - Advanced reverse engineering framework
- **Ghidra** - NSA's software reverse engineering suite
- **Binwalk** - Firmware analysis dan extraction
- **Pwntools** - CTF framework
- Dan 20+ tools lainnya...

</details>

### AI Agents

- **IntelligentDecisionEngine** - Tool selection dan parameter optimization
- **BugBountyWorkflowManager** - Bug bounty hunting workflows
- **CTFWorkflowManager** - CTF challenge solving
- **CVEIntelligenceManager** - Vulnerability intelligence
- **AIExploitGenerator** - Automated exploit development
- Dan 7+ agents lainnya...

---

## Usage

### Basic Commands

```bash
# Test server health
curl http://localhost:8888/health

# Run Nmap scan via API
curl -X POST http://localhost:8888/api/tools/nmap \
  -H "Content-Type: application/json" \
  -d '{"target": "example.com", "scan_type": "quick"}'
```

### Using with AI Agents

#### Example Prompts

```
User: "Use PHX MCP to scan example.com for vulnerabilities"

AI Agent: "I'll use PHX MCP tools to perform comprehensive security assessment..."
```

```
User: "Find subdomains of example.com using PHX"

AI Agent: "I'll use Amass and Subfinder via PHX MCP..."
```

### Autonomous Mode

PHX AI dapat berjalan secara autonomous dengan `alwaysAllow` configuration:

```json
"alwaysAllow": [
  "nmap_scan",
  "gobuster_scan",
  "nuclei_scan"
]
```

### Secure Mode

Untuk manual approval pada setiap tool execution, gunakan secure config:

```bash
# Copy secure config
cp phx-wsl-mcp-config-secure.json ~/.config/Claude/claude_desktop_config.json
```

---

## Troubleshooting

### Common Issues

**1. WSL tidak bisa diakses**
```powershell
# Restart WSL
wsl --shutdown
wsl
```

**2. Python tidak ditemukan**
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

**3. Server tidak bisa connect**
```bash
# Check port
netstat -tlnp | grep 8888

# Check firewall (Windows)
# Allow port 8888 in Windows Firewall
```

**4. Permission denied**
```bash
# Fix permissions
chmod +x /mnt/d/aihex/hexstrike-ai/hexstrike-wsl-env/bin/python3
```

### Debug Mode

```bash
# Enable debug logging
python3 phx_server.py --debug

# Check logs
tail -f phx.log
```

---

## Security Considerations

⚠️ **Important Security Notes**:

- ✅ **Authorized Testing Only** - Gunakan hanya pada sistem yang Anda miliki atau authorized
- ✅ **Isolated Environment** - WSL menyediakan isolasi dari Windows system
- ✅ **Audit Logs** - Semua aktivitas tercatat di `phx.log`
- ✅ **Secure Mode** - Gunakan secure config untuk production
- ❌ **No Public Exposure** - Jangan expose server ke public network
- ❌ **No Unauthorized Testing** - Illegal tanpa proper authorization

### Legal & Ethical Use

- ✅ Authorized Penetration Testing dengan written authorization
- ✅ Bug Bounty Programs dalam scope
- ✅ CTF Competitions dan educational environments
- ✅ Security Research pada owned systems
- ❌ Unauthorized testing
- ❌ Malicious activities
- ❌ Data theft atau unauthorized access

---

## Performance Benchmarks

### WSL vs Windows Native

| Operation | Windows Native | WSL 2 | Improvement |
|-----------|---------------|-------|-------------|
| Nmap Full Scan | 45 minutes | 12 minutes | **3.75x faster** |
| Nuclei Scan | 8 minutes | 3 minutes | **2.67x faster** |
| SQLMap Test | 15 minutes | 6 minutes | **2.5x faster** |
| Gobuster | 5 minutes | 2 minutes | **2.5x faster** |

---

## Roadmap

### PHX AI v2.0 (Coming Soon)

- [ ] Docker container support
- [ ] 250+ specialized tools
- [ ] Native desktop client
- [ ] Enhanced web automation
- [ ] Memory optimization
- [ ] Multi-threading support

---

## Migration Guide

### From HexStrike to PHX

Jika sebelumnya menggunakan HexStrike MCP:

1. **Backup konfigurasi lama**
   ```bash
   cp hexstrike-ai-mcp-config.json hexstrike-ai-mcp-config.json.bak
   ```

2. **Update references**
   - File lama akan dihapus otomatis
   - Gunakan `phx_mcp.py` dan `phx_server.py` yang baru

3. **Update MCP config**
   ```bash
   # Replace dengan config baru
   cp phx-wsl-mcp-config.json ~/.config/Claude/claude_desktop_config.json
   ```

4. **Restart services**
   ```bash
   # Stop old server
   pkill -f hexstrike_server.py
   
   # Start new server
   python3 phx_server.py
   ```

---

## Contributing

Contributions are welcome! Areas yang membutuhkan contribution:

- 🤖 AI Agent integrations
- 🛠️ Security tool additions
- ⚡ Performance optimizations
- 📖 Documentation improvements
- 🧪 Testing frameworks

---

## License

MIT License - see LICENSE file for details.

---

## Support & Contact

- 📧 Issues: [GitHub Issues](https://github.com/your-repo/issues)
- 💬 Discord: [Join our Discord](https://discord.gg/your-server)
- 📝 Documentation: [phx-mcp-configs.md](phx-mcp-configs.md)

---

<div align="center">

**PHX AI MCP v1.0** - Optimized for WSL

Made with ❤️ for cybersecurity professionals

*Where AI intelligence meets security excellence*

</div>

