# Oracle Linux 10 WSL

Oracle Linux 10 Slim distribution for Windows Subsystem for Linux (WSL).

## 📋 Overview

This repository provides Oracle Linux 10 Slim distribution optimized for Windows Subsystem for Linux (WSL). It's based on Oracle's official container image and tailored for WSL environments.

## 💾 Download

**Oracle Linux 10 WSL Image:**
- [oel10.tar.gz (Google Drive)](https://drive.google.com/file/d/1vRb0zccjhXWAPMbA6U3SZ9yMi4uY4olq/view?usp=drive_link)
- File size: ~236MB (compressed)

## 🚀 Installation

### Prerequisites
- Windows 10 version 2004 or later, or Windows 11
- WSL 2 must be installed
- Approximately 1GB of free disk space

### Step 1: Verify WSL Installation
Run PowerShell as Administrator to check if WSL is installed:

```powershell
wsl --version
```

If WSL is not installed:
```powershell
wsl --install
```

### Step 2: Download Oracle Linux 10
Download the `oel10.tar.gz` file from the Google Drive link above.

### Step 3: Import WSL Distribution
Execute the following command in PowerShell:

```powershell
# install example (D drive)
wsl --import oel10 D:\wsl\oel10 path\to\downloaded\oel10.tar.gz
```

> **Note**: Modify the path to match your actual download location.

### Step 4: Start Oracle Linux 10 WSL
```powershell
wsl -d oel10
```

## 🛠 Initial Setup

### Update Packages
```bash
dnf update -y
```

### Create User Account (Optional)
```bash
# Create new user
useradd -m -s /bin/bash yourusername
passwd yourusername

# Grant sudo privileges
usermod -aG wheel yourusername

# Set default user
echo -e "[user]\ndefault=yourusername" >> /etc/wsl.conf
```

### Install Development Tools (Optional)
```bash
# Basic development tools
dnf groupinstall -y "Development Tools"

# Additional useful packages
dnf install -y git vim curl wget htop
```

## 📖 Usage

### List WSL Distributions
```powershell
wsl -l -v
```

### Run Oracle Linux 10
```powershell
# Run as default user
wsl -d oel10

# Run as root
wsl -d oel10 -u root
```

### Terminate WSL Instance
```powershell
wsl -t oel10
```

### Remove WSL Distribution (if needed)
```powershell
wsl --unregister oel10
```

## 🔧 Troubleshooting

### Resolve Mount Errors
If you encounter Windows drive mount errors:

```bash
# Clear /etc/fstab file
sudo > /etc/fstab

# Restart WSL
exit
```

In PowerShell:
```powershell
wsl --shutdown
wsl -d oel10
```

### Enable systemd
```bash
sudo bash -c 'echo -e "[boot]\nsystemd=true" >> /etc/wsl.conf'
```

Restart WSL to activate systemd.

## 📚 Additional Information

### Oracle Linux Features
- **Package Manager**: `dnf` (successor to YUM)
- **Default Shell**: bash
- **Base**: Red Hat Enterprise Linux compatible
- **License**: Oracle Linux is free to use

### Useful Commands
```bash
# Check system information
cat /etc/oracle-release

# List running services
systemctl list-units --type=service --state=running

# Check disk usage
df -h

# Check memory usage
free -h
```

## ⚠️ Important Notes

1. **License**: Free for personal and development use, but check Oracle license policy for commercial use.

2. **Resource Usage**: Oracle Linux may use more disk space and memory compared to Ubuntu or Alpine Linux.

3. **Updates**: Regularly run `dnf update` to apply security patches.

## 🤝 Contributing

Please submit issue reports or improvement suggestions through GitHub Issues.

## 📄 License

This project follows Oracle Linux licensing policy.

## 🔗 Related Links

- [Oracle Linux Official Site](https://www.oracle.com/linux/)
- [WSL Official Documentation](https://docs.microsoft.com/en-us/windows/wsl/)
- [Oracle Container Registry](https://container-registry.oracle.com/)

---

**💡 Tip**: If you encounter issues while using WSL, try shutting down all WSL instances with `wsl --shutdown` and restart.
