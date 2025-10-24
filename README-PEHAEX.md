# PEHAEX - PHX AI MCP Enhanced Version

> **Repository:** https://github.com/Zzz0029/PEHAEX

## 🎉 Successfully Pushed to GitHub!

Repository ini berisi PHX AI MCP (Model Context Protocol) yang sudah diperbaiki dan dioptimalkan untuk Windows + WSL environment.

## 📋 What's Included

### Core Files
- ✅ `phx_server.py` - PHX MCP server (150+ security tools)
- ✅ `phx_mcp.py` - PHX MCP client for Cursor/Claude/VS Code
- ✅ `README.md` - Original HexStrike AI documentation

### Configuration Files (FIXED)
- ✅ `phx-wsl-mcp-config.json` - **WSL configuration (RECOMMENDED)**
- ✅ `phx-mcp-config.json` - Windows native configuration
- ✅ `phx-wsl-mcp-config-secure.json` - WSL with security settings
- ✅ `phx-mcp-configs.md` - Configuration guide

### Documentation (NEW)
- ✅ `QUICK-FIX.txt` - **START HERE!** Quick setup guide
- ✅ `SOLUSI-PHX-NO-TOOLS.md` - Solusi lengkap untuk "no tools" issue
- ✅ `CURSOR-SETUP-INSTRUCTIONS.md` - Instruksi detail setup Cursor
- ✅ `PHX-README.md` - PHX specific documentation

## 🚀 Quick Start

### 1. Start PHX Server

```bash
wsl -- /mnt/d/aihex/PHX/hexstrike-wsl-env/bin/python3 /mnt/d/aihex/PHX/phx_server.py
```

Server akan berjalan di: `http://0.0.0.0:8888`

### 2. Configure Cursor

**Buka:** `QUICK-FIX.txt` dan ikuti 4 langkah sederhana!

Atau manual:
1. Tekan `Ctrl + Shift + P` di Cursor
2. Ketik: "Preferences: Open User Settings (JSON)"
3. Copy config dari `phx-wsl-mcp-config.json`
4. Restart Cursor

### 3. Test Tools

Di Cursor chat:
```
list all available MCP tools from phx-ai
```

## 🔧 What Was Fixed

### Original Issue
- ❌ Server berjalan tapi tools tidak muncul di Cursor
- ❌ Config path salah
- ❌ IP address issue (WSL → Windows connectivity)

### Solutions Applied
- ✅ Fixed Python path untuk WSL: `/mnt/d/aihex/PHX/hexstrike-wsl-env/bin/python3`
- ✅ Fixed server URL: `http://10.255.255.254:8888` (Windows host IP dari WSL)
- ✅ Verified connectivity: WSL ↔ Windows server
- ✅ Created comprehensive documentation
- ✅ Added `.gitignore` untuk clean repo

## 📦 Repository Structure

```
PEHAEX/
├── 📄 README.md                         # Original docs
├── 📄 README-PEHAEX.md                  # This file
├── 📄 QUICK-FIX.txt                     # ⭐ START HERE
├── 📄 SOLUSI-PHX-NO-TOOLS.md           # Complete solution guide
├── 📄 CURSOR-SETUP-INSTRUCTIONS.md     # Detailed setup
├── 📄 PHX-README.md                    # PHX documentation
│
├── 🔧 phx_server.py                    # MCP Server
├── 🔧 phx_mcp.py                       # MCP Client
│
├── ⚙️  phx-wsl-mcp-config.json         # ⭐ WSL Config (RECOMMENDED)
├── ⚙️  phx-mcp-config.json             # Windows Config
├── ⚙️  phx-wsl-mcp-config-secure.json  # WSL Secure Config
├── ⚙️  phx-mcp-configs.md              # Config guide
│
├── 📁 assets/                          # Images and assets
├── 📁 hexstrike-wsl-env/               # WSL Python environment
└── 📁 .git/                            # Git repository
```

## 🎯 Features

### 150+ Security Tools Available
- **Network Scanning:** nmap, masscan, rustscan, autorecon
- **Web Testing:** gobuster, nuclei, sqlmap, nikto, wpscan
- **Password Cracking:** hydra, john, hashcat
- **Binary Analysis:** ghidra, radare2, gdb, pwntools
- **Cloud Security:** prowler, scout-suite, trivy
- **And many more...**

### AI-Powered
- Intelligent tool selection
- Parameter optimization
- Vulnerability correlation
- Automated workflows

## 🔗 Important Links

- **GitHub Repository:** https://github.com/Zzz0029/PEHAEX
- **Original Project:** https://github.com/0x4m4/hexstrike-ai
- **Quick Fix Guide:** [QUICK-FIX.txt](QUICK-FIX.txt)
- **Full Solution:** [SOLUSI-PHX-NO-TOOLS.md](SOLUSI-PHX-NO-TOOLS.md)

## 🆘 Troubleshooting

### Tools tidak muncul di Cursor?
👉 **Read:** `QUICK-FIX.txt`

### Server tidak bisa start?
```bash
# Check if port already in use
netstat -ano | findstr ":8888"

# Kill existing process if needed
taskkill /F /PID <PID_NUMBER>
```

### WSL connectivity issue?
```bash
# Check Windows host IP from WSL
wsl cat /etc/resolv.conf

# Update IP in config if changed
```

## 📊 Commit History

```
✅ dde64ca - Add .gitignore and cleanup old config files
✅ 8e08378 - Add PHX AI MCP fixes: Config corrections, documentation, and troubleshooting guides
✅ c5b4325 - first commit
```

## 🙏 Credits

- **Original Project:** HexStrike AI by [0x4m4](https://github.com/0x4m4/hexstrike-ai)
- **Enhanced Version:** PEHAEX
- **Fixes & Documentation:** Applied for Windows + WSL compatibility

## 📝 License

MIT License (inherited from HexStrike AI)

---

## 🚀 Next Steps

1. **Read:** `QUICK-FIX.txt` untuk setup cepat
2. **Configure:** Cursor dengan config yang sudah diperbaiki  
3. **Test:** Tools availability di Cursor
4. **Enjoy:** 150+ security tools di ujung jari Anda!

---

**Made with ❤️ for cybersecurity automation**

*PEHAEX - Where PHX AI meets practical deployment*

