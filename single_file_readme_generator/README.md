# generate_readme.py

## 介绍

`generate_readme.py` 是一个用于自动生成 README 文件的 Python 脚本。它使用了 OpenAI 的 GPT-4 模型，以及一些其他的 Python 库，如 `rich`, `tiktoken` 等。该脚本可以根据给定的模板和上下文信息，生成相应的 README 文件。

## 安装

使用以下命令安装所需的第三方库：

```bash
pip install rich tiktoken langchain
```

## 使用说明

1. 首先，创建一个 `TemplateContext` 对象，该对象包含了生成 README 所需的所有信息，如角色、任务、信息和额外的指令。

2. 然后，调用 `run` 函数，传入 `TemplateContext` 对象，该函数会返回生成的 README 内容。

3. 最后，调用 `write_to_file` 函数，将生成的 README 内容写入到指定的文件中。

以下是一个简单的使用示例：

```python
readme_generate_context = TemplateContext(
    '一个Python项目的README生成助手',
    (
        '根据 INFO 标签里的代码生成对应的 README。包括以下内容：'
        '# 项目名称'
        '## 介绍'
        '## 安装'
        '## 使用说明'
    ),
    '',
    (
        '1. 使用 markdown 语法。'
        '2. 只输出 README 的内容，不要无关的解释说明。'
        '3. 使用中文。'
        '4. 在 `## 安装` 部分使用一条 pip 命令安装所需的第三方库，不要安装标准库。'
        '5. import 的顺序是标准库，第三方库和本地库，使用空格分割。'
    ),
)

print(readme_generate_context.prompt)

if __name__ == '__main__':
    sys.argv.append('')
    file = sys.argv[1] or __file__
    generate_readme_single_file(file, readme_generate_context)
```

在这个示例中，我们创建了一个 `TemplateContext` 对象，并设置了相应的角色、任务、信息和额外的指令。然后，我们调用 `run` 函数生成 README 内容，并将其写入到文件中。