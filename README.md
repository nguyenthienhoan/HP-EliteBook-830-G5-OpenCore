# HP EliteBook 830 G5 - OpenCore EFI

[![macOS](https://img.shields.io/badge/macOS-Sonoma%2014.x-blue.svg)](https://www.apple.com/macos/)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.9.x-green.svg)](https://github.com/acidanthera/OpenCorePkg)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Geekbench](https://img.shields.io/badge/Geekbench-Score%20Available-orange.svg)](https://browser.geekbench.com/v6/cpu/5901430)

> **⚠️ Disclaimer**: This is a Hackintosh project. Use at your own risk. Apple does not support macOS on non-Apple hardware.

A complete OpenCore EFI configuration for HP EliteBook 830 G5 laptop running macOS Sonoma 14.x with full hardware support and optimization.

## 📸 Screenshots

<div align="center">
  <img src="Picture/Sonoma.png" width="800" alt="macOS Sonoma Desktop">
  <img src="Picture/Sonoma 2.png" width="800" alt="System Information">
  <img src="Picture/Sonoma 3.png" width="800" alt="Hardware Details">
</div>

## 💻 Hardware Specifications

| Component | Specification |
|-----------|---------------|
| **Model** | [HP EliteBook 830 G5](https://support.hp.com/vn-en/document/c05898590) |
| **Processor** | Intel® Core™ i5-8350U (8th Gen)<br/>4 Cores / 8 Threads<br/>1.7 GHz Base / 3.6 GHz Turbo<br/>6 MB Cache |
| **Graphics** | Intel® UHD Graphics 620 |
| **Display** | 13.3" Full HD (1920×1080)<br/>120Hz Refresh Rate<br/>16:9 Aspect Ratio |
| **Storage** | 512 GB M.2 NVMe SSD<br/>WDC PC SN720 (Hackintosh Compatible) |
| **Memory** | 16 GB DDR4-2400 MHz<br/>Samsung Dual-Channel (8 GB × 2) |
| **Wireless** | Broadcom BCM94360CS2<br/>WiFi + Bluetooth (Hackintosh Compatible) |

## ✅ What's Working

- ✅ **CPU**: Intel i5-8350U with proper power management
- ✅ **Graphics**: Intel UHD 620 with full acceleration
- ✅ **Audio**: Built-in speakers and microphone
- ✅ **WiFi & Bluetooth**: Broadcom BCM94360CS2
- ✅ **USB**: All USB ports (2.0/3.0/3.1)
- ✅ **Trackpad**: Multi-touch gestures
- ✅ **Keyboard**: Backlit keyboard with function keys
- ✅ **Sleep/Wake**: Proper sleep and wake functionality
- ✅ **Battery**: Battery status and power management
- ✅ **Camera**: Built-in webcam
- ✅ **Ethernet**: Wired network connection
- ✅ **SD Card Reader**: Media card reader
- ✅ **NFC**: Near Field Communication

## ❌ What's Not Working

- ❌ **Fingerprint Reader**: Not supported
- ❌ **WWAN**: Cellular modem not supported
- ❌ **IR Camera**: Infrared camera not supported
- ❌ **Fan Speed Monitoring**: Hardware monitoring limited

## 📄 Installation Guide

### Prerequisites

- HP EliteBook 830 G5 laptop
- USB drive (16GB+ recommended)
- macOS installer (Sonoma 14.x)
- Basic knowledge of BIOS/UEFI settings

### Step 1: BIOS Configuration

Configure your BIOS settings as follows:

<details>
<summary><strong>Click to expand BIOS settings</strong></summary>

#### Advanced Settings

**Boot Options:**
- Startup Menu Delay: `0`
- Fast Boot: `Disabled`
- CD-ROM Boot: `Disabled`
- USB Storage Boot: `Enabled`
- Network (PXE) Boot: `Disabled`
- UEFI Boot Order: `Enabled`
- Legacy Boot Order: `Enabled`

**Secure Boot Configuration:**
- Legacy Support: `Disabled`
- Secure Boot: `Disabled`

**System Options:**
- Turbo Boost: `Enabled`
- Hyperthreading: `Enabled`
- Multi-processor: `Enabled`
- Virtualization Technology (VTx): `Enabled`
- Virtualization Technology for Directed I/O (VTd): `Enabled`

**Built-In Device Options:**
- Video Memory Size: `64MB`
- Audio Device: `Enabled`
- Wireless Network Device (WLAN): `Enabled`
- Bluetooth: `Enabled`
- Integrated Camera: `Enabled`
- Fingerprint Device: `Disabled`
- NFC: `Enabled`

**Port Options:**
- All USB Ports: `Enabled`
- Media Card Reader: `Enabled`
- Restrict USB Devices: `Allow all USB Devices`

**Power Management:**
- Runtime Power Management: `Enabled`
- Extended Idle Power States: `Enabled`
- Deep Sleep: `Enabled`
- Wake when Lid is Opened: `Enabled`

</details>

### Step 2: Create Installation Media

1. Follow the [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/#making-the-installer) to create a macOS installer
2. Download this EFI folder
3. Copy the EFI folder to the EFI partition of your USB installer

### Step 3: Install macOS

1. Boot from the USB installer (press `F12` during boot to select boot device)
2. Follow the [installation process](https://dortania.github.io/OpenCore-Install-Guide/installation/installation-process.html#booting-the-opencore-usb)
3. After installation, copy the EFI folder to your system's EFI partition

## 🍎 Enable Apple Services

To enable iMessage, FaceTime, and other Apple services:

1. **Generate SMBIOS data:**
   ```bash
   git clone https://github.com/corpnewt/GenSMBIOS
   cd GenSMBIOS
   chmod +x GenSMBIOS.command
   ./GenSMBIOS.command
   ```

2. **Configure SMBIOS:**
   - Type `3` to Generate SMBIOS
   - Type `MacBookPro15,4` and press Enter
   - Type `5` and press Enter

3. **Update config.plist:**
   - Open `/EFI/OC/Config.plist`
   - Navigate to `PlatformInfo → Generic`
   - Replace the generated values for:
     - `MLB`
     - `SystemSerialNumber`
     - `SystemUUID`

## 📁 Repository Structure
