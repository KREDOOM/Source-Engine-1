![[jackal_normal.png]]
— это параметр [[Шейдеры|шейдера]] материала, доступный во всех играх [[Source Engine 1|Source]].
Он определяет [текстуру](https://developer.valvesoftware.com/wiki/Texture "Texture"), которая будет предоставлять информацию о трехмерном освещении для материала. Текстура представляет собой [карту рельефа](https://developer.valvesoftware.com/wiki/Bump_map "Bump map"), но процесс, для которого она используется, называется [![](https://developer.valvesoftware.com/w/images/thumb/9/9a/Wikipedia_icon_small.png/16px-Wikipedia_icon_small.png)](http://en.wikipedia.org/wiki/normal_mapping 'wikipedia:normal Mapping')[normal картографирование](http://en.wikipedia.org/wiki/normal_mapping "wikipedia:normal mapping"). Однако эти два термина часто используются как взаимозаменяемые.

**Предупреждение:** `$bumpmap` отключит per-vertex освещение [prop_static](https://developer.valvesoftware.com/wiki/Prop_static "Prop static") в каждой игре [[Source Engine 1|Source]] до [ветки движка CS:GO](https://developer.valvesoftware.com/wiki/Counter-Strike:_Global_Offensive_engine_branch "Counter-Strike: Global Offensive engine branch").  
В вершинах хранится недостаточно данных для нормального отображения, поэтому у движка нет другого выбора, кроме как отступить.

**Важно:** Кисти с рельефной текстурой и смещения генерируют четыре карты освещения для каждой поверхности (по одной для каждого направления света, плюс версия без рельефа) вместо одной. Если `$bumpmap` или `$normalmap` добавляется в VMT, у которого его не было на момент компиляции, карту необходимо перекомпилировать.

**Примечание.** Это не относится к картам, скомпилированным с использованием параметра `-bumpall` [VBSP](https://developer.valvesoftware.com/wiki/VBSP "VBSP") (который создает 4 карты освещения для всех граней, независимо от того, имеют ли они рельеф). Однако этот параметр не следует использовать часто, поскольку он значительно увеличивает использование карты освещения.

**Важно!** `$bumpmap` не существует для `[LightmappedReflective]`. Вместо этого используйте `$normalmap`.