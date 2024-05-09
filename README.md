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
MSIs interrupt priority high
disable HDCP
build package
```

---

#### Reset GPU overclock and disable start with windows/apply at startup (MSI Afterburner)

---

```python
press ⊞ Win+R > type msconfig > boot > safe boot
reboot
press ⊞ Win+R > type msconfig > boot > safe boot > uncheck > exit without restarting
run DDU uninstall (as admin) > options > remove physX > Clean and restart
reboot
install driver (as admin)
```

---

```python
NVIDIA Control Panel:
Adjust image settings with preview > Use my preference emphasizing > Performance > Apply
Use the advanced 3D image settings > Apply
Manage 3D settings > Global Settings > Anisotropic filtering set what you want
Manage 3D settings > Global Settings > Low Latency Mode Ultra
Manage 3D settings > Global Settings > Power management mode Prefer maximum performance
Manage 3D settings > Global Settings > Preferred refresh rate Highest available
Manage 3D settings > Global Settings > Anisotropic sample optimization On
Manage 3D settings > Global Settings > Negative LOD bias set what you want
Manage 3D settings > Global Settings > Texture filtering Quality set to High performance
Change resolution > set resolutions and refresh rates
Change resolution > NVIDIA color settings set Output color depth and Full dynamic range (all monitors)
Adjust desktop color settings > Digital vibrance 100% (all monitors) (this can reset after changing settings so make sure you check it)
Set up G-SYNC > Enable settings for the selected display model (turn monitor off and on for windows to figure it out)
Adjust video color settings > With the NVIDIA settings > Color 100% saturation > Advanced Full dynamic range (all monitors)
```

---

```python
nvidiaProfileInspector (as admin):
Maximum Pre-Rendered Frames Use the 3D application setting
Texture Filtering - LOD Bias set what you want (Negative LOD bias needs to be set to Allow)
CUDA - Force P2 State Off
rBAR Enabled
```

---

```python
System > Display > Graphics > Default graphics settings:
Hardware-accelerated GPU scheduling On
Variable refresh rate On
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
Add resolutions (2816x1584 ~3k UHD) (3072x1728 3K) (3328x1872 3.25K) (My monitor lets me change to DP 1.2 and that unlocks Customize... button and i change back to DP 1.4)
```
