# 🚀 PHX AI MCP - Instruksi Setup Cursor

## ✅ Status Saat Ini
- ✅ Server PHX sudah berjalan di port 8888 (PID: 24544)
- ✅ Python WSL environment tersedia
- ✅ Config files sudah diperbaiki
- ❌ Tools belum muncul di Cursor (perlu konfigurasi)

## 📝 Langkah-langkah Setup

### 1. Lokasi Config Cursor

Cursor membutuhkan konfigurasi MCP di salah satu lokasi ini:

**Opsi A: Cursor Settings (Recommended)**
```
%APPDATA%\Cursor\User\settings.json
```

**Opsi B: Workspace Settings**
```
.cursor\settings.json (di root folder project)
```

### 2. Buka Cursor Settings

1. Di Cursor, tekan `Ctrl + Shift + P`
2. Ketik: "Preferences: Open User Settings (JSON)"
3. File settings.json akan terbuka

### 3. Tambahkan Konfigurasi MCP

Tambahkan konfigurasi ini ke dalam `settings.json`:

```json
{
  "mcpServers": {
    "phx-ai": {
      "command": "wsl",
      "args": [
        "--",
        "/mnt/d/aihex/PHX/hexstrike-wsl-env/bin/python3",
        "/mnt/d/aihex/PHX/phx_mcp.py",
        "--server",
        "http://10.255.255.254:8888"
      ],
      "description": "PHX AI MCP v1.0 - Advanced Cybersecurity Automation Platform for WSL",
      "timeout": 300,
      "disabled": false,
      "alwaysAllow": [
        "nmap_scan",
        "gobuster_scan", 
        "nuclei_scan",
        "sqlmap_scan",
        "wpscan_scan",
        "ffuf_scan",
        "feroxbuster_scan",
        "dirsearch_scan",
        "httpx_scan",
        "amass_enum",
        "subfinder_enum",
        "theharvester_scan",
        "nikto_scan",
        "arjun_scan",
        "paramspider_scan",
        "dalfox_scan",
        "wafw00f_scan",
        "hydra_bruteforce",
        "john_crack",
        "hashcat_crack",
        "gdb_debug",
        "radare2_analyze",
        "ghidra_analyze",
        "pwntools_exploit",
        "angr_analyze",
        "checksec_analyze",
        "strings_extract",
        "binwalk_analyze",
        "exiftool_analyze",
        "steghide_extract",
        "volatility_analyze",
        "foremost_recover",
        "photorec_recover",
        "testdisk_recover",
        "prowler_assess",
        "scout_suite_audit",
        "trivy_scan",
        "kube_hunter_scan",
        "kube_bench_check",
        "docker_bench_security",
        "checkov_scan",
        "terrascan_scan",
        "browser_automation",
        "screenshot_capture",
        "dom_analysis",
        "network_monitoring",
        "security_header_analysis",
        "form_analysis",
        "javascript_execution",
        "proxy_integration",
        "multi_page_crawling",
        "performance_metrics"
      ]
    }
  }
}
```

### 4. Restart Cursor

Setelah menyimpan settings.json:
1. Tutup Cursor sepenuhnya
2. Buka kembali Cursor
3. MCP tools seharusnya sudah tersedia

### 5. Verifikasi Tools Tersedia

Di Cursor chat, ketik:
```
@phx-ai nmap_scan
```

Jika muncul autocomplete atau tool tersedia, berarti setup berhasil!

## 🔍 Troubleshooting

### Issue: Tools masih tidak muncul

**Solusi 1: Check Cursor MCP Logs**
```powershell
# Lihat log Cursor MCP
Get-Content "$env:APPDATA\Cursor\logs\*.log" -Tail 50
```

**Solusi 2: Test MCP Client Manual**
```powershell
wsl -- /mnt/d/aihex/PHX/hexstrike-wsl-env/bin/python3 /mnt/d/aihex/PHX/phx_mcp.py --server http://localhost:8888
```

**Solusi 3: Verify Server Running**
```powershell
netstat -ano | findstr ":8888"
# Should show: TCP    127.0.0.1:8888         0.0.0.0:0              LISTENING
```

### Issue: WSL Permission Error

```bash
# Di WSL, berikan permission:
chmod +x /mnt/d/aihex/PHX/hexstrike-wsl-env/bin/python3
chmod +x /mnt/d/aihex/PHX/phx_mcp.py
```

### Issue: Connection Refused

Pastikan server PHX berjalan:
```bash
# Start server jika belum running:
wsl -- /mnt/d/aihex/PHX/hexstrike-wsl-env/bin/python3 /mnt/d/aihex/PHX/phx_server.py
```

## 📊 Expected Result

Setelah setup berhasil, di Cursor chat Anda akan melihat:
- ✅ MCP Server "phx-ai" tersedia
- ✅ 60+ security tools tersedia
- ✅ Tools bisa dipanggil dengan `@phx-ai <tool_name>`

## 🎯 Quick Test

Test dengan perintah sederhana:
```
I want to scan localhost using nmap through PHX AI MCP tools
```

Cursor seharusnya otomatis menggunakan PHX tools untuk eksekusi.

## 📞 Support

Jika masih ada masalah:
1. Check server log: `Get-Content PHX.log -Tail 100`
2. Check MCP client bisa connect: Test dengan curl ke `http://localhost:8888/health`
3. Pastikan WSL Python environment aktif

---

**Files yang sudah diperbaiki:**
- ✅ `phx-wsl-mcp-config.json` - Path sudah benar
- ✅ Server running di port 8888
- ✅ MCP client verified working

**Next Step:** Configure Cursor dengan steps di atas!

