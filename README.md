# dsh-minigame-plugin

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![dsh-plugin](https://img.shields.io/badge/dsh-plugin-blue)](https://github.com/topics/dsh-plugin)

**DeepSeek Harness 小游戏制作插件** — 让 AI 帮你快速创建各种 HTML5 小游戏。

## 功能

- 帮助 AI 创建**任意类型**的 HTML5 **2D + 3D** 小游戏，不限制游戏类型，用户想做什么就做什么
- 提供 Canvas 2D / Three.js / Babylon.js 三大引擎，根据需求自动选择
- 内置 17 个参考文档，覆盖常见游戏机制的可复用模式（碰撞检测、粒子系统、物理引擎、网格算法等）
- 支持程序化音效、高分存储
- **多语言国际化**：中/英/日/韩 四语言支持，自动检测浏览器语言，一键切换
- **包体与性能优化**：对象池、离屏 Canvas、InstancedMesh、设备分级、空闲降帧，2D < 40 KB，3D < 128 MB
- **UI 自适应**：自动适配 PC、平板、手机，虚拟摇杆，横竖屏切换，刘海屏安全区域
- **游戏叙事**：三幕式结构、角色设计、多结局，让游戏有故事性
- **高级 UI 设计**：克制构图、去卡片化、暗色主题、有意识的动效
- 单文件、零依赖、打开即玩

## 插件能力

不限制游戏类型，由用户提出需求。以下是插件提供的能力和参考模式：

### 引擎支持
| 引擎 | 维度 | 包体 | 适用场景 |
|------|------|------|----------|
| Canvas 2D | 2D | 零依赖 | 所有 2D 游戏：动作、射击、益智、休闲、物理、平台 |
| Phaser.js | 2D | CDN | 需要完整框架的复杂 2D 游戏 |
| DOM + CSS | 2D | 零依赖 | 卡牌、文字、点击类轻量游戏 |
| Three.js | 3D | ~150KB | 所有 3D 游戏：动作、赛车、射击、解谜、模拟、RPG |
| Babylon.js | 3D | ~500KB | 需要完整引擎的复杂 3D 场景 |

### 参考模式（可组合复用）
| 类别 | 参考文档 | 可复用模式 |
|------|---------|-----------|
| 2D | 弹球、贪吃蛇、射击、平台跳跃、消除、跑酷、俄罗斯方块、2048、打地鼠、记忆翻牌 | 碰撞检测、网格系统、对象池、物理模拟、视差滚动、粒子特效、动画过渡 |
| 3D | Three.js 完整参考 | 3D 场景、物理引擎、InstancedMesh、后处理、射线检测、空间音频 |
| 通用 | 多语言、性能优化、响应式、叙事设计、UI 设计 | i18n、对象池、设备分级、三幕式结构、去卡片化 UI |

## 安装

### 安装到 Web 配置文件

```bash
npx @deepseek-ai/dsh plugin --profile web add github:sasajun2345/dsh-minigame-plugin
```

### 本地开发

```bash
npx @deepseek-ai/dsh plugin --profile web add .
```

### 临时试用

```bash
npx @deepseek-ai/dsh web --patch ./cordis.patch.yml
```

### 验证安装

```bash
npx @deepseek-ai/dsh --profile web --dump-config
```

输出中应包含 `dsh-minigame-plugin` 层和 `minigame-skill-filesystem` 行。

## 使用

安装后，在 DeepSeek Harness 对话中直接描述你想做的游戏即可，技能会自动激活。**不限制游戏类型，任何类型的游戏都可以制作。** 例如：

- "帮我做一个弹球消砖块游戏"
- "做一个贪吃蛇，要有粒子特效"
- "创建一个暗黑主题的射击游戏"
- "帮我做一个 2048 游戏，用粉嫩配色"
- "做一个跑酷游戏，移动端适配"
- "做一个 3D 赛车游戏，有氮气加速"
- "帮我做一个 3D 解谜游戏，物理拖拽"
- "做一个 Roguelike 地牢探险游戏"
- "做一个音游，节奏打击"
- "做一个钓鱼游戏，有收集图鉴"

## 项目结构

```
package.json              Harness bundle 配置
cordis.patch.yml          Cordis 插件补丁
index.js                  技能文件系统入口
skills/minigame/
  SKILL.md                核心技能文件
  references/
    canvas-api.md          Canvas 2D API 速查
    3d-games.md            3D 游戏开发（Three.js / Babylon.js）
    i18n.md                多语言国际化（中/英/日/韩）
    performance.md         包体优化与性能优化
    responsive.md          UI 自适应与多机型适配
    narrative.md           游戏叙事设计（三幕式结构）
    game-ui.md             游戏 UI 设计（克制构图、去卡片化）
    breakout.md            弹球消砖块
    snake.md               贪吃蛇
    shooter.md             射击游戏
    platformer.md          平台跳跃
    match3.md              消除游戏
    runner.md              跑酷游戏
    tetris.md              俄罗斯方块
    2048.md                2048
    whack-a-mole.md        打地鼠
    memory-card.md         记忆翻牌
```

## 依赖

- Node.js >= 20.19.0
- DeepSeek Harness 0.2.x
- peer：`@deepseek-ai/dsh-skill-filesystem` ^0.2.0-rc.2（由 DSH 运行时自带，不由 profile 单独安装）

> **兼容性说明**
> - 本插件不自带 skill-filesystem 副本。旧版把它写成 `dependencies: ^0.1.0-rc.6`，会在 profile 中安装一份 0.1.x 旧包，覆盖 DSH 本体随版本升级的内置实现，进而与 0.2.x 运行时冲突并被禁用；现改为 `peerDependencies`，统一由运行时提供。
> - 技能元数据必须使用 YAML frontmatter（文件首行就是 `---`）。0.2.x 的 `parseFrontmatter` 对首行做硬校验，表格形式的元数据会被判为 `missing YAML frontmatter` 并静默忽略该技能。

## 许可

[MIT](./LICENSE)

---

# dsh-minigame-plugin (English)

A DeepSeek Harness plugin for creating any type of HTML5 2D/3D mini-game. No game type restrictions — users propose what they want, and the plugin composes capabilities to build it. Supports Canvas 2D, Three.js, Babylon.js, with 16 reference documents covering reusable game patterns.

## Capabilities

- **No game type limits** — user proposes any game, plugin composes the right engine and patterns
- Canvas 2D / Three.js / Babylon.js / Phaser.js engines, auto-selected based on need
- 17 reference docs: collision detection, particle systems, physics, grid algorithms, 3D scenes, etc.
- Multi-language: Chinese / English / Japanese / Korean
- Performance: object pooling, offscreen canvas, InstancedMesh, device tiering
- Responsive: PC, tablet, mobile, virtual joystick, landscape/portrait
- Narrative: three-act structure, character design, multi-endings
- Premium UI: restrained composition, cardless layouts, dark theme, intentional motion

## Install

```bash
npx @deepseek-ai/dsh plugin --profile web add github:sasajun2345/dsh-minigame-plugin
```

## Usage

Just describe the game you want to build in a DeepSeek Harness conversation. The skill activates automatically.

## License

MIT