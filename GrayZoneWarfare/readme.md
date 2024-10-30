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
