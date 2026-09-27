# MHAgent Workflow for Codex

这是一个可直接安装到 Codex 的 Skill，用于运行 MHAgent 风格的科研或数学建模工作流。

## 安装

### Windows PowerShell

```powershell
$skillsDir = Join-Path $HOME ".codex\skills"
git clone https://github.com/meanwhile371/mhagent-workflow.git (Join-Path $skillsDir "mhagent-workflow")
```

### macOS 或 Linux

```bash
git clone https://github.com/meanwhile371/mhagent-workflow.git ~/.codex/skills/mhagent-workflow
```

安装后重启 Codex，在对话中使用 `$mhagent-workflow`，或直接请求运行 MHAgent 风格工作流。

## 包含内容

- `SKILL.md`：Skill 的触发条件、执行模式、证据要求和完成标准。
- `references/stages.md`：从项目盘点到最终核验的阶段合同、退出证据和状态文件格式。
- `agents/openai.yaml`：Codex Skill 的名称、简介和默认提示语。

## 工作流阶段

工作流覆盖项目盘点、问题与数据分析、建模、实现与计算、结果与图表、论文写作、编译合规、红队审查，以及改进和最终核验。

运行时会在项目根目录维护 `MH_WORKFLOW_STATE.json`，用于记录当前阶段、证据路径、验证结果和阻塞项。

## 说明

这是 Codex Skill 的工作流定义，不包含独立的 MHAgent 软件运行时，也不包含私有 Capsule、项目数据或用户凭据。
