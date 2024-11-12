### Installing and optimizing new nvidia drivers on windows 11 gaming PC:
#### more to come here i'm going to try to explain all the things like obs/audio/monitors :)

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
disable HDCP
build package
```

---

#### Reset/disable GPU overclock/Fans/Auto-startups (Afterburner/Fan Control/ect)
#### Disable internet

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
Manage 3D settings > Global Settings > Shader Cache Size > Unlimited (def is too low for lots of games will cause compile shader lag, stutters and slow compiling)
Manage 3D settings > Global Settings > Anisotropic sample optimization > On (Off for quality)
Manage 3D settings > Global Settings > Negative LOD bias > Clamp
Manage 3D settings > Global Settings > Texture filtering Quality set to High performance (or Quality for quality*)
Manage 3D settings > Global Settings > Trilinear optimization On
Configure Surround, PhysX > set PhysX to GPU
Change resolution > set resolutions and refresh rates
Change resolution > NVIDIA color settings set Output color depth and Full dynamic range (all monitors)
Adjust desktop color settings > Digital vibrance 100% (all monitors)
Adjust desktop size and position > set Full-screen for all monitors (fixes HDR 1-3 second flicker after hours of gaming)
Adjust video color settings > With the NVIDIA settings > Advanced > Dynamic range Full 0-255 (all monitors)
```

---

```python
System > Display > Graphics > Default graphics settings:
Hardware-accelerated GPU scheduling > On
Optimizations for windowed games > On
```

---

#### Enable GPU overclock/Fans/Auto-startups (Afterburner/Fan Control/ect)
#### Set fan control to 40c-60% and 80c-100% (Just stay above nvidia defaults and turn down if too loud)

---

#### reboot
#### when changing settings things could need to be reapplied make sure you check everything before gaming
#### Enable internet

---
---
---

#### Extra

```python
🟩

Maximum Pre-Rendered Frames/Low Latency Mode/Future Frame Rendering (this is for CPU)
nvidiaProfileInspector (as admin):
set Maximum Pre-Rendered Frames to 1 for best latency (should be default), Nvidia Reflex/Low Latency Mode on On+Boost/Ultra should override this in most games
Old school default was 3, 2 or more could give you more fps at cost of latency on lower end systems

🟩

Windows Game Mode (test yourself an optimized system wont benefit in my experience)
Settings > Gaming > Game Mode > Off
reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AllowAutoGameMode" /t REG_DWORD /d 0 /f
reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AutoGameModeEnabled" /t REG_DWORD /d 0 /f

🟩

nvidiaProfileInspector (as admin) (click magnifying glass for more options):
Texture Filtering - LOD Bias set what you want (Negative LOD bias needs to be set to Allow)
CUDA - Force P2 State off or on (test per-game)

🟩

ReBAR:
Enable above 4g and rebar in your bios (if its supported)
rBAR in nvidiaProfileInspector (as admin):
rBAR Enabled (rebar can cause games to stutter/lag randomly) (test per-game)
rBAR Options set (test per-game)
rBAR Size Limit set (test per-game)

🟩

VRR (FreeSync/G-Sync/AdaptiveSync) could be easier on the eyes and the VRR with LFC (Low Framerate Compensation) could make games feel smoother. Set Off for lowest lantency.
NVIDIA Control Panel:
Set up G-SYNC > Enable settings for the selected display model (turn monitor off and on for windows to figure it out) (or turn off and disable in monitor OSD)
System > Display > Graphics > Default graphics settings:
Variable refresh rate On or off

🟩

Add resolutions 3328x1872 3.25K is mint for people who cant yet push 4k

🟩

set Monitor .icc/icm profile:

put them in here ⊞ Win+R %SystemDrive%Windows/System32/spool/drivers/color

open colorcpl.exe add (sRGB Color Space Profile.icm or sRGB_ICC_v4_Appearance.icc or manufacturer calibration) as default for SDR and check box add advanced color profile .icc for HDR

🟩

HDR how to:

1. download MicrosoftCorporationII.WindowsHDRCalibration_1.0.152.0_neutral_~_8wekyb3d8bbwe.Msixbundle or whatever is latest

2. turn monitor on HDR mode

3. turn on HDR in windows

4. calibrate

🟩

High Precision event timer (HPET) on or off (test i leave it on)

🟩

Enable Message Signaled Interrupts with programs like NVCleanstall 
test MSIs settings like high/irqPolicySpreadMessagesAcrossAllProcessors default 40 series cards drivers enable MSIs on default
Enable manually with registry editor:
Open Device Manager > right click on GPU > Properties > Events (tab) > Device id
&&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&& (looks like this)
replace with your GPU device ID
reg add "HKLM\SYSTEM\CurrentControlSet\Enum\PCI\&&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&&\Device Parameters\Interrupt Management\MessageSignaledInterruptProperties" /v MSISupported /t REG_DWORD /d 1 /f
reboot
```

---
