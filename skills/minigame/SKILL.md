---
name: minigame
description: 小游戏制作专家。帮助创建任意类型的 HTML5 2D/3D 小游戏，由用户提出需求，根据插件能力组合实现。支持 Canvas 2D、Three.js、Babylon.js、Phaser.js 等引擎。提供游戏循环、碰撞检测、粒子特效、音效、3D 场景、物理引擎、游戏叙事、UI 设计等全套能力。当用户提到制作小游戏、HTML5 游戏、网页游戏、2D/3D 游戏、Canvas 游戏、Three.js 游戏、互动游戏、游戏开发时使用。不限制游戏类型，用户想做什么就做什么。
---

# 小游戏制作

本技能帮助 DeepSeek Harness 快速创建各种类型的 HTML5 小游戏，从简单到复杂，提供完整的游戏开发指导和最佳实践。

## 核心原则

1. **单文件优先**：尽量使用单个 HTML 文件（内嵌 CSS + JS），零依赖、零构建，打开即玩。
2. **2D + 3D 全覆盖**：Canvas 2D 做 2D 游戏，Three.js/Babylon.js 做 3D 游戏，按需选择引擎。
3. **多端适配**：自动适配 PC、平板、手机，响应式布局，横竖屏切换。
4. **多语言出海**：支持中/英/日/韩四种语言，自动检测浏览器语言，一键切换。
5. **性能至上**：2D 游戏包体 < 40 KB，3D 游戏包体 < 128 MB，60fps 流畅运行，对象池避免 GC，设备分级降配。
6. **游戏叙事**：三幕式结构、角色设计、多结局，让游戏有故事性。
7. **高级 UI 设计**：克制构图、去卡片化、字体限制、色彩校准、有意识的动效。
8. **即时可玩**：优先使用 Canvas 2D / Three.js，避免繁重的框架引入。
9. **视觉吸引力**：使用粒子效果、动画过渡、色彩搭配提升游戏体验。
10. **渐进增强**：从最简可玩版本开始，逐步添加特效和功能。

## 游戏引擎选择

### Canvas 2D（2D 游戏首选）
- 零依赖，浏览器原生支持
- 适合所有 2D 游戏类型：动作、射击、益智、休闲、物理、平台等
- 使用 `requestAnimationFrame` 驱动游戏循环
- 参考 [canvas-api.md](references/canvas-api.md)

### Phaser.js（2D 复杂游戏）
- 功能完整的 2D 游戏框架
- 内置物理引擎、精灵管理、动画系统
- 适合需要完整框架的复杂 2D 游戏
- CDN 引入：`<script src="https://cdn.jsdelivr.net/npm/phaser@3/dist/phaser.min.js"></script>`

### DOM + CSS（轻量休闲）
- 适合卡牌、文字、点击类轻量游戏
- 利用 CSS 动画和过渡效果
- 更容易做响应式布局

### Three.js（3D 游戏首选）
- 最流行的 WebGL 3D 库，社区资源丰富
- 轻量灵活，按需引入（核心 ~150KB gzipped）
- 适合所有 3D 游戏类型：动作、赛车、射击、解谜、模拟、RPG 等
- CDN Import Map 引入，零构建
- 详细参考 [3d-games.md](references/3d-games.md)

### Babylon.js（3D 复杂游戏）
- 功能完整的 3D 游戏引擎（核心 ~500KB gzipped）
- 内置物理引擎、粒子系统、GUI、音频
- 适合需要完整引擎的复杂 3D 场景
- 详细参考 [3d-games.md](references/3d-games.md)

## 常用模式参考

以下参考文档提供了常见游戏机制的实现模式，但**不限制游戏类型**。用户提出任何游戏类型，都可以从这些模式中组合出对应实现。每个参考文档包含核心算法、数据结构、视觉建议等完整实现细节。

### 2D 参考
| 参考文档 | 核心机制 | 可复用模式 |
|----------|----------|-----------|
| [breakout.md](references/breakout.md) | 弹球反射、砖块消除 | 碰撞检测、反弹角度、粒子爆炸 |
| [snake.md](references/snake.md) | 网格移动、食物生成 | 网格系统、方向控制、增长机制 |
| [shooter.md](references/shooter.md) | 子弹发射、敌人波次 | 对象池、敌人生成模式、道具系统 |
| [platformer.md](references/platformer.md) | 重力物理、平台碰撞 | 物理系统、摄像机跟随、Tile Map |
| [match3.md](references/match3.md) | 网格交换、三消匹配 | 网格算法、重力下落、连锁消除 |
| [runner.md](references/runner.md) | 无限卷轴、障碍躲避 | 视差滚动、难度曲线、跳跃/滑铲 |
| [tetris.md](references/tetris.md) | 方块旋转、消行 | 矩阵旋转、行消除、Ghost piece |
| [2048.md](references/2048.md) | 滑动合并、数字益智 | 网格滑动、合并动画、数字格式化 |
| [whack-a-mole.md](references/whack-a-mole.md) | 随机出现、点击得分 | 倒计时、连击系统、弹出动画 |
| [memory-card.md](references/memory-card.md) | 翻牌配对、记忆挑战 | 翻转动画、配对检测、洗牌算法 |

### 3D 参考
3D 游戏使用 Three.js 或 Babylon.js，详细参考 [3d-games.md](references/3d-games.md)。以下为常见 3D 机制的参考实现：

| 机制 | 实现方式 | 可复用模式 |
|------|---------|-----------|
| 第三人称跑酷 | Three.js + 程序化几何体 | 跑道切换、障碍生成、摄像机跟随 |
| 追尾视角赛车 | Three.js + Cannon-es | 道路生成、转向物理、氮气加速 |
| FPS/TPS 射击 | Three.js + PointerLockControls | 射线检测、敌人 AI、子弹轨迹 |
| 物理解谜 | Three.js + Cannon-es | 重力、碰撞、关节、拖拽交互 |
| 弹球 / 桌球 | Three.js + Cannon-es | 3D 物理反弹、得分机关 |
| 塔防 / 策略 | Three.js + InstancedMesh | 批量渲染、路径寻路、升级系统 |

## 游戏开发通用模式

### 游戏循环
```javascript
class Game {
  constructor() {
    this.canvas = document.getElementById('game')
    this.ctx = this.canvas.getContext('2d')
    this.lastTime = 0
    this.running = true
  }

  loop(timestamp) {
    if (!this.running) return
    const dt = Math.min((timestamp - this.lastTime) / 1000, 0.05) // cap delta time
    this.lastTime = timestamp
    this.update(dt)
    this.render()
    requestAnimationFrame((t) => this.loop(t))
  }

  update(dt) { /* 子类实现 */ }
  render() { /* 子类实现 */ }
}
```

### 矩形碰撞检测
```javascript
function rectCollide(a, b) {
  return (
    a.x < b.x + b.w &&
    a.x + a.w > b.x &&
    a.y < b.y + b.h &&
    a.y + a.h > b.y
  )
}
```

### 圆形碰撞检测
```javascript
function circleCollide(a, b) {
  const dx = a.x - b.x
  const dy = a.y - b.y
  const dist = Math.sqrt(dx * dx + dy * dy)
  return dist < a.radius + b.radius
}
```

### 粒子系统
```javascript
class Particle {
  constructor(x, y, vx, vy, life, color, size) {
    this.x = x; this.y = y
    this.vx = vx; this.vy = vy
    this.life = life; this.maxLife = life
    this.color = color; this.size = size
  }
  update(dt) {
    this.x += this.vx * dt
    this.y += this.vy * dt
    this.vy += 200 * dt // 重力
    this.life -= dt
  }
  get alpha() { return Math.max(0, this.life / this.maxLife) }
}
```

### 精灵动画
```javascript
class Sprite {
  constructor(img, frameW, frameH, frames, fps) {
    this.img = img
    this.frameW = frameW; this.frameH = frameH
    this.frames = frames
    this.frameTime = 0
    this.currentFrame = 0
    this.fps = fps
  }
  update(dt) {
    this.frameTime += dt
    if (this.frameTime >= 1 / this.fps) {
      this.frameTime = 0
      this.currentFrame = (this.currentFrame + 1) % this.frames
    }
  }
  draw(ctx, x, y, w, h) {
    ctx.drawImage(
      this.img,
      this.currentFrame * this.frameW, 0,
      this.frameW, this.frameH,
      x, y, w || this.frameW, h || this.frameH
    )
  }
}
```

## 视觉设计指南

根据用户偏好，遵循以下视觉风格：

### 暗色主题风格
- 背景：接近黑色 (#0a0a0f, #111118)
- 文字：柔和白色 (#e8e8f0)
- 粒子噪点、流光墨染效果
- 使用 CSS backdrop-filter 和渐变叠加

### 粉嫩 Y2K 像素风格
- 粉色系配色 (#ff6b9d, #ff99cc, #ffccee)
- 像素化字体 (Press Start 2P, VT323)
- 霓虹发光效果、扫描线
- 像素化图形，8-bit 风格音效

### 通用美感
- 使用渐变色而非纯色
- 添加微妙的粒子动画背景
- 过渡动画使用 ease-out 缓动
- 按钮和 UI 元素添加 hover 效果

## 游戏叙事设计

借鉴小说创作的三幕式结构，为游戏注入故事性，详细参考 [narrative.md](references/narrative.md)。

### 三幕式结构
- **第一幕（铺垫）**：世界观建立、玩家引入、激励事件（前 30 秒内触发）
- **第二幕（对抗）**：挑战升级、中点转折、低谷时刻（最大挑战）
- **第三幕（解决）**：最终冲刺、高潮对决、成就感

### 多结局设计
- **圆满结局**（默认）：达成目标，正向反馈，引导重玩
- **反转结局**（隐藏）：特定条件触发，揭示隐藏信息
- **无尽模式**：分数即叙事，排行榜驱动

### 叙事原则
- 用环境叙事，不用大段文字
- 教程融入叙事，不打断节奏
- 游戏第一，叙事第二
- 每个阶段一个情感基调

## 游戏 UI 设计

界面设计遵循 award-level 前端设计理念，详细参考 [game-ui.md](references/game-ui.md)。

### 设计三步法
1. **视觉主旨**：一句话描述界面气质（如"暗黑科技 HUD，冷冽金属与霓虹发光"）
2. **内容计划**：主菜单 → 游戏 HUD → 结算 → 设置，每个界面一个职责
3. **交互主旨**：2-3 个动效（入场序列、交互反馈、过渡动画）

### 核心规则
- **克制构图**：优先构图而非组件堆砌，品牌/游戏名最响
- **去卡片化**：默认无卡片，用分区、分割线、留白替代
- **字体限制**：最多 2 个字体，Press Start 2P + system-ui（像素游戏），Satoshi + JetBrains Mono（现代游戏）
- **色彩校准**：最多 1 个强调色，饱和度 < 80%，暗色主题默认
- **形状一致**：全直角 / 全柔和 / 全药丸，选一种贯穿始终

### 推荐配色
```javascript
const PALETTES = {
  darkTech:  { bg: '#0a0a0f', text: '#e8e8f0', accent: '#00f0ff' },
  pixelY2K:  { bg: '#1a0a14', text: '#ffe8f0', accent: '#ff6b9d' },
  cyberpunk: { bg: '#0a0a0a', text: '#f0f0f0', accent: '#ff00ff' },
  nature:    { bg: '#0a0f0a', text: '#e0f0e0', accent: '#44ff44' },
}
```

### 动效规则
- 快节奏（< 300ms），`cubic-bezier(0.16, 1, 0.3, 1)` 缓出
- 按钮 `:active` 时 `scale(0.97)` 模拟按压
- 动效强度 > 3 必须支持 `prefers-reduced-motion`
- 禁止 `window.addEventListener('scroll')` 驱动动画

### 界面检查清单
- 品牌/游戏名在第一屏是否清晰
- 是否有一个强视觉锚点（而非多个分散元素）
- 每个界面是否只有一个职责
- 卡片真的必要吗（优先无卡片）
- 动效是否增强了层级或氛围（而非纯装饰）

## 音效

使用 Web Audio API 生成程序化音效（无需外部文件）：

```javascript
class SFX {
  constructor() { this.ctx = new (window.AudioContext || window.webkitAudioContext)() }

  playTone(freq, duration, type = 'square', volume = 0.3) {
    const osc = this.ctx.createOscillator()
    const gain = this.ctx.createGain()
    osc.type = type
    osc.frequency.value = freq
    gain.gain.setValueAtTime(volume, this.ctx.currentTime)
    gain.gain.exponentialRampToValueAtTime(0.01, this.ctx.currentTime + duration)
    osc.connect(gain).connect(this.ctx.destination)
    osc.start(); osc.stop(this.ctx.currentTime + duration)
  }

  pop() { this.playTone(600, 0.1, 'sine', 0.4) }
  hit() { this.playTone(200, 0.15, 'sawtooth', 0.5) }
  score() { this.playTone(800, 0.1, 'square', 0.3); setTimeout(() => this.playTone(1200, 0.15, 'square', 0.3), 100) }
  gameOver() { this.playTone(400, 0.2, 'sawtooth', 0.4); setTimeout(() => this.playTone(300, 0.2, 'sawtooth', 0.4), 200); setTimeout(() => this.playTone(200, 0.4, 'sawtooth', 0.4), 400) }
}
```

## 多语言国际化 (i18n)

出海游戏必须支持中/英/日/韩四种语言，详细实现参考 [i18n.md](references/i18n.md)。

### 快速集成
```javascript
// 语言检测
function detectLanguage() {
  const saved = localStorage.getItem('gameLang')
  if (saved) return saved
  const lang = navigator.language
  if (lang.startsWith('zh')) return 'zh-CN'
  if (lang.startsWith('ja')) return 'ja'
  if (lang.startsWith('ko')) return 'ko'
  return 'en'
}

// 翻译函数
function t(key) { return I18N[currentLang]?.[key] || key }
```

### 必须覆盖的文本
- 游戏标题、开始/重新开始/暂停/继续按钮
- 分数、最高分、新纪录
- 游戏结束、胜利、失败提示
- 设置菜单（音效、音乐、语言切换）
- 操作提示（键盘/触屏说明）

## 包体与性能优化

游戏必须做到轻量、流畅，详细实现参考 [performance.md](references/performance.md)。

### 关键优化点
- **单文件**：所有 CSS/JS 内嵌 HTML，零外部请求
- **对象池**：粒子、子弹、敌人使用对象池避免 GC
- **离屏 Canvas**：静态背景预渲染到离屏 Canvas
- **设备分级**：根据屏幕尺寸和像素比自动调整粒子数量和特效等级
- **空闲降帧**：页面不可见或闲置时降低帧率省电

### 目标包体
- 简单游戏：< 5 KB
- 中等游戏：< 15 KB
- 复杂游戏：< 40 KB

## UI 自适应与多机型适配

游戏必须在 PC、平板、手机上都完美呈现，详细实现参考 [responsive.md](references/responsive.md)。

### 核心要点
```javascript
// 响应式画布
function setupCanvas() {
  const dpr = window.devicePixelRatio || 1
  const w = container.clientWidth
  const h = container.clientHeight
  const designRatio = 4 / 3
  let gameW = w, gameH = h
  if (w / h > designRatio) gameW = h * designRatio
  else gameH = w / designRatio
  canvas.style.width = gameW + 'px'
  canvas.style.height = gameH + 'px'
  canvas.width = gameW * dpr
  canvas.height = gameH * dpr
}
```

### 必须适配
- 320px ~ 1920px 宽度范围
- 横屏 + 竖屏两种方向
- 刘海屏安全区域（env(safe-area-inset-*)）
- 移动端虚拟摇杆/按钮（触屏设备显示，PC 隐藏）
- 键盘 + 触屏双模式输入
- 防止双击缩放、长按菜单（touch-action: none）

## 存储与排行榜

```javascript
// 本地存储高分
function saveHighScore(key, score) {
  const prev = parseInt(localStorage.getItem(key) || '0')
  if (score > prev) localStorage.setItem(key, score.toString())
  return Math.max(score, prev)
}

function getHighScore(key) {
  return parseInt(localStorage.getItem(key) || '0')
}
```

## 响应风格

- **由用户提出游戏类型**，不预设游戏种类，根据用户需求灵活组合插件能力
- 根据用户描述自动判断 2D/3D，选择合适的引擎（2D 用 Canvas、3D 用 Three.js）
- 先输出完整可玩的最小版本，再逐步添加功能
- 使用程序化图形（Canvas 绘制 / Three.js 程序化几何体）而非图片资源，保持单文件
- 每个游戏都包含：开始界面、游玩界面、结束界面、分数显示
- 添加音效和粒子效果提升质感
- 代码注释用中文，变量名用英文
- **默认生成多语言版本**：文本字典覆盖中/英/日/韩，语言切换器置于设置面板
- **默认移动端优先**：虚拟操控杆/按钮、触屏手势、安全区域适配
- **默认性能优化**：对象池、离屏 Canvas、设备分级、空闲降帧
- **默认游戏叙事**：三幕式结构、情感曲线、多结局设计
- **默认高级 UI**：克制构图、去卡片化、暗色主题、有意识的动效
- **3D 游戏专属**：程序化几何体优先、InstancedMesh 批量渲染、像素比 ≤ 2