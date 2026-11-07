# DSH Cua Driver 电脑操作

[English](README.en.md)

通过一个可同步的配置 bundle，启用 DSH 官方的 Cua Driver 原生提供方。插件只声明依赖和挂载配置，没有自己的 Host、客户端或构建步骤；工具、权限处理、输入执行、截图结果和卸载清理由官方组件负责。

## 使用

在提供 `tools` 和 `systemPrompt` 服务的 DSH profile 安装并启用此 bundle；标准 Web profile 已提供这些服务。使用现有插件同步器记录本插件仓库的完整 40 位 Git 提交，再由官方安装器安装。共享清单登记 `dsh-computer-use-cua`，不要把其 `@deepseek-ai/*` 依赖写入第三方插件清单。

启用前先停用其它电脑操作提供方，包括官方 macOS Computer Use bundle、Cua Driver MCP 以及手工挂载的 native 提供方。插件使用自己的稳定配置行 ID，不覆盖其它 bundle 的行。官方注册服务仅允许一个提供方，冲突时拒绝加载，不自动停用其它插件。

此 bundle 在 Host 顶层注册工具和指导，各 Agent 按 DSH 的作用域规则继承。它不选择或修改默认模型、preset、操作系统权限，也不预留桌面给某个会话。停用 bundle 后由官方生命周期撤销工具并关闭驱动；已经送达应用的输入不会回滚。多个会话使用同一个桌面时需要协调操作。

## 权限与截图

运行 DSH 的进程需要处于可用的图形桌面会话，并具备目标应用所需权限。Windows 的权限级别、应用类型和后台输入能力可能限制操作；驱动拒绝后台操作时，不自动改用前台操作或提升权限。

模型接收截图需要附件存储和明确声明图像输入的模型路由。工具加载或权限检查成功，不等于模型能看到截图，也不等于目标应用的点击、键盘和窗口读取已验收。

## 同步与版本

包声明固定的官方依赖 `0.2.2-rc.1`，原生提供方当前依赖 Cua Driver `0.28.0`。保留 npm optional dependencies，以安装对应平台的原生运行库。

源码 Web 环境的同步器会按接收机实际 DSH 源码对齐官方依赖；本插件的 Git pin 固定配置内容，不能固定另一台电脑的官方源码与驱动版本。每台接收机需核对最终解析来源、版本、加载状态和桌面操作效果。不要把本机源码链接写进共享插件来源。

## 验证范围

Windows x64、Node `24.15.0`、pnpm `11.28.5`、DSH `0.2.2-rc.1` 和 Cua Driver `0.28.0` 已完成官方原生 SDK 只读 e2e、独立 Web 预览、启停生命周期、正式加载与共享清单发布验证。驱动发现 56 个工具，只读窗口查询成功；正式服务中的两个官方组件均运行，原有会话保留。已安装和共享的运行版本固定为 `b293c1c446c1437cfd304ea7b9924f2fb3f0754c`；本次后续提交只补充验证说明，不改变运行配置。没有截图、鼠标键盘输入或模型调用，其它电脑尚未验收。接收机在现有同步器执行“检查更新 → 拉取并应用”，再核对本机加载与桌面权限。详见 [tested-environment.json](tested-environment.json)。

官方能力与限制见 [DSH Computer use](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/subsystems/computer-use.md) 和 [Cua Driver 0.28.0](https://github.com/trycua/cua/tree/cua-driver-rs-v0.28.0/libs/cua-driver)。官方依赖保留各自作者与许可证；本仓库保持私有。
