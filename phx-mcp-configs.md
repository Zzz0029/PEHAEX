# PHX MCP Configuration Guide

PHX AI MCP v1.0 - Advanced Cybersecurity Automation Platform

## Available Configuration Files

### 1. WSL Configuration (Recommended for Windows Users)

**File:** `phx-wsl-mcp-config.json`

Menjalankan PHX MCP melalui WSL (Windows Subsystem for Linux) untuk kompatibilitas maksimal dengan security tools.

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
      "disabled": false
    }
  }
}
```

**Cara Menggunakan:**
1. Pastikan WSL sudah terinstall dan dikonfigurasi
2. Jalankan server di WSL: `wsl -- /mnt/d/aihex/hexstrike-ai/hexstrike-wsl-env/bin/python3 /mnt/d/aihex/hexstrike-ai/phx_server.py`
3. Copy isi file `phx-wsl-mcp-config.json` ke konfigurasi MCP client Anda

### 2. WSL Secure Mode

**File:** `phx-wsl-mcp-config-secure.json`

Mode secure yang memerlukan approval manual untuk setiap tool execution.

### 3. Windows Native Configuration

**File:** `phx-mcp-config.json`

Menjalankan PHX MCP secara native di Windows (tanpa WSL).

```json
{
  "mcpServers": {
    "phx-ai": {
      "command": "D:/aihex/hexstrike-ai/hexstrike-env/bin/python",
      "args": [
        "D:/aihex/hexstrike-ai/phx_mcp.py",
        "--server",
        "http://localhost:8888"
      ]
    }
  }
}
```

**Cara Menggunakan:**
1. Jalankan server di Windows: `D:\aihex\hexstrike-ai\hexstrike-env\Scripts\python.exe phx_server.py`
2. Copy isi file `phx-mcp-config.json` ke konfigurasi MCP client Anda

## Setup Instructions

### WSL Setup (Recommended)

1. **Install WSL (jika belum):**
   ```powershell
   wsl --install
   ```

2. **Setup Python Environment di WSL:**
   ```bash
   # Masuk ke WSL
   wsl
   
   # Navigate ke project directory
   cd /mnt/d/aihex/hexstrike-ai
   
   # Buat virtual environment
   python3 -m venv hexstrike-wsl-env
   source hexstrike-wsl-env/bin/activate
   
   # Install dependencies
   pip3 install -r requirements.txt
   ```

3. **Install Security Tools di WSL:**
   ```bash
   # Update package list
   sudo apt update
   
   # Install essential tools
   sudo apt install -y nmap gobuster nuclei sqlmap nikto \
                      hydra john hashcat radare2 gdb binwalk
   ```

4. **Start Server di WSL:**
   ```bash
   # Dari WSL terminal
   cd /mnt/d/aihex/hexstrike-ai
   source hexstrike-wsl-env/bin/activate
   python3 phx_server.py
   ```

5. **Konfigurasi MCP Client:**
   - Copy isi dari `phx-wsl-mcp-config.json`
   - Paste ke file konfigurasi MCP client Anda:
     - **Cursor/Claude Desktop:** `~/.config/Claude/claude_desktop_config.json`
     - **VS Code Copilot:** `.vscode/settings.json`
   - Restart MCP client

### Windows Native Setup

1. **Setup Python Environment:**
   ```powershell
   cd D:\aihex\hexstrike-ai
   python -m venv hexstrike-env
   .\hexstrike-env\Scripts\activate
   pip install -r requirements.txt
   ```

2. **Start Server:**
   ```powershell
   .\hexstrike-env\Scripts\python.exe phx_server.py
   ```

3. **Konfigurasi MCP Client:**
   - Copy isi dari `phx-mcp-config.json`
   - Sesuaikan path jika berbeda
   - Paste ke file konfigurasi MCP client Anda

## Testing Connection

### Test Server Health
```bash
# Dari browser atau curl
curl http://localhost:8888/health

# Expected response:
{
  "status": "healthy",
  "message": "PHX AI Tools API Server is operational"
}
```

### Test MCP Connection
Setelah mengkonfigurasi MCP client, coba prompt berikut:

```
Use PHX MCP to scan example.com with nmap
```

## Troubleshooting

### WSL Issues

**Problem:** Command 'wsl' not found
```powershell
# Install WSL
wsl --install
```

**Problem:** Python not found in WSL
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

**Problem:** Permission denied
```bash
# Fix permissions
chmod +x /mnt/d/aihex/hexstrike-ai/hexstrike-wsl-env/bin/python3
```

### Connection Issues

**Problem:** Cannot connect to server
```bash
# Check if server is running
netstat -tlnp | grep 8888

# Check firewall
# Windows: Allow port 8888 in Windows Firewall
# WSL: No firewall by default
```

**Problem:** Server starts but MCP can't connect
- Pastikan path di config file benar
- Pastikan server berjalan di port 8888
- Check log file: `phx.log`

## Advanced Configuration

### Custom Port
```bash
# Start server on custom port
python3 phx_server.py --port 9999

# Update config file:
"args": [
  "/mnt/d/aihex/hexstrike-ai/phx_mcp.py",
  "--server",
  "http://localhost:9999"
]
```

### Debug Mode
```bash
python3 phx_server.py --debug
```

### Environment Variables
```bash
export PHX_PORT=8888
export PHX_HOST=127.0.0.1
python3 phx_server.py
```

## Security Notes

⚠️ **Important:**
- Mode WSL lebih aman karena isolated dari Windows system
- Gunakan secure mode untuk production
- Monitor log file secara regular
- Jangan expose server ke public network

## Support

Untuk issue dan pertanyaan:
- Check `phx.log` untuk error details
- Pastikan semua dependencies terinstall
- Verify path configurations

## Migration dari HexStrike

Jika sebelumnya menggunakan HexStrike MCP:
1. Backup konfigurasi lama
2. Update path ke `phx_mcp.py` dan `phx_server.py`
3. Restart MCP client
4. File lama akan dihapus otomatis

---

**PHX AI MCP v1.0** - Powered by Advanced Cybersecurity Intelligence

