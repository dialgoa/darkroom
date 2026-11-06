# darkroom

基于 **SpektraLab** 开发的非官方 Android 胶片修图应用。

Android 版本维护与界面改造由 **抖音 • Oliver** 完成。

> **最新：0.8.2 fix2 修复验证版，应用内相机暂未开放。** 请使用手机系统相机拍摄，再导入 darkroom 修图。原 0.8.2 的 JPG、RAW 分辨率与画质问题仍待后续修复和真机验收。

## 开源声明与非商业倡议 | Open Source & Non-Commercial Appeal

**Darkroom 是一款免费、开源的 Android 胶片摄影与照片编辑应用。** 本项目基于 SpektraLab，Android 版本维护与界面改造由 **抖音 • Oliver** 完成。

作者明确反对第三方倒卖本项目 APK、通过收费包装误导用户、冒充项目官方或虚假宣称独家授权，并倡议保持免费分享、透明协作与尊重贡献者的开源精神。

欢迎学习、修改、贡献及依照适用许可证再分发。请保留应有的上游版权、许可证和来源说明。

**许可证说明：** 本项目沿用 GPL-3.0-or-later 等适用许可证；以上非商业倡议表达维护者立场，**不构成额外的许可限制**。GPL 允许符合其条款的商业使用与再分发。

## 下载和使用

最新发布为 **[0.8.2 fix2 修复验证版（Pre-release）](https://github.com/dialgoa/darkroom/releases/tag/v0.8.2-fix2)**，安装文件名为 `darkroom0.8.2.fix2.apk`。要求 Android 9 及以上、ARM64 设备，照片处理使用 Vulkan。

**fix2 为独立验证包**：内部版本 `0.8.2-fix2`，版本代码 `22`，包名 `com.gapetes.spectraldarkroom.validation`。它与原版分开安装、可共存，不会覆盖原版或自动迁移原版照片库与设置。

APK 大小为 29,121,127 字节，SHA-256 为 `20e446148d355a1f08b08a41c548c6242d2988604ef2d273452d895d76857606`。

原版 **0.8.2** 的完整源码以 `darkroom-0.8.2-source.zip` 归档，和原版 APK 一起保留在本仓库的 [v0.8.2 Release](https://github.com/dialgoa/darkroom/releases/tag/v0.8.2)。解压源码 ZIP 后可查看全部 Java / C++ 源码、原生引擎、资源、依赖和构建脚本。下载安装 APK 后，使用「导入照片」进入修图流程。胶片模拟、调整、边框、日期和导出的详细说明位于源码 ZIP 内的 `android/README.zh-CN.md`。

**本次 fix2 上传仅提供 APK，对应完整源码未随本次文件提供。** `darkroom-0.8.2-source.zip` 属于原 0.8.2，不能视为与 fix2 APK 完全对应。GitHub 自动生成的 `Source code` 压缩包包含仓库文档和构建配置。

## 项目来源和署名

本项目基于 JamesQiu2005 及贡献者开发的 SpektraLab，复用了其 C++ 胶片模拟引擎与相关资源，并进行 Android 移植、界面与交互改造。原始项目、文档和版权署名均保留。

- 上游项目为 [JamesQiu2005/SpektraLab](https://github.com/JamesQiu2005/SpektraLab)。
- 胶片过程模型、原始实测配置与印相 LUT 的相关工作来自 Andrea Volpato 的 [spektrafilm](https://github.com/andreavolpato/spektrafilm)。
- Android 版本维护与界面改造署名为 **抖音 • Oliver**。

这是独立维护的衍生项目，SpektraLab 原作者与上游贡献者的版权、许可证和致谢按原文保留。上游介绍可参阅 [原英文 README](README.SpektraLab.md) 和 [原中文 README](README.SpektraLab.zh-CN.md)。

## 0.8.2 fix2 更新

与原版 APK 对比确认的变化：

- 相机入口改为“待开发”及对应提示，当前使用导入照片进行修图。
- 更新照片解码、编辑重置与片边设置相关实现，补充双张半格和追加导入的操作提示。
- 更新原生引擎及片边光照 Vulkan 着色器，包含常规、兼容和分段处理版本。
- 更新印字字体处理，补充 Imprint 字体、DejaVu 和 stb 的许可文件。
- 相关界面署名统一为 **抖音 • Oliver**，保留基于 SpektraLab 的来源说明。

已核对 APK 结构、ZIP CRC 完整性、版本信息及 SHA-256；本次仅重命名上传，未改动 APK 内容。真机色彩、稳定性和完整导出仍待验收，详细内容见 [fix2 发布说明](https://github.com/dialgoa/darkroom/releases/tag/v0.8.2-fix2)。

## 0.8.2 原版更新与已知问题

- 修正相机 Provia 100F 等反转片预览的显影路径，更新颜色缓存版本。
- 继承 0.8.1 的 JPG / RAW / JPG+RAW 选项与闪光灯图标。
- **已知问题仍包括相机 JPG、RAW 分辨率与画质异常，请暂时勿用相机。** 本版本没有完成这些问题的修复与真机验收。

完整版本说明见 Releases 页面。自动化检查不能替代手机实拍确认。

## 编译

以下构建流程针对已提供源码的 **原版 0.8.2**，不代表能重现本次 fix2 APK。

固定使用 JDK 17、Gradle 8.9、Android SDK 35 与 Build Tools 35.0.0。解压 `darkroom-0.8.2-source.zip`，进入解压后的目录，然后执行以下命令，可以使用随源码保存的 ARM64 引擎构建 Android 界面并运行现有单元测试。

```bash
cd android
bash gradlew -PreuseEngine :app:assembleDebug :app:testDebugUnitTest :app:lintDebug
```

产物位于 `android/app/build/outputs/apk/debug/app-debug.apk`。Windows 可使用 `gradlew.bat`。需要从 C++ 源码重建引擎时，请按源码中的 `android/README.zh-CN.md` 安装固定版本 NDK 和 CMake，并移除 `-PreuseEngine`。

GitHub Actions 的 Android 工作流从 Release 下载并核验固定版本源码，只使用仓库读取权限，构建 APK、运行单元测试和 Lint，并保存构建报告。仓库保留标准开发签名以方便当前测试版覆盖升级。它的用途为测试构建，发布签名的设置见 Android 文档。

## 许可证

源码沿用 **GPL-3.0-or-later**，完整文本见 [LICENSE.txt](LICENSE.txt)。配置和 LUT 等资源遵循各自许可证，包括 CC BY-SA 4.0。第三方组件与资源的说明见 [NOTICE.txt](NOTICE.txt) 和源码 ZIP 内的 `android/licenses/`、`license/` 与上游资源目录。

原 0.8.2 的 APK 与对应源码保留在其 Release；fix2 对应源码的提供情况见上文。再分发时应保留上游版权、许可证与来源说明。

