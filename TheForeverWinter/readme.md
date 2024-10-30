How to Optimize Performance by Editing GameUserSettings.ini

If you're experiencing low FPS or performance issues, you can improve the game's performance by editing the ```GameUserSettings.ini``` file. This guide will show you how to disable RTX Ray Tracing, Lumen technology, and make other optimizations for better frame rates.

Step-by-Step Instructions

Locate the ```GameUserSettings.ini``` file: The configuration file is located at the following path:

%localappdata%\ForeverWinter\Saved\Config\Windows

You can copy and paste this path into the File Explorer address bar.

Once there, find the file named GameUserSettings.ini and open it with Notepad or any text editor.

Modify Graphics Settings for Better Performance:

Adjust the following values in the GameUserSettings.ini file to reduce the load on your system and increase FPS.
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
3. Disable RTX Ray Tracing and Lumen Technology: Ray Tracing and Lumen lighting are very performance-intensive. Disabling them will greatly improve FPS if they are enabled in the game. Add the following lines to your configuration to disable them:
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
4. Disable Frame Rate Smoothing: By default, Unreal Engine might smooth the frame rate to prevent sharp fluctuations. Disabling this can improve FPS stability. Add the following line to the ```[Script/Engine.Engine]``` section of your GameUserSettings.ini:
```
[/Script/Engine.Engine]
bSmoothFrameRate=False
```
5. Optional: Adjust Resolution and Frame Rate Limit: Lowering your in-game resolution (e.g., from 2560x1440 to 1920x1080) can significantly improve FPS. Limiting the frame rate to a specific value can also help stabilize performance. Adjust these settings in the ```[ForeverWinter.FWGameUserSettings]``` section:
```
[/Script/ForeverWinter.FWGameUserSettings]
bUseVSync=False                   ; Disable VSync for higher FPS
bUseDynamicResolution=True        ; Enable dynamic resolution to adapt to performance needs
ResolutionSizeX=1920              ; Set resolution width to 1920 (Full HD)
ResolutionSizeY=1080              ; Set resolution height to 1080 (Full HD)
FrameRateLimit=120.000000         ; Limit frame rate to 120 FPS for smoother gameplay
```
6. Save the File: After making these changes, save the GameUserSettings.ini file and close the editor. 7. Restart the Game: Launch ForeverWinter and check your performance. You should notice better FPS and smoother gameplay, especially in demanding areas.

Summary of Changes:

Lowered graphics settings to reduce GPU load and improve performance.
Disabled RTX Ray Tracing and Lumen technology to avoid the performance hit from advanced lighting effects.
Disabled Frame Rate Smoothing to remove artificial FPS caps and fluctuations. Lowered resolution and frame rate limit for stable, high-performance gameplay.

# OPTIONAL - Engine.ini
Create a new file called ```Engine.ini``` in the same folder as ```GameUserSettings.ini```.
Next, add the following lines to the file: 

```
[/Script/Engine.RendererSettings]
r.AntiAliasingMethod=0
r.Upscale.Quality=0
r.Upscale.Softness=0
```

These variables disable all Anti-Aliasing methods, resulting in crisp gameplay but with increased aliasing, dithering, and shimmer. The upscale variables sharpen the resolution scaler and apply a “nearest neighbor” method for pixel reduction. The devs seem to force TSR on the resolution scaler, causing the game to look blurry, almost as if smeared in Vaseline when you reduce pixel count. These variables elimate that. Try these changes and see if you prefer the results.

2. Override the resolution scaler:

You can force the resolution scaler to a value of your choice, overriding the in-game setting. Once you add this variable, you won’t be able to adjust it on the fly. Start by setting it according to your native resolution. Keep in mind that lowering your native resolution in-game without the resolution scaler can reduce UI quality (I don't recommend this). The resolution scaler reduces the number of pixels rendered, lowering GPU stress but also reducing fidelity, which can cause blurring. Set this anywhere between 40-100 as going lower causes graphics anomolies. I set mine to around 40. Ideally you'll want to be around 75% of your native resolution (variable 75). The goal is to find your sweet spot as the lower the variable the higher the FPS but a dramatic falloff of fidelity.
```
r.ScreenPercentage=40
```

3. Sharpen the game without third-party filters:

You can use the following variable to sharpen the image. Set it to your preference—it doesn’t affect performance much. I recommend a value between 0.5 and 1, but you can go up to 2.5, though this may result in oversharpening.
```
r.Tonemapper.Sharpen=0.5
```
4. Disable unnecessary effects:

You can experiment with removing post-processing effects like bloom, film grain, and chromatic aberration using the variables below:
```
r.TextureStreaming=0
r.DepthOfFieldQuality=0
r.BloomQuality=0
r.FilmGrain=0
r.SceneColorFringeQuality=0
r.DisableDistortion=1
r.Tonemapper.Quality=0
r.LensFlareQuality=0
```
5. Disable fog effects:

You can also disable fog effects to further increase FPS. Be warned, though, this may make the game look flatter and affect the atmosphere the devs intended.
```
r.Fog=0
r.VolumetricFog=0
```


# Make the file read-only:
After editing the Engine.ini file, go to "File > Save". Then right-click the file, select "Properties > General", and check the "Read-only" box. This is important because it prevents the game from auto-deleting the file, which would force you to recreate it each time. If you would like to modify the file futher after initial testing you will have to uncheck read only, make variable updates, save, and then recheck read only again. 

