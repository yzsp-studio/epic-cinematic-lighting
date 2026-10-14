# 剧情类型 × 情绪 → 光影配方详细表

> 本文件是 SKILL.md 附录「剧情类型→光影快速推荐」的展开版。
> 每个配方包含完整的 prompt 可用光影描述，可直接复制使用。

---

## 1. 浪漫类

### 1.1 初恋/心动

| 要素 | 配方 |
|------|------|
| 基础布光 | 逆光(Back) + 环形光(Loop) |
| 光比 | 1:1.5~1:2（柔和） |
| 色温 | 3200-3800K 暖金 |
| 时段 | 黄金时段 / 午后斜阳 |
| Tier 2 | 实用光源（阳光穿过窗帘 / 灯笼 / 串灯） |
| 光影质感 | 极柔(heavily diffused)，无硬边阴影 |
| Prompt | `Warm golden hour backlight creating soft halo around hair, gentle loop lighting on face from 30° left at 3500K, ratio 1:2, heavily diffused with no hard shadows, warm light filtering through sheer curtains` |

### 1.2 热恋/激情

| 要素 | 配方 |
|------|------|
| 基础布光 | 侧光(Side) 45° + 轮廓光(Rim) |
| 光比 | 1:3（有对比但不压迫） |
| 色温 | 3000-3500K 暖橙偏红 |
| 时段 | 夜间室内 |
| Tier 2 | 实用光源（烛光 / 壁炉）+ 色温对比（窗外冷蓝月光） |
| Prompt | `Warm candlelight as key from left at 3000K, ratio 1:3, orange-amber tones on skin, cool blue moonlight 7500K from window behind creating rim light separation, intimate and warm` |

### 1.3 告白/求婚

| 要素 | 配方 |
|------|------|
| 基础布光 | 蝶光(Butterfly) 或黄金时段逆光 |
| 光比 | 1:1.5（近乎均匀但有方向） |
| 色温 | 3500-4000K |
| Tier 2 | 体积光（如阳光穿林 / 飘浮微尘中的光束） |
| Prompt | `Golden hour backlight with visible warm light rays through trees, butterfly lighting on face from above, ratio 1:1.5, soft volumetric beams in slightly hazy air, dreamy and ethereal 3800K` |

---

## 2. 悬疑/惊悚类

### 2.1 跟踪/潜行

| 要素 | 配方 |
|------|------|
| 基础布光 | 窄光(Short) + 单一侧光源 |
| 光比 | 1:6~1:8（大面积暗） |
| 色温 | 6500-8000K 冷色 |
| 时段 | 夜间 / 阴天 |
| Tier 2 | 负补光 + 纹理投影（百叶窗 / 栏杆） |
| Prompt | `Short lighting with shadow side facing camera, single cold light source 7000K from far left, ratio 1:8, negative fill creating pitch-black shadows, gobo shadow patterns from chain-link fence falling across face` |

### 2.2 真相揭示

| 要素 | 配方 |
|------|------|
| 基础布光 | 顶光(Top) 单一硬光 |
| 光比 | 1:4~1:6 |
| 色温 | 5600K 中性白 |
| Tier 2 | 明暗对比(Chiaroscuro) |
| Prompt | `Single hard overhead light casting deep eye socket shadows, chiaroscuro contrast, face half-revealed half-hidden, stark white 5600K against absolute black background, interrogation-room feel` |

### 2.3 恐怖/惊吓

| 要素 | 配方 |
|------|------|
| 基础布光 | 底光(Under) |
| 光比 | 1:8+（极端） |
| 色温 | 极端混合：冷绿 7000K+ 底光 + 暖红闪烁 |
| Tier 2 | 色温对比（冷暖极端对撞） |
| Prompt | `Eerie under-lighting from below casting unnatural upward shadows, sickly green-tinted 7500K, ratio 1:10, occasional warm red flicker from unseen source, deep pitch-black background, horror atmosphere` |

---

## 3. 动作/史诗类

### 3.1 英雄登场

| 要素 | 配方 |
|------|------|
| 基础布光 | 逆光(Back) 强剪影 → 侧光(Side)渐显 |
| 光比 | 初始 1:16（纯剪影）→ 渐变至 1:4 |
| 色温 | 5000-5600K 中性偏暖 |
| Tier 2 | 体积光(god rays / dust motes) |
| 图片 Prompt | `Dramatic silhouette backlight, strong rim light at 5600K outlining heroic figure, volumetric god rays streaming from behind, golden dust particles visible in light beams, ratio 1:4 with minimal fill` |
| 视频 Prompt | `Opens with full silhouette against bright backlight (ratio 1:16), volumetric rays streaming past. As figure steps forward, side key light at 5200K gradually reveals face and form, transitioning to ratio 1:4 by end of shot` |

### 3.2 最终对决

| 要素 | 配方 |
|------|------|
| 基础布光 | 分割光(Split) 双侧对立 |
| 光比 | 1:8（极硬） |
| 色温 | 5600K 偏冷，无暖色调 |
| Tier 2 | 明暗对比(Chiaroscuro) |
| Prompt | `Split lighting with hard key from sharp left at 5600K, opposite side in total darkness, chiaroscuro intensity, razor-sharp shadow line down center of face, no fill light, no ambient bounce, stark confrontational` |

### 3.3 战斗/追逐

| 要素 | 配方 |
|------|------|
| 基础布光 | 多方向硬光（模拟混乱环境） |
| 光比 | 变化中（1:3→1:6 交替） |
| 色温 | 混合色温（火焰 2500K + 月光 7000K） |
| Tier 2 | 色温对比 + 实用光源（爆炸/火焰/车灯） |
| Prompt | `Chaotic mixed lighting: warm fire glow 2500K from ground level, cold moonlight 7000K from above, hard shifting shadows, practical light from explosions creating brief warm flashes, dynamic ratio shifts between 1:3 and 1:6` |

---

## 4. 权力/政治类

### 4.1 王座/审判

| 要素 | 配方 |
|------|------|
| 基础布光 | 顶光(Top) + 窄光(Short) |
| 光比 | 1:6（控制性高对比） |
| 色温 | 5000-5500K 中性偏冷 |
| Tier 2 | 体积光（从高窗射入）+ 明暗对比 |
| Prompt | `Regal top light from high windows with visible volumetric beams, short lighting on throne figure creating mysterious shadow-heavy face, ratio 1:6, chiaroscuro depth, cold neutral 5200K, dust motes floating in light shafts` |

### 4.2 阴谋/密室

| 要素 | 配方 |
|------|------|
| 基础布光 | 单一实用光源（台灯/蜡烛） |
| 光比 | 1:8+（极暗环境仅一处亮光） |
| 色温 | 暖 3000K（实用光源本色） |
| Tier 2 | 实用光源叙事 + 负补光 |
| Prompt | `Single practical desk lamp as only light source at 3000K, warm pool of light on documents and hands, negative fill everywhere else creating deep impenetrable darkness, ratio 1:10, secretive intimate` |

---

## 5. 情感/文艺类

### 5.1 孤独/离别

| 要素 | 配方 |
|------|------|
| 基础布光 | 窗光(Window) 单侧 + 蓝调时刻 |
| 光比 | 1:4~1:5 |
| 色温 | 7000-8000K 冷蓝 |
| Tier 2 | 负补光 + 纹理投影（窗框阴影） |
| Prompt | `Cool blue hour window light from right at 7500K, ratio 1:5, negative fill on left side, window frame gobo pattern casting geometric shadows across empty room, melancholic and still` |

### 5.2 回忆/闪回

| 要素 | 配方 |
|------|------|
| 基础布光 | 过曝逆光(Blown-out Back) |
| 光比 | 1:1（整体偏亮偏白） |
| 色温 | 4000-4500K 暖柔 |
| Tier 2 | 实用光源（模拟记忆中的温暖）+ 体积光 |
| Prompt | `Slightly overexposed warm backlight 4200K, dreamy haze reducing contrast, ratio near 1:1, soft volumetric light through memory-like haze, faded edges, nostalgic warmth, gentle lens flare` |

### 5.3 绝望/崩溃

| 要素 | 配方 |
|------|------|
| 基础布光 | 顶光(Top) 极窄光束 |
| 光比 | 1:10+（周围几乎全黑） |
| 色温 | 6000K 冷白 |
| Tier 2 | 负补光（绝对暗） |
| Prompt | `Single narrow overhead spotlight at 6000K, harsh pool of cold white light on figure, everything beyond the circle in absolute darkness, ratio 1:12, negative fill all around, isolation and despair` |

---

## 6. 日常/生活类

### 6.1 晨起/清晨

| 要素 | 配方 |
|------|------|
| 基础布光 | 窗光(Window) + 标准三点 |
| 光比 | 1:2（自然柔和） |
| 色温 | 4500-5000K 偏暖白 |
| Tier 2 | 无需（Tier 1 足够） |
| Prompt | `Soft morning window light from right at 4800K, standard three-point with gentle fill from left, ratio 1:2, clean natural illumination, subtle warm bounce from wooden surfaces` |

### 6.2 办公室/职场

| 要素 | 配方 |
|------|------|
| 基础布光 | 顶部面光（荧光灯模拟）+ 屏幕光 |
| 光比 | 1:2~1:3 |
| 色温 | 混合：天花板 5500K + 屏幕 6500K 偏蓝 |
| Tier 2 | 色温对比（冷荧光 + 暖窗光）可选 |
| Prompt | `Overhead fluorescent panel lighting at 5500K casting flat even illumination, cool blue computer screen glow at 6500K on face from front, optional warm window light from side creating subtle color contrast, ratio 1:2, corporate mundane` |

### 6.3 夜间街道

| 要素 | 配方 |
|------|------|
| 基础布光 | 多方向实用光源（路灯/店铺/车灯） |
| 光比 | 变化，整体 1:4~1:6 |
| 色温 | 极端混合：钠灯 2700K + LED 5000K + 霓虹各色 |
| Tier 2 | 实用光源叙事 + 色温对比 |
| Prompt | `Urban night street lit by mixed practicals: warm sodium streetlamp 2700K from above-left, cool LED shopfront 5000K from right, colorful neon reflections on wet pavement, ratio varies 1:4 to 1:6, puddle reflections doubling light sources, noir urban atmosphere` |
