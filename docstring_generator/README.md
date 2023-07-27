# 项目名称
Python Docstring Generator

## 介绍
Python Docstring Generator 是一个使用 OpenAI GPT-3.5-turbo 模型的 Python 代码文档生成器。它可以自动为你的 Python 代码生成 Google 风格的 docstring，帮助你更好地理解和维护你的代码。

## 安装
使用 pip 命令安装所需的第三方库：
```bash
pip install rich langchain tiktoken
```

## 使用说明
1. 首先，创建一个 `TemplateContext` 实例，设置你的角色、任务、信息和额外信息。
```python
generate_docstring_context = TemplateContext(
    '一个Python代码的docstring生成器',
    (
        '使用谷歌 docstring 风格给 INFO 标签里的代码中的函数和类生成对应的 docstring。'
        '同时需要在函数签名中使用类型注解。'
    ),
    '',
    (
        '你只需要生成修改后的代码，不要额外的说明和解释。'
    ),
)
```
2. 然后，调用 `generate_docstring_single_file` 函数，传入你的文件路径和 `TemplateContext` 实例，它会为你的代码生成 docstring，并保存到一个新的文件中。
```python
generate_docstring_single_file(file, generate_docstring_context)
```
3. 最后，你可以在新生成的文件中查看带有 docstring 的代码。

注意：这个项目目前只支持生成单个文件的 docstring，如果你需要为整个项目生成 docstring，你可能需要自己写一个循环来处理每个文件。