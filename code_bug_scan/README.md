# 项目名称
LangChain Code Scan

## 介绍
LangChain Code Scan 是一个用于扫描代码库并发现潜在 BUG 和风险的 Python 工具。它使用 OpenAI 的 GPT-4 模型进行代码分析，并将结果保存为 Markdown 文件。此工具可以帮助提升代码质量和系统的安全性。

## 安装
使用 pip 命令安装所需的第三方库：
```bash
pip install langchain tiktoken rich
```

## 使用说明
1. 首先，你需要创建一个 `TemplateContext` 实例，定义你的角色、任务、信息和额外的指令。
2. 然后，使用 `scan_code_repo` 函数扫描你的代码库。你需要提供代码库的路径、文件模式和 `TemplateContext` 实例。
3. 扫描结果将保存在代码库的 `ai_bugs` 目录下，每个文件的分析结果都将保存为一个单独的 Markdown 文件。

以下是一个简单的使用示例：
```python
from pathlib import Path
from code_scan import TemplateContext, scan_code_repo

repo_scan_context = TemplateContext(
    "一个代码BUG扫描助手。",
    (
        "扫描 INFO 标签里的代码并发现BUG和潜在的风险。"
        "帮助我提升代码质量和系统的安全性。"
    ),
    "",
    "",
)

REPO = Path(__file__).parent.parent
PATTERN = "*.py"
scan_code_repo(REPO, PATTERN, repo_scan_context)
```
在这个示例中，我们扫描了当前代码库中的所有 Python 文件，并将结果保存在 `ai_bugs` 目录下。