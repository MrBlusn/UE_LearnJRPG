# LearnJRPG

> 一个使用 **Unreal Engine 5.4** 与 **BluePrint** 构建的像素风格日式回合制 RPG 游戏。

<p align="center">
  <img src="https://img.shields.io/badge/Engine-Unreal%20Engine%205.6-blue?logo=unrealengine" alt="Unreal Engine 5.4">
  <img src="https://img.shields.io/badge/Language-C%2B%2B%20%2F%20BluePrint-orange" alt="C++ / BluePrint">
  <img src="https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-lightgrey" alt="Windows | Linux">
</p>

---

## 📖 项目简介

**LearnJRPG** 是一款功能完备的像素风 JRPG 游戏原型，涵盖了回合制 RPG 的完整核心循环。项目完全基于 BluePrint 可视化脚本构建，辅以极少量 C++ 胶水代码，非常适合学习 UE5 游戏开发。

### 🎮 核心玩法

- **🗺️ 野外探索** — 在像素风格的世界中移动，与 NPC/场景交互，触发战斗
- **⚔️ 回合制战斗** — 4人队伍对抗多种敌人，经典指令式战斗
- **🎯 技能系统** — 7个主动技能 + 3种消耗道具，技能随等级解锁
- **📈 成长系统** — 战斗获得经验值，升级提升属性
- **💾 存档系统** — 多槽位手动存档/读档

---

## 🏗️ 项目架构

```
LearnJRPG/
├── Content/
│   ├── BluePrint/           # 核心游戏逻辑 (Blueprint)
│   │   ├── Battle/          # 战斗系统
│   │   ├── Components/      # Actor组件
│   │   ├── Field/           # 野外探索系统
│   │   ├── FrameWork/       # GameMode / GameInstance / PlayerController
│   │   └── SaveLoad/        # 存档对象
│   ├── Data/DataAssets/     # 数据驱动配置
│   │   ├── AreaData/        # 区域数据
│   │   ├── BattleCharData/  # 角色战斗属性
│   │   ├── ItemData/        # 道具数据
│   │   ├── PartyMemberData/ # 队伍成员信息
│   │   ├── SkillData/       # 技能数据
│   │   └── GlobalVariables/ # 全局变量
│   ├── Definitions/         # 枚举 / 结构体 / 接口 / 函数库
│   ├── Input/               # Enhanced Input 配置
│   ├── Levels/              # 关卡地图
│   │   ├── Field/           # 野外地图 (3张)
│   │   └── Battle/          # 战斗地图 (2张)
│   ├── UI/                  # UI 资源 (Widget Blueprint)
│   └── Art/                 # 美术资源 (523个)
├── Config/                  # 项目配置
└── LearnJRPG.uproject       # 项目文件
```

### 🔄 三层 GameMode 架构

项目通过 **GameInstance** 作为全局中枢，在三个独立的 GameMode 之间切换：

| GameMode | 场景 | 说明 |
|----------|------|------|
| `GM_MainMenu` | `L_MainMenu` | 主菜单（开始游戏 / 加载存档） |
| `GM_Field` | `L_Field_*` | 野外探索（移动、交互、遇敌） |
| `GM_Battle` | `L_Battle_*` | 回合制战斗（指令选择、技能释放） |

---

## 👥 角色与职业

### 玩家队伍 (4人)

| 角色 | 职业 | 定位 | 技能 |
|------|------|------|------|
| 🗡️ **Warrior** | 战士 | 近战物理输出 | Slash（劈砍）、Cleave（横扫） |
| 🏹 **Ranger** | 游侠 | 远程物理输出 | 基础攻击 |
| 🔮 **Mage** | 法师 | 魔法输出 | FirePillar（火柱） |
| 🛡️ **Paladin** | 圣骑士 | 治疗/支援 | HolyLight（圣光）、HolyCircle（圣环） |

### 敌人 (3种)

| 敌人 | 技能 |
|------|------|
| 🟢 Slime（史莱姆） | Scratch（抓挠） |
| 🐗 Boar（野猪） | Swipe（猛击） |
| 🐺 Wolf（狼） | Scratch（抓挠） |

---

## 📋 已实现功能

- [x] 主菜单（开始游戏、加载存档）
- [x] 野外移动与场景交互
- [x] 宝箱开启
- [x] 存档点交互
- [x] 区域切换与地名显示
- [x] 随机/触发遇敌
- [x] 回合制战斗（攻击 / 技能 / 道具 / 防御）
- [x] 技能选择与目标选取
- [x] 回合顺序显示
- [x] 伤害/治疗浮动文字（含暴击）
- [x] 战斗结算（胜/败）
- [x] 经验值获取与进度条动画
- [x] 等级提升与属性成长
- [x] 技能随等级解锁
- [x] 多槽位手动存档/读档
- [x] 暂停菜单
- [x] 场景转场效果
- [x] 战斗失败后可加载存档

---

## 🚀 快速开始

### 环境要求

- **Unreal Engine 5.6** 或更高版本
- **Windows 10/11** (推荐) 或 Linux
- **Visual Studio 2022** (Windows 编译)
- 从 Epic Marketplace 安装 **PaperZD** 插件

### 运行步骤

1. **克隆仓库**
   ```bash
   git clone https://github.com/CoreCaster/LearnJRPG.git
   ```

2. **安装 PaperZD 插件**
   - 在 Epic Games Launcher 中前往 Marketplace
   - 搜索 "PaperZD" 并安装到 UE 5.4 引擎

3. **打开项目**
   - 双击 `LearnJRPG.uproject` 打开项目
   - 如提示需要重新编译，选择 "Yes"

4. **运行游戏**
   - 在编辑器中点击 ▶️ Play
   - 默认启动地图：`L_Field_IronWood`（铁木村）

### 操作方式

| 按键 | 功能 |
|------|------|
| `WASD` / 左摇杆 | 移动角色 |
| `E` / 交互键 | 与场景交互（开宝箱/存档） |
| `Esc` / 暂停键 | 打开暂停菜单 |
| `↑↓←→` / 方向键 | 战斗菜单导航 |
| `Enter` / 确认键 | 战斗菜单确认 |

---

## 🔧 技术要点

- **Input System**: 使用 Enhanced Input 系统，野外与战斗各自独立 Input Mapping Context
- **UI Framework**: 基于 CommonUI 的跨平台 UI 方案
- **Animation**: PaperZD 驱动的 2D 动画状态机
- **Data-Driven**: 所有角色属性、技能、道具、区域数据均通过 DataAsset 配置
- **Save System**: 基于 UE 原生 `USaveGame` 的多槽位序列化存档
- **Rendering**: 启用 Lumen 全局光照 + 硬件光线追踪 + TAA

---

## 📦 使用的插件

| 插件 | 来源 | 用途 |
|------|------|------|
| [PaperZD](https://www.unrealengine.com/marketplace/en-US/product/paperzd) | Epic Marketplace | 2D 动画状态机 |
| ModelingToolsEditorMode | 引擎内置 | 编辑器建模工具 |
| Enhanced Input | 引擎内置 | 增强输入系统 |
| CommonUI | 引擎内置 | 通用 UI 框架 |

---

## 📝 许可

本项目仅用于学习目的。

---

*Made with Unreal Engine 5.6 & BluePrint Visual Scripting*
