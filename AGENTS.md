# Repository Guidelines

## 项目结构与模块组织

本仓库是 “AI Engineering from Scratch” 的简体中文版。课程内容位于 `phases/<NN>-<phase-name>/<NN>-<lesson-name>/`。一节标准课程通常包含 `docs/zh.md`、可运行示例 `code/`、可选 notebook `notebook/`、课程素材 `assets/`，以及可复用产出物 `outputs/`。静态网站文件位于 `site/`；`site/build.js` 会解析 `README.md`、`ROADMAP.md` 和 `glossary/terms.md`，生成 `site/data.js`。顶层 `assets/` 存放全局视觉素材，`scripts/` 存放审计、校验和脚手架工具。

## 构建、测试与本地开发命令

安装 Python 依赖：

```bash
uv venv
uv pip install -r requirements.txt
```

运行某节课的代码示例，例如：

```bash
python phases/01-math-foundations/01-linear-algebra-intuition/code/vectors.py
```

修改 `README.md`、`ROADMAP.md` 或术语表后，重新生成并校验站点数据：

```bash
node site/build.js
node site/build.js --check
```

常用仓库检查命令：

```bash
python scripts/check_readme_counts.py
python scripts/audit_lessons.py
```

## 代码风格与命名约定

课程文风应直接、实用、像人写的内容。标题中不要添加装饰性 emoji。编辑 `README.md` 和 `ROADMAP.md` 时，必须保留解析器依赖的表格结构、阶段标题和状态符号。课程目录使用数字前缀和 kebab-case，例如 `05-jupyter-notebooks`。翻译文件放在 `docs/<lang>.md`；只翻译说明文字，不翻译代码。代码应能在 `requirements.txt` 所列依赖下直接运行，并避免不必要的注释。

## 测试指南

本仓库没有统一测试套件。请按改动范围验证：运行修改过的课程代码，从头到尾执行 notebook，并运行相关 `scripts/` 工具。若修改了目录或站点输入文件，运行 `node site/build.js --check`，并检查 `git diff site/data.js`；结构安全的改动不应产生意外目录变化。

## 提交与 Pull Request 规范

近期提交多使用简洁描述，常见格式包括 `feat(site): ...`、`chore(site): ...`。每个 PR 只处理一件事。PR 应说明改动内容、列出已运行的验证命令、按需关联 issue；若影响网站界面，请附截图。贡献时遵守 `CONTRIBUTING.md` 和项目行为准则。

## Agent 专用说明

不要重写无关翻译或生成数据。修改会被解析器读取的文件时，保留精确的表格形状、阶段标题和 roadmap 状态标记。优先做小而可验证的改动，避免大范围重写。
