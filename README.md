# 3Dsolar（3D 模拟太阳系）

> 基于 React 架构的 3D 模拟太阳系，并附带多个独立 Three.js 演示页面。

## 项目简介

**3Dsolar** 是一套 3D 太阳系模拟项目，包含两部分：

1. **`solar-3d-react`** —— 主程序，采用 **React + Vite + Three.js** 构建，提供完整的控制面板与星球信息交互。
2. **`solar_3d_001 / 002 / 003.html`** —— 三个独立的单文件演示页，通过 CDN 引入 Three.js（r128）与 OrbitControls，**打开即看**，方便快速体验。

在线演示默认展示主程序 `solar-3d-react` 构建后的效果。

## 功能特性

### 主程序（solar-3d-react）
- ☀️ **完整太阳系**：太阳、八大行星、月球等天体，按真实比例参数建模与运行。
- ⏯️ **时间控制**：暂停 / 继续、调节时间流速，观察行星公转与自转。
- 🛰️ **轨道与星空**：可切换显示行星轨道线、背景星空。
- 🔍 **显示选项**：行星名称标注、全局缩放（global scale）等。
- 🪐 **点击查询**：点击任意行星 / 太阳 / 月球，弹出资料卡，展示真实直径、距日距离、公转周期、自转周期、表面温度、卫星数量、大气等信息。
- 🎵 **背景音乐**：内置可开关的环境音乐。

### 独立演示页（solar_3d_001 / 002 / 003.html）
- 单文件、零安装：通过 CDN 加载 Three.js r128 + OrbitControls。
- 鼠标拖拽旋转、滚轮缩放，直观查看太阳系运行。

## 技术栈

| 部分 | 技术 |
|---|---|
| 主程序 | React 18、ReactDOM 18、Three.js 0.160、Vite 5 |
| 独立演示页 | Three.js r128（CDN）+ OrbitControls（CDN） |
| 数据 | `src/data/planetData.js`（行星真实参数） |

## 目录结构

```
3Dsolar/
├── solar-3d-react/            # 主程序（React + Vite + Three.js）
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   ├── public/
│   └── src/
│       ├── App.jsx            # 顶层组件：状态与交互编排
│       ├── main.jsx           # 入口
│       ├── components/        # ControlPanel / PlanetInfo / PlanetLabels / StatusDisplay
│       ├── three/             # SolarSystemScene + planets/ + sun/ + utils/
│       ├── data/              # planetData.js 行星数据
│       └── styles/
├── solar_3d_001.html          # 独立 Three.js(r128) 演示页
├── solar_3d_002.html
├── solar_3d_003.html
└── 星球贴图链接汇总.txt         # 星球贴图资源链接汇总
```

## 本地运行

### 主程序（solar-3d-react）
```bash
cd solar-3d-react
npm install
npm run dev      # 启动开发服务器，按终端提示打开本地地址
# 生产构建：
npm run build
npm run preview
```

### 独立演示页
无需安装，直接用浏览器打开对应 HTML 文件即可：
```bash
# 也可起本地服务器后访问
python -m http.server 8080
# 浏览器打开 http://localhost:8080/solar_3d_001.html
```

## 在线演示

🌐 https://chenbenkong.github.io/3Dsolar/

## 说明 / 备注

- 行星尺寸与轨道距离在视觉上做了压缩（否则太阳系将空旷到无法同框），但运动关系与参数均基于真实天文数据。
- 独立演示页依赖公共 CDN 加载 Three.js，运行时需联网。
