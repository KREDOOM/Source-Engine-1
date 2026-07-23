![[jackal_normal.png]]
— это параметр [[Шейдеры|шейдера]] материала, доступный во всех играх [[Source Engine 1|Source]].
It specifies a [texture](https://developer.valvesoftware.com/wiki/Texture "Texture") that will provide three-dimensional lighting information for a material. The texture is a [bump map](https://developer.valvesoftware.com/wiki/Bump_map "Bump map"), but the process it is used for is called [![](https://developer.valvesoftware.com/w/images/thumb/9/9a/Wikipedia_icon_small.png/16px-Wikipedia_icon_small.png)](http://en.wikipedia.org/wiki/normal_mapping "wikipedia:normal mapping")[normal mapping](http://en.wikipedia.org/wiki/normal_mapping "wikipedia:normal mapping"). The two terms are often used interchangeably, however.

**Warning:**`$bumpmap` will disable [prop_static](https://developer.valvesoftware.com/wiki/Prop_static "Prop static")'s per-vertex lighting in every Source game before [CS:GO engine branch](https://developer.valvesoftware.com/wiki/Counter-Strike:_Global_Offensive_engine_branch "Counter-Strike: Global Offensive engine branch").  
Not enough data is stored in the vertices for normal mapping, so the engine has no choice but to fall back.

**Important:**Bumpmapped brushes and displacements generate four lightmaps per-surface (one for each light direction, plus non-bumped version), instead of one. If `$bumpmap` or `$normalmap` is added to a VMT that did not have it at the time of compilation, the map must be recompiled.

**Note:**This does not apply to maps compiled using the `-bumpall` [VBSP](https://developer.valvesoftware.com/wiki/VBSP "VBSP") parameter (Which creates 4 lightmaps for all faces, regardless of if they are bumpmapped). This parameter should not be used often, however, as it significantly increases lightmap usage.

**Important:**`$bumpmap` does not exist for `[LightmappedReflective](https://developer.valvesoftware.com/wiki/LightmappedReflective "LightmappedReflective")`. Use `$normalmap` instead.