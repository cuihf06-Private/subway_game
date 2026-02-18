# 地铁模拟器 - Subway Simulator

一个基于 Web 技术的地铁模拟器游戏，可以打包成 Android APK。

## 功能特性

- 🚇 真实的地铁进站、停靠、离站模拟
- 🚪 屏蔽门和列车门联动开关
- 🎵 真实的地铁音效（叮咚声、报站、开关门）
- 🗺️ 线路图显示
- 📱 支持移动端和桌面端
- 🤖 自动循环模式

## 在线体验

直接打开 `index.html` 文件即可在浏览器中体验。

## 项目说明

项目使用 Capacitor 将网页游戏打包成 Android APK。GitHub Actions 会在构建时自动创建 `www` 目录并复制所有网页资源，无需手动配置签名密钥。

## 打包成 Android APK

### 自动构建

每次推送到 `main` 分支都会自动触发构建并创建 Release：

```bash
git add .
git commit -m "你的提交信息"
git push origin main
```

构建完成后，会自动创建一个 prerelease，可以在 Releases 页面下载 APK。

### 创建正式版本

推送 tag 会创建正式版本的 Release：

```bash
git tag v1.0.0
git push origin v1.0.0
```

APK 会作为正式版本发布到 GitHub Releases 页面。

### 手动触发

在 GitHub Actions 页面点击 "Run workflow" 按钮。

## 本地开发

### 安装依赖

```bash
npm install
```

### 添加 Android 平台

```bash
npx cap add android
```

### 同步代码到 Android

首先创建 www 目录并复制文件：

```bash
mkdir -p www
cp index.html www/
cp *.mp3 www/
npx cap sync android
```

### 在 Android Studio 中打开

```bash
npx cap open android
```

## 项目结构

```
subway_game/
├── index.html              # 主游戏文件
├── *.mp3                   # 音效文件
├── package.json            # Node.js 配置
├── capacitor.config.json   # Capacitor 配置
└── .github/
    └── workflows/
        └── build-android.yml  # GitHub Actions 配置
```

## 技术栈

- HTML5 + CSS3 + JavaScript
- Capacitor 5.x（用于打包成原生应用）
- GitHub Actions（自动化构建）

## 许可证

MIT License
