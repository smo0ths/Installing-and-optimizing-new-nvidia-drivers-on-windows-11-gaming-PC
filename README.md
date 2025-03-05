### Installing and optimizing new nvidia drivers on windows 11 gaming PC:
#### check 🟩 Extra after you install for advanced info

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
#### Disable internet (press ⊞ Win+R ncpa.cpl)
#### turn off any program running on gpu (if you want)
#### unplug all but main monitor (if you want)

---

```python
press ⊞ Win+R > type msconfig > boot > safe boot
reboot
press ⊞ Win+R > type msconfig > boot > safe boot > uncheck > exit without restarting*
run Display Driver Uninstaller.exe (DDU) > options > remove physX > Clean and restart (reboot*)
install driver click custom (advanced)
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
Manage 3D settings > Global Settings > Anisotropic sample optimization > On (nul on High quality)          (or leave default)
Manage 3D settings > Global Settings > Negative LOD bias > Allow (Clamp if not scaling)                    (or leave default)
Manage 3D settings > Global Settings > Texture filtering Quality > High performance (or High quality)      (or leave default)
Manage 3D settings > Global Settings > Trilinear optimization > On (nul on High quality)                   (or leave default)
Configure Surround, PhysX > set PhysX to GPU
plug in other monitors (Rotate display/Set up G-SYNC(checkbox)/Set up multiple displays if needed)
Change resolution > set resolutions and refresh rates (all monitors)
Change resolution > NVIDIA color settings set Output color depth and Full dynamic range (all monitors)
Adjust desktop color settings > Digital vibrance 100% (all monitors)
Adjust video color settings > With the NVIDIA settings > Advanced > Dynamic range Full 0-255 (all monitors)
```

---

```python
press ⊞ Win+R type "colorcpl" add and remove correct profiles

System > Display > Graphics > Default settings
Optimizations for windowed games > On
Advanced graphics settings > Hardware-accelerated GPU scheduling > On
Advanced graphics settings > Variable refresh rate > On (if using)
Custom settings for applications (remove apps or make sure the games are set to high performance)

System > Display > Color management > Automatically manage color for apps > off (24h2 broke color fix)

turn HDR on and make sure SDR content brightness is on 80 and turn off if not using
```

---

#### Enable GPU overclock/Set fans higher than defaults/Auto-startups (Afterburner/ect)

---

#### reboot
#### Disable/Uninstall High Definition Audio Device if you dont need in sound, video and game controllers (press ⊞ Win+R devmgmt.msc)
#### Block nvdisplay.container.exe and nvngx_update.exe
#### Enable internet (press ⊞ Win+R ncpa.cpl)

---
---
---

#### 🟩 Extra

```python

🟩 nvidia Profile Inspector:

nvidiaProfileInspector (as admin) (click magnifying glass for more options)
edit _GLOBAL_DRIVER_PROFILE (Base Profile) or games name to add/edit settings (create profile)
Enable DLSS-FG override (does nothing, you do it manually, nvngx_dlssg.dll) (Enhanced FG/lower vram usage and better)
Enable DLSS-RR override (does nothing, you do it manually, nvngx_dlssd.dll) (Ray Reconstruction/test fps/quality difference)
Enable DLSS-SR override (does nothing, you do it manually, nvngx_dlss.dll) (DLSS-SR/DLSS/12345679)
Override DLSSG multi-frame count (50 series)
Override DLSS-SR presets (set to 0x0000000B is "Preset K" its the transformer model preset) (0x0000000A is "Preset J" an older version)

"nvngx_dlss.dll" "nvngx_dlssd.dll" "nvngx_dlssg.dll" (can be updated manually from github "NVIDIA/DLSS" and frame gen from "NVIDIAGameWorks/Streamline" or both)
you can use dev DLSS dll files from github (CTRL+ALT+] changes preset) (CTRL+ALT+Y on/off autoexposure) real time testing

to see what preset you are using type this on/off command in cmd.exe (press ⊞ Win+R cmd)
on*
reg add "HKLM\SOFTWARE\NVIDIA Corporation\Global\NGXCore" /v "ShowDlssIndicator" /t REG_DWORD /d 1024 /f
off*
reg add "HKLM\SOFTWARE\NVIDIA Corporation\Global\NGXCore" /v "ShowDlssIndicator" /t REG_DWORD /d 0 /f

in my test DLSS transformers model cost 5 fps lower but looks better at perfromance quality(1080p) to 4k(2160p) and other, can cause weird aa stuff just like any scaler

Texture Filtering - LOD Bias set what you want (Negative LOD bias needs to be set to Allow) (for testing)
CUDA - Force P2 State off or on (test per-game)

-------------------------------------------------------------

🟩 HWiNFO64:

set polling period global 2000ms and check only current in show columns (general tab)
only check validate windows positions/PresentMon Support/Remember Preferences (General/user interface)
disable everything in Safety tab (main settings)
Shrink window by removing rightmost table (arrows pointing on bottom of program)
disable monitoring/logging everything but these (disable everything then add them in Layout tab)
Framerate (Presented)
GPU Temperature
CPU Package (temp)
GPU Core Load
Max CPU/Thread Usage (100% on a core could be memory leak)
GPU Memory Allocated (VRAM)
Physical Memory Used (RAM)

-------------------------------------------------------------

🟩 Afterburner/RTSS:

afterburner just needs enable hardware control and monitoring (general tab) for fan enable user defined software automatic fan control (fan tab)
set fan curve (40% @40c 100% @90c @5000ms) also set your fans in pc case in bios (80% @40c 100% @60c @3000ms-5000ms)
afterburner needs enable low-level IO driver (general tab) to monitor cpu temps
hardware polling period 2000ms (monitoring tab)
for fps to show in rts just check Framerate (monitoring tab)
start with windows (general tab)
apply overclocking at system startup (if overclocking)

rtss needs enable 64-bit applications support service (general tab)
disable plugins (plugins tab)
framerate averaging interval 2000ms

-------------------------------------------------------------

🟩 NVIDIA App/FrameView App:

NVIDIA App (install exe) (Alt+Z) (nvidiaProfileInspector is better)
uses ~256mb of vram when open on home screen, 100mb vram in graphics, little more ram few more exes
requires "nvcontainer.exe" and/or "NVIDIA app.exe" internet telemetry to work, then you can block it (restart app for it to work)
run Autoruns and uncheck \NVIDIA app SelfUpdate_{}
run Autoruns and uncheck nvvad_WaveExtensible (nvvad64v.sys,NVIDIA Virtual Audio Device)

FrameView App for overlay (install exe) (uses modified PresentMon)
NVIDIA Overlay.exe(s) run at higher priority
FvSvc (nvfvsdksvc_x64.exe,FrameViewSDK) allows statistics overlay

-------------------------------------------------------------

🟩 frame latency stuff:

Maximum Pre-Rendered Frames/Low Latency Mode/Future Frame Rendering/Nvidia Reflex On+Boost(Prefer maximum performance)/AMD Anti-Lag/ULLM
you can change this 1 threw 8 in nvidiaProfileInspector
Old school default was 3, 2 or more could give you more fps at cost of latency
best bet is the use whats in the game and lowest and go up from there if its stuttering/laggy because some settings/modes conflict

-------------------------------------------------------------

🟩 Windows Game Mode:

test yourself an optimized system wont benefit in my experience
Settings > Gaming > Game Mode > Off
reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AllowAutoGameMode" /t REG_DWORD /d 0 /f
reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AutoGameModeEnabled" /t REG_DWORD /d 0 /f

-------------------------------------------------------------

🟩 FPS cap:

for keeping under max VRR or using LFC and/or keeping thermals and utilization down
best practice -2fps under refresh rate
do not use with frame gen
NVIDIA Control Panel
Manage 3D settings > Global Settings > Max Frame Rate
Manage 3D settings > Global Settings > Background Application Max Frame Rate

-------------------------------------------------------------

🟩 ReBAR:

Enable above 4g and rebar in your bios (if its supported)
rBAR in nvidiaProfileInspector (as admin)
rBAR Enabled (rebar can cause games to stutter/lag randomly/crash) (test per-game)
rBAR Options set (test per-game)
rBAR Size Limit set (test per-game)

-------------------------------------------------------------

🟩 VRR:

FreeSync/G-Sync/AdaptiveSync
could be easier on the eyes and the VRR with LFC (Low Framerate Compensation) could make games feel smoother
Set Off for lowest latency
Only way to tell if VRR is working is in monitor on screen display (OSD) some games might need to be changed to fullscreen and/or boarderless back and forth for VRR to actually work
NVIDIA Control Panel
Set up G-SYNC > Enable settings for the selected display model (might need turn monitor on/off) (or turn off and disable in monitor OSD)
System > Display > Graphics > Default graphics settings:
Variable refresh rate On or off

-------------------------------------------------------------

🟩 Custom resolutions:

Change resolution > Customize... (might have to lower a DP1.4 to DP1.2 and/or turn off DSC(Display Stream Compression) to get the button to work)
Add resolutions 3328x1872 (3.25K) is mint for people who cant yet push 4k

-------------------------------------------------------------

🟩 HDR/SDR profiles:

Monitor .icc/icm profile
1. put ICC Profiles in here open ⊞ Win+R %SystemDrive%Windows/System32/spool/drivers/color
2. open ⊞ Win+R colorcpl.exe (click add and add ICC profiles, click Add as HDR Profile for hdr icc profiles)
3. find manufactures icc profile or search for them or buy a monitor calibration tool (or use phone) (remember calibration is subjective)

Windows HDR Calibration
1. download MicrosoftCorporationII.WindowsHDRCalibration_1.0.152.0_neutral_~_8wekyb3d8bbwe.Msixbundle (or newer)
2. turn monitor on HDR mode
3. turn on HDR in windows
4. calibrate

Quick SDR/HDR calibration
1. System > Display > Color profile > sRGB to Gamma2.2 (srgb_to_gamma2p2_sdr.icm) (SDR)
2. System > Display > Color profile > SDR ACM: srgb_d50 [ srgb_to_gamma2p2.cal ] (srgb_to_gamma2p2_400_mhc2.icm) (HDR)
3. find these on github they have a nice gamma roll from zero

-------------------------------------------------------------

🟩 High Precision event timer:

High Precision event timer (HPET) on or off (test i leave it on) (press ⊞ Win+R devmgmt.msc)

-------------------------------------------------------------

🟩 Message Signaled Interrupts:

Enable Message Signaled Interrupts with programs like NVCleanstall
default 40 series cards drivers enable MSIs on default

Enable manually with registry editor
Open Device Manager > right click on GPU > Properties > Events (tab) > Device id
&&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&& (looks like this)
replace with your GPU device ID
reg add "HKLM\SYSTEM\CurrentControlSet\Enum\PCI\&&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&&\Device Parameters\Interrupt Management\MessageSignaledInterruptProperties" /v "MSISupported" /t REG_DWORD /d 1 /f
reboot
```

---
