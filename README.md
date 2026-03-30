# 项目管理系统

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![OpenClaw Compatible](https://img.shields.io/badge/OpenClaw-Compatible-blue.svg)](https://openclaw.ai)

> AI Agent 专用项目管理框架。从立项到交付的全流程管理，结构化工作流、模板和质量门。

## 概述

项目管理系统是一个**生产级工作流编排框架**，专为 AI Agent 团队设计。它提供结构化流程、角色操作手册和质量保障机制，管理项目从开始到结束的全过程。

### 解决的问题

AI Agent 在复杂项目中需要：
- **清晰的角色定义** - 谁在什么时候做什么
- **结构化工作流** - 步骤化流程
- **质量门** - 内置评审和验收标准
- **任务追踪** - 任务生命周期状态机
- **通信协议** - Agent 如何协调

本系统提供以上所有功能，并在真实多 Agent 项目中经过验证。

## 平台兼容性

| 平台 | 支持 | 说明 |
|------|------|------|
| **OpenClaw** | ✅ 原生 | 为 OpenClaw Agent 团队设计 |
| **Claude Code** | ✅ 兼容 | 适配 Claude 项目工作流 |
| **Cursor** | ✅ 兼容 | 可适配 Cursor 任务系统 |
| **通用 LLM** | ✅ 兼容 | 适用于任何 Agent 团队 |

### 系统要求

- **可选**: Python 3.8+（用于仪表盘工具）
- **可选**: OpenClaw >= 2026.3.0（用于 skill 集成）
- **主要**: 基于 Markdown，可在任何文本编辑器中使用

## 架构

\\\
┌─────────────────────────────────────────────────────────────┐
│                    项目生命周期                              │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  立项 → 定义 → 派发 → 执行 → 评审 → 验收                     │
│      ↑                                              │        │
│      └────────────── 返工循环 ─────────────────────┘        │
│                                                              │
├─────────────────────────────────────────────────────────────┤
│  角色: 决策者 | 派活方 | 执行方                              │
├─────────────────────────────────────────────────────────────┤
│  门禁: 质量评审 | 验收标准 | 签字确认                        │
└─────────────────────────────────────────────────────────────┘
\\\

## 核心组件

### 文档（14 个）

| 文档 | 用途 | 目标读者 |
|------|------|----------|
| \philosophy.md\ | 设计理念 | 所有角色 |
| \coordinator.md\ | 派活方操作手册 | 项目负责人 |
| \executor.md\ | 执行方操作手册 | 任务执行者 |
| \	ask-management.md\ | 任务状态机 | 所有角色 |
| \quality.md\ | 质量保障 | 评审者 |
| \communication.md\ | 通信协议 | 所有角色 |
| \governance.md\ | 决策治理 | 决策者 |
| \self-loop.md\ | 运行时恢复 | 系统运维 |
| \untime.md\ | 运行时行为 | 所有角色 |
| \lifecycle.md\ | 项目阶段 | 所有角色 |
| \scheduling.md\ | 任务调度 | 派活方 |
| \knowledge.md\ | 知识管理 | 所有角色 |
| \decision-guide.md\ | 决策指南 | 决策者 |
| \collaboration.md\ | 多 Agent 协作 | 所有角色 |

### 模板（10 个）

| 模板 | 用途 | 使用时机 |
|------|------|----------|
| \project-brief.md\ | 项目立项 | 启动新项目 |
| \	ask-spec.md\ | 任务规格书 | 派发任务 |
| \eview-record.md\ | 评审记录 | 评审交付物 |
| \cceptance-record.md\ | 验收记录 | 验收交付物 |
| \change-request.md\ | 变更请求 | 请求范围变更 |
| \milestone-report.md\ | 里程碑报告 | 里程碑完成 |
| \inal-report.md\ | 项目交付报告 | 项目完成 |
| \isk-register.md\ | 风险登记表 | 项目全周期 |
| \	ask-registry.md\ | 任务登记表 | 项目全周期 |
| \status.md\ | 状态更新 | 定期汇报 |

## 任务状态机

\\\
                    ┌──────────────┐
                    │   待派发     │
                    │   PENDING    │
                    └──────┬───────┘
                           │ 派发
                           ▼
                    ┌──────────────┐
         ┌──────────│   进行中     │──────────┐
         │          │ IN_PROGRESS  │          │
         │          └──────────────┘          │
         │                   │ 完成           │
         │                   ▼                │
         │          ┌──────────────┐          │
         │          │   已完成     │          │
         │          │  COMPLETED   │          │
         │          └──────┬───────┘          │
         │                 │ 评审             │
         │                 ▼                  │
         │          ┌──────────────┐          │
         │          │   已验收     │◄─────────┘
         │          │   ACCEPTED   │
         │          └──────────────┘
         │
         │ 返工
         ▼
  ┌──────────────┐
  │    返工中    │
  │    REWORK    │
  └──────┬───────┘
         │ 重新提交
         └──────────► 已完成
\\\

## 安装

### 快速开始

\\\ash
# 克隆仓库
git clone https://github.com/don068589/project-management-cn.git
cd project-management-cn

# 填写你的资源
# 编辑 resource-profiles.md 记录你的 Agent 和工具
\\\

### OpenClaw 用户

\\\ash
# 作为 skill 安装
cd ~/.openclaw/skills
git clone https://github.com/don068589/project-management-cn.git
\\\

## 使用方法

### 角色选择

| 你的角色 | 从这里开始 |
|----------|------------|
| 项目负责人 | \docs/coordinator.md\ |
| 任务执行者 | \docs/executor.md\ |
| 决策者 | \docs/decision-guide.md\ |
| 系统新手 | \docs/philosophy.md\ |

### 典型工作流

1. **启动项目** → 使用 \	emplates/project-brief.md\
2. **拆解任务** → 使用 \	emplates/task-spec.md\
3. **派发给执行者** → 遵循 \docs/coordinator.md\
4. **执行任务** → 遵循 \docs/executor.md\
5. **评审交付物** → 使用 \	emplates/review-record.md\
6. **验收或驳回** → 更新任务状态
7. **交付项目** → 使用 \	emplates/final-report.md\

### 仪表盘（可选）

\\\ash
# 查看项目仪表盘
python tools/dashboard.py

# 系统健康检查
python tools/system-check.py
\\\

## 质量门

### 评审标准

- [ ] 交付物符合任务规格
- [ ] 无严重缺陷
- [ ] 文档完整
- [ ] 测试通过（如适用）
- [ ] 评审人签字

### 验收标准

- [ ] 所有评审标准满足
- [ ] 集成测试通过（如适用）
- [ ] 干系人批准
- [ ] 最终文档完整

## 自循环保障

系统包含**运行时恢复机制**（\docs/self-loop.md\），确保：

- Agent 可从中断中恢复
- 任务状态被保留
- 不会丢失工作
- Agent 之间无缝交接

## 文件结构

\\\
project-management/
├── SKILL.md              # OpenClaw skill 定义
├── README.md             # 本文件
├── CHANGELOG.md          # 版本历史
├── LICENSE               # MIT 许可证
├── resource-profiles.md  # 执行方资源（填写这个！）
├── docs/                 # 详细文档
│   ├── philosophy.md     # 从这里开始
│   ├── coordinator.md    # 项目负责人
│   ├── executor.md       # 任务执行者
│   └── ...               # 共 14 个文档
├── templates/            # 即用模板
│   ├── project-brief.md
│   ├── task-spec.md
│   └── ...               # 共 10 个模板
└── tools/                # 可选工具
    ├── dashboard.py      # 可视化仪表盘
    └── system-check.py   # 健康检查
\\\

## 贡献

参见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 许可证

MIT License - 可自由使用、修改和分发。

## 致谢

为 OpenClaw Agent 团队构建。在真实多 Agent 项目中经过验证。