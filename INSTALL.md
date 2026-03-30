# 安装指南

## 前置要求

- **OpenClaw** 已安装并配置（独立使用可选）
- **Python 3.8+**（可选，用于看板工具）
- **Git**（可选，用于 system-check.py）

## 第一步：下载

### 方式 A：从 GitHub 克隆

```bash
git clone https://github.com/openclaw/project-management.git
cd project-management
```

### 方式 B：作为 OpenClaw Skill 安装

```bash
cd ~/.openclaw/skills
git clone https://github.com/openclaw/project-management.git
```

### 方式 C：下载 ZIP

从 [GitHub Releases](https://github.com/openclaw/project-management/releases) 下载并解压。

## 第二步：配置资源

填写 `resource-profiles.md`，记录你的执行资源：

```markdown
### 示例：你的 Agent 团队

**基本信息**
- 类型：AI Agent
- 首次合作：YYYY-MM-DD

**能力**
- 任务类型 A
- 任务类型 B
- 任务类型 C

**调用方式**
- 方法：sessions_send(agentId="xxx", message="...")
```

## 第三步：阅读文档

根据你的角色：

| 角色 | 首读文档 |
|------|----------|
| 项目总指挥 | `docs/coordinator.md` |
| 任务执行者 | `docs/executor.md` |
| 双角色 | `docs/philosophy.md` |

## 第四步：开始使用

1. 创建项目立项：`templates/project-brief.md`
2. 拆解任务：`templates/task-spec.md`
3. 分发到执行资源
4. 评审验收：`templates/review-record.md`

## 验证安装

检查系统文件完整性：

```bash
python3 tools/system-check.py
```

Windows 下：

```bash
python tools/system-check.py
```

## 可选：项目看板

查看项目状态：

```bash
python3 tools/dashboard.py --project your-project-name
```

## 安装后目录结构

```
project-management/
├── docs/                 # 按角色阅读
├── templates/            # 复制使用
├── tools/                # 可选工具
├── resource-profiles.md  # 你的资源（需填写！）
├── SKILL.md              # Skill 定义
└── README.md             # 说明
```

## 更新

```bash
git pull origin main
```

## 常见问题

### "Module not found"
Python 脚本是可选的。核心系统不依赖它们。

### "项目数据放哪里？"
在系统目录外创建独立的 `projects-data/` 目录。

## 下一步

- 阅读你角色的操作手册
- 用一个简单项目试用模板
- 随着资源增加更新 `resource-profiles.md`