# Hackintosh EFI for ASUS 600 Series + Intel Core i5-12400F + AMD RX 570

[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.6-blue.svg)](https://github.com/acidanthera/OpenCorePkg)
[![macOS](https://img.shields.io/badge/macOS-Ventura%2013.7.8-brightgreen.svg)](https://www.apple.com/macos/)

成熟稳定、开箱即用的 12 代 Intel 酷睿 Hackintosh (黑苹果) EFI 配置文件。支持与 Windows 11 双系统共存。

---

## 🖥 硬件配置 (Hardware Specifications)

| 部件 (Component) | 规格型号 (Specification) | 驱动状态 (Status) |
| :--- | :--- | :--- |
| **处理器 (CPU)** | Intel Core i5-12400F (12代 Alder Lake / 6C 12T) | 原生睿频与能耗调度 (CPUFriend / RestrictEvents) |
| **主板 (Motherboard)** | 华硕 (ASUS) 600 系列主板 (PRIME B660 / H610) | 传感器完美工作 (VirtualSMC / SMCSuperIO) |
| **独立显卡 (GPU)** | AMD Radeon RX 570 (8GB VRAM / Polaris 20) | 原生免驱 / 4K UHD 110Hz 输出 / Metal 2 硬件加速 |
| **板载声卡 (Audio)** | Realtek ALC897 (Layout-ID: 11) | 内建输入输出正常 (AppleALC) |
| **有线网卡 (LAN)** | Intel Gigabit LAN (I219 / Intel 千兆) | 原生千兆握手 (IntelMausi) |
| **无线网卡 (Wi-Fi)** | Broadcom BCM4360 / BCM43xx (PCIe) | 原生免驱支持 802.11ac 5GHz 80MHz |
| **蓝牙 (Bluetooth)** | Broadcom BCM20702B0 (USB 内置) | 原生 Apple ID / 隔空投送 / 接力 / Apple Watch 解锁 |
| **固态硬盘 (Storage)** | NVMe PCIe SSD (WD Blue SN570 / Kingbank KP230) | 原生电源管理 (NVMeFix) |

---

## 🌟 状态与功能特性 (What's Working)

- [x] **图形加速与显示**：AMD RX 570 原生免驱，支持 DP 4K UHD 60~120Hz 高清输出，Metal 硬件解码正常。
- [x] **Apple 原生生态**：隔空投送 (AirDrop)、接力 (Handoff)、随航 (Sidecar)、隔空播放 (AirPlay)、Apple Watch 靠近解锁完全原生可用。
- [x] **音效与麦克风**：板载耳机/音箱输出、麦克风输入正常切换。
- [x] **USB 端口**：已完成精准端口定制（映射至 11 个以内），睡眠不被非预期外设秒唤醒。
- [x] **电源管理与休眠**：S3 深度断电睡眠正常，风扇彻底停转，支持键鼠唤醒。
- [x] **系统更新防护**：`SecureBootModel` 预设为 `Disabled`，免疫 macOS 14/15 误升级推送，长久稳定养老 Ventura。

---

## ⚙️ 推荐主板 BIOS 设置 (BIOS Settings)

### 需开启 (Enable)
- **Advanced** ➔ **CPU Configuration** ➔ **Intel (VMX) Virtualization Technology**: `Enabled`
- **Advanced** ➔ **System Agent (SA) Configuration** ➔ **VT-d**: `Enabled`
- **Advanced** ➔ **USB Configuration** ➔ **XHCI Hand-off**: `Enabled`
- **Advanced** ➔ **SATA Configuration** ➔ **SATA Mode**: `AHCI`

### 需关闭 (Disable)
- **Boot** ➔ **Fast Boot**: `Disabled`
- **Boot** ➔ **Secure Boot** ➔ **OS Type**: `Other OS`
- **Advanced** ➔ **APM Configuration** ➔ **Power On By RTC**: `Disabled`

---

## ⚠️ 重要说明：生成专属于你的三码 (SMBIOS)

为了保护隐私，本仓库的 `EFI/OC/Config.plist` 中的机器三码已被脱敏置空。
**在首次引导前，请务必使用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成你的专属三码：**

1. 机型选择：`MacPro7,1`
2. 用 OpenCore Configurator 或 ProperTree 打开 `EFI/OC/Config.plist`；
3. 将生成的以下四项填入 `PlatformInfo` ➔ `Generic`：
   * `SystemSerialNumber` (序列号)
   * `MLB` (主板序列号)
   * `SystemUUID` (系统 UUID)
   * `ROM` (MAC 地址，可留空或填入你的网卡物理地址)
4. 保存后放入启动盘 EFI 分区即可顺畅引导。

---

## 📜 鸣谢 (Credits)
- [Acidanthera](https://github.com/acidanthera) 团队维护的 OpenCore 及核心 Kexts 驱动。
- Dortania 编写的 [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)。
