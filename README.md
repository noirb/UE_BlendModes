# UE_BlendModes
An expanded set of BlendMode Material Functions for Unreal Engine

These have only been tested & evaluated in UE5, but it's very likely that they would also work fine in 4.26+

## What's Included

36 new blend functions, and wrappers around the 14 built-in blend functions to include an `Opacity` parameter to allow you to adjust how much of the blend is applied to the final result.

In the material editor, all of the included functions can be found under `NB - Blends` in the function library.

## Usage

All nodes have 3 inputs:

|           |   |
|-----------|---|
| `Base`    | Base image/texture/color the blend operation is being applied TO. <br> e.g. in a post process material, this will likely be your scene color. If this were an image editing program, `Base` would refer to the lower of the two layers. |
| `Blend`   | The image/texture/color which will be blended with `Base`. <br> In an image editing program, `Blend` would refer to the upper layer to which the blend mode is applied.                                                                 |
| `Opacity` | `[Optional]` A value between `0` and `1` which will adjust the "intensity" of the blending operation. Analogous to adjusting the opacity of the `Blend` layer in an image editing application.<br>At `0.0`, the output will be identical to `Base`.<br>Can be used to smoothly interpolate between blends. <br> Defaults to `1.0` |

## Blend Functions

| Blend Function       | Description                                                                | Notes                                                                                                                  |
|----------------------|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| `Blend_Add`          | Simple Additive Blending                                                   |                                                                                                                        |
| `Blend_Average`      | Averages the two inputs                                                    |                                                                                                                        |
| `Blend_Color`        | Applies Hue & Saturation of `Blend` image to `Base` image                  | Operates in HSL colorspace                                                                                             |
| `Blend_ColorBurn`    |                                                                            | Wrapper around [Blend_ColorBurn](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)   |
| `Blend_ColorDodge`   |                                                                            | Wrapper around [Blend_ColorDodge](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)  |
| `Blend_Darken`       |                                                                            | Wrapper around [Blend_Darken](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)      |
| `Blend_DarkerColor`  | Returns whichever input is darker                                          | Operates in HSL colorspace                                                                                             |
| `Blend_Difference`   | Subtracts `Base` image from `Blend` image                                  | Wrapper around [Blend_Difference](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)  |
| `Blend_Dissolve`     | Randomly selects pixels from `Blend` and `Base`                            | Requires `float4` inputs, kind of expensive (>100 instructions)                                                        |
| `Blend_Divide`       | Divides `Base` by the `Blend` image                                        |                                                                                                                        |
| `Blend_Exclusion`    |                                                                            | Wrapper around [Blend_Exclusion](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)   |
| `Blend_Extremity`    |                                                                            |                                                                                                                        |
| `Blend_Far`          | Only accepts colors from `Blend` which exceed a set distance from `Base`   |                                                                                                                        |
| `Blend_Frect`        | Intersection of `Freeze` and `Reflect`                                     |                                                                                                                        |
| `Blend_Freeze`       |                                                                            |                                                                                                                        |
| `Blend_Gleat`        | Intersection of `Glow` and `Heat`                                          |                                                                                                                        |
| `Blend_Glow`         |                                                                            |                                                                                                                        |
| `Blend_GrainExtract` |                                                                            |                                                                                                                        |
| `Blend_GrainMerge`   | The reverse operation of `GrainExtract`                                    |                                                                                                                        |
| `Blend_HardLight`    |                                                                            | Wrapper around [Blend_HardLight](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)   |
| `Blend_HardMix`      | Adds color components together; if > 1.0, then returns 1.0, else 0.0       |                                                                                                                        |
| `Blend_Harmonic`     | Harmonic mean of `Base` and `Blend`                                        |                                                                                                                        |
| `Blend_Heat`         | `Blend_Freeze` with the inputs swapped                                     |                                                                                                                        |
| `Blend_Helow`        | Intersection of `Heat` and `Glow`                                          |                                                                                                                        |
| `Blend_Hue`          | Applies the Hue of the `Blend` image to the `Base` image                   | Operates in HSL space                                                                                                  |
| `Blend_Interpolation`| Sine-based blending, yields smooth results                                 |                                                                                                                        |
| `Blend_Lighten`      |                                                                            | Wrapper around [Blend_Lighten](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)     |
| `Blend_LighterColor` | Returns whichever input is lighter                                         | Operates in HSL colorspace                                                                                             |
| `Blend_LinearBurn`   |                                                                            | Wrapper around [Blend_LinearBurn](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)  |
| `Blend_LinearDodge`  |                                                                            | Wrapper around [Blend_LinearDodge](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/) |
| `Blend_LinearLight`  |                                                                            | Wrapper around [Blend_LinearLight](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/) |
| `Blend_Luminosity`   | Applies the Luminosity of the `Blend` image to the `Base` image            | Operates in HSL colorspace                                                                                             |
| `Blend_Multiply`     | Simple Multiplicative Blending                                             |                                                                                                                        |
| `Blend_MultiplyAdd`  | Yields similar color adjustments to `Multiply` without darkening the image |                                                                                                                        |
| `Blend_Near`         | Only accepts colors from `Blend` which are under a set distance from `Base`|                                                                                                                        |
| `Blend_Negation`     | Subtracts `Blend` image from `Base` and inverts the result                 |                                                                                                                        |
| `Blend_Overlay`      |                                                                            | Wrapper around [Blend_Overlay](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)     |
| `Blend_PenumbraA`    |                                                                            |                                                                                                                        |
| `Blend_PenumbraB`    | `Blend_PenumbraA` with the inputs swapped                                  |                                                                                                                        |
| `Blend_Phoenix`      |                                                                            |                                                                                                                        |
| `Blend_PinLight`     |                                                                            | Wrapper around [Blend_PinLight](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)    |
| `Blend_Power`        | Quadratic mean of `Base` and `Blend`                                       |                                                                                                                        |
| `Blend_Reeze`        | Intersection of `Reflect` and `Freeze`. Like a less posterized `HardMix`.  |                                                                                                                        |
| `Blend_Reflect`      |                                                                            |                                                                                                                        |
| `Blend_Saturation`   | Applies the Saturation of the `Blend` image to the `Base` image            |                                                                                                                        |
| `Blend_Screen`       |                                                                            | Wrapper around [Blend_Screen](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)      |
| `Blend_Sine`         | `sin(Base + Blend) * Pi/2`                                                 |                                                                                                                        |
| `Blend_Softlight`    |                                                                            | Wrapper around [Blend_Softlight](https://docs.unrealengine.com/5.0/en-US/blend-material-functions-in-unreal-engine/)   |
| `Blend_Subtract`     | Subtracts `Blend` image from `Base`                                        |                                                                                                                        |
| `Blend_VividLight`   |                                                                            |                                                                                                                        |

## Additional Functions

To support the implementation of the above blendmodes, a few helper functions were created which might also be useful in other contexts:

| Function             | Description                                                                                                 |
|----------------------|-------------------------------------------------------------------------------------------------------------|
| `HSLtoRGB`           | Converts a vec3 from the [HSL](https://en.wikipedia.org/wiki/HSL_and_HSV) colorspace back to RGB.           |
| `RGBtoHSL`           | Converts a vec3 from the RGB colorspace to [HSL](https://en.wikipedia.org/wiki/HSL_and_HSV).                |