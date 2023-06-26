# OpenCore-R73700x macOS Ventura
[r/Hackintosh Post here](https://www.reddit.com/r/hackintosh/comments/wupfex/success_windows_macos_on_ryzen_7_3700x_rx_6600_xt/?utm_source=share&utm_medium=web2x&context=3)


Opencore config for my PC.
Current OC version: 0.9.3

### Hardware
- Case: Sharkoon DG7000-G RGB
- RAM: G.Skill 32GB Aegis DDR4-3000 CL16 Dual Kit
- SSD (Windows): Samsung 860 Evo 500GB
- SSD (macOS): Samsung 980 500GB
- HDD Backup: WD 1TB (idk specific information)
- GPU: RX 6600 XT (PowerColor Red Devil)
- CPU: AMD Ryzen 7 3700x
- Mainboard: ASRock X570 Phantom Gaming 4
- Ethernet: Giga PHY Intel® I211AT
- Audio: Realtek ALC1200 (layout 1, 2, 3, 4, 5, 7, 11, 27, 28, 29)
- WiFi & Bluetooth: Fenvi T919 (Link)
- Power: 750 Watt be quiet! Straight Power 11
- DVD Drive: LiteOn iHAS324 DVD-RW SATA

### Benchmarks
- [Geekbench 5](https://browser.geekbench.com/v5/cpu/21144550)

### Installation
1. Download the latest release
2. Download propertree and edit EFI/OC/config.plist
    1. Change PlatformInfo -> MLB, ROM, SystemUUID and SystemSerialNumber using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)
3. Create the macOS Installer USB-Stick using [this](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) guide. You don't need to create the EFI, that work have I done already. 
4. Update the BIOS settings according to [this](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#intel-bios-settings) guide. 
5. Insert USB and boot! When entering the macOS Recovery, click Disk Utility, format your Disk as APFS/GUID and then install macOS.

### Working
- iServices
- Davinci Resolve
- Audio (over USB, didn’t test the headphone-jack)
- GPU Acceleration
- WiFi + Bluetooth
- AirDrop, all Continuity features
- USB Ports (only on the back, I had to remove the USB-Header cable for the io-panel to get bluetooth working)
- Shutdown and Restart
- CPU temp
- Xcode
- Magic Keyboard and Mouse working in Bios, Windows and macOS without reconnecting (used a native apple-wifi-card and connected it in macOS, didn’t have to install bootcamp but wasn’t allowed to install the bluetooth driver)


### Not working
- Ethernet (AppleIGB kext currently not working, [Link to my issue](https://github.com/donatengit/AppleIGB/issues/11))
- Fan speed (AMD Power Gadget can view it but other apps in macos like the macs fan control doesn’t)
- Apple Magic Mouse scrolling under windows, because if I install the drivers of my bluetooth card I’d have to reconnect it everytime
- Sidecar because unsupported iGPU on AMD (or no iGPU found)

### Fixed bugs
- <strike>Constant SSD speed (going up and down randomly)</strike>
-> fixed by setting the `SetApfsTrimTimeout` (trim timeout on boot) to `4294967295` (maximum value)