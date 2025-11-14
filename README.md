## Installing and optimizing new nvidia drivers on windows 11 gaming PC:
#### check 🟩 Extra for advanced info (i cover a lot)
#
* download driver > run NVCleanstall.exe > use driver files on disk
* check Legacy Control Panel > Microsoft Visual C 2017 Runtimes > PhysX
* check disable installer telemetry & advertising > perform clean install > disable Ansel
* check show expert tweaks > disable HDCP
* next > build package
#
* nvidiaProfileInspector delete "settings.xml" press <kbd>⊞ Win+R</kbd> type "%localappdata%\NVIDIA Profile Inspector"
* update nvidiaProfileInspector: [nvidiaProfileInspector](https://github.com/Orbmu2k/nvidiaProfileInspector/releases)
#
* Disable GPU stuff (afterburner ect/auto-startups)
* Disable internet (press <kbd>⊞ Win+R</kbd> type "ncpa.cpl")
#
* press <kbd>⊞ Win+R</kbd> type "msconfig" > boot > safe boot
* reboot*
* press <kbd>⊞ Win+R</kbd> type "msconfig" > boot > safe boot > uncheck > exit without restarting*
* run Display Driver Uninstaller.exe as admin (DDU) > options > check remove physX > uncheck prevent downloads of drivers/save log files/create a restore point/auto check for DDU updates/show offers
* select device type > GPU > Clean and restart (reboots*)
#
* install driver click custom (advanced) and next
#
* open Display settings (right click) set up main display/orientations
#
* open NVIDIA Control Panel (right click)
* in Adjust image settings with preview > check Use my preference emphasizing Performance > Apply
* check Use the advanced 3D image settings > Apply
#
* 3D Settings > Manage 3D settings > Anisotropic filtering > Appplication-controlled (or off/4x/8x/16x)
* 3D Settings > Manage 3D settings > Low Latency Mode > Ultra (check 🟩 for more info)
* 3D Settings > Manage 3D settings > Power management mode > Prefer maximum performance
* 3D Settings > Manage 3D settings > Preferred refresh rate > Highest available
* 3D Settings > Manage 3D settings > Shader Cache Size > Unlimited (def is too low for lots of games will cause compile shader lag, stutters and slow compiling)
* 3D Settings > Manage 3D settings > Anisotropic sample optimization > On (or leave default)
* 3D Settings > Manage 3D settings > Negative LOD bias > Allow (Clamp for 0 LOD bias, 0/+ helps GPU bound, -0 used in dlss ect for image quality)
* 3D Settings > Manage 3D settings > Texture filtering Quality > High performance (or leave default)
* 3D Settings > Manage 3D settings > Trilinear optimization > On (or leave default)
* Apply
* 3D Settings > Configure Surround, PhysX > set PhysX to GPU
* Display > Change resolution > set res and hz (all monitors) > Apply
* Display > Change resolution > check use NVIDIA color settings set BPC (8bpc or 10bpc) and output dynamic range to full (0-255 rgb) (all monitors) > Apply
* Display > Adjust desktop color settings > Digital vibrance 100% (all monitors) > Apply
* Display > Set up G-SYNC > check Enable settings for the selected display model if you are using gsnyc (check 🟩 for more info)
* Video > Adjust video color settings > check With the NVIDIA settings > Advanced > Dynamic range > Full (0-255) (all monitors) > Apply
#
* open Display settings (right click):
* Color profile > Automatically manage color for apps > off (very important) (use your monitor for color or this will destroy colors, ACM will turn itself back on when changing output color depth in NvCpl so dont do that after, check 🟩 for more info)
* Graphics > Auto HDR > Off*
* Graphics > Optimizations for windowed games > On
* Graphics > Advanced graphics settings > Hardware-accelerated GPU scheduling (HAGS) (Required* for framegen) > On
* Graphics > Custom settings for applications (remove apps or make sure the games are set to high performance)
#
* press <kbd>⊞ Win+R</kbd> type "colorcpl" add/remove color profiles (click add... and add profiles, check Add as HDR Profile for hdr ones)
* open Display settings > turn HDR on* and set SDR content brightness then turn off if not using (check 🟩 for more info)
#
* reboot
* Enable GPU stuff (afterburner ect/auto-startups)
* Enable internet (press <kbd>⊞ Win+R</kbd> type ncpa.cpl)
* reboot (again)
---
---
---
## 🟩 Extra (ADVANCED)
---
---
---
## 🟩 Advanced github i made and use:
* [Registry Tweaks Refresh](https://github.com/smo0ths/Registry-Tweaks-Refresh.bat)
* [My Network Adaptor Settings](https://github.com/smo0ths/My-Network-Adaptor-Settings)
* [FIREWALL lock down but functional ruleset](https://github.com/smo0ths/FIREWALL-lock-down-but-functional-ruleset)
---
---
---
## 🟩 VRR ect:
* Variable Refresh Rate/FreeSync/G-Sync/AdaptiveSync/vsync/ULMB2/DyAc
#
* your monitor will have an option to turn it on or off
* Only way to tell if VRR is working is in monitor on screen display (OSD)
* Monitor's Over Drive setting can't be higher than normal usually or it will cause inverse ghosting with VRR on
* G‑Sync for windowed and full screen mode (can cause rare desktop stutter issues so dont use)
#
* loweset latency is this order from written
* 1 → reflex no fps cap (with high fps)
* 2 → ultra low latency mode no fps cap
* 3 → all the above with fps cap (stable frame times)
* 4 → Maximum Pre-Rendered Frames 1 (low latency mode on) no fps cap
* 4a → Maximum Pre-Rendered Frames 1 (low latency mode on) with fps cap (stable frame times)
* 4b → snycs/all the above with or w/o fps cap (gsync range) (recommended for most games and use 1 → for competitive)
* 5 → snycs/all the above with fps cap for LFC(Low Framerate Compensation)
#
* gsnyc helps if a games fps is unstable and fluctuates around 70-130 fps because 130 fps as the lowest fluctiation would be harder to notice
* latency is: Input → Game logic → GPU → Display → Your eyes
* blur busters recommend force on vsync in nvcpl so when sync goes below or above monitor supported gsync hz it will still only show synced frames (test this may help LFC)
* ULMB2 backlight strobing on some monitors with gsnyc (ULMB1 killed brightness, ULMB2 is just the best IPS tech use it if you have it)
* DyAc(1/2) fastest TN panel stuff
#
* find stable frame times:
* find your lowest fluctuation fps(or 1% lows) during high intensity multiplayer or heavy rpg game ect and set fps cap there or just rely on gsnyc
* dont go lower than 130 fps cap with framegens or you will start to notice it (some might be fine with that)
---
---
---
## 🟩 nvidia Profile Inspector:
* nvidiaProfileInspector (as admin) (click magnifying glass for more options)
* search for game or edit global or add game and edit
#
* what i use in _GLOBAL_DRIVER_PROFILE (Base Profile)
* DLSS > Forced Preset Letter > set Preset K (Transformer) or Preset E (CNN) (recommended K)
* DLSS-RR > Forced Preset Letter > set Preset J (Transformer) or Preset E (CNN) (recommended J)
* Apply changes
#
* update your DLSS files manualy from [streamline-sdk-v#.#.#\bin\x64](https://github.com/NVIDIA-RTX/Streamline/releases) (devs dont do it and idk what nvidia is doing)
* you can use dev DLSS dll files from github (CTRL+ALT+] changes preset) (CTRL+ALT+Y on/off autoexposure) real time testing
#
* to see what preset you are using type this on/off command in cmd.exe (press <kbd>⊞ Win+R</kbd> type "cmd")
* on*
* reg add "HKLM\SOFTWARE\NVIDIA Corporation\Global\NGXCore" /v "ShowDlssIndicator" /t REG_DWORD /d 1024 /f
* off*
* reg add "HKLM\SOFTWARE\NVIDIA Corporation\Global\NGXCore" /v "ShowDlssIndicator" /t REG_DWORD /d 0 /f
#
* Texture Filtering - LOD Bias set what you want (Negative LOD bias needs to be set to Allow) (for testing)
* CUDA - Force P2 State off or on (test per-game)
* Smooth Motion - Enable off/on (test if you cant use FG or OptiScaler*)
---
---
---
## 🟩 Proper HDR calibration info:
* install Windows HDR Calibration app, turn monitor in HDR mode, enable HDR in windows
* Minimum luminance: ~0 nits OLED, ~0.001/0.02 nits MiniLED set to 0 (HDR10 cant encode literal zero)
* Maximum luminance (MaxCLL): find yours on RTINGS or somewhere on the internet
* Maximum full frame luminance (MaxFALL): find yours on RTINGS or somewhere on the internet
* color saturation: set to 0
#
* MaxCLL = brightest pixel (single brightest pixel in the entire content in nits) 
* MaxFALL = brightest average frame (brightest average frame in the entire content in nits)
* MaxCLL/MaxFALL dont change the panels physical brightness, they guide tone mapping
* Incorrectly low values = conservative metadata → flatter bright scenes, earlier highlight clipping (not good)
#
* Paper white (reference UI/mid‑tone brightness): ~400 nits default; ~200–250 nits in bright rooms, ~100–150 nits in dark rooms usually recommended
* Paper white = a creative/mastering choice for HDR mid‑tones
#
* On Windows, the "SDR content brightness slider" controls how "SDR white maps into HDR mode" its relative to your displays peak brightness, not a fixed nit value*
* SDR white mapping = a Windows system setting that decides how legacy SDR content is displayed inside HDR mode
* This setting doesnt change MaxCLL/MaxFALL (content metadata), but it affects how comfortable SDR looks alongside HDR highlights
* Reference HDR1000 → ~75/80% for ~400/600 nits → 100% for ~700/800 nits (SDR white mapping)
* Reference HDR1700/2000 → ~50/75% for ~400/600 nits → ~75/80% for ~600/800 nits → 100% for ~1000/1200 nits (SDR white mapping)
#
* movies/shows: MaxCLL/MaxFALL = static metadata values from mastering data (conservative, fixed for entire title)
* games: HDR tone mapping is variable/dynamic, not bound to static MaxCLL/MaxFALL the values can shift in real time
* games can override max nits
* higher UI values can fix tonemapping in complex UI elements like maps in games (450+ nits values)
* HDR is about contrast and color space
#
* HDR adds a little latency
* use Video > Adjust video image settings > RTX video enhancement > super resolution/high dynamic range to enhance content
* put ICC Profiles in here press <kbd>⊞ Win+R</kbd> type %SystemDrive%Windows/System32/spool/drivers/color
* find manufactures icc profile they are for SDR or just use windows default
* search for sRGB to Gamma 2.2 to test aswell it actually does something to SDR
* cables, make sure you have proper cables
* ABL (Automatic Brightness Limiter) is a thing
---
---
---
## 🟩 audio:
* set to 32 bit (avoids truncation/dither/conversion step) 24khz is fine, and 48kHz or match kHz of the content you are listening to
* bits is dynamic range to noise floor and sample rate is time points of a wave signal (Bits = vertical resolution, Sample rate = horizontal resolution)
* Exclusive Mode: always use exclusive mode on DAC/AMP/SOUNDCARD (unless you have problems with capture cards or something)
* Exclusive Mode: Uncheck on microphone multitasking (OBS/Discord/games/etc) unless you are studio recording and need less latency ect.
* Exclusive Mode: again check for audiophile music listening or studio recording (bit‑perfect/lowest latency)
* Exclusive Mode: think of it as switching modes: streaming mode (shared) vs listening mode (exclusive)
* keep all audio windows/games at 100% until the last stage (DAC/AMP/soundcard software) for audiophile/bit perfect sound
* audio path: Audio decoding → Resampling (Windows) → DAC (Hardware) → Your ears
* virtual surround sound can make games/movies/shows sound good but it almost always makes voices and music sound worse
* stereo is what you want to use unless your system and the content supports real surround sound
#
* EQ audio(10band):
* (31Hz/62Hz/125Hz/250Hz/500Hz/1kHz/2kHz/4kHz/8kHz/16kHz) (0/-1/-1/+1/-1/+1/0/+1/-1/-1) for clean listening higher or lower volumes
* (31Hz/62Hz/125Hz/250Hz/500Hz/1kHz/2kHz/4kHz/8kHz/16kHz) (0/0/+1/0/-1/+1/0/0/+1/+1) i usually use this lower/medium volumes
* for more bass/treble raise 62Hz/4kHz might need to raise higher freqs when you do for brightness
#
* EQ voice: set your format to 1 channel* and 24bit/48kHz 
* everyone has a different sound freq and women might need a bit different eq
* use Equalizer APO or something (Equalizer APO needs Signal Enhancements(enable audio enhancements) to function)
* best universal from flat response eq: (i use VSTPlugins\ReaPlugs\reaeq-standalone.dll)
* 1(change to Band)  125.0/ 2.5/0.70 (Hz/dB/oct)
* 2(band)            500.0/-2.5/0.70 (Hz/dB/oct)
* 3(band)           3000.0/ 1.0/0.70 (Hz/dB/oct)
* 4(change to Band) 7000.0/ 3.5/0.70 (Hz/dB/oct)
#
* RNNoise for noise cancellation settings: vad threshold 0.95 / grace period 50 / retroactive 0 (this can remove whispering/whisling and adds a little latency)
* press <kbd>⊞ Win+R</kbd> type "mmsys.cpl" disable* Signal Enhancements (bass boost/virtual surround/room correction/loudness equalization/speaker fill/noise suppression/echo cancellation/automatic gain control/ect)
* disable all other audio devices  press <kbd>⊞ Win+R</kbd> type "mmsys.cpl"
---
---
---
## 🟩 HWiNFO64:
* sensors-only
* set polling period global 2000ms and check only current in show columns (general tab)
* only check validate windows positions/PresentMon Support/Remember Preferences (General/user interface)
* disable everything in Safety tab (main settings)
* Shrink window by removing rightmost table (arrows pointing on bottom of program)
* disable monitoring/logging everything but these (disable everything then add them in Layout tab)
* Framerate (Presented) (uncheck PresentMon Support and disable this when not in use, anticheats don't like it either)
* GPU Temperature
* CPU Package (temp)
* D3D(3D) utilization(GPU 3D rendering pipeline) more important for gaming performance information
* GPU Core Load(general workloads/activity/busy) not just 3D rendering but other rendering/streaming/accelerated tasks/compute/decoding/encoding/simulations/AI/machine learning etc.
* Max CPU/Thread Usage (100% on a core could be memory leak)
* GPU Memory Allocated (VRAM)
* Physical Memory Used (RAM)
---
---
---
## 🟩 Afterburner/RTSS:
* afterburner just needs enable hardware control and monitoring (general tab) for fan enable user defined software automatic fan control (fan tab)
* set fan curve (40% @30c 100% @70c/80c/90c if noisy) also set your fans in pc case in bios (80% @40c 100% @60c or just run them max unless they are <1400rpm and loud)
* for modern GPU's turning down power limit to 80/90% can lower heat/power output and not lose much fps
* afterburner needs enable low-level IO driver (general tab) to monitor cpu temps
* hardware polling period 2000ms (monitoring tab)
* for fps to show in rts click show OSD/show own statistics for Afterburner check Framerate/show OSD (monitoring tab)
* start with windows (general tab)
* apply overclocking at system startup (if overclocking)
* rtss needs enable 64-bit applications support service (general tab)
* disable plugins (plugins tab)
* framerate averaging interval 2000ms
#
* afterburner general uncheck synchronize settings for similar graphics processors
* afterburner profiles > profile contents > check both boxes
#
* general > uncheck/check rtss Inject NVIDIA Reflex latency markers
* can measure end-to-end latency more accurately
* you can break down where latency is introduced (CPU, GPU, or display)
* markers only appear if the game itself supports Reflex and exposes those hooks
---
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
#
* you can also just install FrameView App by itself its lightweight
---
---
---
## 🟩 frame latency stuff:
* Maximum Pre-Rendered Frames/Low Latency Mode/Future Frame Rendering/Nvidia Reflex
* your goal should be to have no more than 9ms latency in your frame times
* games without reflex will need low latency mode on ultra to work properly with sync modes (rarely ultra can cause stutter/lag on some API)
* if you are not using syncs/low latency mode ultra/reflex then use -2 fps frame cap of max hz and low latency mode on(Maximum Pre-Rendered Frames 1, or low latency mode off and Maximum Pre-Rendered Frames 1 threw 8 in nvidiaProfileInspector)
---
---
---
## 🟩 mouse/keyboard:
* dpi should be 1000/1300 for lowest latency (1000 recommended)
* hz should be 1000 or 2000hz (higher will raise cpu % usage and 8000hz should be fine for a keyboard all you need for these is USB 2.0)
* sensitivity, i like 1:1 6in 1080° turn for freelook/reflex sights and 9in 90° for anything 4x+ scopes (for 3rd person RPG games 4in 1080° for freelook)
* keep your sensitivity the same so you dont suck, find that perfect 1:1 sens for competitive i used to use 7in 1080° turn
#
* best rapid trigger settings all keys (0.6 actuation is pretty much a mouse click)
* actuation point(0.6) continuous rapid trigger(0.2 sensitivity) 1000hz/8000hz (competitive games faster)
* actuation point(0.6) traditional rapid trigger(0.6 sensitivity) 1000hz/8000hz (momentum/physics heavier movement games faster)
* actuation point(0.8) continuous rapid trigger(0.2 sensitivity) 1000hz/8000hz (competitive games fast)
* actuation point(0.8) traditional rapid trigger(0.8 sensitivity) 1000hz/8000hz (momentum/physics heavier movement games fast)
---
---
---
## 🟩 MPO Multi-Plane Overlay:
* on can help cpu bound ect, off can fix display problems ect, can you even disable it? idk
* test press <kbd>⊞ Win+R</kbd> type "dxdiag" save all information... and search for "MPO MaxPlanes"
* MPO on*
* reg delete "HKLM\SOFTWARE\Microsoft\Windows\Dwm" /v "OverlayTestMode" /f
* MPO off*
* reg add "HKLM\SOFTWARE\Microsoft\Windows\Dwm" /v "OverlayTestMode" /t REG_DWORD /d 5 /f
---
---
---
## 🟩 UUP dump:
* something to look into if you are making windows iso
* [UUP dump](https://uupdump.net/)
---
---
---
## 🟩 Microsoft Program Install Uninstall Tool:
* if things wont uninstall use this
* [Download troubleshooter](https://support.microsoft.com/en-us/topic/fix-problems-that-block-programs-from-being-installed-or-removed-cca7d1b6-65a9-3d98-426b-e9f927e1eb4d)
---
---
---
## 🟩 Windows Game Mode:
* Settings > Gaming > Game Mode > On/Off
* reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AllowAutoGameMode" /t REG_DWORD /d 1 /f
* reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AutoGameModeEnabled" /t REG_DWORD /d 1 /f
---
---
---
## 🟩 my Cleanup Windows 11 PowerShell Script:
* [Cleanup Windows 11 PowerShell Script](https://github.com/smo0ths/Cleanup-Windows-11-PowerShell-Script)
---
---
---
## 🟩 after updating windows cleanup:
* Use /ResetBase only if you're sure you won’t need to uninstall updates and want to reclaim maximum space
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "Dism.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase"
* or
* Use /StartComponentCleanup for regular maintenance
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "Dism.exe /online /Cleanup-Image /StartComponentCleanup"
---
---
---
## 🟩 you think your windows is currupt:
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "sfc /scannow"
* then
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "DISM /Online /Cleanup-Image /RestoreHealth"
---
---
---
## 🟩 FPS cap:
* for VRR (variable refresh rate) or LFC (Low Framerate Compensation) and/or keeping thermals/utilization down
* framerate limiter types async/front edge sync/back edge sync/nvidia reflex/nvidia/game engines
* 1 fps buffer caps are lowest latency (some limiters are actually 2/3 frame buffers like nvidia's non reflex one)
* best practice -2fps under refresh rate
* AI frame gens can be capped (reflex limiter or others) to lower utilizations, smooth motion seems to like no cap (maybe fixed in newer driver)
* rtss > fraterate limit -2 under monitor max hz (or lower for stable/and/or LFC)
* rtss > setup > enable framerate limiter > NVIDIA reflex (is ultra low latency if not used with reflex i think)
---
---
---
## 🟩 ReBAR:
* Enable rebar in your bios (or don't to avoid problems)
* rBAR in nvidiaProfileInspector:
* rBAR - Enable > Enabled (rebar can cause games to stutter/lag randomly/crash and run slow so test per-game)
---
---
---
## 🟩 check nvidia driver security fixes:
* [Security Bulletins](https://www.nvidia.com/en-us/security/)
---
---
---
## 🟩 Custom resolutions:
* Change resolution > Customize... (might have to lower a DP1.4 to DP1.2 and/or turn off DSC(Display Stream Compression) to get the button to work)
* Add resolutions 3328x1872 (3.25K) is mint for people who cant yet push 4k
---
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
---
## 🟩 monitors:
* ideal distance your eyes should be for 4k 27inch monitor (min 16.8inch/max 20.4inch) and pointing at 33.3% below the top of your monitor flat
* only ever use your monitor to change sharpness disable it everywhere else (unless its dlss then default is prob intentional for PQ without monitor sharpness or any PQ accurate filter in game engines who knows)
* make sure max brightness is on, anything that dims your screen is set off, OLED users research what your settings do, then adjust brightness
* OLED = perfect blacks, but brightness + burn‑in concerns.
* Mini‑LED = brightness champ, but local dimming zones matter.
* Micro‑LED = the dream tech that does it all (someday).
---
---
---
## 🟩 OBS:
* settings > stream > ignore stream serv setting recommendations
* output > rescale output disabled > constant bitrate > 6000/7500kbps > keyframe 2s > P5 > HQ > uncheck both > 2 b-frames
* output > audio > 256kbps or 320kbps
* audio > 48kHz
* video > output 1664x936 > 60fps
* advanced > sRGB > limited > enable browser source hardware acceleration (check if GPU is better uncheck if CPU is better or test it)
#
* 🔴 Re-add your browser(browser sources) after updates and often to fix old rendering bugs/memory leaks/Trigger optimized versions of embedded web content/reset any lingering settings or permissions that raise 3D gpu usage and lower performance
* paste browser(browser sources) as reference in other scenes
* set game capture RGB10A2 Color Space set to Rec. 2100 (PQ) when you are playing in HDR so your stream can see the game tone‑mapped to SDR (remember* to turn it back to sRGB* when playing in SDR)
* set your display captures for desktop checkbox to Force SDR for if you are ever in HDR for viewers
* turn off Docks > Audio Mixer because it cost you 2fps in every game
* -5dB on obs desktop audio can help keep your sound balanced
* two pass (quarter res) can help quality a little if you want to test
#
* clear/delete obs cookies and cache:
* %AppData%\obs-studio\plugin_config\obs-browser\obs_profile_cookies
* %AppData%\obs-studio\plugin_config\obs-browser\Cache
---
---
---
## 🟩 Interrupt Affinity Policy Tool and Msi Utility v3:
* these are tools to see Interrupt Affinity and interrupt priority and they edit the registry so there's a manual way
* all i know is drives set interrupt priority to high and advanced policies to IrqPolicySpreadMessagesAcrossAllProcessors and internet adaptors/pci/usb host controllers are defaulted
* only tweak i can see helping latency is interrupt priorites to high for a sound card on one host controller or maybe anything, as long as you dont have too much on high interrupt prioirity
* if there is data on any actual differences let me know
---
---
---
## 🟩 page files ect:
* check automatically manage paging file size for all drives (Helps prevent bottlenecks)
* Multiple page files are processed parallelly to split IO operations, which noticeably increases the performance.
* click on all drives and uncheck in general compress/allow files to have contents indexed
* use [MonitorIO](https://github.com/smo0ths/MonitorIO) i made if you want to see IO in realtime
---
---
---
## 🟩 random windows stuff:
* delete random credentials (virtualapp/didlogical is for windows sign in stuff dont remove it)
* press <kbd>⊞ Win+R</kbd> type "control.exe keymgr.dll"
* add/remove accounts
* press <kbd>⊞ Win+R</kbd> type "ms-settings:emailandaccounts"
---
---
---
## 🟩 power stuff:
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61" unlocks ultimate Performance
* press <kbd>⊞ Win+R</kbd> type "powercfg.cpl" > check ultimate Performance
* i also do
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "powercfg -setacvalueindex SCHEME_CURRENT SUB_VIDEO VIDEOIDLE 0" default 15 minutes
* press <kbd>⊞ Win+R</kbd> type "control.exe powercfg.cpl,,3" > desktop background settings > slide show > setting: paused
* press <kbd>⊞ Win+R</kbd> type "control.exe powercfg.cpl,,3" > usb settings > usb selective suspend setting > setting: disabled
#
* debug or start over press <kbd>⊞ Win+R</kbd> type "powercfg -restoredefaultschemes"
---
---
---
## 🟩 device manager:
* disable/fix stuff
* press <kbd>⊞ Win+R</kbd> type "devmgmt.msc"
---
---
---
## 🟩 task scheduler:
* disable things you dont want
* press <kbd>⊞ Win+R</kbd> type "taskschd.msc"
---
---
---
## 🟩 windows performance options:
* press <kbd>⊞ Win+R</kbd> type "SystemPropertiesPerformance"
* click custom check only show window contents while dragging and smooth edges of screen fonts (or do whatever)
---
---
---
## 🟩 Windows Features (optionalfeatures):
* press <kbd>⊞ Win+R</kbd> type "optionalfeatures" (in appwiz.cpl)
* only things needed for gaming pc is
* .NET Framework 3.5 (includes .NET 2.0 and 3.0) (no sub checkboxes needed)
* .NET Framework 4.8 Advanced Services (no sub checkboxes needed)
* Also press <kbd>⊞ Win+R</kbd> type "ms-settings:optionalfeatures" (in SystemSettings.exe)
* click view features and remove stuff you dont use
---
---
---
## 🟩 game deals:
* buy from offical main launchers
* use [gg.deals/deals](https://gg.deals/deals/?platform=1&sort=date&store=4,5,6,22,38,57,1169&tag=-117,-79,-25&type=1,2)
---
---
---
## 🟩 High Precision event timer/Time Stamp Counter:
* HPET should be off, press <kbd>⊞ Win+R</kbd> type "cmd" then type "bcdedit /enum" useplatformclock should not be there win11 uses invariant TSC type "bcdedit /deletevalue useplatformclock" to delete
---
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
---
## 🟩 bios:
* update your bios
* install m.2 drivers
* overclock: Prime95 (p95v3019b20.win64 or >) Small FFTs(default) Self-test 48K passed! (takes few minutes/clocks should not fluctuate/check Core Thermal Throttling) is the unrealistic* stable standard imo
* make sure drives/pci devices are not sharing lanes (causes instability) check your bios manual(RTFM)
* you can unplug and hold down power button for 15 to 30 seconds to discharge residual electricity
#
* Enable Above 4G memory/Crypto Currency mining/MMIO BIOS assignment (if you have more than 4gb of vram)
* Above Above 4G memory/Crypto Currency mining/MMIO BIOS assignment lets the system map all of your GPUs VRAM/PCIe resources above the 4GB address limit, preventing conflicts and ensuring full stability/compatibility
#
* set rebar off in bios to avoid a potential mess
* ReBAR needs CSM off/UEFI on/Above 4G memory/Crypto Currency mining/MMIO BIOS assignment
---
---
---
## 🟩 delete stuff not using or is security vulnerability:
* don't delete things that microsoft regularly updates that may have Common Vulnerabilities and Exposures (CVE)
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "%windir%\system32\drivers"
* get list: 
* press <kbd>⊞ Win+R</kbd> type "cmd" then type "dir C:\Windows\System32\drivers\*.sys /b"
---
---
---
## 🟩 Adjust desktop size and position (nvcpl):
* perform scaling on display or gpu (test) (or leave default)
* integer scaling setup (can't use with DSC)
