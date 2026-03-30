# SKILL.md - Project Management System

A comprehensive project management system for AI agents. Manage projects from initiation to delivery with structured workflows, templates, and quality gates.

## Description

通用项目管理系统。覆盖项目从立项到验收的全流程管理，包含：
- 角色操作手册（派活方/执行方）
- 14 个规则文档
- 10 个模板文件
- 质量保障机制
- 任务状态机
- 自循环保障

## When to Use

- 用户要求立项、规划项目
- 用户提到"项目管理"、"任务分发"、"评审验收"
- 需要多 agent 协作完成复杂任务
- 需要追踪项目进度和质量

## Installation

```bash
cd ~/.openclaw/skills
git clone https://github.com/openclaw/project-management.git
```

## Post-Installation Setup

### 1. Initialize Resource Profiles

首次使用时，填写 `resource-profiles.md` 记录你的执行资源：

```markdown
### 示例：Claude Code

**基本信息**
- 类型：CLI 工具
- 首次合作：2026-03-30

**能力**
- 复杂代码重构
- 多文件修改
- 代码审查

**调用方式**
- 命令：`claude --print --permission-mode bypassPermissions`
```

### 2. Optional: Add to Agent's TOOLS.md

如果你希望 agent 主动使用本系统，可以在 agent 的 TOOLS.md 添加：

```markdown
## 项目管理系统

- **位置**: ~/.openclaw/skills/project-management/
- **用途**: 立项、任务分发、评审验收
- **触发**: 用户提到"项目管理"、"立项"、"分发任务"
```

## Quick Start

### 1. 初始化

首次使用时，填写 `resource-profiles.md` 记录你的执行资源（agent、CLI 工具等）。

### 2. 派活方（项目总指挥）

```
读 docs/coordinator.md → 了解完整流程
用 templates/project-brief.md → 创建立项文档
用 templates/task-spec.md → 创建任务规格书
用 templates/review-record.md → 评审验收
```

### 3. 执行方（接活干活）

```
读 docs/executor.md → 了解执行规范
读 task-spec → 按规格书执行
更新任务状态 → 反馈进展
```

## Files Structure

```
project-management/
├── SKILL.md              # 本文件
├── README.md             # 系统大纲
├── data_structure.md     # 项目库索引
├── docs/                 # 详细规则文档
│   ├── coordinator.md    # 派活方操作手册 ⭐
│   ├── executor.md       # 执行方操作手册 ⭐
│   ├── philosophy.md     # 设计理念
│   └── ...               # 其他文档
├── templates/            # 模板库
│   ├── project-brief.md  # 项目立项 ⭐
│   ├── task-spec.md      # 任务规格书 ⭐
│   └── ...               # 其他模板
└── tools/
    ├── dashboard.py      # 项目看板
    └── system-check.py   # 完整性检查
```

## Key Workflows

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

## Customization

- `resource-profiles.md`: 填入你的执行资源信息
- `templates/`: 根据需要修改模板
- `improvements.md`: 记录改进建议

## Dependencies

- Python 3.8+ (可选，用于 dashboard.py)
- Git (可选，用于 system-check.py)

## License

MIT License

## Links

- [GitHub](https://github.com/openclaw/project-management)
- [Documentation](./docs/)
