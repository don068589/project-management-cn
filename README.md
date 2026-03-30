# 项目管理系统

> 通用项目管理基座。任何 agent 拿到本系统，即可从立项到验收全程管理项目。

## 这是什么？

一套完整的项目管理框架，覆盖项目从立项到交付的全流程。

**核心特性：**
- 📋 **全生命周期管理** — 立项、执行、评审、交付
- 📚 **14 个文档文件** — 每个环节的详细规则
- 📝 **10 个模板** — 开箱即用的项目文档
- ✅ **质量门禁** — 内置评审和验收机制
- 🔄 **自维持** — 运行时恢复和自循环保障

## 安装

### 方式 1：从 GitHub 克隆（推荐）

```bash
git clone https://github.com/openclaw/project-management.git
cd project-management

# 填写你的资源
# 编辑 resource-profiles.md，记录你的 agent 和工具
```

### 方式 2：下载 ZIP

从 [GitHub Releases](https://github.com/openclaw/project-management/releases) 下载并解压。

> **注意**：作为 OpenClaw Skill 安装时，克隆到 `~/.openclaw/skills/`。

### 方式 3：下载 ZIP

从 [GitHub Releases](https://github.com/openclaw/project-management/releases) 下载并解压。

### 首次使用

1. 填写 `resource-profiles.md`，记录你的执行资源
2. 如需管理项目，读 `docs/coordinator.md`
3. 如需执行任务，读 `docs/executor.md`
4. 开始使用 `templates/` 下的模板

## 核心流程

### 项目生命周期

```
立项 → 需求确认 → 拆解 → 分发 → 执行 → 评审 → 验收 → 归档
```

### 任务状态

```
待分发 → 进行中 → 待评审 → 已验收
                    ↓
                 返工 → 待评审
```

## 目录结构

```
project-management/
├── SKILL.md              # OpenClaw Skill 定义
├── README.md             # 英文说明
├── README_CN.md          # 本文件
├── CHANGELOG.md          # 版本历史
├── LICENSE               # MIT 许可证
├── resource-profiles.md  # 执行资源档案（需填写）
├── docs/                 # 详细文档
│   ├── coordinator.md    # 派活方操作手册
│   ├── executor.md       # 执行方操作手册
│   ├── philosophy.md     # 设计理念
│   └── ...               # 更多文档
├── templates/            # 模板库
│   ├── project-brief.md  # 项目立项
│   ├── task-spec.md      # 任务规格书
│   ├── review-record.md  # 评审记录
│   └── ...               # 更多模板
└── tools/                # 可选工具
```

## 关键文档

| 文档 | 用途 |
|------|------|
| `coordinator.md` | 如何管理项目 |
| `executor.md` | 如何执行任务 |
| `task-management.md` | 任务状态机 |
| `quality.md` | 质量保障 |
| `templates/` | 复制使用 |

## 模板清单

| 模板 | 用途 |
|------|------|
| `project-brief.md` | 启动新项目 |
| `task-spec.md` | 定义任务 |
| `review-record.md` | 评审完成的工作 |
| `final-report.md` | 项目交付 |
| `risk-register.md` | 追踪风险 |

## 许可证

MIT License — 自由使用、修改、分发。
