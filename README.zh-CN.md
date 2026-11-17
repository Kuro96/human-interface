# human-interface

面向 AI 编程助手的人机界面工程规则，适用于图形界面（GUI）和命令行界面（CLI）的构建、修改与审查。

[English](<README.md>) · [技能全文](<SKILL.md>)

## 覆盖范围

| 场景 | 重点 |
| --- | --- |
| 通用界面 | 易读名称、主要结果、合理默认值、精简输出、可执行的错误提示 |
| GUI | 优先主工作区、紧凑面板、分组行、单一滚动区域、宿主主题变量 |
| CLI | 结果与日志分流、简单命令、紧凑进度、适配终端环境 |
| 编码前 | **过滤 → 合并 → 适配** |

完整规则见 [SKILL.md](<SKILL.md>)。

## 安装

克隆仓库：

```sh
git clone https://github.com/Kuro96/human-interface.git
```

将 [SKILL.md](<SKILL.md>) 复制或链接到编程助手的技能目录，结构如下：

```text
<助手技能目录>/
└── human-interface/
    └── SKILL.md
```

按照所用助手的说明加载本地技能。技能名称为 `human-interface`。

使用 DeepSeek Harness 时，也可以直接克隆到用户技能目录：

```sh
mkdir -p "$HOME/.dsh/skills"
git clone https://github.com/Kuro96/human-interface.git "$HOME/.dsh/skills/human-interface"
```

## 使用

在具体界面任务中指定技能：

> 使用 human-interface 审查这个设置页面，在修改前完成过滤、合并和适配。

> 使用 human-interface 构建文件列表 CLI，采用合理默认值，将主要结果写入 stdout，将进度写入 stderr。

支持直接读取指令文件的助手，可以在任务中附上 [SKILL.md](<SKILL.md>)。

## 示例

| 场景 | 面向用户的呈现 |
| --- | --- |
| 内部项目记录 | 列表展示项目名称，技术元数据按需展开 |
| 次要面板暂无内容 | 折叠面板，将空间留给主工作区 |
| CLI 长时间运行 | 在 stderr 上更新单行进度，结束时输出简短总结 |
| 输出到管道或文件，或使用 `--json` / `--plain` | 输出保持简洁，主要数据走 stdout，诊断信息走 stderr |
| 保存失败 | “保存失败，请检查网络连接后重试。” |

CLI 格式还应遵循 `NO_COLOR`，GUI 样式使用宿主项目的 CSS 变量。

## 参与改进

欢迎通过 issue 或 pull request 提供界面问题、具体示例和改进建议。规则变更集中在 [SKILL.md](<SKILL.md>)，使用说明的中英文版本同步更新。
