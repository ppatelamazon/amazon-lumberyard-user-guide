# Debugging Issues<a name="debugging-intro"></a>


****  

|  | 
| --- |
| This topic references tools and features that are [legacy](https://docs.aws.amazon.com/lumberyard/latest/userguide/ly-glos-chap.html#legacy)\. If you want to use legacy tools in Lumberyard Editor, disable the [CryEntity Removal gem](https://docs.aws.amazon.com/lumberyard/latest/userguide/gems-system-cryentity-removal-gem.html) using the [Project Configurator](https://docs.aws.amazon.com/lumberyard/latest/userguide/configurator-intro.html) or the [command line](https://docs.aws.amazon.com/lumberyard/latest/userguide/lmbr-exe.html)\. To learn more about legacy features, see the [Amazon Lumberyard Legacy Reference](https://docs.aws.amazon.com/lumberyard/latest/legacyreference/)\. | 

Lumberyard provides the following built\-in debugging and profiling tools that you can use to locate and fix performance issues\.
+ [Character skeleton debugging](https://docs.aws.amazon.com/lumberyard/latest/legacyreference/char-model-debugging.html) – Use the `p_draw_helpers` console variable to debug character skeleton issues\.
+ [Cinematics debugging](cinematics-debugging.md) – Debug cinematics issues\.
+ [Flow Graph debugging](https://docs.aws.amazon.com/lumberyard/latest/legacyreference/fg-debugging-intro.html) – Use the Flow Graph debugger and console variables to debug flow graph issues\.
+ [Mannequin debugging](https://docs.aws.amazon.com/lumberyard/latest/legacyreference/mannequin-debugging-intro.html) – Debug Mannequin system issues\.
+ [Particle debugging](particle-debugging.md) – Debug particles\.
+ [Vegetation debugging](vegetation-debugging.md) – Debug vegetation objects\.

## Using Console Debug Views<a name="debugging-debug-views"></a>

The viewport window displays debugging information by default when you are in gameplay mode \(**Ctrl\+G**\)\. You can toggle this information on or off by pressing the tilde \(**\~**\) key\. Use the following console variables and values to generate viewing modes in the viewport that are useful for debugging\.
+ `e_Camerafreeze 1` – Freezes the camera to see what is rendered from the camera's point of view and what is occluded\. Also useful for debugging object culling and LOD\.
+ `e_DefaultMaterial 1` – Applies a uniform, flat, gray material to every surface in the level\.
+ `e_memoryProfiling 1` – Prints onscreen statistics for the amount of GPU memory that textures and buffers use\.  
![\[Using the e_memoryProfiling console variable to display VRAM usage.\]](http://docs.aws.amazon.com/lumberyard/latest/userguide/images/debugging-debug-views-vram-usage.png)
+ `e_TerrainBBoxes` – Displays terrain bounding boxes\.
+ `p_debug_joints 1` – Shows the mass of objects in kilograms and the joint that is linked to the object\. To display joints, you must first enable `p_draw_helpers 1`\.
+ `p_draw_helpers 1` – Shows physics proxy meshes in addition to the render geometry\.
+ `r_DisplayInfo 0` – Disables the debugging text\.
+ `r_DisplayInfo 1 | 2 | 3 | 4` – Enables various levels of debugging text\. Displays memory consumption, frame rate, triangle count, visible light sources, and drawcall count\. Use a value of `2` to display more detailed information\. Use a value of `3` to display only frames per second \(FPS\) and frame time in milliseconds\.
+ `r_wireframe 1 | 2` – Use a value of `1` to draw the level in wireframe mode\. Use a value of `2` to draw the level in vertex mode\. Both include the objects that are hidden from view\.
+ `r_ShowLines 2` – Overlays the wireframe only on the front\-facing geometry\. Anything behind this geometry isn't rendered\.
+ `r_TexBindMode 6` – Applies a uniform, flat, gray material with normal map information to every surface in the level\.

### Using DebugDraw Console Variables<a name="debugging-debug-views-debugdraw"></a>

Use the following console variables and values to display information about your level\.
+ `e_DebugDraw 1` – Displays the name of the `.cgf` used, polycount, and LOD\.
+ `e_DebugDraw 2` – Displays a color\-coded polygon count\.
+ `e_DebugDraw 3` – Displays a color\-coded LOD count\. Flashing color indicates no LOD information\.
+ `e_DebugDraw 4` – Displays object texture memory usage\.
+ `e_DebugDraw 5` – Displays a color\-coded number of render materials\.
+ `e_DebugDraw 6` – Displays ambient color\.
+ `e_DebugDraw 7` – Display triangle count, number of render materials, and texture memory\.
+ `e_DebugDraw 8` – Displays RenderWorld statistics \(with view cones\)\.
+ `e_DebugDraw 9` – Displays RenderWorld statistics \(with view cones without lights\)\.
+ `e_DebugDraw 10` – Displays render geometry with simple lines and triangles\.
+ `e_DebugDraw 11` – Displays render occlusion geometry\. 
+ `e_DebugDraw 12` – Displays render occlusion geometry without render geometry\.
+ `e_DebugDraw 13` – Displays occlusion amount \(used during AO computations\)\.
+ `e_DebugDraw 15` – Displays helpers\.
+ `e_DebugDraw 16` – Displays debug gun\.
+ `e_DebugDraw 17` – Displays streaming information \(buffer sizes\)\.
+ `e_DebugDraw 18` – Displays streaming information \(required streaming speed\)\.
+ `e_DebugDraw 19` – Displays physics proxy triangle count\.
+ `e_DebugDraw 20` – Displays object instant texture memory usage\.
+ `e_DebugDraw 21` – Displays animated object distance to camera\.
+ `e_DebugDraw 22` – Display object's current LOD vertex count\.

### Using GBuffer Console Variables<a name="debugging-debug-views-gbuffer"></a>

Use the following console variables and values to display materials, colors, shadows, albedo, and other characteristics in your level\.
+ `r_DebugGBuffer 1` – Shows normals of all assets in the level\.
+ `r_DebugGBuffer 2` – Shows the roughness or glossiness of the surfaces\.
+ `r_DebugGBuffer 3` – Shows the specular color of materials\.
+ `r_DebugGBuffer 4` – Shows the albedo of all surfaces in the level\.
+ `r_DebugGBuffer 5` – Shows the lighting model in the level\. Gray = standard \| Yellow = transmittance \| Blue = POM self\-shadowing\.
+ `r_DebugGBuffer 6` – Shows the translucency values that are set on assets in the level\. Black = none\.
+ `r_DebugGBuffer 7` – Shows self\-shadowing of materials that use Offset Bump mapping or Parallax Occlusion Mapping\.
+ `r_DebugGBuffer 8` – Shows in red and yellow any asset that uses SSS\. The brighter the color, the higher the SSS index\.
+ `r_DebugGBuffer 9` – Shows whether specular colors are in a reasonable range as follows: 
  + **Blue** – The specular color is too low\.
  + **Orange** – The specular color is too high for dielectric materials\.
  + **Pink** – The specular color is valid only for rusted or oxidized metals\.