# Stage Contracts

Use these contracts as evidence gates. Skip a stage only when it is outside the user's scope or equivalent current evidence already exists.

## Stage 0: Intake and inventory

Identify the problem statement, deliverables, constraints, data sources, existing artifacts, target language and format, and execution mode. Record source files and SHA-256 hashes for immutable inputs when practical.

Exit evidence: input inventory, explicit unknowns, output plan, and initialized `MH_WORKFLOW_STATE.json`.

## Stage 1: Problem and data analysis

Extract every question, constraint, symbol, unit, evaluation rule, and required deliverable. Profile real data for schema, missingness, ranges, time coverage, duplicates, and internal consistency. Separate observed facts from assumptions and proposed methods.

Exit evidence: a problem-analysis report, a machine-readable facts file, and CSV copies of generated data summaries.

## Stage 2: Modeling

Define notation, assumptions, objectives, constraints, identification or optimization strategy, baselines, validation design, and failure conditions. Show derivations without skipping steps. Connect every model component to the problem statement or cited evidence.

Exit evidence: modeling report with complete equations, assumptions, units, solver or estimator choice, and a verification plan.

## Stage 3: Implementation and computation

Implement reproducible code around a single source of parameters. Preserve deterministic seeds where applicable. Write raw and summarized results to structured files. Run targeted tests, boundary checks, and independent recomputation of critical constraints or statistics.

Exit evidence: executable code, environment notes, logs, result files, CSV counterparts, and passing computational checks.

## Stage 4: Results and figures

Analyze only current authoritative results. Build figures and tables from structured outputs rather than manually transcribed values. Use an installed result-analysis or figure skill when it fits. Keep labels, legends, annotations, and colorbars in independent regions and inspect rendered outputs.

Exit evidence: publication-ready figures and tables, source scripts, underlying CSV data, and recorded visual and numeric checks.

## Stage 5: Paper writing

Write from the verified evidence ledger. Keep Context, Content, Conclusion structure at paragraph and section level when required. Ensure abstract, main text, tables, figures, and conclusion use consistent numbers and claim strength. Verify each citation against a retrievable source.

Exit evidence: complete manuscript source, bibliography, claim-to-evidence mapping, and the required top-journal gap analysis.

## Stage 6: Compilation and compliance

Compile the actual submission source. For Chinese LaTeX use XeLaTeX and compatible packages. Check references, cross-references, fonts, page geometry, figure cropping, table overflow, missing glyphs, and output-file completeness. Treat successful compilation as format evidence only, not scientific validation.

Exit evidence: final PDF or requested document, clean compilation log, compliance report, and CSV copies of numeric compliance summaries.

## Stage 7: Red-team review

Review as six roles: contradiction finder, Reviewer 2, reverse derivation, destructive test, assumption stress test, and belief update. Prioritize invalid conclusions, unsupported claims, method defects, data leakage, missing controls, weak baselines, and irreproducibility.

Exit evidence: severity-ranked review with file and line references where possible, plus a concrete remediation list.

## Stage 8: Improvement loop and final verification

Fix supported findings in descending severity. Re-run only affected computations and downstream artifacts. Repeat independent verification until two consecutive review passes find no new blocking defect, or report the unresolved blocker honestly.

Exit evidence: synchronized final artifacts, three-pass verification record when required, residual-risk statement, and completed `MH_WORKFLOW_STATE.json`.

## State schema

Use this compact structure and add fields only when they carry real evidence:

```json
{
  "schema_version": 1,
  "mode": "full|gated|focused",
  "project_root": "absolute path",
  "current_stage": 0,
  "stages": [
    {
      "id": 0,
      "name": "intake",
      "status": "pending|in_progress|complete|failed|skipped",
      "evidence": [],
      "verification": [],
      "blockers": []
    }
  ],
  "next_action": "",
  "updated_at": "ISO-8601 timestamp"
}
```
