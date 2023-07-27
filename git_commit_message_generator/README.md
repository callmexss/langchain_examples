# 项目名称
Git Commit Message Generator

## 介绍
这是一个使用 Python 编写的 Git Commit Message 生成器。它使用 OpenAI 的 GPT-3.5 模型，根据 git diff 信息自动生成恰当的 commit message。同时，它遵循一定的规范，包括新功能、修复Bug、文档更新、代码风格调整、代码重构、测试相关、构建过程或辅助工具的修改、性能优化、持续集成的配置或脚本更新、代码回退等。

## 安装
使用 pip 命令安装所需的第三方库：
```bash
pip install langchain rich tiktoken
```

## 使用说明
1. 首先，创建一个 `TemplateContext` 实例，设置你的角色、任务、信息和额外信息。
2. 然后，调用 `generate_git_commit_message` 函数，它会根据你的 `TemplateContext` 生成 commit message。
3. 最后，你可以看到生成的 commit message 和使用的 token 数量。

例如：
```python
commit_message_context = TemplateContext(
    "一个 git commit message 生成器",
    (
        "根据 INFO 标签里的 git diff 信息，生成恰当的 commit message\n"
        "请遵循下面的规范：\n"
        "feat：新功能（feature） 用于描述新增的功能点或功能模块\n"
        "fix：修复Bug 用于描述修复的bug或错误\n"
        "docs：文档更新 用于描述更新或修改文档\n"
        "style：代码风格调整 用于描述调整代码格式、空格、缩进等风格调整\n"
        "refactor：代码重构 用于描述代码重构、优化\n"
        "test：测试相关 用于描述新增、修改或删除测试用例代码\n"
        "chore：构建过程或辅助工具的修改 用于描述构建配置、工具更新、脚本的更新等\n"
        "perf：性能优化 用于描述性能优化相关的代码修改\n"
        "ci：持续集成的配置或脚本更新 用于描述持续集成的配置、脚本的更新\n"
        "revert：代码回退 用于描述代码回退操作\n"
    ),
    "",
    "使用英文生成 commit message，返回完整的 git 命令。",
)

print(commit_message_context.prompt)
generate_git_commit_message(commit_message_context)
```
这将会生成一个符合规范的 commit message。