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

项目使用 Capacitor 将网页游戏打包成 Android APK。所有网页资源（HTML、音频文件）会在构建时自动复制到 `www` 目录，该目录已添加到 `.gitignore` 中。

## 打包成 Android APK

### 前置要求

1. 生成签名密钥（用于签名 APK）：

```bash
keytool -genkey -v -keystore release.keystore -alias release -keyalg RSA -keysize 2048 -validity 10000
```

2. 将密钥转换为 Base64：

```bash
base64 release.keystore > release.keystore.base64
```

3. 在 GitHub 仓库设置中添加以下 Secrets：
   - `SIGNING_KEY`: release.keystore.base64 文件的内容
   - `ALIAS`: 密钥别名（例如：release）
   - `KEY_STORE_PASSWORD`: keystore 密码
   - `KEY_PASSWORD`: 密钥密码

### 触发构建

有两种方式触发 APK 构建：

#### 方式 1: 创建 Git Tag（推荐）

```bash
git tag v1.0.0
git push origin v1.0.0
```

#### 方式 2: 手动触发

1. 进入 GitHub 仓库的 Actions 页面
2. 选择 "Build Android APK" workflow
3. 点击 "Run workflow" 按钮

### 下载 APK

构建完成后，APK 文件会自动发布到 GitHub Releases 页面。

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

```bash
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
