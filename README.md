<p align="center">
  <img src="assets/qf-banner.svg" width="100%" alt="清风工具箱"/>
</p>

<p align="center">
  <a href="https://github.com/qingfengOfficial/qingfeng-kit/releases/latest">
    <img src="https://img.shields.io/github/v/release/qingfengOfficial/qingfeng-kit?style=flat-square&label=最新版本&color=00bcd4" alt="release"/>
  </a>
  <img src="https://img.shields.io/github/downloads/qingfengOfficial/qingfeng-kit/total?style=flat-square&label=总下载&color=4dd0e1" alt="downloads"/>
  <img src="https://img.shields.io/badge/Android-10%2B-3ddc84?style=flat-square&logo=android&logoColor=white" alt="Android 10+"/>
  <img src="https://img.shields.io/badge/语言-Kotlin-7f52ff?style=flat-square&logo=kotlin&logoColor=white" alt="Kotlin"/>
  <img src="https://img.shields.io/badge/UI-Compose%20%2F%20Material3-4dd0e1?style=flat-square" alt="Compose"/>
</p>

**多合一 Android 工具箱**：音乐 · 阅读 · 天气 · 红外 · 桌面组件 · 自动化，一个 App 全搞定。Jetpack Compose 原生开发，无 WebView 套壳。

> 本仓库同时作为 **App 内更新检查** 源：客户端启动时读取本仓库 `/releases/latest`，发现新版本即弹窗提示。

---

## ✨ 功能亮点

| 模块 | 功能 |
|------|------|
| 🎵 **音乐** | LX 音源生态（多平台源）、三源快速竞速取链、自动换源续播、**MusicSourceScheduler 来源调度**（来源记忆/健康快照/临时熔断/并发预算）、高品质下载（内嵌封面+歌词）、独立下载队列、歌词缓存落盘 + **LrcLib 歌词库**、通知栏播放控制（锁屏/蓝牙线控）、智能省流、**均衡器、账号中心、取链全链路 Trace ID + 日志脱敏** |
| 📖 **阅读** | 书源搜索（JS / CSS / JSONPath / XPath / 正则）、**Legado 规则引擎全源码移植（94 文件）**、独立 **ReaderJsEngine**（QuickJS 隔离执行 + 超时 + 内存上限）、书源导入、**Cookie 桥（起点等站点 Cookie 自动注入）、书源分组、探索页** |
| 📁 **文件传输** | **局域网快传**：LocalSend v2.2 兼容、**独立 mTLS 加密入口**（证书指纹固定）、**清风断点续传 V1**（4 MiB 分块 / checkpoint / SHA-256 校验）、连接限流（64 会话 / 单 IP 8）、传输提速、接收进度与 Trace ID |
| 🎬 **视频** | **视频客户端**：媒体服务器连接、TMDB API、OVP URL 安全校验 |
| 🌤 **天气** | 逐时/7 日预报、多城市、动态 Hero 图标、桌面小组件、后台自动刷新 |
| 🔧 **工具** | 红外遥控（真实 NEC 帧发送）、指南针、垃圾清理、计算器、单位换算、二维码、噪声仪、健康管理、文件工具、**备份恢复、全局搜索、工作台** |
| 📱 **桌面组件** | **小组件中心**、Glance 桌面小组件（天气/步骤/音乐/工具）、**原生组件预览、组件固定（Pin）** |
| ⚙️ **其他** | 120Hz 高刷、全局转场动画开关、设计规范预览、启动闪屏动画、动态取色主题、App 内更新检查 |

---

## ⬇️ 下载安装

| 版本 | 说明 | 链接 |
|------|------|------|
| **v2.2**（最新 Release） | 局域网快传重整（mTLS+断点续传V1）+ 音乐链路整改 | [GitHub Release](https://github.com/qingfengOfficial/qingfeng-kit/releases/tag/v2.2) |
| v2.1 | 音乐深度优化 + 通知栏升级 + 性能优化 | [GitHub Release](https://github.com/qingfengOfficial/qingfeng-kit/releases/tag/v2.1) |
| v2.0 | 多音源并发 + 高品质下载内嵌封面歌词 | [GitHub Release](https://github.com/qingfengOfficial/qingfeng-kit/releases/tag/v2.0) |
| v1.0 | 初版：工具集 + 原子组件 | [GitHub Release](https://github.com/qingfengOfficial/qingfeng-kit/releases/tag/v1.0) |

- **直接下载 APK**：`qingfeng-kit-v2.2-release.apk`（约 155 MB）
  https://github.com/qingfengOfficial/qingfeng-kit/releases/download/v2.2/qingfeng-kit-v2.2-release.apk
- **源码包**：按版发布（已剔除 `keystore` / `local.properties` 等敏感文件；v2.2 未附带源码包）
- 安装后进入 App，`设置 → 检查更新` 可手动校验版本

> 📌 APK 体积较大（含 ffmpeg-kit / PDFBox / Legado 引擎等完整能力），请耐心等待下载。

---

## 🏗 本地构建

```bash
# 环境要求
#   JDK 17 · Gradle 8.11.1 · AGP 8.7.3 · Kotlin 1.9.20

export JAVA_HOME=<你的 JDK 17 路径>
./gradlew :app:assembleDebug        # Debug 包
./gradlew :app:assembleRelease      # Release 包（需配置 release 签名）
```

- 模块：`app`（主工程） + `module-chart`（图表模块）
- Release 签名：`app/release.keystore`（alias `toolbox`），凭据从 `local.properties` 的 `RELEASE_*` 读取
- 当前 Release 构建关闭 R8（`isMinifyEnabled=false`），避免 ffmpeg-kit / PDFBox 等可选依赖缺类问题

---

## 📜 版本历史

- **v2.2**（2026-11-08）：局域网快传重整（mTLS 独立入口 + 连接限流 + 传输提速 + 断点续传 V1）、音乐链路整改（Trace ID/安全续播/来源调度）、播放队列确认、视频客户端、书源增强
- **v2.1**（2026-10-06）：音乐模块深度优化（智能省流/播放加速/自动换源/下载队列/歌词持久化）、通知栏升级（封面+线控）、性能优化、动画增强、启动更新检查
- **v2.0**（2026-10-05）：多音源并发取链、高品质下载（内嵌封面歌词）、发现页搜索、红外 NEC 真实帧、坏码库自动升级
- **v1.0**（2026-09-12）：初版交付，工具集 + 桌面原子组件 + 更新检查链路

---

## 🛡 安全说明

- 发布到本仓库的**源码包已剔除签名密钥**（`*.keystore` / `*.jks` / `*.p12` / `local.properties`），请勿以任何形式提交敏感凭据
- 仓库仅托管编译产物与源码，不收集任何用户数据

---

## 📄 License

自定义开源许可协议（见 [LICENSE](LICENSE)）