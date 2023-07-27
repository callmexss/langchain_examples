# 项目名称
Code Scan

## 介绍
Code Scan 是一个使用 OpenAI 的 GPT-3.5-turbo 模型进行代码扫描的工具。它可以扫描指定的代码仓库，分析代码，并生成相应的 AI 笔记。这个工具可以帮助你理解代码的功能，并提供可能的改进建议。

## 安装
使用以下命令安装所需的第三方库：
```bash
pip install rich langchain tiktoken
```

## 使用说明
首先，你需要创建一个 `TemplateContext` 对象，指定 AI 的角色，任务，代码信息和额外的指令。例如：
```python
repo_scan_context = TemplateContext(
    '你是一个代码扫描助手。',
    (
        '你需要扫描 INFO 标签里的代码并给出解释和建议，'
        '忽略所有开头的 import 的语句。'
    ),
    '',
    (
        '如果你发现代码中有BUG或者错误，'
        '请帮我记录下来并告知我错误的原因和改进建议。'
        '请使用中文回复，不要给出没有意义的建议。'
    ),
)
```
然后，使用 `scan_code_repo` 函数扫描指定的代码仓库：
```python
scan_code_repo(REPO, PATTERN, repo_scan_context)
```
其中，`REPO` 是你要扫描的代码仓库的路径，`PATTERN` 是你要扫描的文件的模式，`repo_scan_context` 是你创建的 `TemplateContext` 对象。

扫描完成后，AI 笔记将保存在 `ai_notes` 文件夹中。