# Hackintosh EFI: 华硕 ASUS PRIME H610M-A D4 + Intel i5-12400F + AMD RX 570

[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.6-blue.svg)](https://github.com/acidanthera/OpenCorePkg)
[![macOS](https://img.shields.io/badge/macOS-Ventura%2013.7.8-brightgreen.svg)](https://www.apple.com/macos/)

成熟稳定、开箱即用的 12 代 Intel 酷睿 Hackintosh (黑苹果) EFI 配置文件。原生体验接近白果，支持与 Windows 11 双系统共存。

---

## 🖥 硬件配置清单 (Hardware Specifications)

| 部件 (Component) | 精确型号 (Exact Model) | 驱动状态 (Status) |
| :--- | :--- | :--- |
| **处理器 (CPU)** | **Intel Core i5-12400F** (12代 Alder Lake / 6C 12T) | 原生睿频与能耗调度 (CPUFriend / RestrictEvents) |
| **主板 (Motherboard)** | **华硕 (ASUS) PRIME H610M-A D4** | 传感器完美工作 (VirtualSMC / SMCSuperIO / ALC897) |
| **独立显卡 (GPU)** | **AMD Radeon RX 570 (8GB 显存 / 满血版)** | 原生免驱 / 4K UHD 110Hz 输出 / Metal 硬件加速 |
| **内存 (RAM)** | **金百达 (Kingbank) DDR4 3200MHz 16GB** | 运行正常 |
| **固态硬盘 (SSD)** | **西部数据 (WD Blue) SN570 500GB NVMe** | 原生电源管理与节能 (NVMeFix) |
| **无线网卡 (Wi-Fi)** | **博通 Broadcom BCM94360CD** (PCIe 原生免驱卡) | 纯原生免驱支持 802.11ac 5GHz 80MHz 高速通道 |
| **蓝牙 (Bluetooth)** | **BCM20702B0** (BCM94360CD 板载 USB 蓝牙) | 原生 Apple ID / 隔空投送 / 接力 / Apple Watch 解锁 |
| **板载声卡 (Audio)** | **Realtek ALC897** (Layout-ID: 11) | 内建输入输出完美 (AppleALC) |
| **板载网卡 (LAN)** | **Intel I219-V 千兆网卡** | 原生千兆握手 (IntelMausi) |

---

## 🌟 状态与功能特性 (What's Working)

- [x] **图形加速与显示**：AMD RX 570 原生免驱，支持 DP 4K UHD 60~120Hz 高清输出，Metal 硬件解码正常。
- [x] **Apple 原生生态**：得益于 BCM94360CD 白果卡，隔空投送 (AirDrop)、接力 (Handoff)、随航 (Sidecar)、隔空播放 (AirPlay)、Apple Watch 靠近解锁完全原生可用。
- [x] **音效与麦克风**：板载耳机/音箱输出、麦克风输入正常切换。
- [x] **USB 端口**：已为华硕 H610M-A 制作专属 `USBPorts.kext` 定制驱动（映射至 11 个端口），规避 15 端口限制与唤醒冲突。
- [x] **电源管理与休眠**：S3 深度断电睡眠正常，风扇彻底停转，支持键鼠随时唤醒。
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

为了保护个人隐私，本仓库的 `EFI/OC/Config.plist` 中的机器三码已被脱敏置空。
**在首次引导前，请务必使用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成你的专属三码：**

1. 机型选择：`MacPro7,1`
2. 用 OpenCore Configurator 或 ProperTree 打开 `EFI/OC/Config.plist`；
3. 将生成的以下四项填入 `PlatformInfo` ➔ `Generic`：
   * `SystemSerialNumber` (序列号)
   * `MLB` (主板序列号)
   * `SystemUUID` (系统 UUID)
   * `ROM` (MAC 地址，可填入网卡物理地址或使用 000000000000)
4. 保存后放入启动盘 EFI 分区即可顺畅引导。

---

## 📜 鸣谢 (Credits)
- [Acidanthera](https://github.com/acidanthera) 团队维护的 OpenCore 及核心 Kexts 驱动。
- Dortania 编写的 [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/)。
