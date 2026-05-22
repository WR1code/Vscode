```markdown
# VS Code 配置 CMake 快捷键一键编译指南 (`Ctrl + Shift + B`)

本指南介绍如何通过配置 VS Code 的 `tasks.json` 文件，将 `Ctrl + Shift + B` 快捷键绑定到 CMake 的编译（Build）命令上，实现快捷键一键编译。

## ⚙️ 设置方法

### 1. 打开任务配置
* **快捷键：** `Ctrl + Shift + P`
* **操作：** 在 VS Code 中按下 `Ctrl + Shift + P` 打开命令面板，输入 `Tasks: Configure Default Build Task`（配置默认生成任务），然后按下回车。

### 2. 选择或创建 `tasks.json`
根据 VS Code 弹出的提示进行选择：
* 如果你之前配置过编译器（如 `g++`），列表里会直接显示你的编译器名称，**直接点击它**。
* 如果列表里只有 `Create tasks.json file from template`，点击它并选择 `Others`。
* 此时，VS Code 会在项目根目录的 `.vscode/` 文件夹下自动创建一个 `tasks.json` 文件。

### 3. 配置默认编译属性
打开 `.vscode/tasks.json` 文件，将里面的内容**完全替换**为以下 CMake 编译配置。

> 💡 **核心逻辑**：将 `"command"` 设置为 `"build"`，并将 `"group"` 中的 `"isDefault"` 设置为 `true`。

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "type": "cmake",
            "label": "CMake: 编译",
            "command": "build",
            "problemMatcher": [],
            "detail": "CMake 模板 编译 任务",
            "group": {
                "kind": "build",
                "isDefault": true // 确保一键触发编译的关键配置
            }
        }
    ]
}
