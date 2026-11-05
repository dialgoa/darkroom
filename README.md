# darkroom

基于 **SpektraLab** 开发的非官方 Android 胶片修图应用。

Android 版本维护与界面改造由 **抖音 • Oliver** 完成。

> **0.8.2 相机功能请暂时不要使用。** 已收到应用内相机拍摄的 JPG、RAW 分辨率与画质问题反馈，修复和真机验收将在后续版本进行。请先使用手机系统相机拍摄，再导入 darkroom 修图。当前 APK 仍保留相机入口。

## 下载和使用

当前版本为 **0.8.2 测试版**，安装文件名为 `darkroom-0.8.2.apk`。要求 Android 9 及以上、ARM64 设备，照片处理使用 Vulkan。

完整源码以 `darkroom-0.8.2-source.zip` 归档，和 APK 一起放在本仓库的 [Releases](https://github.com/dialgoa/darkroom/releases)。解压源码 ZIP 后可查看全部 Java / C++ 源码、原生引擎、资源、依赖和构建脚本。下载安装 APK 后，使用「导入照片」进入修图流程。胶片模拟、调整、边框、日期和导出的详细说明位于源码 ZIP 内的 `android/README.zh-CN.md`。

完整应用源码请下载 Releases 中的 `darkroom-0.8.2-source.zip`。GitHub 自动生成的 `Source code` 压缩包包含仓库文档和构建配置。

## 项目来源和署名

本项目基于 JamesQiu2005 及贡献者开发的 SpektraLab，复用了其 C++ 胶片模拟引擎与相关资源，并进行 Android 移植、界面与交互改造。原始项目、文档和版权署名均保留。

- 上游项目为 [JamesQiu2005/SpektraLab](https://github.com/JamesQiu2005/SpektraLab)。
- 胶片过程模型、原始实测配置与印相 LUT 的相关工作来自 Andrea Volpato 的 [spektrafilm](https://github.com/andreavolpato/spektrafilm)。
- Android 版本维护与界面改造署名为 **抖音 • Oliver**。

这是独立维护的衍生项目，SpektraLab 原作者与上游贡献者的版权、许可证和致谢按原文保留。上游介绍可参阅 [原英文 README](README.SpektraLab.md) 和 [原中文 README](README.SpektraLab.zh-CN.md)。

## 0.8.2 更新与已知问题

- 修正相机 Provia 100F 等反转片预览的显影路径，更新颜色缓存版本。
- 继承 0.8.1 的 JPG / RAW / JPG+RAW 选项与闪光灯图标。
- **已知问题仍包括相机 JPG、RAW 分辨率与画质异常，请暂时勿用相机。** 本版本没有完成这些问题的修复与真机验收。

完整版本说明见 Releases 页面。自动化检查不能替代手机实拍确认。

## 编译

固定使用 JDK 17、Gradle 8.9、Android SDK 35 与 Build Tools 35.0.0。解压 `darkroom-0.8.2-source.zip`，进入解压后的目录，然后执行以下命令，可以使用随源码保存的 ARM64 引擎构建 Android 界面并运行现有单元测试。

```bash
cd android
bash gradlew -PreuseEngine :app:assembleDebug :app:testDebugUnitTest :app:lintDebug
```

产物位于 `android/app/build/outputs/apk/debug/app-debug.apk`。Windows 可使用 `gradlew.bat`。需要从 C++ 源码重建引擎时，请按源码中的 `android/README.zh-CN.md` 安装固定版本 NDK 和 CMake，并移除 `-PreuseEngine`。

GitHub Actions 的 Android 工作流从 Release 下载并核验固定版本源码，只使用仓库读取权限，构建 APK、运行单元测试和 Lint，并保存构建报告。仓库保留标准开发签名以方便当前测试版覆盖升级。它的用途为测试构建，发布签名的设置见 Android 文档。

## 许可证

源码沿用 **GPL-3.0-or-later**，完整文本见 [LICENSE.txt](LICENSE.txt)。配置和 LUT 等资源遵循各自许可证，包括 CC BY-SA 4.0。第三方组件与资源的说明见 [NOTICE.txt](NOTICE.txt) 和源码 ZIP 内的 `android/licenses/`、`license/` 与上游资源目录。

APK 与对应源码一起提供。再分发时应保留上游版权、许可证与来源说明。

