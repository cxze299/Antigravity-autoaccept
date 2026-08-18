# Antigravity-AutoAccept

> 🚀 一键开启 Antigravity 客户端的“全自动无人值守”模式 (YOLO Mode)

这是一个用于 **Antigravity** 客户端的自定义配置文件。通过修改全局权限和执行策略，它可以彻底关闭 AI 代理在执行命令、读写文件时的确认弹窗，实现真正的全自动运行。

## ✨ 特性 (Features)

* **🚫 零弹窗打断**：开启 `CASCADE_COMMANDS_AUTO_EXECUTION_ON`，多步任务连续执行。
* **🔓 终极文件权限**：配置通配符 `read_file(*)` 和 `write_file(*)`，允许跨系统无缝读取和修改文件。
* **💻 终端免审批**：支持 `command(*)` 和 `unsandboxed(*)`，自动运行所有脚本和命令。
* **⚡ 加速执行**：浏览器和产物审查均开启 Turbo 模式，提升整体响应和执行速度。

## ⚙️ 配置文件 (config.json)

你可以直接使用以下配置来覆盖默认设置。

```json
{
  "userSettings": {
    "artifactReviewMode": "ARTIFACT_REVIEW_MODE_TURBO",
    "autoExecutionPolicy": "CASCADE_COMMANDS_AUTO_EXECUTION_ON",
    "browserJsExecutionPolicy": "BROWSER_JS_EXECUTION_POLICY_TURBO",
    "enableTerminalSandbox": false,
    "globalPermissionGrants": {
      "allow": [
        "read_file(*)",
        "write_file(*)",
        "command(*)",
        "unsandboxed(*)"
      ]
    },
    "nonWorkspaceFileAccessPolicy": "AGENT_SETTING_POLICY_ALLOW",
    "queuedMessageDeliveryStrategy": "MESSAGE_DELIVERY_STRATEGY_WHEN_IDLE",
    "remoteControlHostname": "YOUR_HOSTNAME_HERE",
    "useAiCredits": false
  }
}
```

## 🚀 如何获取并修改你的主机名？(重要)

**【极度重要】你必须将上方配置文件中的 `"YOUR_HOSTNAME_HERE"` 更改为你自己电脑的实际主机名！** 如果不修改或填错，可能会导致客户端识别失败或连接异常。

### 1. 推荐方案（最简单安全）
直接保留你原本 `config.json` 里 `"remoteControlHostname"` 字段原有的值，**不要用我的模板去覆盖它**。只修改其他权限相关的字段。

### 2. 手动获取方案（如果你不小心覆盖了）
如果你需要重新填写，可以通过以下方式查询你的电脑主机名：

*   **🪟 Windows:** 
    1. 按 `Win + R`，输入 `cmd` 并回车打开命令提示符。
    2. 输入 `hostname` 并回车，显示出来的英文/数字组合就是你的主机名。
*   **🍎 macOS / 🐧 Linux:** 
    1. 打开“终端 (Terminal)”。
    2. 输入 `hostname` 并回车即可查看。

### 3. 修改配置
获取到主机名后（例如查出是 `DESKTOP-ABC1234`），将配置代码中的对应行改为：
`"remoteControlHostname": "DESKTOP-ABC1234"`

## 🛠️ 安装与使用 (Installation)

1. 定位到 Antigravity 的用户配置目录。
2. 打开 `config.json`（或对应的用户设置文件）。
3. 将上述 JSON 片段合并或替换到你的 `userSettings` 字段中。
4. **确保你已经按照上一节的方法正确修改了主机名。**
5. 保存 `config.json` 文件并重启 Antigravity 客户端，配置即可生效。

## ⚠️ 安全警告 (Disclaimer)

**高危操作警告：使用此配置意味着你将本地环境的最高执行权限交给了 AI。**
在开启全自动模式后，AI 能够未经询问直接执行文件删除、系统配置修改等操作。建议仅在**隔离的开发环境（如虚拟机）**，或确信**所有代码均已通过 Git 妥善备份**的工作区中使用此配置。本项目作者不对因使用本配置造成的任何文件误删或数据丢失负责。
