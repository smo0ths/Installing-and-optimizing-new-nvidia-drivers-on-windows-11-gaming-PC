## Installing and optimizing new nvidia drivers on windows 11 gaming PC:
#### check 🟩 Extra for advanced info (i cover a lot)
#
* download driver > run NVCleanstall.exe > use driver files on disk
* check Legacy Control Panel > Microsoft Visual C 2017 Runtimes > PhysX
* check disable installer telemetry & advertising > perform clean install > disable Ansel
* check show expert tweaks > disable HDCP
* next > build package
#
* Disable GPU stuff (afterburner ect/auto-startups)
* Disable internet (press ⊞ Win+R ncpa.cpl)
#
* press <kbd>⊞ Win+R</kbd> type "msconfig" > boot > safe boot
* reboot*
* press <kbd>⊞ Win+R</kbd> type "msconfig" > boot > safe boot > uncheck > exit without restarting*
* run Display Driver Uninstaller.exe (DDU) > options > remove physX > uncheck prevent downloads of drivers... (you are offline)
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
* 3D Settings > Manage 3D settings > Anisotropic filtering > Appplication-controlled or off/4x/8x/16x
* 3D Settings > Manage 3D settings > Low Latency Mode > Ultra (check 🟩 for more info)
* 3D Settings > Manage 3D settings > Power management mode > Prefer maximum performance
* 3D Settings > Manage 3D settings > Preferred refresh rate > Highest available (now is default)
* 3D Settings > Manage 3D settings > Shader Cache Size > Unlimited (def is too low for lots of games will cause compile shader lag, stutters and slow compiling)
* 3D Settings > Manage 3D settings > Anisotropic sample optimization > On (or leave default)
* 3D Settings > Manage 3D settings > Negative LOD bias > Allow (Clamp for 0 LOD bias, 0/+ helps GPU bound, -0 used in dlss ect for image quality) (or leave default)
* 3D Settings > Manage 3D settings > Texture filtering Quality > High performance (high quality if you are cpu bound) (or leave default)
* 3D Settings > Manage 3D settings > Trilinear optimization > On (or leave default)
* Apply
* 3D Settings > Configure Surround, PhysX > set PhysX to GPU
* Display > Change resolution > set res and hz (all monitors) > Apply
* Display > Change resolution > check use NVIDIA color settings set BPC (8bpc or 10bpc) and output dynamic range to full (0-255 rgb) (all monitors) > Apply
* Display > Adjust desktop color settings > Digital vibrance 100% (all monitors) > Apply
* Display > Set up G-SYNC > check Enable settings for the selected display model (check 🟩 for more info)
* Video > Adjust video color settings > check With the NVIDIA settings > Advanced > Dynamic range > Full (0-255) (all monitors) > Apply
#
* open Display settings (right click):
* Color profile > Automatically manage color for apps > off (very important) (use your monitor for color or this will destroy colors, ACM will turn itself back on when changing output color depth in NvCpl so dont do that after, check 🟩 for more info)
* Graphics > Auto HDR > Off*
* Graphics > Optimizations for windowed games > On
* Graphics > Advanced graphics settings > Hardware-accelerated GPU scheduling (HAGS) (Required* for framegen) > On
* Graphics > Custom settings for applications (remove apps or make sure the games are set to high performance)
#
* press <kbd>⊞ Win+R</kbd> type "colorcpl" add and remove correct profiles
* open Display settings > turn HDR on* then turn off if not using (check 🟩 for more info)
#
* Enable GPU stuff (afterburner ect/auto-startups)
* reboot
* Enable internet (press <kbd>⊞ Win+R</kbd> type "ncpa.cpl")
---
---
---
---
---
---
---
---
## 🟩 Extra (ADVANCED)
## 🟩 Advanced github i do:
* use [Registry Tweaks Refresh](https://github.com/smo0ths/Registry-Tweaks-Refresh.bat)
* use [My Network Adaptor Settings](https://github.com/smo0ths/My-Network-Adaptor-Settings)
* use [FIREWALL lock down but functional ruleset](https://github.com/smo0ths/FIREWALL-lock-down-but-functional-ruleset)
* optimize that shit
---
---
---
## 🟩 VRR ect:
* Variable Refresh Rate/FreeSync/G-Sync/AdaptiveSync/ULMB2
#
* your monitor will have an option to turn it on or off
* Only way to tell if VRR is working is in monitor on screen display (OSD)
* Monitor's Over Drive setting can't be higher than normal usually or it will cause inverse ghosting with VRR on
* G‑Sync for windowed and full screen mode (can cause rare desktop stutter issues so dont use)
#
* loweset latency is this order from written
* 1 → reflex no fps cap
* 2 → ultra low latency mode no fps cap
* 3 → all the above with fps cap (stable frame times)
* 4 → Maximum Pre-Rendered Frames 1 (low latency mode on) no fps cap
* 4a → Maximum Pre-Rendered Frames 1 (low latency mode on) with fps cap (stable frame times)
* 4b → snycs/all the above with or w/o fps cap (gsync range) (recommended for most games and use 1 → for competitive)
* 5 → snycs/all the above with fps cap for LFC(Low Framerate Compensation)
#
* latency is: Input → Game logic → GPU → Display → Your eyes
* blur busters recommend force on vsync in nvcpl so when sync goes below or above monitor supported gsync hz it will still only show synced frames (test this may help LFC)
* ULMB2 backlight strobing on some monitors with gsnyc (ULMB1 killed brightness, ULMB2 is just the best IPS tech use it if you have it)
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
* rBar - Enable > Enable
* Apply changes
#
* update your DLSS files manualy from NVIDIAGameWorks/Streamline github (devs dont do it and idk what nvidia is doing)
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
* Smooth Motion - Enable off/on (test if you cant use FG or OptiScaler*)
---
---
---
## 🟩 audio:
* set bits to 24 or 32bits and 48kHz or 96kHz (i use 24/96kHz i hear the extra points in 96kHz)
* bits is dynamic range to noise floor and sample rate is time points of a wave signal (Bits = vertical resolution, Sample rate = horizontal resolution)
* Exclusive Mode: Uncheck for multitasking (OBS/Discord/games/etc). Check for audiophile music listening or studio recording (bit‑perfect)
* keep all audio windows/games at 100% until the last stage (DAC/AMP/soundcard software) for audiophile/bit perfect sound
* audio path: Audio decoding → Resampling (Windows) → DAC (Hardware) → Your ears
* use surround sound > HTRF > (for games/movies/shows) and stereo is best for most music
* EQ audio: for 10band set 0/-1/-1/+1/-1/0/+1/-1/-1 for most headsets, 0,0,+1,-1,+1,0,0,+1,+1 for more bass/treble and raise 62Hz/4kHz if you need more bass/treble
#
* EQ voice: set your format to 1 channel* and 24bit/48kHz 
* everyone has a different sound freq and women might need a bit different eq
* use Equalizer APO or something
* best universal from flat response eq: (i use VSTPlugins\ReaPlugs\reaeq-standalone.dll)
* 1(change to Band)  125.0/ 2.5/0.70 (Hz/dB/oct)
* 2(band)            500.0/-2.5/0.70 (Hz/dB/oct)
* 3(band)           3000.0/ 1.0/0.70 (Hz/dB/oct)
* 4(change to Band) 7000.0/ 3.5/0.70 (Hz/dB/oct)
---
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
---
## 🟩 Afterburner/RTSS:
* afterburner just needs enable hardware control and monitoring (general tab) for fan enable user defined software automatic fan control (fan tab)
* set fan curve (40% @30c 100% @70/80/or90c if noisy @5000ms) also set your fans in pc case in bios (80% @40c 100% @60c @3000ms-5000ms)
* for modern GPU's turning down power limit to 80/90% can lower heat/power output and not lose much fps
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
* hz should be 1000 or whatever crazy max you have
* sensitivity, i like 1:1 6in 1080° turn for freelook/reflex sights and 9in 90° for anything 4x+ scopes (for 3rd person RPG games 4in 1080° for freelook)
* keep your sensitivity the same so you dont suck, find that perfect 1:1 sens for competitive i used to use 7in 1080° turn
* other to do
---
---
---
## 🟩 MPO Multi-Plane Overlay:
* on can help cpu bound ect, off can fix display problems ect, can you even disable it? idk
* test type dxdiag save search for "MPO MaxPlanes"
* MPO on*
* reg delete "HKLM\SOFTWARE\Microsoft\Windows\Dwm" /v "OverlayTestMode" /f
* MPO off*
* reg add "HKLM\SOFTWARE\Microsoft\Windows\Dwm" /v "OverlayTestMode" /t REG_DWORD /d 5 /f
---
---
---
## 🟩 Windows Game Mode:
* test yourself an optimized system wont benefit in my experience
* Settings > Gaming > Game Mode > Off
* reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AllowAutoGameMode" /t REG_DWORD /d 0 /f
* reg add "HKCU\SOFTWARE\Microsoft\GameBar" /v "AutoGameModeEnabled" /t REG_DWORD /d 0 /f
---
---
---
## 🟩 FPS cap:
* for VRR (variable refresh rate) or LFC (Low Framerate Compensation) and/or keeping thermals/utilization down
* framerate limiter types async/front edge sync/back edge sync/nvidia reflex/nvidia/game engines
* 1 fps buffer caps are lowest latency (some limiters are actually 2/3 frame buffers like nvidia's non reflex one)
* best practice -2fps under refresh rate
* AI frame gens can be capped (reflex limiter or others) to lower utilizations, smooth motion seems to like no cap
* rtss > fraterate limit -2 under monitor max hz (or lower for stable/and/or LFC)
* rtss > setup > enable framerate limiter > NVIDIA reflex (is ultra low latency if not used with reflex i think)
---
---
---
## 🟩 ReBAR:
* Enable rebar in your bios (if its supported)
* rBAR in nvidiaProfileInspector (as admin)
* rBar - Enable > Enable (rebar can cause games to stutter/lag randomly/crash) (test per-game)
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
## 🟩 HDR/SDR profiles:
* Monitor .icc/icm profile
* put ICC Profiles in here open ⊞ Win+R %SystemDrive%Windows/System32/spool/drivers/color
* open ⊞ Win+R colorcpl.exe (click add and add ICC profiles, click Add as HDR Profile for hdr icc profiles)
* find manufactures icc profile or search for them or buy a monitor calibration tool (or use phone) (calibration is subjective in color spaces because nobody knows what they are doing)
* HDR adds a little latency
* use Video > Adjust video image settings > RTX video enhancement > super resolution/high dynamic range to enhance content
#
* Windows HDR Calibration
* download MicrosoftCorporationII.WindowsHDRCalibration_1.0.152.0_neutral_~_8wekyb3d8bbwe.Msixbundle (or newer)
* turn monitor on HDR mode
* turn on HDR in windows
* games can override max nits and keep it in mind you are calibrating a white box
* leave the color saturation section on 0 and do that elsewhere or make multiple profiles
* calibrate
#
* interesting SDR/HDR calibration (not recommended just test)
* System > Display > Color profile > sRGB to Gamma2.2 (srgb_to_gamma2p2_sdr.icm) (SDR)
* System > Display > Color profile > SDR ACM: srgb_d50 [ srgb_to_gamma2p2.cal ] (srgb_to_gamma2p2_400_mhc2.icm) (HDR)
* find these on github they have a nice gamma roll from zero but crush black levels
---
---
---
## 🟩 monitors:
* ideal distance your eyes should be for 4k 27inch monitor (min 16.8inch/max 20.4inch) and pointing at 33.3% below the top of your monitor flat
* only ever use your monitor to change sharpness disable it everywhere else
* OLED = perfect blacks, but brightness + burn‑in concerns.
* Mini‑LED = brightness champ, but local dimming zones matter.
* Micro‑LED = the dream tech that does it all (someday).
---
---
---
## 🟩 OBS:
* settings > stream > ignore stream serv setting recommendations
* output > rescale output disabled > constant bitrate > 6000/7500kbps > keyframe 2s > P5 > HQ > two pass (quarter res) > uncheck both > 2 b-frames
* output > audio > 256kbps or 320kbps
* audio > 48kHz
* video > output 1664x936 > 60fps
* advanced > sRGB > limited > sources uncheck browser source hardware acceleration
#
* set game capture RGB10A2 Color Space set to Rec. 2100 (PQ) when you are playing in HDR so your stream can see the game tone‑mapped to SDR
* set your display captures for desktop checkbox to Force SDR for if you are ever in HDR for viewers
* turn off Docks > Audio Mixer because it cost you 2fps in every game
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
## 🟩 game deals:
* use [gg.deals/deals](https://gg.deals/deals/?platform=1&sort=date&store=4,5,6,22,38,57,1169&tag=-117,-79,-25&type=1,2)
---
---
---
## 🟩 High Precision event timer/Time Stamp Counter:
* HPET should be off, in cmd type "bcdedit /enum" "useplatformclock" should not be there win11 uses invariant TSC "bcdedit /deletevalue useplatformclock" to delete
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
* overclocking to do
* CSM off + UEFI on + 4G Decoding on = ReBAR works
---
---
---
## 🟩 Adjust desktop size and position (nvcpl):
* perform scaling on display or gpu (test) (or leave default)
* integer scaling setup (can't use with DSC)
