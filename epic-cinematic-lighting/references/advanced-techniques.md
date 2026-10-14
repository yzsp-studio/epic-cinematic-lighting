# 高阶光影技法详细参数

> 本文件是 SKILL.md STEP 2「Tier 2 高阶史诗光影」的展开参考。
> 包含每种技法的详细参数、变体、AI 模型适配注意事项和扩展 prompt 示例。

---

## 1. 体积光 (Volumetric Light)

### 原理
光线穿过含有微粒的空气（烟雾/灰尘/雾气/水汽），形成肉眼可见的光束。

### 参数控制

| 参数 | 低密度（柔和） | 中密度（电影级） | 高密度（史诗级） |
|------|-------------|---------------|---------------|
| 介质 | 轻雾 / 自然灰尘 | 烟雾 / 薄雾 | 浓雾 / 烟 / 蒸汽 |
| 光束可见度 | 隐约可见 | 清晰光柱 | 强烈光幕 |
| 光源类型 | 自然光（窗户/门缝） | 聚光灯/高窗 | 太阳直射/巨型光源 |
| Prompt 修饰 | `faint light rays, subtle haze` | `visible light beams, dusty atmosphere` | `dramatic god rays, thick volumetric shafts of light` |

### 变体

| 变体名称 | 效果 | Prompt 关键词 |
|---------|------|--------------|
| God Rays / 丁达尔效应 | 从高处穿透云层/树冠/窗户的光柱 | `god rays streaming through clouds/canopy/stained glass` |
| 尘埃微光 | 空气中浮尘被侧光照亮 | `visible dust motes floating in shaft of light` |
| 雾中光束 | 雾气中扩散的光锥 | `light beam diffusing through fog, wide cone of illumination` |
| 烟雾弥漫 | 烟雾中的环境漫射 | `smoke-filled room with light scattering through haze` |
| 水下焦散 | 水面折射光斑 | `underwater caustic light patterns dancing on surfaces` |

### AI 模型适配

| 模型 | 体积光响应 | 注意事项 |
|------|----------|---------|
| Seedance 2.0 | ★★★★ 好 | 写明介质类型（dust/fog/smoke），否则可能生成纯光斑 |
| Kling | ★★★ 中 | 静态体积光效果好，动态光束易闪烁 |
| Veo3 | ★★★★ 好 | 可同时描述光的声音效果（如风声吹动尘埃） |
| Wan | ★★★ 中 | I2V 模式下首帧需已含体积光线索 |

---

## 2. 明暗对比法 (Chiaroscuro)

### 原理
极端的明暗对比，源自卡拉瓦乔(Caravaggio)和伦勃朗的绘画传统。主体被强光照亮，背景和周围沉入深黑。

### 参数控制

| 参数 | 轻度 | 标准 | 极端 |
|------|------|------|------|
| 光比 | 1:6 | 1:8~1:10 | 1:12+ |
| 背景亮度 | 深灰可辨 | 接近纯黑 | 绝对纯黑 |
| 高光面积 | 面部 50%+ | 面部 30-40% | 面部 < 25% |
| 阴影过渡 | 有过渡带 | 窄过渡 | 几乎无过渡（硬切） |
| Prompt 修饰 | `chiaroscuro-inspired, visible shadows` | `chiaroscuro lighting, deep blacks, bright highlights` | `extreme chiaroscuro, Caravaggio-level contrast, face emerging from absolute darkness` |

### AI 模型适配

| 模型 | 响应 | 注意事项 |
|------|------|---------|
| Seedance 2.0 | ★★★★ | 写明 ratio 数值 + 背景明确为 dark/black，效果稳定 |
| Kling | ★★★★ | 极端对比表现好，用 "deep blacks, bright highlights" 强化 |
| Veo3 | ★★★ | 8s 内保持高对比稳定，但暗部可能出现噪点闪烁 |
| Wan | ★★★ | 首帧必须已呈现高对比状态，prompt 仅维持不要试图从平光变化到 chiaroscuro |

### 与黑色电影(Film Noir)的区别

| 维度 | Chiaroscuro | Film Noir |
|------|------------|-----------|
| 光源 | 单一强方向光 | 多光源（百叶窗/霓虹/路灯） |
| 阴影 | 深但「干净」 | 复杂纹理阴影（百叶窗条纹等） |
| 色温 | 暖（油画感）或中性 | 冷（城市夜晚） |
| 情绪 | 内省、道德、神圣 | 犯罪、腐败、疲惫 |
| Prompt 区别 | `chiaroscuro, oil painting light, Renaissance-inspired` | `noir lighting, venetian blind shadows, neon-lit rain, cynical` |

---

## 3. 负补光 (Negative Fill)

### 原理
使用黑色旗板/吸光材料主动削减环境反射光，让阴影更深更黑。与「不加补光」不同——负补光是**主动吸收**已有的环境光。

### 何时使用
- 场景有大量环境反射光（白墙/浅色地板）但需要深阴影
- 需要「干净的黑」而非「灰蒙蒙的暗」
- 悬疑/孤独/内省场景的阴影加深

### Prompt 写法

```
# 错误：只是说不加补光
no fill light on shadow side

# 正确：主动描述吸光效果
negative fill on shadow side absorbing all bounce light,
shadow areas rendered as deep pure black with no reflected
ambient, creating stark separation between lit and unlit areas
```

### 组合建议

| 搭配 | 效果 | 示例场景 |
|------|------|---------|
| 伦勃朗 + 负补光 | 经典三角光 + 暗侧纯黑 | 深夜独白 |
| 窗光 + 负补光 | 自然单侧 + 对侧死黑 | 雨天窗边沉思 |
| 分割光 + 负补光 | 半脸全黑半脸全亮 | 身份危机/双面人 |

### AI 模型适配

| 模型 | 响应 | 注意事项 |
|------|------|---------|
| Seedance 2.0 | ★★★ | 需明确写 "absorbing bounce light, pure black shadows"，否则仍有轻微补光 |
| Kling | ★★★ | 效果类似，写 "no reflected light, absolute dark" |
| Veo3 | ★★★ | 整体响应中等，暗部保持纯黑较好 |
| Wan | ★★ | I2V 首帧需已有负补光效果，纯 prompt 描述难以从有补光变为无补光 |

---

## 4. 色温对比 (Mixed Color Temperature)

### 原理
同一画面中存在两种或以上不同色温的光源，制造视觉张力和叙事深度。

### 经典组合

| 组合 | 色温 | 情绪 | 典型场景 | Prompt |
|------|------|------|---------|--------|
| 暖内冷外 | 室内 3200K / 窗外 7000K | 安全与威胁对比 | 夜间室内看窗外 | `warm interior lamp light 3200K on face, cold blue moonlight 7500K from window behind, color temperature clash` |
| 冷上暖下 | 天花板 6500K / 桌面灯 3000K | 制度与人性 | 审讯室/医院 | `cold overhead fluorescent 6500K washing out surroundings, warm desk lamp 3000K creating intimate pool on face and hands` |
| 霓虹混合 | 多色点光源 | 迷乱、都市、赛博 | 夜店/东京街头 | `neon-lit scene with pink light from left, cyan light from right, warm yellow streetlamp from above, chaotic color temperature mixing` |
| 火光冷夜 | 火焰 2000-2500K / 夜空 8000K+ | 原始温暖 vs 荒野寒冷 | 营地/野外 | `warm orange campfire glow 2200K from below, cold night sky ambient 8000K+ from above, stark warm-cool contrast on face` |

### AI 模型适配

| 模型 | 色温对比响应 | 最佳写法 |
|------|------------|---------|
| Seedance 2.0 | ★★★★ | 写具体 K 值 + 光源位置 + 颜色词 |
| Kling | ★★★ | 用颜色词（warm amber / cool blue）优于 K 值 |
| Veo3 | ★★★★ | 可加声音线索辅助（如荧光灯嗡嗡声暗示冷光） |
| Wan | ★★★ | 首帧需已含色温线索，prompt 描述变化即可 |

---

## 5. 纹理投影 (Gobo / Cookie)

### 原理
光线通过遮挡物（百叶窗/树叶/栏杆/花纹窗棂）投射图案阴影到主体或环境上。

### 常用图案

| 遮挡物 | 投影效果 | 情绪 | Prompt |
|--------|---------|------|--------|
| 百叶窗 | 水平条纹 | 窥探、监禁、noir | `venetian blind shadow stripes across face and wall` |
| 树叶/枝干 | 有机碎斑 | 自然、平静、隐藏 | `dappled leaf shadow patterns from overhead foliage, organic light-dark mosaic` |
| 窗框十字 | 十字格阴影 | 孤独、等待、静谧 | `window frame cross shadow falling on floor and subject` |
| 铁栏杆/栅栏 | 垂直线条 | 囚禁、阻隔、危险 | `prison bar shadow lines striping across face` |
| 花纹窗棂/教堂玻璃 | 复杂几何 | 神圣、异域、高贵 | `intricate stained glass shadow patterns casting colored geometric shapes` |
| 旋转风扇 | 间歇闪烁（视频） | 审讯、紧张、时间流逝 | `rotating ceiling fan blade shadows sweeping across scene rhythmically` |

### AI 模型适配

| 模型 | 图片响应 | 视频响应 | 注意事项 |
|------|---------|---------|---------|
| Seedance 2.0 | ★★★★ | ★★★ | 静态 gobo 优秀；动态（风扇旋转）需首帧已含阴影图案 |
| Kling | ★★★★ | ★★ | 图片精确；视频中动态阴影可能闪烁或消失 |
| Veo3 | ★★★★ | ★★★ | 百叶窗/窗框效果好，可配合声音线索增强 |
| Wan | ★★★ | ★★ | 首帧必须已有阴影图案，prompt 描述保持即可 |

---

## 6. 实用光源叙事 (Practical Lighting)

### 原理
画面中可见的光源（台灯/烛光/手机屏/霓虹灯牌/车灯/电视）同时充当叙事道具和布光工具。

### 实用光源库

| 光源 | 色温 | 光质 | 叙事含义 | Prompt 关键词 |
|------|------|------|---------|--------------|
| 蜡烛/油灯 | 1800-2200K | 极暖、摇曳、微弱 | 亲密、原始、脆弱 | `candlelight flickering, warm amber 2000K, dancing shadows` |
| 台灯 | 2700-3500K | 暖、定向、有限范围 | 工作、专注、孤独 | `desk lamp casting warm directional pool of light, 3000K` |
| 壁炉/篝火 | 2000-2500K | 暖橙、跳动、底光 | 温暖、故事、原始 | `firelight glow from below, warm orange 2200K, flickering` |
| 手机/平板屏幕 | 6000-7000K | 冷蓝白、正面近距 | 现代、孤独、失眠 | `phone screen glow illuminating face from below in cool blue-white 6500K` |
| 电视/显示器 | 变化 | 变化色彩、闪烁 | 被动、麻木、信息 | `TV screen casting shifting colored light on face, alternating warm and cool` |
| 霓虹灯牌 | 单色 (红/蓝/粉/绿) | 硬、单色、恒定 | 都市、欲望、人造 | `neon sign glow in [color], hard colored light from shopfront` |
| 路灯(钠灯) | 2200-2700K | 暖橙、顶光、有限锥形 | 都市夜晚、孤独、等待 | `sodium streetlamp casting warm orange cone of light from above, 2500K` |
| 路灯(LED) | 4000-5500K | 冷白、均匀、现代 | 清冷、现代、监控 | `modern LED streetlamp cold white light 5000K, clinical illumination` |
| 车灯(远光) | 5000-6000K | 强、平行、移动 | 危险、暴露、闯入 | `car headlights sweeping across scene, harsh white beams 5500K` |
| 闪电 | 6500-8000K | 极强瞬间、全方位 | 恐惧、启示、混乱 | `brief lightning flash illuminating everything in cold blue-white 7000K, then darkness` |
| 火柴/打火机 | 1800-2000K | 极弱、极暖、短暂 | 希望微光、短暂 | `match flame tiny warm glow 1900K, illuminating only inches of surrounding darkness` |

### 纯实用光源场景写法

当场景完全由实用光源照明（无外部布光）：

```
Lit entirely by practical sources within the scene:
[primary practical] as key light,
[secondary practical] providing fill/accent,
no external lighting, no studio lights,
all illumination motivated by visible in-frame sources
```

**示例**（深夜书房）：
```
Lit entirely by practical sources: warm desk lamp 3000K as key
from upper-left casting directional pool on books and hands,
faint cool laptop screen glow 6500K providing subtle front fill
on face, warm embers from dying fireplace 2000K creating soft
amber ambience from lower-right. No external lighting. All shadows
motivated by these three visible sources.
```

### AI 模型适配

| 模型 | 响应 | 注意事项 |
|------|------|---------|
| Seedance 2.0 | ★★★★ | 对可见光源（烛光/台灯/霓虹）响应好，写明光源在画面中的位置 |
| Kling | ★★★ | 烛光/火光摇曳效果好，霓虹色彩准确度中等 |
| Veo3 | ★★★★★ | 最佳——可同时描述光源发出的声音（蜡烛噼啪/荧光灯嗡嗡），视听一体 |
| Wan | ★★★ | 首帧需已含可见光源，prompt 描述光源的动态效果（摇曳/闪烁）|

---

## 7. 光线演变 (Light Shift) — 视频专用

### 原理
光影状态在视频时间轴上发生有设计的变化，服务于情绪转折或时间叙事。

### 演变模式

| 模式 | 描述 | 适用场景 | Prompt 结构 |
|------|------|---------|------------|
| 渐变(Gradual) | 光影在整段视频中缓慢变化 | 日落、情绪渐变 | `lighting gradually shifts from [A] to [B] over the duration` |
| 触发(Triggered) | 因角色动作/事件导致光影突变 | 开灯、拉窗帘、爆炸 | `when [event], lighting abruptly changes from [A] to [B]` |
| 循环(Cyclic) | 光影有节奏地反复变化 | 霓虹闪烁、灯塔旋转 | `rhythmic light pulsing between [A] and [B] every N seconds` |
| 层进(Escalating) | 光影变化逐步加强 | 紧张升级、暴风雨来临 | `lighting contrast progressively intensifies from ratio 1:2 to 1:8` |

### 视频光影时间轴模板

```
[0s]: 初始光影状态（详细描述）
[Ns]: 触发事件 / 过渡中点
[末尾]: 最终光影状态（详细描述）
变化方式：gradual / triggered / cyclic / escalating
```

**示例**（10s 角色从希望到绝望）：
```
[0-3s]: Warm golden hour light from window at 3800K, ratio 1:2,
soft and hopeful, gentle fill from interior bounce.
[3-7s]: Light gradually cools and dims as clouds cover the sun,
shifting from 3800K to 6000K, ratio tightening from 1:2 to 1:5,
shadows deepening on face.
[7-10s]: Cold overcast light at 7000K, ratio 1:6, flat and bleak,
warm tones completely absent, desaturated harsh reality.
Change: gradual continuous shift in color temperature and intensity.
```

### AI 模型适配

| 模型 | 响应 | 注意事项 |
|------|------|---------|
| Seedance 2.0 | ★★★★ | 渐变(Gradual)和触发(Triggered)效果好，6-10s 内光影变化自然 |
| Kling | ★★★ | 渐变效果中等，触发型（开灯/爆炸）效果好 |
| Veo3 | ★★★★ | 8s 内渐变流畅，可用 first+last frame 锚定起止光影状态 |
| Wan | ★★ | 15s 内渐变可能不完整，建议拆成多段 5s 分别控制 |
