## Installing and optimizing new nvidia drivers on windows 11 gaming PC:
#### check 🟩 Extra for advanced info [(twitch)](https://twitch.tv/smoothschannel) [(paypal support)](https://www.paypal.com/donate/?business=krtr5pj8dlata&no_recurring=0&item_name=dono&currency_code=usd) [(streamlabs support)](https://streamlabs.com/smoothschannel/tip)
#
* run NVCleanstall.exe
* download driver
* use driver files on disk
* check Legacy Control Panel > Microsoft Visual C 2017 Runtimes > PhysX
* disable installer telemetry & advertising
* perform clean install > disable MPO > disable Ansel
* show expert tweaks > disable HDCP
* build package
#
* Reset/disable GPU overclock/Fans/Auto-startups (Afterburner/ect)
* Disable internet (press ⊞ Win+R ncpa.cpl)
#
* press ⊞ Win+R > type msconfig > boot > safe boot
* reboot
* press ⊞ Win+R > type msconfig > boot > safe boot > uncheck > exit without restarting*
* run Display Driver Uninstaller.exe (DDU) > options > remove physX > uncheck prevent downloads of drivers from "windows update" when "windows" search for a driver for a device (you are offline) > Clean and restart (reboot*)
* install driver click custom (advanced)
#
* open NVIDIA Control Panel
* Adjust image settings with preview > Use my preference emphasizing > Performance > Apply
* Use the advanced 3D image settings > Apply
* Manage 3D settings > Global Settings > Anisotropic filtering > Appplication-controlled or off/4x/8x/16x
* Manage 3D settings > Global Settings > Low Latency Mode > Ultra (test and check 🟩 for more info)
* Manage 3D settings > Global Settings > Power management mode > Prefer maximum performance
* Manage 3D settings > Global Settings > Preferred refresh rate > Highest available
* Manage 3D settings > Global Settings > Shader Cache Size > Unlimited (def is too low for lots of games will cause compile shader lag, stutters and slow compiling)
* Manage 3D settings > Global Settings > Anisotropic sample optimization > On (nul on High quality)          (or leave default)
* Manage 3D settings > Global Settings > Negative LOD bias > Allow (Clamp if not scaling)                    (or leave default)
* Manage 3D settings > Global Settings > Texture filtering Quality > High performance (or High quality)      (or leave default)
* Manage 3D settings > Global Settings > Trilinear optimization > On (nul on High quality)                   (or leave default)
* Configure Surround, PhysX > set PhysX to GPU
* Change resolution > set resolutions and refresh rates (all monitors)
* Change resolution > NVIDIA color settings set Output color depth and Full dynamic range (all monitors)
* Adjust desktop color settings > Digital vibrance 100% (all monitors)
* Adjust video color settings > With the NVIDIA settings > Advanced > Dynamic range Full 0-255 (all monitors)
#
* System > Display > Graphics > Default settings
* Optimizations for windowed games > On
* Advanced graphics settings > Hardware-accelerated GPU scheduling > On
* Custom settings for applications (remove apps or make sure the games are set to high performance)
#
* press ⊞ Win+R type "colorcpl" add and remove correct profiles
* System > Display > Color management > Automatically manage color for apps > off (use your monitor for color or this will destroy colors, check 🟩 for more info)
* turn HDR on and make sure SDR content brightness is on 80 and turn off if not using (HDR adds latency so use for entertainment)
#
* Enable GPU overclock > Set fans higher than defaults > Auto-startups (Afterburner/ect)
* reboot
* Enable internet (press ⊞ Win+R ncpa.cpl)
---
---
## 🟩 Extra
---
---
## 🟩 VRR ect:
* Variable Refresh Rate/FreeSync/G-Sync/AdaptiveSync/ULMB2
#
* your monitor will have an option on turn it on or off
* NVIDIA Control Panel > Set up G-SYNC > Enable settings for the selected display model (checkbox)
#
* loweset latency is this order from written
1. reflex no fps cap
2. ultra low latency mode no fps cap
3. Maximum Pre-Rendered Frames 1 (low latency mode on) no fps cap
4. snycs/all the above with no fps cap or fps cap (gsync range)
5. snycs/all the above with fps cap with LFC(Low Framerate Compensation)
#
* blur busters recommend force on vsync in nvcpl so than when sync goes below or above monitor supported gsync hz it will still only show synced frames (test this may help LFC)
* ULMB2 backlight strobing on some monitors with gsnyc (ULMB1 killed brightness, ULMB2 is just the best IPS tech use it if you have it)
* Only way to tell if VRR is working is in monitor on screen display (OSD) some games might need to be changed to fullscreen and/or boarderless back and forth for VRR to actually work
---
---
## 🟩 nvidia Profile Inspector:
* nvidiaProfileInspector (as admin) (click magnifying glass for more options)
* search for game or edit global or add game and edit
#
* DLSS - Forced Preset Letter (Preset K is for DLSS4 and Preset C is for DLSS3)
#
* "nvngx_dlss.dll" "nvngx_dlssd.dll" "nvngx_dlssg.dll" (can be updated manually from github "NVIDIA/DLSS" and frame gen from "NVIDIAGameWorks/Streamline" or both)
* you can use dev DLSS dll files from github (CTRL+ALT+] changes preset) (CTRL+ALT+Y on/off autoexposure) real time testing
#
* to see what preset you are using type this on/off command in cmd.exe (press ⊞ Win+R cmd)
* on*
* reg add "HKLM\SOFTWARE\NVIDIA Corporation\Global\NGXCore" /v "ShowDlssIndicator" /t REG_DWORD /d 1024 /f
* off*
* reg add "HKLM\SOFTWARE\NVIDIA Corporation\Global\NGXCore" /v "ShowDlssIndicator" /t REG_DWORD /d 0 /f
#
* Texture Filtering - LOD Bias set what you want (Negative LOD bias needs to be set to Allow) (for testing)
* CUDA - Force P2 State off or on (test per-game)
---
---
## 🟩 HWiNFO64:
* set polling period global 2000ms and check only current in show columns (general tab)
* only check validate windows positions/PresentMon Support/Remember Preferences (General/user interface)
* disable everything in Safety tab (main settings)
* Shrink window by removing rightmost table (arrows pointing on bottom of program)
* disable monitoring/logging everything but these (disable everything then add them in Layout tab)
* Framerate (Presented)
* GPU Temperature
* CPU Package (temp)
* GPU Core Load
* Max CPU/Thread Usage (100% on a core could be memory leak)
* GPU Memory Allocated (VRAM)
* Physical Memory Used (RAM)
---
---
## 🟩 Afterburner/RTSS:
* afterburner just needs enable hardware control and monitoring (general tab) for fan enable user defined software automatic fan control (fan tab)
* set fan curve (40% @40c 100% @90c @5000ms) also set your fans in pc case in bios (80% @40c 100% @60c @3000ms-5000ms)
* afterburner needs enable low-level IO driver (general tab) to monitor cpu temps
* hardware polling period 2000ms (monitoring tab)
* for fps to show in rts just check Framerate (monitoring tab)
* start with windows (general tab)
* apply overclocking at system startup (if overclocking)
* rtss needs enable 64-bit applications support service (general tab)
* disable plugins (plugins tab)
* framerate averaging interval 2000ms
---
---
## 🟩 NVIDIA App/FrameView App:
* NVIDIA App (Alt+Z)
* uses ~256mb of vram when open on home screen, 100mb vram in graphics, little more ram few more exes
* requires "nvcontainer.exe" and/or "NVIDIA app.exe" internet telemetry to work, then you can block it (restart app for it to work)
* run Autoruns and uncheck \NVIDIA app SelfUpdate_{}
* run Autoruns and uncheck nvvad_WaveExtensible (nvvad64v.sys,NVIDIA Virtual Audio Device)
#
* FrameView App for overlay (uses modified PresentMon)
* NVIDIA Overlay.exe(s) run at higher priority
* FvSvc (nvfvsdksvc_x64.exe,FrameViewSDK) allows statistics overlay
---
---
## 🟩 frame latency stuff:
* Maximum Pre-Rendered Frames/Low Latency Mode/Future Frame Rendering/Nvidia Reflex
* games without reflex will need low latency mode on ultra to work properly with sync modes (rarely ultra can cause stutter/lag on some API)
* if you are not using syncs/low latency mode ultra/reflex then use -2 fps frame cap of max hz and low latency mode on(Maximum Pre-Rendered Frames 1, or low latency mode off and Maximum Pre-Rendered Frames 1 threw 8 in nvidiaProfileInspector)
---
---
## 🟩 Windows Game Mode:
* test yourself an optimized system wont benefit in my experience
* Settings > Gaming > Game Mode > Off
* reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AllowAutoGameMode" /t REG_DWORD /d 0 /f
* reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AutoGameModeEnabled" /t REG_DWORD /d 0 /f
---
---
## 🟩 FPS cap:
* for VRR (variable refresh rate) or LFC (Low Framerate Compensation) and/or keeping thermals/utilization down
* 1 fps buffer caps are lowest latency use in game fps limiter first then rtss/nvidia ect
* best practice -2fps under refresh rate
* do not use with frame gen
* rtss > fraterate limit -2 under monitor max hz (or lower for stable/and/or LFC)
* rtss > setup > enable framerate limiter > NVIDIA reflex (is ultra low latency if not used with reflex)
---
---
## 🟩 ReBAR:
* Enable rebar in your bios (if its supported)
* rBAR in nvidiaProfileInspector (as admin)
* rBAR Enabled (rebar can cause games to stutter/lag randomly/crash) (test per-game)
* rBAR - Intel CPU Exclusion (idk)
* rBAR Options set (test per-game)
* rBAR Size Limit set (test per-game)
---
---
## 🟩 Custom resolutions:
* Change resolution > Customize... (might have to lower a DP1.4 to DP1.2 and/or turn off DSC(Display Stream Compression) to get the button to work)
* Add resolutions 3328x1872 (3.25K) is mint for people who cant yet push 4k
---
---
## 🟩 Automatically manage color/automatic color management (ACM)
* System > Display > Color management > Automatically manage color for apps > off
* Only used in SDR, ACM reads the EDID and tries to clamp to sRGB if your monitor has a wide gamut
* If your monitor does not have wide gamut or is clamped to sRGB this will only make colors even less accurate (desaturate colors)
* ACM will turn itself back on when changing output color depth in NvCpl (destroying colors as it does)
* Also right click > properties > compatibility > use legacy display ICC colour management > on a programs .exe (bypasses ACM and is SDR only)
---
---
## 🟩 HDR/SDR profiles:
* Monitor .icc/icm profile
* put ICC Profiles in here open ⊞ Win+R %SystemDrive%Windows/System32/spool/drivers/color
* open ⊞ Win+R colorcpl.exe (click add and add ICC profiles, click Add as HDR Profile for hdr icc profiles)
* find manufactures icc profile or search for them or buy a monitor calibration tool (or use phone) (remember calibration is subjective)
#
* Windows HDR Calibration
* download MicrosoftCorporationII.WindowsHDRCalibration_1.0.152.0_neutral_~_8wekyb3d8bbwe.Msixbundle (or newer)
* turn monitor on HDR mode
* turn on HDR in windows
* calibrate
#
* Quick SDR/HDR calibration
* System > Display > Color profile > sRGB to Gamma2.2 (srgb_to_gamma2p2_sdr.icm) (SDR)
* System > Display > Color profile > SDR ACM: srgb_d50 [ srgb_to_gamma2p2.cal ] (srgb_to_gamma2p2_400_mhc2.icm) (HDR)
* find these on github they have a nice gamma roll from zero
---
---
## 🟩 High Precision event timer:
* High Precision event timer (HPET) on or off (test i leave it on) (press ⊞ Win+R devmgmt.msc)
---
---
## 🟩 Message Signaled Interrupts:
* Enable Message Signaled Interrupts with programs like NVCleanstall
* default 40 series cards drivers enable MSIs on default
#
* Enable manually with registry editor
* Open Device Manager > right click on GPU > Properties > Events (tab) > Device id
* &&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&& (looks like this)
* replace with your GPU device ID
* reg add "HKLM\SYSTEM\CurrentControlSet\Enum\PCI\&&&_&&&&&&&&_&&&&&&&&&&&_&&&&&&&&&&&&_&&\&&&&&&&&&&&&&&&&&\Device Parameters\Interrupt Management\MessageSignaledInterruptProperties" /v "MSISupported" /t REG_DWORD /d 1 /f
* reboot
---
---
## 🟩 Adjust desktop size and position (nvcpl):
* No scaling > GPU > check override the mode (test)
* scaling mode test no scaling
* perform scaling on display or gpu (test)
* integer scaling setup (can't use with DSC)
