---
name: epic-cinematic-lighting
version: 1.0.0
description: >
  史诗级电影光影设计专家。根据分镜/剧情/场景，自动选择布光方案，
  输出可直接嵌入 AI 图片或视频 prompt 的精确光影描述。
  Tier 1 基础：三点布光变体、情绪光比映射、光线方向八式、时段光线、low-key/high-key；
  Tier 2 高阶：体积光、明暗对比(Chiaroscuro)、负补光、色温对比、纹理投影(Gobo)、实用光源叙事。
  内置「剧情→光影配方」速查，双用途适配图片与视频。
  触发词：光影设计、布光方案、lighting design、cinematic lighting、
  epic lighting、光影配方、三点布光、Rembrandt lighting、split lighting、
  rim light/轮廓光、backlight/逆光、体积光/volumetric light/god rays、
  chiaroscuro/明暗对比、negative fill/负补光、色温/color temperature、
  golden hour/blue hour、low-key、high-key、practical lighting、
  让光影更电影感、光线太平、光影不够好、布光太平。
  NOT for：后期调色/LUT（用调色工具）、3D渲染引擎布光（用3D工具）、
  舞台DMX灯控、纯色彩理论（用 color-vocabulary）。
summary-cn: 史诗级电影光影设计——根据剧情场景自动选择布光方案，输出可直接嵌入 prompt 的精确光影描述
summary-en: Epic cinematic lighting designer — auto-selects lighting setups from story/scene context, outputs prompt-ready light descriptions
tags: [Image, Video, lighting, cinematography, visual-design, prompt-engineering]
tags-cn: [图片, 视频, 光影, 电影摄影, 布光]
trigger-words: [光影设计, 布光方案, lighting design, cinematic lighting, epic lighting, 光影配方, 三点布光, Rembrandt lighting, split lighting, 轮廓光, rim light, 逆光, backlight, 体积光, volumetric light, god rays, 明暗对比, chiaroscuro, 负补光, negative fill, 色温, color temperature, golden hour, blue hour, low-key, high-key, practical lighting, 让光影更电影感, 光线太平, 光影不够好, 布光太平]
author: yzsp-ai
repository: https://github.com/yzsp-ai
---


# 史诗级电影光影设计 Skill

> **定位**：将电影摄影学(Cinematography)的布光体系转化为 AI 可理解的光影描述，
> 让每一帧画面都有「被设计过的光」而非「默认均匀光」。

## 边界守卫

本 Skill 专注于**光影设计与布光描述**。以下请求不在范围内：

- 后期调色/LUT → 建议使用调色工具或色彩参考文件
- 3D 渲染引擎灯光参数 → 建议使用对应 3D 工具
- 舞台实体灯光控制 → 建议查阅 DMX 控台手册
- 纯色彩搭配理论 → 建议参考 color-vocabulary 知识库

---

## 铁律（6 条）

| # | 铁律 | 原因 |
|---|------|------|
| 1 | **禁止使用 "cinematic lighting" 作为唯一光影描述** | AI 模型对此通用词无差别响应，等于没写。必须指定具体光源类型+方向+质感 |
| 2 | **每个场景至少声明 3 个光影要素：光源类型 + 光线方向 + 光影比例/强度** | 缺任一要素，AI 会用默认均匀光填充，失去电影感 |
| 3 | **光影描述用物理语言，禁用文学修辞** | ✗「如梦似幻的光芒」→ ✓「soft diffused key light from upper-left at 45°, fill ratio 1:4, warm 3200K」 |
| 4 | **同一项目/序列的光影必须锁定一致性参数** | 光源方向、色温基调、光比范围在同序列中保持一致，否则剪辑后光影跳跃 |
| 5 | **先确定光影方案，再写其他 prompt 内容** | 光影决定画面 60% 的情绪基调。后补光影 = 光影沦为装饰而非叙事 |
| 6 | **双媒介适配：图片 prompt 写完整参数，视频 prompt 写光影变化过程** | 图片是瞬间光影状态；视频需要描述光影在时间轴上的演变（如「light gradually shifts from warm to cool」）|

---

## 反模式表

| 反模式 | 为什么翻车 | 正确做法 |
|--------|-----------|---------|
| 只写 "dramatic lighting" | 模型理解为随机加对比度，无方向性 | 写 "strong key light from camera-left at 30° with deep shadows on the right side, ratio 1:8" |
| 写 "perfect lighting" | AI 倾向生成无瑕疵的均匀光，失去质感 | 写具体光源 + 刻意加入 light falloff / spill / flare 等不完美元素 |
| 光影与情绪矛盾 | 悬疑场景写 "bright even lighting" → 紧张感归零 | 查阅 Tier 1 情绪光比映射表，匹配正确方案 |
| 多光源但不分主次 | AI 无法判断哪个是主光，生成光影混乱 | 明确标注 key/fill/back 层级：「key light from left (strongest), fill light from right (1/4 intensity), rim light from behind」 |
| 图片和视频用同一句光影描述 | 图片需要瞬间状态，视频需要时间变化 | 图片：「Rembrandt lighting, warm key from upper-left」；视频：同句 + 「light slowly intensifies as character steps forward」 |
| 忽略环境反射光 | 室内/近物场景缺少反射光 → 暗部死黑不自然 | 补充环境光描述：「warm bounce light from the wooden floor」「cool reflected light from the blue wall」 |
| 堆砌 5+ 种灯光类型 | 超出 AI 模型实际可控范围，生成混乱 | 最多 3 种光源层级（key + fill + accent），Tier 2 技法叠加不超过 2 种 |

---

## STEP 0：场景分析 → 光影方案自动选择

收到场景/分镜/剧情描述后，按以下决策树选择光影层级：

```
输入：场景描述 / 分镜脚本 / 情绪关键词
  │
  ├─ 提取 3 要素：❶ 场景类型  ❷ 情绪基调  ❸ 时间/空间
  │
  ├─ 查表：→ references/lighting-recipes.md（剧情类型×情绪 → 配方）
  │         → references/scene-lighting-atlas.md（场景空间 → 光源配置）
  │
  ├─ 判断层级：
  │   ├─ 日常/对话/解释性场景 → Tier 1 基础方案（够用即止）
  │   ├─ 情绪转折/高潮/视觉冲击场景 → Tier 2 高阶方案
  │   └─ 不确定 → 默认 Tier 1，标注「可升级 Tier 2」
  │
  ├─ Fallback（用户未提供情绪/场景信息时）：
  │   默认 = 标准三点布光, 5600K 日光, 光比 1:2, 柔光质感
  │   输出时标注「已使用默认中性光影方案，如需调整请提供场景情绪」
  │
  └─ 输出：完整光影描述（可直接粘贴到 prompt）
```

---

## STEP 1：Tier 1 基础史诗光影

> **目标**：让 AI 生成的画面从「默认均匀光」升级到「有设计感的电影光」。
> **适用**：所有场景的基础配置，日常/对话/解释性场景的完整方案。

### 1.1 三点布光法及变体

| 布光类型 | 主光(Key) | 补光(Fill) | 轮廓光(Back/Rim) | 情绪效果 | Prompt 关键词 |
|---------|-----------|-----------|-----------------|---------|--------------|
| 标准三点 | 45° 侧上方 | 对侧平光 1:2 | 正后方 | 均衡、专业 | `standard three-point lighting, key light 45° upper-left, fill from right at half intensity, backlight rim` |
| 伦勃朗光(Rembrandt) | 45° 侧上方 | 极弱或无 1:4~1:8 | 可选 | 戏剧性、内省 | `Rembrandt lighting, triangular shadow on cheek, strong key from upper-left, minimal fill, ratio 1:4` |
| 分割光(Split) | 正侧方 90° | 无 | 可选 | 对立、冲突 | `split lighting, half face in shadow half illuminated, key light at 90° from left` |
| 蝶光(Butterfly/Paramount) | 正上方鼻尖 | 下方反射 | 两侧轮廓 | 优雅、魅力 | `butterfly lighting, key light directly above, symmetrical nose shadow, glamour style` |
| 环形光(Loop) | 30-45° 微偏 | 对侧柔光 | 可选 | 自然、亲和 | `loop lighting, small shadow from nose angled to cheek, soft key from 30° left` |
| 宽光(Broad) | 朝向镜头的脸侧 | 暗侧极弱 | 对侧 | 脸显宽、开放 | `broad lighting, illuminated side facing camera, shadow side away` |
| 窄光(Short) | 远离镜头的脸侧 | 近侧极弱 | 可选 | 脸显瘦、神秘 | `short lighting, shadow side facing camera, key on far cheek` |

### 1.2 情绪 → 光比映射表

| 情绪基调 | 光比(Key:Fill) | 阴影密度 | 色温方向 | 典型场景 |
|---------|---------------|---------|---------|---------|
| 温暖/治愈 | 1:2 (柔和) | 低，阴影透亮 | 暖色 3200-4000K | 家庭团聚、回忆、治愈 |
| 中性/叙事 | 1:2~1:3 | 中等 | 日光 5600K | 日常对话、解释、过渡 |
| 紧张/悬疑 | 1:4~1:8 (硬朗) | 高，深黑阴影 | 冷色 6500-8000K | 审讯、跟踪、秘密 |
| 浪漫/梦幻 | 1:1~1:2 | 极低，几乎无影 | 暖偏粉 3500K | 约会、初恋、幻想 |
| 压迫/恐惧 | 1:8+ (极端) | 极高，面部大面积黑 | 冷偏绿 7000K+ | 恐怖、囚禁、绝望 |
| 权力/威严 | 1:4~1:6 | 高，但有控制 | 中性偏冷 5000-6000K | 王座、审判、CEO |
| 孤独/忧郁 | 1:3~1:5 | 中高 | 冷蓝 7000K | 雨夜、空房间、离别 |
| 喜悦/活力 | 1:1~1:2 | 极低 | 暖色 4000-5000K | 庆祝、运动、晨跑 |

### 1.2b Low-key / High-key 整体光调

| 光调 | 定义 | 光比范围 | 画面特征 | 适用场景 | Prompt 关键词 |
|------|------|---------|---------|---------|--------------|
| Low-key | 画面整体偏暗，大面积阴影，仅关键区域亮 | 1:4~1:8+ | 暗调为主，高对比，深沉 | 悬疑、恐怖、黑色电影、权力、内省 | `low-key lighting, predominantly dark frame, selective highlights, deep shadows dominating` |
| High-key | 画面整体明亮，阴影极少，色调轻盈 | 1:1~1:2 | 亮调为主，低对比，轻快 | 喜剧、广告、时尚、梦境、天堂 | `high-key lighting, bright even illumination, minimal shadows, airy and clean` |

> Low-key/High-key 是**整体光调方向**，与具体布光类型（伦勃朗/分割/蝶光）正交使用。
> 例如：Low-key + 伦勃朗 = 暗调戏剧肖像；High-key + 蝶光 = 明亮时尚大片。

### 1.3 光线方向八式

| 方向 | 角度 | 效果 | 适用场景 | Prompt 片段 |
|------|------|------|---------|------------|
| 顺光(Front) | 0° 正面 | 平坦、清晰、无戏剧性 | 证件照、产品展示 | `flat front lighting, even illumination` |
| 侧光(Side) | 90° | 质感强、轮廓突出 | 肖像、雕塑感 | `hard side light from left, strong texture and form` |
| 45° 斜光 | 45° | 最通用、立体感好 | 绝大多数叙事场景 | `key light at 45 degrees from upper-left` |
| 逆光(Back) | 180° | 剪影、轮廓描边、神圣感 | 英雄登场、告别、神秘 | `strong backlight creating silhouette, rim light outlining figure` |
| 顶光(Top) | 90° 正上方 | 审判感、宿命、压迫 | 审讯室、舞台聚光灯 | `overhead top light casting deep eye shadows, theatrical` |
| 底光(Under) | -90° 下方 | 诡异、恐怖、反常 | 恐怖片、营火故事 | `under-lighting from below, casting upward shadows, eerie` |
| 伦勃朗角(Rembrandt) | 45° 上+45° 侧 | 经典三角形面影 | 人物内心独白 | `Rembrandt angle, triangle of light on shadowed cheek` |
| 边缘光(Kicker/Edge) | 135-160° 后侧 | 将主体从背景分离 | 任何需要主体突出的场景 | `edge light from behind-left, separating subject from background` |

### 1.4 时段光线系统

| 时段 | 色温 | 光线特征 | 情绪关联 | Prompt 关键词 |
|------|------|---------|---------|--------------|
| 黎明(Dawn) | 2500-3500K | 极柔、低角度、长影 | 希望、新生、宁静 | `pre-dawn light, soft warm glow on horizon, long gentle shadows` |
| 黄金时段(Golden Hour) | 3000-4000K | 暖金、低角度侧射 | 怀旧、浪漫、温馨 | `golden hour sunlight, warm amber rays at low angle, long shadows` |
| 正午(High Noon) | 5500-6000K | 硬顶光、短影、高对比 | 暴露、对峙、残酷 | `harsh noon sun directly overhead, short sharp shadows, high contrast` |
| 蓝调时刻(Blue Hour) | 7000-10000K | 冷蓝均匀、无明确方向 | 忧郁、反思、神秘 | `blue hour ambient light, cool desaturated tones, no direct sunlight` |
| 夜间人造光 | 混合色温 | 点状、多方向、色温混杂 | 都市、孤独、危险 | `artificial night lighting, mixed color temperatures, neon warm-cool contrast` |
| 阴天(Overcast) | 6000-7000K | 极柔漫射、无影、平光 | 平静、压抑、沉思 | `overcast diffused daylight, soft even illumination, no hard shadows` |
| 暴风雨 | 5000-7000K | 间歇闪光+暗基底 | 危机、转折、情绪爆发 | `storm light, dark base illumination with intermittent lightning flashes` |

---

## STEP 2：Tier 2 高阶史诗光影

> **目标**：在 Tier 1 基础上叠加高阶技法，实现电影大师级视觉冲击。
> **适用**：情绪转折、高潮、主视觉、海报级画面。
> **铁律**：Tier 2 技法叠加不超过 2 种，与 Tier 1 基础方案组合使用。

> 详细参数和扩展用例见 `references/advanced-techniques.md`。

### 2.1 高阶技法速查表

| 技法 | 核心效果 | 何时使用 | Prompt 核心片段 | 叠加上限 |
|------|---------|---------|----------------|---------|
| 体积光(Volumetric) | 可见光束、空气中的光 | 神圣、史诗、森林、教堂 | `volumetric light rays, visible beams cutting through haze/dust/fog` | 单独或 +1 |
| 明暗对比(Chiaroscuro) | 极端明暗、卡拉瓦乔式 | 道德抉择、内心冲突、权力 | `chiaroscuro lighting, extreme contrast, deep blacks against bright highlights, Caravaggio-inspired` | 单独 |
| 负补光(Negative Fill) | 主动削减补光、加深阴影 | 悬疑、孤独、内省 | `negative fill on shadow side, deep unlit shadows, no bounce light` | +Tier 1 任一 |
| 色温对比(Mixed Temp) | 冷暖光源同画面对撞 | 冲突、过渡、都市 | `warm practical light 3200K from left, cool moonlight 7500K from right window` | +Tier 1 任一 |
| 纹理投影(Gobo/Cookie) | 通过遮挡物投射图案阴影 | 窗户光斑、百叶窗、树影 | `gobo shadow patterns from venetian blinds falling across face and wall` | +Tier 1 任一 |
| 实用光源叙事(Practical) | 画面内可见光源驱动布光 | 台灯/烛光/手机/霓虹 | `lit only by practical sources: a desk lamp casting warm pool of light, phone screen illuminating face with cool glow` | 单独或 +1 |
| 光线演变(Light Shift) | 光影在时间轴上变化（视频专用） | 情绪转折、时间流逝 | `lighting gradually shifts from warm golden to cold blue as the mood darkens` | 视频专用 |

### 2.2 Tier 2 组合规则

```
基本原则：Tier 1 基础方案 + 最多 2 种 Tier 2 技法
```

| 合法组合示例 | 场景 |
|------------|------|
| 伦勃朗光 + 体积光 | 教堂忏悔：侧光打出面部三角 + 窗户射入可见光束 |
| 分割光 + 负补光 | 审讯室：正侧硬光 + 暗侧完全无补光 |
| 标准三点 + 色温对比 | 办公室夜戏：冷色荧光灯 + 暖色台灯 |
| 逆光 + 实用光源 | 酒吧告别：吧台霓虹勾勒轮廓 + 烛光照脸 |

| 非法组合（禁止） | 原因 |
|----------------|------|
| 明暗对比 + 体积光 + 色温对比 | 3 种 Tier 2 叠加，超出 AI 可控范围 |
| 蝶光 + 明暗对比 | 蝶光追求均匀对称，与极端明暗矛盾 |
| 顺光 + 负补光 | 顺光无阴影可供削减，负补光无意义 |

---

## STEP 3：输出格式

### 3.1 图片 prompt 光影模块

```
[Lighting]: [光源类型] from [方向+角度], [色温/颜色], [光比/强度],
[补光描述], [轮廓光/环境光], [Tier 2 技法(如有)],
[光影质感修饰: soft/hard/diffused/specular]
```

**示例**（悬疑人物肖像）：
```
Rembrandt lighting with strong key light from upper-left at 45°,
color temperature 5600K, ratio 1:6 with minimal fill,
subtle rim light from behind-right separating subject from dark background,
negative fill on shadow side creating deep blacks,
hard light quality with sharp shadow edges
```

### 3.2 视频 prompt 光影模块

在图片基础上增加**时间维度**：

```
[Static lighting base]: [同图片格式]
[Light evolution]: [光影随时间/动作的变化描述]
```

**示例**（角色走进房间 10s）：
```
Scene opens in silhouette with strong backlight from doorway (ratio 1:8).
As character steps forward, warm practical lamp light (3200K) gradually
reveals face from the left side. By mid-scene, lighting transitions to
Rembrandt pattern with the lamp as key. Soft ambient bounce from wooden
floor provides subtle fill. Light quality shifts from hard to soft as
character moves away from doorway toward lamp.
```

### 3.3 媒介风格锁

| 媒介 | 光影描述偏重 | NOT 使用 |
|------|------------|---------|
| 写实 | 物理准确、具体色温K值、光比数值、真实光源名称 | 不用动漫光影词汇 |
| 动漫 | 赛璐璐明暗分区、色块阴影、高光点、环境反射色 | 不用物理布光参数 |
| 3D | 灯光类型名称(area/spot/directional)、HDRI、GI | 不用摄影布光术语 |

---

## STEP 4：自检（黑盒执行，不输出给用户）

生成光影描述后，静默检查以下 5 项：

1. ✅ 是否包含至少 3 要素（光源类型 + 方向 + 强度/光比）？
2. ✅ 光影情绪是否与场景情绪一致？（查 1.2 映射表）
3. ✅ Tier 2 技法是否 ≤ 2 种？组合是否合法？（查 2.2 规则）
4. ✅ 是否使用了具体物理语言而非文学修辞？
5. ✅ 图片/视频媒介是否用了正确格式？（图片=瞬间状态/视频=时间演变）

未通过 → 自动修正后输出，不告知用户检查过程。

---

## 附录：剧情类型 → 光影快速推荐

> 完整配方表见 `references/lighting-recipes.md`，场景空间光影图谱见 `references/scene-lighting-atlas.md`。

| 剧情类型 | 推荐基础(Tier 1) | 可选进阶(Tier 2) | 关键色温 |
|---------|----------------|-----------------|---------|
| 浪漫告白 | 逆光/黄金时段 + 光比 1:2 | 实用光源(烛光/灯笼) | 3000-3500K |
| 悬疑追踪 | 分割光 + 光比 1:6 | 负补光 + 纹理投影 | 6500-8000K |
| 英雄登场 | 逆光剪影 → 侧光揭示 | 体积光(god rays) | 5000-5600K |
| 内心独白 | 伦勃朗光 + 光比 1:4 | 负补光 | 4500-5500K |
| 最终对决 | 分割光 + 光比 1:8 | 明暗对比(Chiaroscuro) | 5600K 偏冷 |
| 温馨家庭 | 环形光 + 光比 1:2 | 实用光源(壁炉/台灯) | 3200-3800K |
| 恐怖揭示 | 底光 + 光比 1:8+ | 色温对比(冷绿+暖红) | 极端混合 |
| 权力交锋 | 顶光 + 光比 1:6 | 明暗对比 | 5000-6000K |
| 告别离散 | 逆光 + 蓝调时刻 | 光线演变(暖→冷) | 3500→7000K |
| 日常过渡 | 标准三点 + 光比 1:2 | 无需 Tier 2 | 5600K |
