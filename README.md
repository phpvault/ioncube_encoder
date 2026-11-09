<div align="center">

# PHPVault ionCube Encoder

**Official ionCube PHP encoder — download, configure, and run. No build required.**

[![Telegram](https://img.shields.io/badge/Telegram-@phpvault-2CA5E0?logo=telegram)](https://t.me/phpvault)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux%20%7C%20macOS%20%7C%20FreeBSD-blue)](#download)
[![PHP](https://img.shields.io/badge/PHP-7.1%20→%208.4-777BB4?logo=php)](#supported-php-versions)

</div>

---

## What it does

Drop your plain PHP source files into the `source/` folder, run the binary, and get official ionCube compiled & protected bytecode files in `encoded/` — preserving the full directory tree.

```
source/
├── index.php          ← plain PHP source
└── app/
    └── core.php       ← plain PHP source

       ↓  encoder --php 8.2  ↓

encoded/
├── index.php          ✓ ionCube protected bytecode
└── app/
    └── core.php       ✓ ionCube protected bytecode
```

---

## Download

> Pre-compiled static binaries — no installation, no dependencies.
> Download the archive for your platform, extract, and run.

### Latest release

| Platform | Architecture | Download |
|----------|-------------|---------|
| **Windows** | amd64 (64-bit) | [encoder-windows-amd64.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-windows-amd64.zip) |
| **Windows** | x86 (32-bit) | [encoder-windows-386.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-windows-386.zip) |
| **Windows** | ARM64 | [encoder-windows-arm64.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-windows-arm64.zip) |
| **Linux** | amd64 (64-bit) | [encoder-linux-amd64.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-linux-amd64.zip) |
| **Linux** | x86 (32-bit) | [encoder-linux-386.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-linux-386.zip) |
| **Linux** | ARM64 / aarch64 | [encoder-linux-arm64.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-linux-arm64.zip) |
| **Linux** | ARM32 (ARMv7) | [encoder-linux-armv7.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-linux-armv7.zip) |
| **macOS** | Intel (amd64) | [encoder-darwin-amd64.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-darwin-amd64.zip) |
| **macOS** | Apple Silicon (ARM64 M1/M2/M3/M4) | [encoder-darwin-arm64.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-darwin-arm64.zip) |
| **FreeBSD** | amd64 | [encoder-freebsd-amd64.zip](https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-freebsd-amd64.zip) |

---

## Quick Start

### Step 1 — Download & extract

**Windows (PowerShell)**
```powershell
# Download
Invoke-WebRequest -Uri "https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-windows-amd64.zip" -OutFile encoder.zip
Expand-Archive encoder.zip .
```

**Linux / macOS (bash)**
```bash
# Download
curl -L "https://github.com/phpvault/ioncube_encoder/raw/refs/heads/main/encoders/encoder-linux-amd64.zip" -o encoder.zip
unzip encoder.zip
chmod +x encoder-linux-amd64
```

### Step 2 — Configure Key

Save your key once with:

```bash
./encoder config -key YOUR_KEY_HERE
```

Or set the environment variable:

```bash
export EASYENCODER_API_KEY="YOUR_KEY_HERE"
```

> **Get your key & credits →** Join **[@phpvault](https://t.me/phpvault)** on Telegram.

### Step 3 — Put PHP files in `source/`

The `source/` and `encoded/` directories are handled automatically.
Copy your PHP source scripts or whole project folders there — subdirectories are fully preserved.

```
your-folder/
├── encoder.exe        (or encoder-linux-amd64, encoder-macos-arm64 …)
├── source/
│   └── your-files.php
└── encoded/           ← encoded files generated here
```

### Step 4 — Run

```bash
# Default target PHP version (8.2)
./encoder -i ./source -o ./encoded

# Target specific PHP version (7.1 – 8.4)
./encoder -i ./source -o ./encoded --php 8.1
./encoder -i ./source -o ./encoded --php 7.4

# Max Obfuscation profile
./encoder -i ./source -o ./encoded --type ioncube_max

# Help
./encoder --help
```

---

## Supported PHP Versions

Official ionCube compiler engines supported:

| Target Runtime | Versions |
|----------------|----------|
| **PHP 7.x** | `7.1` `7.2` `7.4` |
| **PHP 8.x** | `8.1` `8.2` `8.3` `8.4` |

Default target version: **8.2**

---

## Usage Reference

```
Usage: encoder [flags] <command> [arguments]
       encoder -i <input_path> [-o <output_path>] [flags]

Commands:
  encode <path>     Encode a single PHP file or an entire directory
  credits, balance  Show your remaining account credits and expiry
  ping              Test connectivity and verify your key
  config            View or update saved key
  help, -h          Show this help message

Options:
  -i, -input <path>   PHP file or folder to encode
  -o, -output <path>  Destination file or folder
  -key <key>          Your Access Key (or env EASYENCODER_API_KEY)
  -php <version>      Target PHP: 7.1, 7.2, 7.4, 8.1, 8.2, 8.3, 8.4 (default: 8.2)
  -type <profile>     Profile: ioncube (ASCII), ioncube_binary, ioncube_max (default: ioncube)
  -strip-comments     Strip comments and PHPDoc before encoding (default: true)
  -header <comment>   Custom copyright comment in file header
  -concurrency <n>    Parallel workers for directories (default: 4)
  -timeout <sec>      Timeout in seconds per job (default: 120)
```

### Example output

```
==================================================
  EasyEncoder ionCube Compilation  |  PHP 8.2
==================================================

 Target PHP:     PHP 8.2
 Encoder Type:   ioncube
 Input Dir:      source/
 Output Dir:     encoded/
 Concurrency:    4 parallel workers
==================================================
 [>] Encoding index.php ...
 [✓] Done   index.php -> encoded/index.php
 [>] Encoding app/core.php ...
 [✓] Done   app/core.php -> encoded/app/core.php

==================================================
 SUMMARY:
   Total PHP Files:      2
   Successfully Encoded: 2
   Failed:               0
   Destination:          encoded/
==================================================
```

---

## Error Reference

| Error | Meaning |
|-------|---------|
| `Key is required` | Pass `-key ...` or save it via `encoder config -key ...` |
| `unauthorized` | Key is invalid, inactive, or revoked |
| `subscription_required` | Service access requires an active plan |
| `insufficient_credits` | Account has 0 credits — top up credits via Telegram |
| `rate_limited` | Request rate limit reached — please slow down |
| `Connection failed` | Network connectivity error — check your internet connection |

---

## Exit Codes

| Code | Meaning |
|------|---------|
| `0` | All files encoded successfully |
| `1` | Configuration, authorization, or encoding error |

---

## Support & Access Key

Join the official Telegram channel for updates, announcements, and support:

**➜ [@phpvault](https://t.me/phpvault)**

---

<div align="center">
<sub>PHPVault ionCube Encoder — pre-built static binaries, no dependencies required</sub>
</div>
