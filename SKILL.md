---
name: mhagent-workflow
description: >-
  Run a Codex-native research or mathematical-modeling pipeline modeled on the
  MHAgent workflow, covering problem analysis, modeling, implementation,
  results, figures, paper writing, compilation, and review. Use when the user
  invokes $mhagent-workflow, asks to run the MHAgent-style workflow inside
  Codex, requests an end-to-end modeling paper, or asks to resume one.
---

# MHAgent Workflow for Codex

This is a Codex-native orchestrator. It reproduces the workflow structure and quality gates without reading, decrypting, or invoking MHAgent Capsule files.

## Start

1. Read the applicable `AGENTS.md` files before changing anything.
2. Treat the current workspace as the project unless the user names another directory.
3. Inventory the question, requirements, data, existing code, results, figures, and manuscript. Reuse verified artifacts instead of regenerating them.
4. Read [references/stages.md](references/stages.md), then select the earliest stage whose required evidence is missing.
5. Maintain `MH_WORKFLOW_STATE.json` in the project root. Create it only when execution begins. Record the selected mode, current stage, stage status, evidence paths, verification results, blockers, and next action. Never mark a stage complete from prose alone.

## Modes

- `full`: Run all applicable stages continuously. Use when the user asks for a complete workflow, end-to-end delivery, or says to finish without stopping.
- `gated`: Run one stage, report its evidence and wait at the next material decision gate. Use when the user asks for stepwise control.
- `focused`: Run only the named stage or artifact. Do not broaden a focused request into the full pipeline.

Infer the mode from the request. If invocation contains no task details, inspect the workspace first and ask only for information that cannot be inferred and would materially change the analysis.

## Execution Rules

- Follow the stage order in `references/stages.md`, but enter at the first incomplete stage supported by the user's existing artifacts.
- Use relevant installed skills when they improve the stage. Read the selected skill's `SKILL.md` before following it. Do not require a named child skill when it is absent; execute the stage contract directly with appropriate local tools.
- Keep claims tied to source data, executable code, and current outputs. Do not invent data, references, statistical results, or completed checks.
- Keep code, results, figures, and manuscript synchronized. When they disagree, investigate the discrepancy instead of choosing one as authoritative without evidence.
- Preserve user files and unrelated changes. Work incrementally and do not delete historical results to conceal drift.
- Every tabular or numeric output must have a CSV counterpart in the same output directory with the same stem when the active project instructions require it.
- For figures, verify data provenance, dimensions, legibility, and absence of text-data overlap. Re-render until checks pass.
- For Chinese LaTeX, produce Overleaf-compatible source and compile with XeLaTeX when a local compile is requested.
- After every manuscript modification, produce or refresh the top-journal gap analysis required by the active project instructions.
- Apply the active verification standard. If three-pass verification is required, perform three genuinely different checks and record each result in state.

## Resume

When the user says `继续`, `resume`, or asks to reopen the workflow:

1. Read `MH_WORKFLOW_STATE.json` if present.
2. Recheck current files and running processes; state is a pointer, not proof.
3. Resume the first `in_progress`, `failed`, or evidence-incomplete stage.
4. Do not rerun completed expensive work unless inputs changed or verification reveals drift.

## Completion

Completion requires all applicable stage exit criteria to pass, no unresolved blocker affecting the main conclusion, and final deliverables to exist on disk. Summarize actual outputs, verification performed, residual limitations, and exact paths. Never equate pipeline completion with scientific validity.
