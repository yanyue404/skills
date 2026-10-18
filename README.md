# skills

Cursor Agent Skills 集合。每一项目录是一项可以单独安装的技能：`SKILL.md` 告诉智能体何时启用、按什么步骤执行；同目录里的脚本和示例供它直接调用。

A collection of [Cursor Agent Skills](https://cursor.com/docs/skills). Copy a skill directory into Cursor to install it.

## 技能

| 目录 | 作用 |
| --- | --- |
| [docx-template](docx-template/) | 扫描 `.docx` 模板中的 `{{变量名}}` 与 `{{img_图片名}}`，填写后生成或修改 Word 文档 |

## 安装

```bash
git clone https://github.com/yanyue404/skills.git
cd skills
```

复制整个技能目录，不要只复制 `SKILL.md`。脚本、模板和示例都在同一目录里。

在所有项目中使用，放到用户级目录：

```bash
# macOS / Linux
mkdir -p ~/.cursor/skills
cp -R docx-template ~/.cursor/skills/docx-template
```

```powershell
# Windows PowerShell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.cursor\skills" | Out-Null
Copy-Item -Recurse -Force docx-template "$env:USERPROFILE\.cursor\skills\docx-template"
```

只在当前仓库使用时，复制到该仓库的 `.cursor/skills/docx-template/`。Cursor 也会读取 `.agents/skills/`。

装好后新开一轮对话。智能体会按 `SKILL.md` 的描述自行选用；也可以在 Agent 输入框输入 `/`，搜索技能名手动挂上。

各技能的 Python 依赖写在该目录的 `requirements.txt`。以 docx-template 为例，在技能目录中执行：

```bash
pip install -r requirements.txt
```

## 仓库约定

新技能放在仓库根目录，文件夹名就是技能名，使用小写字母、数字和连字符，并且与 `SKILL.md` 开头的 `name` 一致。

- `SKILL.md`：给智能体的步骤和完成标准
- `README.md`：给人看的安装与命令说明
- `scripts/`、`assets/`：可选。示例、模板和样例数据使用虚构内容

不要提交真实机构、人名，或未获授权的文档。技能若带 Python 依赖，在该目录提供 `requirements.txt`。

## 许可

[MIT](LICENSE)
