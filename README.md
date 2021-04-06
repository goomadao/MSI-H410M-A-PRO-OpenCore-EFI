# 微星 H410M-A PRO OpenCore EFI

## 介绍

- 可用于引导~~Bug~~Big Sur 11.2.3，其他版本及 Catalina 请自行测试。
- OpenCore 版本:0.6.8
  - 声卡设备地址为`PciRoot(0x0)/Pci(0x1F,0x3)`
  - USB controller 为`0xA3AF`，因此`USBInjectAll.kext`和`XHCI-unsupported.kext`也需要修改。
  - 以上`USBInjectAll.kext` 以及 `XHCI-unsupported.kext` 可以在[Modified Kexts](./Modified%20Kexts)中找到

### 正常工作

- [x] 板载声卡
- [x] 板载网卡
- [x] 核显硬解
- [x] Airdrop / Handoff / Sidecar
- [x] 睡眠 / 唤醒
- [x] USB2.0 / USB 3.0
- [x] DRM

### 待解决问题

- [ ] ~~Big Sur 下 AirPods Pro 有问题，两只耳机都戴上时左耳无声音，但暂停、切换降噪等其他功能都正常；只戴左耳时左耳才有声音。Catalina 无此问题，暂时没找到解决办法~~(是我自己在设置里面设置成了右声道（x
- [ ] 音频输出正常，但输入无法正常工作，可能需要更换其他 layout。

## 我的配置

|    硬件    |         型号         |
| :--------: | :------------------: |
|    主板    |   MSI H410M-A PRO    |
|    CPU     |  QSRK(i5 10500 ES)   |
|    内存    | 棘蛇 DDR4 2666 16G×2 |
|    硬盘    |   西数 SN720 500G    |
| 蓝牙及无线 |     BCM94360CS2      |

## Tips

- 请自行修改 config.plist 中的`MLB`, `SystemSerialNumber`以及`SystemUUID`
- 本 EFI 使用核显连接显示器，可用缓冲帧有`07009B3E`和`00009B3E`，不过会出现黑屏问题，需要开关显示器才能解决。如果使用独显连接显示器，请将缓冲帧更改为`0300C89B`，并且`device-id`也可以删除。([参考](https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#deviceproperties))
- USB 已经进行定制，如果 USB 端口与本主板不一致可以使用 repo 中的[`USBInjectAll.kext`](./Modified%20Kexts/USBInjectAll.kext)再自己进行定制。

## 鸣谢

[Dortania's OpenCore Install Guide](https://dortania.github.io/getting-started/)

[OCBuilder](https://github.com/Pavo-IM/ocbuilder)
