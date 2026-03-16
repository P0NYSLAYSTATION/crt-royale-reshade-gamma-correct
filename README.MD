This is a fork of akgunter's port, with gamma-correction options added and a closer approximation of the original libretro version's gaussian beam sampling, significantly reducing clipping and crush.

### USING THE ENCODING AND DECODING OPTIONS
Using one of the provided encoding options will generally always reduce the amount of crush. 

Old games that do not use an encoding standard are usually closer to BT.1886 or pure power-law, so either decode BT.1886 or use the sRGB encode and decode. 

Linear color is also an option but outside of a few engines that do weird gamma ramp stuff, this can blow out bright colors excessively. 

From mid-2000s onward, most games are sRGB encoded.

If you have selected a decoding standard then you should usually also encode to that standard, otherwise use whichever standard is closer to your physical monitor characteristics and settings.

If you are playing a game that applies its own gamma ramp, you should set that to a neutral value if possible. If that is not possible, for example in Goldsource engine games, then better results will be achieved by using the bt.1886 standard regardless of what encoding standard the game actually uses, in-game gamma ramp to 2.2 or 2.4. Unreal Engine 1 uses an inverse gamma ramp, so you will need to max out the in-game gamma ramp, encode to bt.1886 and decode to linear.

When using a narrow scanline thickness, you may still see some blown out overbrights and clipped whites. These can usually be fixed by raising the bloom excess and bloom underestimation parameters, which will fix this issue at the cost of a slightly blurrier overall image.

Unfortunately the shader produces a lot of severe artefacts when using float textures so don't expect any HDR encoding standards to be added anytime soon, fixing those artefacts would be a much more significant task than the minor edits and additions this fork currently provides.

#### CREDIT
The vast majority of the code here is taken from the current libretro shader repositories, so the most of the credit goes to those authors.

[libretro/glsl-shaders](https://github.com/libretro/glsl-shaders)<br>
[libretro/slang-shaders](https://github.com/libretro/slang-shaders)

Special thanks goes to Matsilagi for his time, suggestions, testing, debugging, and enthusiasm. It's been tremendously helpful, especially in figuring out some of the nastier bugs.
Lord of Lunacy and Marty McFly helped me with some optimizations that were really cool.
Thank you Crosire and co. for all their work on ReShade.
Thanks to andersstorhaug for the idea to let the user rotate the screen.


#### API SUPPORT
This shader should work with DX9, DX10/11/12, OpenGL, and Vulkan. It'll probably spit out a bunch of yellow error messages in DX9, but that's okay.


#### SUGGESTED REPOSITORIES
[Matsilagi/RSRetroArch](https://github.com/Matsilagi/RSRetroArch) - Matsilagi has a chunk of other RetroArch shaders ported over here already. The PAL and NTSC shaders are particularly useful (load them before crt-royale).


#### SETUP
The shader's UI includes tips and descriptions for setting it up well. Prioritize the Phosphor Mask and Scanlines sections.


You can go to [the wiki](https://github.com/akgunter/crt-royale-reshade/wiki) for more detailed info on the different options.







