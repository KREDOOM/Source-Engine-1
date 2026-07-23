`$envmapmask` - это [материальный](https://developer.valvesoftware.com/wiki/Ru/Material "Ru/Material") параметр [шейдера](https://developer.valvesoftware.com/wiki/Ru/Shader "Ru/Shader"), доступно для всех игр на движке [Source](https://developer.valvesoftware.com/wiki/Ru/Source "Ru/Source"). Этот параметр определяет **маску бликов**, которая влияет на то, насколько сильно каждый пиксель материала отражает свет от [$envmap](https://developer.valvesoftware.com/wiki/Ru/$envmap "Ru/$envmap"). Маска должна быть изображением в градациях серого, в котором полностью отражающие области являются белыми, а полностью матовые области - черными. Для отражения диффузного типа, которое не зависит от`$envmap,`см.[$phong](https://developer.valvesoftware.com/wiki/Ru/$phong "Ru/$phong").

**Баг:**В играх на [Source 2007](https://developer.valvesoftware.com/wiki/Ru/Orange_Box_\(engine_branch\) "Ru/Orange Box (engine branch)") использование `$envmapmask`, которая не хранится во вложенной подпапке, приведет к сбою загрузки текстуры в игре.  [нужно проверить в [?](https://developer.valvesoftware.com/wiki/Template:BugNotice#Parameters "Template:BugNotice")]

**Предупреждение:**В большинстве случаев, `$envmapmask` не будет работать с материалами, использующими [$bumpmap](https://developer.valvesoftware.com/w/index.php?title=Ru/$bumpmap&action=edit&redlink=1 "Ru/$bumpmap (page does not exist)"). Смотреть [#Альтернативные_методы](https://developer.valvesoftware.com/wiki/Ru/$envmapmask#%D0%90%D0%BB%D1%8C%D1%82%D0%B5%D1%80%D0%BD%D0%B0%D1%82%D0%B8%D0%B2%D0%BD%D1%8B%D0%B5_%D0%BC%D0%B5%D1%82%D0%BE%D0%B4%D1%8B).

**Примечание:**Исключения:

- **[LightmappedReflective](https://developer.valvesoftware.com/wiki/LightmappedReflective "LightmappedReflective")** (использует [$normalmap](https://developer.valvesoftware.com/w/index.php?title=Ru/$normalmap&action=edit&redlink=1 "Ru/$normalmap (page does not exist)"))
- (_только_ в [![Mapbase](https://developer.valvesoftware.com/w/images/thumb/5/5b/Mapbase-16px.png/16px-Mapbase-16px.png)](https://developer.valvesoftware.com/wiki/Ru/Mapbase "Mapbase")) **[VertexLitGeneric](https://developer.valvesoftware.com/wiki/VertexLitGeneric "VertexLitGeneric")**
- (_только_ в [![Counter-Strike: Global Offensive](https://developer.valvesoftware.com/w/images/thumb/8/85/Csgo_icon.png/16px-Csgo_icon.png)](https://developer.valvesoftware.com/wiki/Ru/Counter-Strike:_Global_Offensive "Counter-Strike: Global Offensive"))**[LightmappedGeneric](https://developer.valvesoftware.com/wiki/LightmappedGeneric "LightmappedGeneric")**

**Предупреждение:**`$envmapmask` не будет работать с материалами, использующими [$phong](https://developer.valvesoftware.com/wiki/Ru/$phong "Ru/$phong"). По умолчанию envmap будет использовать альфа-канал [$basetexture](https://developer.valvesoftware.com/wiki/Ru/$basetexture "Ru/$basetexture") для маскировки.

**Примечание:**Маски бликов традиционно являются чёрно-белыми, однако они могут иметь цвет. В таком случае информация о цвете будет использоваться как потексельная $envmaptint.

## Пример синтаксиса VMT

$envmapmask <текстура>

[VertexLitGeneric](https://developer.valvesoftware.com/w/index.php?title=Ru/VertexLitGeneric&action=edit&redlink=1 "Ru/VertexLitGeneric (page does not exist)")([en](https://developer.valvesoftware.com/wiki/VertexLitGeneric))
{
	[$envmap](https://developer.valvesoftware.com/wiki/Ru/$envmap "Ru/$envmap")			env_cubemap
	**$envmapmask		"props/tvscreen_test"**
}

## Дополнительные параметры

[![](https://developer.valvesoftware.com/w/images/thumb/d/da/Scanner_mask.jpg/250px-Scanner_mask.jpg)](https://developer.valvesoftware.com/wiki/File:Scanner_mask.jpg)

Маска блика [npc_cscanner](https://developer.valvesoftware.com/wiki/Ru/Npc_cscanner "Ru/Npc cscanner")'а.

[$envmapmasktransform](https://developer.valvesoftware.com/w/index.php?title=Ru/$envmapmasktransform&action=edit&redlink=1 "Ru/$envmapmasktransform (page does not exist)")([en](https://developer.valvesoftware.com/wiki/$envmapmasktransform)) <[matrix](https://developer.valvesoftware.com/w/index.php?title=Ru/Matrix&action=edit&redlink=1 "Ru/Matrix (page does not exist)")([en](https://developer.valvesoftware.com/wiki/Matrix))> (DX9 SM2)

Трансформирует текстуру маски бликов.

Положение по умолчанию: `center .5 .5 scale 1 1 rotate 0 translate 0 0`.

1. `center` определяет центр вращения. Необходим только при использовании `rotate`.
2. `scale` вписывает текстуру в материал заданное количество раз. `2 1` - это 50%-ый масштаб по горизонтальной оси X, а размер по вертикальной оси Y остаётся исходным.
3. `rotate` вращение текстуры _против_ часовой стрелки в градусах. Возможны любые числовые значения, включая отрицательные.
4. `translate` сдвиг текстуры на указанную величину. Значение `.5` сдвинет текстуру на 50% размера. Указание 1 сдвинет текстуру на её размер, что фактически ничего не изменит.

**Примечание:**_Все значения_ должны быть указаны!

**Баг:**Масштабирование текстуры может вызвать странные проблемы, когда инструмент «Texture Lock» в Hammer фактически не фиксирует текстуру на месте.  [нужно проверить в [?](https://developer.valvesoftware.com/wiki/Template:BugNotice#Parameters "Template:BugNotice")]

**Баг:**Вращение текстур, покрывающих элементы карты, отсчитывается относительно начала координат карты. Чтобы исправить это, нужно изменить положение центра в VMT на точку отсчёта элемента карты.  [нужно проверить в [?](https://developer.valvesoftware.com/wiki/Template:BugNotice#Parameters "Template:BugNotice")]

[$envmapmaskscale](https://developer.valvesoftware.com/w/index.php?title=Ru/$envmapmaskscale&action=edit&redlink=1 "Ru/$envmapmaskscale (page does not exist)")([en](https://developer.valvesoftware.com/wiki/$envmapmaskscale)) <[число с плавающей запятой](https://developer.valvesoftware.com/wiki/Ru/Float "Ru/Float")> (DX8)

Масштабирует маску бликов до заданного значения. Смотреть `$envmapmasktransform` (выше).

[$envmapmaskframe](https://developer.valvesoftware.com/w/index.php?title=Ru/$envmapmaskframe&action=edit&redlink=1 "Ru/$envmapmaskframe (page does not exist)")([en](https://developer.valvesoftware.com/wiki/$envmapmaskframe)) <[целое число](https://developer.valvesoftware.com/wiki/Ru/Integer "Ru/Integer")>

Кадр для начала анимированной маски бликов.