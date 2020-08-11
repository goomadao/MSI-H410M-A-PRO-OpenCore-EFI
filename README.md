# 微星H410M-A PRO OpenCore EFI

## 介绍

- 可用于引导Catalina 10.15.6以及~~Bug~~Big Sur public beta 1
- 所有Kext以及OpenCorePkg都是由最新commit编译的(均为Release版)。[编译时间: 2020-08-11]
    - 声卡设备为`0xA3F0`，[AppleALC](https://github.com/goomadao/AppleALC/releases/tag/1.5.1.1)基于最新commit修改并编译。
    - USB controller为`0xA3AF`，因此`USBInjectAll.kext`和`XHCI-unsupported.kext`也需要修改。
    - 以上三个Kext可以在[Modified Kexts](./Modified%20Kexts)中找到
### 正常工作
- [x] 板载声卡
- [x] 板载网卡
- [x] 核显硬解
- [x] Airdrop / Handoff / Sidecar
- [x] 睡眠 / 唤醒
- [x] USB2.0 / USB 3.0
### 待解决问题
- [ ] DRM
- [ ] 其他，欢迎提出，会尽快解决

## 我的配置
| 硬件 | 型号 |
| :-: | :-: |
| 主板 | MSI H410M-A PRO |
| CPU | QSRK(i5 10500 ES) |
| 显卡 | RX570 4GB |
| 内存 | 棘蛇 DDR4 2666 16G×2 |
| 硬盘 | 西数 SN720 500G |
| 蓝牙及无线 | BCM94360CS2 |

## Tips
- 请自行修改config.plist中的`MLB`, `SystemSerialNumber`以及`SystemUUID`
- 为了引导~~Bug~~Big Sur，对CPU进行了仿冒，否则开机会卡EB。如果用于引导Catalina，可以将其删除。
- 如果使用核显连接显示器，请将缓冲帧由`0300C89B`改为`07009B3E`
- USB已经进行定制，如果USB端口与本主板不一致可以使用repo中的[`USBInjectAll.kext`](./Modified%20Kexts/USBInjectAll.kext)再自己进行定制。

## 鸣谢
[Dortania's OpenCore Install Guide](https://dortania.github.io/getting-started/)

[OCBuilder](https://github.com/Pavo-IM/ocbuilder)