# Aseprite Github Actions Builder

[English](https://github.com/WenqiOfficial/aseprite_builder/blob/master/README.md) | [简体中文](https://github.com/WenqiOfficial/aseprite_builder/blob/master/README-chs.md)

# 实现功能
通过Github Actions自动构建macOS、Ubuntu、Windows的Aseprite</br>
不包含任何恶意代码</br>
可选构建后的程序文件不会公开发布.</br>
可选仅在Actions draft可见(仅库所有者可见).

# 使用方法
1. Clone 或者 Fork 本仓库.
2. 按照你的需求编辑Actions配置文件 `/.github/workflows/aseprite_build_deploy.yml`
3. 编辑 **os** 行，选择你需要构建的平台.(可选)

        strategy:
            matrix:
                os: [windows-latest, ubuntu-latest, macOS-latest]
4. 保存并提交.
5. 前往 Actions 并启用.
8. 等待自动构建或是手动开始构建.
9. 从 Github Release 找到构建完成的文件.
        
# 代码实现
Actions 代码参照 [Aseprite repo](https://github.com/aseprite/aseprite/blob/master/INSTALL.md)

1. 每日定时检查、当本仓库有新提交、手动执行时便会与上游仓库Release对比.
2. 当上游仓库存在新的Release时将会启动执行系统版本的构建任务.

构建过程：
1. 从缓存获取 Skia.
2. 使用 CMake & Ninja 构建.
3. 将构建好的文件打包并上传至仓库Release中.

# 附加说明

**如果运行构建好的文件出现 `libcrypto-1_1-x64.dll` 文件报错**

1. 下载 [libcrypto-1_1-x64.dll](https://github.com/WenqiOfficial/aseprite_builder/raw/master/libcrypto-1_1-x64.dll).
2. 将 `libcrypto-1_1-x64.dll` 放至 `C:\Windows\System32` 中.

**中文汉化包**
[Aseprite-Simplified-Chinese](https://github.com/J-11/Aseprite-Simplified-Chinese/blob/master/README.md).

# 构建用时
Github每月会提供2000分钟的Actions余额(应该够用了...吧).</br>
不同系统的构建任务同样会消耗不同的Actions余额 [billing for GitHub Actions](https://help.github.com/en/github/setting-up-and-managing-billing-and-payments-on-github/about-billing-for-github-actions#about-billing-for-github-actions)</br>
构建所有系统大约会消耗 114 分钟余额 (12 * 2 + 10 * 1 + 8 * 10)</br>
总之还是推荐用到什么系统就构建对应系统.

|系统|用时(分钟)|倍率
|---|---|---|
|Windows|12|2|
|Ubuntu|10|1|
|macOS|8|10|

# 参考的其他库
- [aseprite-macos-buildsh](https://github.com/haxpor/aseprite-macos-buildsh)
- [action_aseprite](https://github.com/Insouciant21/action_aseprite)

# 支持 Aseprite 开发！
[Buy Aseprite](https://aseprite.org/#buy)
