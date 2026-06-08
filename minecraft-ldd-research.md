# Minecraft 建造规划器 — 市场调研报告

> 调研日期：2026-06-08 | 作者：Fragile-373

---

## 一、市场盘子

Minecraft 2026 年仍处于巅峰期：

| 指标 | 数据 |
|------|------|
| 月活用户 (MAU) | ~2.12 亿 |
| 总销量 | 3.5 亿+（史上最高） |
| 日均活跃 | ~3,196 万 |
| PC Java 版占比 | ~32%（约 6,800 万 MAU） |
| 2025 Q1 峰值 MAU | 2.225 亿（电影效应） |

Java 版用户是这款工具的核心目标群体——他们使用模组、下载 schematic、搞建筑。

建筑是 Minecraft 最核心的玩法之一。Planet Minecraft 等 schematic 分享站是社区主流节点，Litematica（全息蓝图模组）在 CurseForge 上有巨大下载量——**「人们需要建筑规划工具」是已验证的需求**。

Sources:
- [Minecraft User and Revenue Statistics (2026) — Host Havoc](https://hosthavoc.com/blog/minecraft-statistics)
- [Minecraft Active Player Count — MMO Stats](https://mmostats.com/game/minecraft)

---

## 二、竞品全景与缺口

按从「游戏内工具」到「外部独立工具」的光谱排列：

| 类别 | 代表产品 | 形态 | 核心缺陷 |
|------|---------|------|---------|
| 游戏内模组 | WorldEdit / Litematica | 模组 | 必须在游戏内操作，无法离线规划 |
| 浏览器编辑器 | Cubical.xyz | Web (WebGL) | 最接近 LDD 设想，但已半废弃，需 archive.org 访问 |
| 开源协作编辑器 | MCWebEdit | Web + 后端 | 需部署 Node.js + MongoDB，面向协作而非个人 |
| 蓝图导出工具 | Schematic2Blueprint | Java 桌面 | 只做 schematic→图层图片单向转换，不能交互编辑 |
| 通用体素编辑器 | MagicaVoxel / Goxel / VengiVoxEdit | 桌面 | 艺术家工具，缺少 Minecraft 方块体系、放置逻辑、图层教学功能 |
| 通用体素编辑器 | Avoyd | 桌面 (付费 €15) | 可导入 Minecraft 地图，支持巨大场景 (256k³)，但非面向建筑教学 |
| 第一人称编辑器 | Woxel | 桌面 | Minecraft 式操控，开放获取，但功能偏简单 |
| 手机蓝图 | NOOBO (Android) | 移动端 | 预置蓝图库，用户不能自己设计 |
| 游戏内蓝图 | Litematica 分层模式 | 模组 | 全息投影叠加，适合跟随建造，不适合制作教学材料 |
| 游戏内设计 | Architect Block Mod | Fabric 模组 | 3D 网格设计系统 (16×16×16 / 32×32×32)，游戏内设计再一键建造 |

**核心缺口：没有一个工具能同时做到「像 LDD 那样交互式搭建 + 像乐高说明书那样分层导出教学」。**

Cubical.xyz 曾是最接近的——20+ 笔刷工具、Minecraft 式操控、schematic 导入导出、自定义主题和渲染——但它已停止维护。Schematic2Blueprint 能出图层图但不能交互编辑。MagicaVoxel 能编辑但不是 Minecraft 原生体验。

这个交集目前是空白的。

Sources:
- [Cubical.xyz — Minecraft 3D Schematic Creator (Archive)](https://web.archive.org/web/20250223154938/https://cubical.xyz/)
- [MCWebEdit — Browser-based collaborative voxel editor](https://github.com/atomdellow/MCWebEdit)
- [Schematic2Blueprint — GitLab](https://gitlab.com/Pit64/schematic2blueprint)
- [MagicaVoxel vs Voxel comparison — Slant](https://www.slant.co/versus/5460/5450/~voxel_vs_magicavoxel)
- [Woxel — Minecraft-like voxel editor](https://woxel.net/)
- [NOOBO — Minecraft Building Guide (Google Play)](https://play.google.com/store/apps/details?id=com.icystudios.noobo)
- [Architect Block — Modrinth](https://modrinth.com/mod/advance-architect-block)

---

## 三、产品定位

> **LDD for Minecraft**：打开软件 → 从方块面板选材 → 在 3D 网格中搭建 → 支持图层系统 → 一键导出「乐高说明书式」分层建造指南

### 三个核心差异化点

**1. 图层教学系统。** 目前没有任何工具把「图层→说明书」作为核心功能。乐高说明书的精髓是「每步只加几块，从下往上逐层推进」。Minecraft 建筑教程（B站/YouTube）基本都是视频形式，没人做成分步静态说明书。建筑类 UP 主和服务器建筑团队是天然的目标用户。

**2. Java 版放置逻辑。** 方块朝向（楼梯、活塞、原木的方向）、含水状态、半砖叠加——这些 Java 版的特性在通用体素编辑器里完全没有。适配这些规则后，建筑导出就能直接对应游戏内操作，不需要玩家自己脑补转换。

**3. 模组方块支持。** 能导入模组的方块定义（通过读取 mod jar 或资源包），覆盖玩家使用各种模组（Chisel & Bits、Create、家具模组等）搭建的需求。这是桌面端的独特优势——网页工具无法访问本地模组文件。

---

## 四、商业价值判断

### 初步结论：短期直接变现有限，中期有机会

**不利因素：**
- Minecraft 玩家习惯了免费工具（WorldEdit、Litematica、Cubical.xyz 全是免费的）
- Mojang 的 EULA 对「Minecraft 相关」付费产品有商标使用限制
- 桌面软件付费转化率天然低于 SaaS，一次性买断模式天花板低

**有利因素：**
- 目标人群庞大（Java 版 6,800 万 MAU），即使 0.1% 转化也有 6.8 万用户
- 建筑类 YouTuber / B站 UP 主是有付费意愿的创作者群体（他们需要制作教程）
- Schematic2Blueprint 验证了「建筑教学」方向有需求
- NOOBO 在 Google Play 的存在证明移动端有人为此付费

### 推荐商业模式

| 阶段 | 策略 | 定价 |
|------|------|------|
| MVP | 免费开源，GitHub 发布，积累种子用户和反馈 | 免费 |
| 成长期 | 基础版免费 + Pro 版付费（模组方块导入 + 高级导出格式 + 动画说明书 + 材质包支持） | $9.99–$19.99 买断 或 $3.99/月 |
| 成熟期 | 社区市场：用户上传/售卖建筑蓝图，平台抽成 | 30% 平台抽成 |

建筑教学场景不容低估——B站 Minecraft 建筑教程播放量动辄几十万，YouTube 上更是千万级。如果头部 UP 主用这款工具制作说明书，本身就是最好的推广渠道。

---

## 五、技术可行性

| 需求 | 推荐方案 | 说明 |
|------|---------|------|
| 3D 渲染 | Three.js（已验证）或 Rust + wgpu | Three.js 已有 pixel-ring 项目的实战基础 |
| 桌面打包 | Tauri | 比 Electron 轻量，安装包小，Rust 后端性能好 |
| Java 版方块数据 | 解析 Minecraft jar 中 blockstates JSON | Mojang 公开格式，可自动提取 |
| 模组方块 | 解析 Fabric/Forge mod jar 注册表 | 需持续维护各模组加载器兼容性 |
| 图层说明书导出 | Canvas / Sharp 渲染逐层俯视图 + PDF 生成 | 2D 俯视图 + 材料清单 + 步骤标注 |
| 跨平台 | Tauri + Rust → Windows / macOS / Linux | 一次开发三端覆盖 |

---

## 六、核心风险

1. **Mojang 商标/EULA 风险。** 不能叫「Minecraft LDD」，不能直接内置 Minecraft 的方块纹理（需让用户自行导入资源包）。品牌隔离要仔细设计。

2. **模组方块兼容性。** Forge / Fabric / Quilt 生态碎片化，每个版本的方块注册表格式不同，维护模组方块数据库是持续的体力活。建议 MVP 只做原版方块。

3. **用户习惯迁移。** 玩家习惯在游戏内建造（即时反馈 + 沉浸感），能否让他们切换到「先规划再建造」的流程，需要产品设计验证。Litematica 的流行说明全息投影叠加更符合现有习惯。

4. **竞争风险。** 如果 Mojang/Microsoft 在官方启动器中加入类似功能（类似 Bedrock 版的 structure block 增强版），独立工具的价值会被大幅削弱。

---

## 七、MVP 建议范围

| 包含 | 不包含 |
|------|--------|
| 3D 网格搭方块（原版方块） | 模组方块 |
| 图层管理（添加/删除/重排层） | 红石/命令方块逻辑 |
| 导出分层说明书 PNG/PDF | 动画视频导出 |
| 用户自行导入资源包渲染 | 内置 Minecraft 纹理 |
| schematic 导入/导出 | 多人协作 |
| 撤销/重做 | Marketplace |
| Windows / macOS / Linux | 移动端 |

---

## 八、总结

**有搞头，但有条件。**

直接对标 LDD 做「全功能 Minecraft 建造器」会陷入与 WorldEdit / Litematica / Cubical.xyz 的功能军备竞赛。真正的蓝海是**「图层教学说明书」**——目前整个生态里没有人做好的事情。

建议路径：MVP 免费开源验证需求 → Pro 版付费解锁高级功能 → 社区市场做平台。

如果能把「建筑教学」这个场景做透，让 B站/YouTube 的建筑 UP 主把它当作标配工具，这个产品就有护城河。
