How to Optimize Performance by Editing GameUserSettings.ini

If you're experiencing low FPS or performance issues, you can improve the game's performance by editing the ```GameUserSettings.ini``` file. This guide will show you how to disable RTX Ray Tracing, Lumen technology, and make other optimizations for better frame rates.

Step-by-Step Instructions

Locate the ```GameUserSettings.ini``` file: The configuration file is located at the following path:

```%localappdata%\GZW\Saved\Config\Windows```

You can copy and paste this path into the File Explorer address bar.

Once there, find the file named ```GameUserSettings.ini``` and open it with Notepad or any text editor.

Modify Graphics Settings for Better Performance:

Adjust the following values in the ```GameUserSettings.ini``` file to reduce the load on your system and increase FPS. 

```
[ScalabilityGroups]
sg.ResolutionQuality=65.0         ; Lower resolution scale (between 0-100) for better performance
sg.ViewDistanceQuality=1          ; Decrease the view distance to reduce rendering load
sg.AntiAliasingQuality=0          ; Disable anti-aliasing for higher FPS
sg.ShadowQuality=0                ; Disable shadows for a performance boost
sg.GlobalIlluminationQuality=0    ; Disable global illumination to save GPU power
sg.ReflectionQuality=0            ; Disable reflections for better FPS
sg.PostProcessQuality=1           ; Lower post-processing effects
sg.TextureQuality=0               ; Use lower texture quality for smoother performance
sg.EffectsQuality=0               ; Disable effects like particles and explosions
sg.FoliageQuality=0               ; Reduce foliage detail for better performance
sg.ShadingQuality=0               ; Disable complex shading effects
sg.LandscapeQuality=2             ; Lower landscape detail to reduce GPU load
```

Disable RTX Ray Tracing and Lumen Technology: Ray Tracing and Lumen lighting are very performance-intensive. Disabling them will greatly improve FPS if they are enabled in the game. Add the following lines to your configuration to disable them: 

```
[SystemSettings]
r.RayTracing=False
r.RayTracing.Shadows=False
r.RayTracing.Reflections=False
r.RayTracing.AmbientOcclusion=False
r.RayTracing.GlobalIllumination=False
r.RayTracing.Lighting=False
r.RayTracing.Translucency=False
r.RayTracing.SkyLight=False
r.Lumen.Reflections=False
r.Lumen.Reflections.HardwareRayTracing=False
r.Lumen.Reflections.ScreenTraces=False
r.Lumen.GlobalIllumination=False
r.Lumen.ScreenProbeGather=False
r.BloomQuality=0
r.LensFlareQuality=0
r.LensFlareQuality=0
r.PostProcessAAQuality=0
r.PostProcessAAQuality=0
r.DepthOfFieldQuality=0
r.DefaultFeature.AntiAliasing=0
r.MaxAnisotropy=16
```

Disable Frame Rate Smoothing: By default, Unreal Engine might smooth the frame rate to prevent sharp fluctuations. Disabling this can improve FPS stability. Add the following line to the ```[Script/Engine.Engine]``` section of your ```GameUserSettings.ini```:
```
[/Script/Engine.Engine]
bSmoothFrameRate=False
```

Optional: Adjust Resolution and Frame Rate Limit:

Lowering your in-game resolution (e.g., from 2560x1440 to 1920x1080) can significantly improve FPS.
Limiting the frame rate to a specific value can also help stabilize performance.

Adjust these settings in the ```[/Script/MadfingerGame.MFGGameUserSettings]``` section:
```
[/Script/MadfingerGame.MFGGameUserSettings]
bUseVSync=False                   ; Disable VSync for higher FPS
bUseDynamicResolution=True        ; Enable dynamic resolution to adapt to performance needs
ResolutionSizeX=1920              ; Set resolution width to 1920 (Full HD)
ResolutionSizeY=1080              ; Set resolution height to 1080 (Full HD)
FrameRateLimit=120.000000         ; Limit frame rate to 120 FPS for smoother gameplay
```
Summary of Changes:

Lowered graphics settings to reduce GPU load and improve performance.
Disabled RTX Ray Tracing and Lumen technology to avoid the performance hit from advanced lighting effects.
Disabled Frame Rate Smoothing to remove artificial FPS caps and fluctuations.
Lowered resolution and frame rate limit for stable, high-performance gameplay.

OPTIONAL: Make an Engine.ini

Create a new separate file, Engine.ini.
The easiest way to do this is by copying your existing ```GameUserSettings.ini``` file and renaming it to ```Engine.ini```. Once renamed, open the new file with Notepad and delete all existing variables in it.

2. Add the following lines to the file:
```
[/script/engine.renderersettings]
r.AntiAliasingMethod=0 ; Disable all Anti-Aliasing methods. Personally I don't recommend using this line as it makes very pixelated graphics.
r.Upscale.Quality=0 ; Sharpen the resolution scaler and apply a “nearest neighbor” method for pixel reduction.
r.Upscale.Softness=0
r.Tonemapper.Sharpen=0.5 ;Sharpen the game without third-party filters. Set it to your preference 0.5 to 2.5.
r.TextureStreaming=0
r.DepthOfFieldQuality=0
r.BloomQuality=0
r.FilmGrain=0
r.SceneColorFringeQuality=0
r.DisableDistortion=1
r.Tonemapper.Quality=0
r.LensFlareQuality=0
r.Fog=0 ; Disables Fog effect
r.VolumetricFog=0 ; Disables Volumetric Fog effect

[/script/engine.renderersettings]
r.OneFrameThreadLag=0 ; disables frame delay from the processing thread (improves responsiveness)

[/script/engine.inputsettings]
bEnableMouseSmoothing=False ; disables mouse smoothing
bViewAccelerationEnabled=False ; disables mouse acceleration
bDisableMouseAcceleration=False ; disables mouse acceleration
```

# Make Both of Files file read-only

After editing the Engine.ini and/or GameUserSettings.ini file, go to "File > Save". Then right-click the file, select "Properties > General", and check the "Read-only" box. This is important because it prevents the game from auto-deleting the file, which would force you to recreate it each time. If you would like to modify the file further after initial testing you will have to un-check read only, make variable updates, save, and then recheck read only again.
