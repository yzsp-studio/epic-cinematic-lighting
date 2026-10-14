# 场景类型光影图谱

> 按空间类型索引光影配置。当已知场景空间但不确定光影方案时查阅此表。
> 每个场景提供「默认光源配置」+「情绪可调参数」+「Prompt 模板」。

---

## 室内场景

### 卧室

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 窗光（自然光）或台灯/床头灯（夜间） |
| 色温范围 | 白天 5000-5600K / 夜间 2700-3200K |
| 光质 | 柔（窗帘过滤/灯罩漫射） |
| 默认光比 | 1:2~1:3 |
| 环境反射 | 暖色床单/木地板反射暖调补光 |
| Prompt 模板 | `Soft [morning/evening] light through sheer curtains from [direction], [warm/cool] [K]K, diffused and gentle, ratio 1:[N], [warm bounce from bedding / dim lamplight glow]` |

**情绪调节**：
- 温馨晨起 → 暖窗光 4500K + 低光比 1:2
- 失眠深夜 → 手机屏冷光 6500K + 全黑环境 1:10
- 亲密场景 → 烛光/台灯 2800K + 极柔 + 逆光轮廓

### 客厅/起居室

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 多窗自然光 + 室内灯具 |
| 色温范围 | 4500-5600K |
| 光质 | 中柔（窗户较大但有散射） |
| 默认光比 | 1:2（明亮通透） |
| 环境反射 | 墙面/家具大面积反射 |
| Prompt 模板 | `Bright living room with natural light from [large windows/glass doors], [K]K, open airy illumination ratio 1:[N], [warm wood floor bounce / cool wall reflections]` |

### 厨房/餐厅

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 顶灯 + 灶台/操作台局部光 |
| 色温 | 3500-4500K（暖白，食物友好） |
| 光质 | 中硬（操作灯定向）+ 柔环境 |
| 默认光比 | 1:2~1:3 |
| Prompt 模板 | `Kitchen lit by overhead pendant lamp [K]K casting downward pool on counter, warm ambient fill from [window/range hood], food surfaces reflecting warm tones, ratio 1:[N]` |

### 浴室

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 镜前灯 + 顶灯 |
| 色温 | 4000-5000K（偏白净） |
| 光质 | 半硬（镜面反射增加对比） |
| 特殊元素 | 镜面反射形成二次光源、瓷砖高光 |
| Prompt 模板 | `Bathroom mirror vanity light at [K]K from above face, reflective tile surfaces creating multiple light bounces, clinical white illumination, ratio 1:[N]` |

### 办公室/会议室

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 天花板面板灯（荧光/LED）+ 屏幕光 |
| 色温 | 5000-6000K（冷白办公） |
| 光质 | 极柔平（面光源） |
| 默认光比 | 1:1.5~1:2（几乎无影） |
| Prompt 模板 | `Flat overhead office panel lighting at [K]K, even corporate illumination with minimal shadows, computer screen glow adding cool accent on face, sterile and neutral, ratio 1:[N]` |

### 审讯室/密室

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 单一吊灯（裸灯泡）或顶部聚光灯 |
| 色温 | 5000-5600K（中性冷白） |
| 光质 | 硬（裸灯泡/聚光灯无柔化） |
| 默认光比 | 1:6~1:10（高对比） |
| Prompt 模板 | `Single bare overhead bulb [K]K casting harsh downward light, deep eye socket shadows, stark interrogation lighting, dark surrounding walls absorbing light, ratio 1:[N], oppressive` |

### 教堂/庙宇/神殿

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 高窗射入的自然光 + 烛火 |
| 色温 | 混合：窗光 5600K + 烛光 2000K |
| 光质 | 体积光（灰尘/烟雾中可见光柱） |
| 默认光比 | 1:4~1:6（大面积暗 + 光柱高亮） |
| Prompt 模板 | `Cathedral interior with volumetric shafts of light streaming through tall stained glass windows at 5600K, dust motes visible in beams, warm candlelight 2000K from altar creating secondary warm glow, vast dark vaulted ceiling, ratio 1:[N], sacred and awe-inspiring` |

### 酒吧/夜店

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 霓虹 + 酒架背光 + 环境LED |
| 色温 | 极端混合多色 |
| 光质 | 硬点光 + 彩色漫射 |
| 默认光比 | 1:4~1:6 |
| Prompt 模板 | `Neon-lit bar interior with [color] neon accents, warm amber backlit liquor shelf, cool blue LED strips, mixed color temperature creating vivid shadows, ratio 1:[N], moody nightlife atmosphere` |

---

## 室外场景

### 城市街道（白天）

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 太阳（直射或建筑遮挡） |
| 色温 | 5200-6000K |
| 光质 | 随时段变化：正午硬 / 黄金时段柔 |
| 特殊元素 | 建筑投影、车辆反射、玻璃幕墙反射光 |
| Prompt 模板 | `Urban street in [time of day] light at [K]K, [hard shadows from buildings / soft golden light between structures], [building reflections / asphalt heat haze], city architecture framing the light` |

### 城市街道（夜间）

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 路灯 + 店铺 + 车灯 + 霓虹 |
| 色温 | 极端混合 |
| 光质 | 多方向点光源 |
| 特殊元素 | 湿地面反射（雨后效果倍增） |
| Prompt 模板 | `Night street lit by mixed urban sources: [sodium/LED] streetlamp [K]K from above, [neon/shopfront] glow from sides, [wet pavement reflections doubling lights / dry concrete absorbing light], noir urban atmosphere, ratio 1:[N]` |

### 森林/树林

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 穿透树冠的阳光 |
| 色温 | 5200-5800K（树叶过滤偏绿） |
| 光质 | 斑驳碎光（天然 gobo） |
| 特殊元素 | 树叶 gobo 阴影、体积光柱 |
| Prompt 模板 | `Sunlight filtering through forest canopy creating dappled light pattern on ground and figure, visible volumetric rays through morning mist, warm-green filtered [K]K, natural gobo from leaves and branches, ratio 1:[N]` |

### 海边/湖边

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 太阳 + 水面反射(二次光源) |
| 色温 | 5200-6500K（水面反射偏冷蓝） |
| 光质 | 多方向（天空+水面两个大面光源） |
| 特殊元素 | 水面波光粼粼的动态反射光 |
| Prompt 模板 | `[Time of day] light at the [sea/lake]shore, sun at [K]K from [direction], water surface acting as secondary light source reflecting cool shimmer onto figure from below, sparkling light dancing across skin, ratio 1:[N]` |

### 沙漠/荒原

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 强烈直射阳光 |
| 色温 | 5800-6500K（紫外线偏蓝白） |
| 光质 | 极硬（无遮挡无散射） |
| 特殊元素 | 地面反射热浪、极长阴影（低角度时） |
| Prompt 模板 | `Harsh unfiltered desert sun at [K]K from [high angle/low angle], extreme hard shadows with sharp edges, hot sand reflecting warm bounce from below, [heat haze distortion / long dramatic shadow], high contrast ratio 1:[N], merciless exposure` |

### 雪景

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 天空漫射 + 雪面反射(巨型补光) |
| 色温 | 6000-8000K（偏冷蓝白） |
| 光质 | 极柔（雪面充当天然反光板） |
| 特殊元素 | 雪面高反射率导致光比极低、人物面部可能过亮 |
| Prompt 模板 | `Snow-covered landscape acting as giant reflector, cool ambient light [K]K from overcast sky, extremely low contrast from snow bounce, [blue shadows on snow / warm accent from [practical source]], crystalline cold atmosphere, ratio 1:[N]` |

---

## 特殊空间

### 车内

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 挡风玻璃/侧窗透入的外部光 + 仪表盘 |
| 色温 | 混合：外部光色温 + 仪表盘 4000-5000K |
| 光质 | 窗框 gobo + 变化光（经过建筑/树木时光影闪烁） |
| Prompt 模板 | `Interior car lighting: [daylight/streetlight] filtering through windshield and side windows, dashboard instruments casting subtle [warm/cool] glow on lower face, shifting light-shadow pattern as car moves past [trees/buildings/streetlamps]` |

### 电梯

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 顶部面板灯 |
| 色温 | 4000-5000K |
| 光质 | 平、均匀、无逃脱 |
| 特殊元素 | 金属壁面反射、封闭感、镜面多角度反射 |
| Prompt 模板 | `Enclosed elevator interior with flat overhead panel light at [K]K, metallic walls creating multiple reflections and secondary light sources, claustrophobic even illumination, nowhere to hide in shadow, ratio 1:[N]` |

### 隧道/地下通道

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 间隔荧光灯 / 隧道口自然光 |
| 色温 | 荧光灯 4000-5000K / 远处出口 5600K |
| 光质 | 间歇性（灯与灯之间有暗区）|
| 特殊元素 | 明暗交替节奏、尽头光源（希望/危险） |
| Prompt 模板 | `Underground tunnel with rhythmic overhead [fluorescent/sodium] lights at [K]K creating alternating bright and dark zones, [distant daylight at tunnel end / absolute darkness ahead], damp walls with subtle reflections, ratio shifts between 1:2 and 1:8 as figure moves between light pools` |

### 舞台/表演空间

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 聚光灯(Spotlight) + 面光 + 侧光 |
| 色温 | 可控全范围 |
| 光质 | 从极硬聚光到柔面光 |
| 特殊元素 | 黑色背景吞噬环境、烟雾机增强体积光 |
| Prompt 模板 | `Stage spotlight at [K]K [from above/from front], performer isolated in pool of light against black void, [haze machine creating visible beam / clean sharp spotlight edge], theatrical dramatic ratio 1:[N]` |

### 水下

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 水面上方的阳光/月光，经水面折射 |
| 色温 | 6000-8000K（水体吸收暖色，偏蓝绿） |
| 光质 | 极柔漫射 + 焦散光斑(caustics) |
| 特殊元素 | 波纹光斑在物体表面舞动、随深度增加光线衰减、气泡散射 |
| Prompt 模板 | `Underwater lighting: sunlight filtering through water surface creating dancing caustic light patterns, blue-green color shift at [K]K, light intensity decreasing with depth, [air bubbles catching light / bioluminescent glow], ratio 1:[N]` |

### 太空/零重力

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 恒星直射（无大气散射=极硬极亮） |
| 色温 | 5800K（太阳）但无大气过滤，呈纯白 |
| 光质 | 极硬无衰减、阴影绝对漆黑（无大气散射补光） |
| 特殊元素 | 明暗交界线极锐利、无渐变过渡、地球反射光(Earthshine)为冷蓝补光 |
| Prompt 模板 | `Space lighting: harsh unfiltered sunlight at 5800K from [direction], absolute razor-sharp shadow line with zero gradation, shadow side in complete vacuum-black, [cool blue Earthshine providing faint fill / starfield in background], no atmosphere, no diffusion, ratio 1:[extreme]` |

### 虚拟/数字空间

| 要素 | 默认配置 |
|------|---------|
| 主要光源 | 无物理约束——自发光表面/数据流/全局辉光 |
| 色温 | 不受限（常用霓虹蓝/洋红/青色/矩阵绿） |
| 光质 | 可违反物理（无衰减发光/无影光源/自发光物体） |
| 特殊元素 | 物体自发光、网格线发光、数据粒子光源、全息投影光 |
| Prompt 模板 | `Virtual space lighting: [neon blue/cyan/magenta] self-luminous surfaces, objects emitting their own glow with no natural light source, [holographic projections / glowing data streams / luminous grid lines], physically impossible lighting with no shadows or inverted shadows, digital surreal atmosphere` |
