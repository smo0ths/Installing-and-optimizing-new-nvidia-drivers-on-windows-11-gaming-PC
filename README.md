### Installing and optimizing new nvidia drivers on windows 11 gaming PC:

---

```python
NVCleanstall:
download driver
use driver files on disk
check PhysX, Microsoft Visual C 2017 Runtimes and NV container
disable installer telemetry & advertising
perform clean install
disable MPO
disable Ansel
show expert tweaks
Enable Message Signaled Interrupts (high/irqPolicySpreadMessagesAcrossAllProcessors test or skip)
disable HDCP
build package
```

---

#### Reset GPU overclock and disable start with windows/apply at startup (MSI Afterburner)

---

```python
press ⊞ Win+R > type msconfig > boot > safe boot
reboot
press ⊞ Win+R > type msconfig > boot > safe boot > uncheck > exit without restarting*
run DDU uninstall (as admin) > options > remove physX > Clean and restart
install driver (as admin)
```

---

```python
NVIDIA Control Panel:
Adjust image settings with preview > Use my preference emphasizing > Performance > Apply
Use the advanced 3D image settings > Apply
Manage 3D settings > Global Settings > Anisotropic filtering > Appplication-controlled or off/4x/8x/16x
Manage 3D settings > Global Settings > Low Latency Mode > Ultra
Manage 3D settings > Global Settings > Power management mode > Prefer maximum performance
Manage 3D settings > Global Settings > Preferred refresh rate > Highest available
Manage 3D settings > Global Settings > Anisotropic sample optimization > On
Manage 3D settings > Global Settings > Negative LOD bias > Clamp
Manage 3D settings > Global Settings > Texture filtering Quality set to High performance (or Quality)
Manage 3D settings > Global Settings > Trilinear optimization On
Configure Surround, PhysX > set PhysX to GPU
Change resolution > set resolutions and refresh rates
Change resolution > NVIDIA color settings set Output color depth and Full dynamic range (all monitors)
Adjust desktop color settings > Digital vibrance 100% (all monitors) (this can reset after changing settings so make sure you check it)
Set up G-SYNC > Enable settings for the selected display model (turn monitor off and on for windows to figure it out) (or turn off and disable in monitor OSD)
Adjust video color settings > With the NVIDIA settings > Color 100% saturation > Advanced Full dynamic range (all monitors)
```

---

```python
nvidiaProfileInspector (as admin):
Texture Filtering - LOD Bias set what you want (Negative LOD bias needs to be set to Allow)
CUDA - Force P2 State off or on (test per-game)
rBAR Enabled (test per-game)
rBAR Options set (test per-game)
rBAR Size Limit set (test per-game)
Apply
```

---

```python
System > Display > Graphics > Default graphics settings:
Hardware-accelerated GPU scheduling On
Variable refresh rate On or off
Optimizations for windowed games On
```

---

#### Enable GPU overclock User define fan control and check start with windows (MSI Afterburner)

---

### reboot

---
---
---

### Extra

```python
Add resolutions 3328x1872 3.25K is mint for people who cant yet push 4k on 4k monitors

///

set Monitor .icc/icm profile:

put them in here ⊞ Win+R %SystemDrive%Windows/System32/spool/drivers/color

open colorcpl.exe add (sRGB Color Space Profile.icm or sRGB_ICC_v4_Appearance.icc or manufacturer calibration) as default for SDR and check box add advanced color profile .icc for HDR

///

HDR how to:

1. download MicrosoftCorporationII.WindowsHDRCalibration_1.0.152.0_neutral_~_8wekyb3d8bbwe.Msixbundle or whatever is latest

2. turn monitor on HDR mode

3. turn on HDR in windows

4. calibrate

///

High Precision event timer (HPET) on off (test)

///

add Message Signaled Interrupts manually (test)
reg add "HKLM\SYSTEM\ControlSet001\Enum\PCI\VEN_10DE&DEV_1E84&SUBSYS_139E10DE&REV_A1\4&3aaa5e18&0&0008\Device Parameters\Interrupt Management\MessageSignaledInterruptProperties" /v MSISupported /t REG_DWORD /d 1 /f
```

---
