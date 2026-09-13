# 盯盘 APP - Android 构建说明

## 🚀 GitHub Actions 自动编译（推荐）

1. 在 GitHub 创建一个新仓库（比如 `stock-float`）
2. 把 `android/` 目录下的所有文件推到仓库
3. 推送后 GitHub Actions 自动编译 APK
4. 在仓库的 **Actions** 页签 → 最新构建 → **Artifacts** 下载 APK

```bash
cd android
git init
git add .
git commit -m "init"
git remote add origin https://github.com/你的用户名/stock-float.git
git push -u origin main
```

APK 编译完成后，在仓库页面：**Actions** → 点击最新构建 → 下方 **Artifacts** → 下载 `StockFloat-debug`

## 🛠️ 本地编译

需要：
- JDK 17+
- Android SDK（通过 Android Studio 安装）

```bash
cd android
chmod +x gradlew
./gradlew assembleDebug
# APK 生成在 app/build/outputs/apk/debug/
```

## 📱 安装到手机

```bash
adb install app/build/outputs/apk/debug/app-debug.apk
```

或者直接把 APK 文件传到手机，点击安装。

## 📦 项目结构

```
android/
├── app/
│   ├── src/main/
│   │   ├── assets/          ← 网页资源（index.html 等）
│   │   ├── java/.../        ← MainActivity（WebView 壳）
│   │   ├── res/             ← 图标、主题
│   │   └── AndroidManifest.xml
│   ├── build.gradle
│   └── proguard-rules.pro
├── .github/workflows/       ← 自动编译配置
├── build.gradle
├── settings.gradle
└── gradlew
```

## ✨ 特性

- 原生 Android APP（WebView 壳）
- 全屏沉浸式
- 支持 A 股 / 港股实时行情
- 折叠屏适配
- 离线可用
- APK 体积 < 2MB
