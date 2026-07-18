# Maker Stack

Maker Stack 是一组面向 Claude Code 的开发工程插件集合，按 Keystone 的 Marketplace 格式组织。它不是一个业务应用，而是从系统建模、前端开发、Git 交付到性能和质量治理的工程能力入口。

## 适用场景总览

| 场景 | 推荐插件 |
| --- | --- |
| 读懂后端系统、DDD 建模、CQRS、应用层和设计模式 | `backend-best-practices` |
| 新建或重构 React、Vue 3、Svelte 前端 | `consistent-frontend` |
| worktree、提交、同步、PR、Epic、Hotfix 和 Git 恢复 | `git-workflow` |
| Go 性能审计、基准、pprof、容量和授权优化 | `go-performance-skills` |
| Svelte / SvelteKit 的质量、安全、测试、性能和发布审计 | `svelte-quality-suite` |

## 插件清单

### 1. backend-best-practices

后端架构治理插件，覆盖 DDD、应用层、CQRS 读模型、GoF 设计模式和系统读码。

- **Command**：34 个，包含 `system-model-view-read`、`ddd-new`、`ddd-refactor`、`ddd-review`、`ddd-application-review`、`cqrs-read-model-*`、`design-pattern-*` 等。
- **Workflow**：7 个，覆盖系统阅读、greenfield、brownfield、读模型和设计模式流程。
- **Skill**：57 个，按 DDD、CQRS 和设计模式阶段拆分。
- **适用场景**：既有后端重构、新业务建模、应用层审查、复杂查询拆分和设计模式适配。
- **不适用场景**：简单 CRUD 小改、纯 UI、单纯运维或没有业务约束的“一键重写”。

仓库：[Capsule7446/backend-best-practices](https://github.com/Capsule7446/backend-best-practices)

### 2. consistent-frontend

统一、可维护的前端架构插件，将 DDD / Clean Architecture、Feature-Sliced Design、Design System 和状态机结合起来。

- **Command**：1 个，`fe-build`。
- **Workflow**：没有独立 Workflow 目录；`fe-build` 内部编排探索、设计、实现、审查和验证。
- **Skill**：1 个主 Skill，附带 5 份框架、结构和工作流参考资料。
- **适用场景**：新建页面、既有模块 retrofit、前后端 DTO 隔离、React / Vue 3 / Svelte 的结构统一。
- **不适用场景**：简单文案或 CSS 修改、纯后端建模和纯 Git 操作。

仓库：[Capsule7446/consistent-frontend](https://github.com/Capsule7446/consistent-frontend)

### 3. git-workflow

带风险分级和安全门禁的 Git 交付插件，覆盖 worktree、原子提交、同步、PR、集成和恢复。

- **Command**：3 个，`commit`、`ship`、`worktree`。
- **Workflow**：3 个，`workflow-deliver`、`workflow-epic`、`workflow-hotfix`。
- **Skill**：7 个，覆盖路由、worktree、提交、同步、交付、集成和恢复。
- **适用场景**：多人或多 Agent 并行开发、Epic 拆分、紧急修复、Conventional Commits 和误操作恢复。
- **不适用场景**：未经授权的强制推送、远程分支删除或破坏性历史改写。

仓库：[Capsule7446/git-workflow](https://github.com/Capsule7446/git-workflow)

### 4. go-performance-skills

以证据为基础的 Go 性能工程插件，默认只读审计，覆盖 16 个性能维度和全量编排。

- **Command**：没有独立 Command 目录。
- **Workflow**：没有独立 Workflow 目录。
- **Skill**：17 个入口 Skill（`go-optimize-all` 加 16 个维度 Skill），另有 `_go-perf-core` 证据协议、评分标准、安全门禁和校验脚本。
- **适用场景**：CPU、内存、GC、分配、并发、I/O、HTTP、数据库、缓存、序列化、容量和可观测性问题。
- **不适用场景**：没有基线的猜测式优化、未授权生产压测或可能影响稳定性的实验。

仓库：[Capsule7446/go-performance-skills](https://github.com/Capsule7446/go-performance-skills)

### 5. svelte-quality-suite

面向 Svelte / SvelteKit 的系统性质量审计与优化插件，支持 `audit`、`optimize` 和 `audit-optimize` 模式。

- **Command**：没有独立 Command 目录。
- **Workflow**：没有独立 Workflow 目录；统一由 `orchestrate-svelte-quality` 编排。
- **Skill**：18 个，包含 17 个质量维度 Skill 和 1 个总编排 Skill。
- **适用场景**：响应式、SSR / hydration、Bundle、Web Vitals、类型、测试、安全、CI、发布和容量治理。
- **不适用场景**：非 Svelte 项目的通用审查、UI 审美、SEO、Design Token 或纯视觉设计。

仓库：[Capsule7446/svelte-quality-suite](https://github.com/Capsule7446/svelte-quality-suite)

## 推荐使用顺序

一个典型的全栈任务可以按以下顺序使用：

```text
1. git-workflow:worktree       创建隔离工作区
2. backend-best-practices      梳理后端模型和接口边界
3. consistent-frontend         设计前端分层、状态和组件契约
4. svelte-quality-suite        如果是 Svelte，执行质量与安全审计
5. go-performance-skills       如果是 Go，基于基线执行性能审计
6. git-workflow:commit/ship    提交、同步并交付 PR
```

不需要使用全部插件。应根据项目技术栈、变更风险和验收目标选择最小能力集合。

## 安装

```text
/plugin marketplace add Capsule7446/maker-stack
/plugin install backend-best-practices@maker-stack
/plugin install consistent-frontend@maker-stack
/plugin install git-workflow@maker-stack
/plugin install go-performance-skills@maker-stack
/plugin install svelte-quality-suite@maker-stack
```

## 验证

权威配置位于 [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json)。在 Marketplace 仓库目录执行：

```text
claude plugin validate .
```

## 清单审查结论

当前五个插件均有独立、明确且互补的职责，没有发现应整体移除的插件。没有 Command 或 Workflow 的插件是有意采用 Skill-only 入口，并非缺失。仓库内部的 `references/`、`assets/`、校验脚本和 CI 文件应继续保留；它们分别支撑运行协议、证据报告、打包验证和仓库维护。是否从发布压缩包排除 `.github/`、`research/` 或 `scripts/`，应由各插件自己的打包脚本决定，不应从源码仓库直接删除。

## License

[MIT](LICENSE)
