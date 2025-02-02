### Installing and optimizing new nvidia drivers on windows 11 gaming PC:
#### more to come

---

```python
run NVCleanstall.exe
download driver
use driver files on disk
check Legacy Control Panel, Microsoft Visual C 2017 Runtimes, PhysX
disable installer telemetry & advertising
perform clean install
disable MPO
disable Ansel
show expert tweaks
disable HDCP
build package
```

---

#### Reset/disable GPU overclock/Fans/Auto-startups (Afterburner/ect)
#### Disable internet (⊞ Win+R ncpa.cpl)

---

```python
press ⊞ Win+R > type msconfig > boot > safe boot
reboot
press ⊞ Win+R > type msconfig > boot > safe boot > uncheck > exit without restarting*
run DDU uninstall (as admin) > options > remove physX > Clean and restart
install driver (w/o app,custom)
```

---

```python
NVIDIA Control Panel
Adjust image settings with preview > Use my preference emphasizing > Performance > Apply
Use the advanced 3D image settings > Apply
Manage 3D settings > Global Settings > Anisotropic filtering > Appplication-controlled or off/4x/8x/16x
Manage 3D settings > Global Settings > Low Latency Mode > Off (Ultra can cause lag/stutter on certain API, new API decide this for you usually)
Manage 3D settings > Global Settings > Power management mode > Prefer maximum performance
Manage 3D settings > Global Settings > Preferred refresh rate > Highest available
Manage 3D settings > Global Settings > Shader Cache Size > Unlimited (def is too low for lots of games will cause compile shader lag, stutters and slow compiling)
Manage 3D settings > Global Settings > Anisotropic sample optimization > On (nul on High quality)
Manage 3D settings > Global Settings > Negative LOD bias > Allow (Clamp if not scaling)
Manage 3D settings > Global Settings > Texture filtering Quality set to High performance (or High quality)
Manage 3D settings > Global Settings > Trilinear optimization On (nul on High quality)
Configure Surround, PhysX > set PhysX to GPU
Change resolution > set resolutions and refresh rates (all monitors)
Change resolution > NVIDIA color settings set Output color depth and Full dynamic range (all monitors)
Adjust desktop color settings > Digital vibrance 100% (all monitors)
Adjust video color settings > With the NVIDIA settings > Advanced > Dynamic range Full 0-255 (all monitors)
```

---

```python
System > Display > Graphics > Default graphics settings
Hardware-accelerated GPU scheduling > On
Optimizations for windowed games > On
System > Display > Color management > Automatically manage color for apps > off (24h2 broke color fix)
```

---

#### Enable GPU overclock/Set fans higher than defaults/Auto-startups (Afterburner/ect)

---

#### reboot
#### Disable/Uninstall High Definition Audio Device if you dont need in sound, video and game controllers (⊞ Win+R devmgmt.msc)
#### Block nvdisplay.container.exe
#### Enable internet (⊞ Win+R ncpa.cpl)

---
---
---

#### Extra

```python
🟩

nvidiaProfileInspector (as admin) (click magnifying glass for more options)
edit _GLOBAL_DRIVER_PROFILE (Base Profile) or game name to add RR/DLSS/ect
NVIDIA Predefined Ansel Usage - 0x00000001 ANSEL_ALLOW_DISALLOWED (test)
Enable DLSS-FG override -
Enable DLSS-RR override -
Enable DLSS-SR override - (DLSS4 override DLSS3) (test)
Override DLSSG multi-frame count -
Override DLSS-SR presets - 
Texture Filtering - LOD Bias set what you want (Negative LOD bias needs to be set to Allow) (for testing)
CUDA - Force P2 State off or on (test per-game)

🟩

NVIDIA App (install exe) (Alt+Z) (nvidiaProfileInspector is what i will probably use exclusivly for DLSS4)
uses ~256mb of vram when open on home screen, 100mb vram in graphics, little more ram few more exes
requires "nvcontainer.exe" and/or "NVIDIA app.exe" internet telemetry to work, then you can block it (restart app for it to work)
run Autoruns and uncheck \NVIDIA app SelfUpdate_{}
run Autoruns and uncheck nvvad_WaveExtensible (nvvad64v.sys,NVIDIA Virtual Audio Device)

FrameView App for overlay (install exe) (testing)
NVIDIA Overlay.exe(s) run at higher priority
FvSvc (nvfvsdksvc_x64.exe,FrameViewSDK) allows statistics overlay

Reboots your PC when you go to play a game if you have apps running like "PresentMon_x64.exe/HWiNFO64.exe" and probably others like this

🟩

Maximum Pre-Rendered Frames/Low Latency Mode/Future Frame Rendering/Nvidia Reflex On+Boost(Prefer maximum performance)/AMD Anti-Lag/ULLM

you can change this 1 threw 8 in nvidiaProfileInspector but new stuff like reflex and frame gen play with these (i mean ai)
Old school default was 3, 2 or more could give you more fps at cost of latency
best bet is the use whats in the game and lowest and go up from there if its stuttering/laggy because some settings/modes conflict

🟩

Windows Game Mode (test yourself an optimized system wont benefit in my experience)
Settings > Gaming > Game Mode > Off
reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AllowAutoGameMode" /t REG_DWORD /d 0 /f
reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AutoGameModeEnabled" /t REG_DWORD /d 0 /f

🟩

FPS cap (for keeping under max VRR or using LFC and/or keeping thermals and utilization down) (best practice -2fps under refresh rate) (do not use with frame gen)
NVIDIA Control Panel
Manage 3D settings > Global Settings > Max Frame Rate
Manage 3D settings > Global Settings > Background Application Max Frame Rate

🟩

ReBAR
Enable above 4g and rebar in your bios (if its supported)
rBAR in nvidiaProfileInspector (as admin)
rBAR Enabled (rebar can cause games to stutter/lag randomly) (test per-game)
rBAR Options set (test per-game)
rBAR Size Limit set (test per-game)

🟩

VRR (FreeSync/G-Sync/AdaptiveSync) could be easier on the eyes and the VRR with LFC (Low Framerate Compensation) could make games feel smoother. Set Off for lowest lantency.
Only way to tell if VRR is working is in monitor on screen display (OSD) some games might need to be changed to fullscreen and/or boarderless back and forth for VRR to actually work.

NVIDIA Control Panel
Set up G-SYNC > Enable settings for the selected display model (might need turn monitor on/off) (or turn off and disable in monitor OSD)
System > Display > Graphics > Default graphics settings:
Variable refresh rate On or off

🟩

Custom resolutions
Change resolution > Customize... (might have to lower a DP1.4 to DP1.2 and/or turn off DSC(Display Stream Compression) to get the button to work)
Add resolutions 3328x1872 (3.25K) is mint for people who cant yet push 4k

🟩

Monitor .icc/icm profile
1. put ICC Profiles in here open ⊞ Win+R %SystemDrive%Windows/System32/spool/drivers/color
2. open ⊞ Win+R colorcpl.exe (click add and add ICC profiles, click Add as HDR Profile for hdr icc profiles)
3. find manufactures icc profile or search for them or buy a monitor calibration tool (or use phone) (remember calibration is subjective)

Quick SDR/HDR calibration
1. System > Display > Color profile > sRGB to Gamma2.2 (srgb_to_gamma2p2_sdr.icm) (SDR)
2. System > Display > Color profile > SDR ACM: srgb_d50 [ srgb_to_gamma2p2.cal ] (srgb_to_gamma2p2_400_mhc2.icm) (HDR)
3. find these on github they have a nice gamma roll from zero

Windows HDR Calibration
1. download MicrosoftCorporationII.WindowsHDRCalibration_1.0.152.0_neutral_~_8wekyb3d8bbwe.Msixbundle (or newer)
2. turn monitor on HDR mode
3. turn on HDR in windows
4. calibrate

🟩

High Precision event timer (HPET) on or off (test i leave it on)

🟩

Enable Message Signaled Interrupts with programs like NVCleanstall 
default 40 series cards drivers enable MSIs on default
high/irqPolicySpreadMessagesAcrossAllProcessors (test)

Enable manually with registry editor
Open Device Manager > right click on GPU > Properties > Events (tab) > Device id
&&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&& (looks like this)
replace with your GPU device ID
reg add "HKLM\SYSTEM\CurrentControlSet\Enum\PCI\&&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&&\Device Parameters\Interrupt Management\MessageSignaledInterruptProperties" /v "MSISupported" /t REG_DWORD /d 1 /f
reboot

🟩
```

---
