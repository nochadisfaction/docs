## Master Training Gap Closure Plan

### Scope

- Align Stage 1 workflow with the master multi-stage training epic.
- Enforce stage ratio governance in code (not only docs).
- Track unfinished epic items as explicit execution tasks.

### Completed Today

- Located and reviewed Stage 1 notebook workflow in [ai/lab/Stage1_Training_Notebook.ipynb](ai/lab/Stage1_Training_Notebook.ipynb).
- Compared against [ai/training/ready_packages/MASTER_TRAINING_EPIC.md](ai/training/ready_packages/MASTER_TRAINING_EPIC.md) and [ai/pipelines/orchestrator/MasterTrainingPlan.md](ai/pipelines/orchestrator/MasterTrainingPlan.md).
- Implemented manifest-driven stage distribution loading and final stage drift validation in [ai/pipelines/orchestrator/orchestration/integrated_training_pipeline.py](ai/pipelines/orchestrator/orchestration/integrated_training_pipeline.py).

### Unfinished Epic Items (Execution Queue)

- Stage sampling parity and tolerance enforcement across outputs.
- Stage-specific quality validators and crisis override policy wiring.
- Edge/safety DPO scenario bank ingestion into Stage 3.
- Voice signature and persona gate requirements for Stage 4.
- Stage-level train/val/test split outputs and release manifest verification.
- Ops checklist completion tracking (inventory freshness, prompt mirror freshness, voice export freshness).

### Next Steps (Order of Execution)

1. Add hard-fail option when stage drift exceeds tolerance in integrated pipeline report.
2. Add stage-specific quality profiles from policy manifest to filtering logic.
3. Add stage-aware split export (train/val/test per stage + aggregate split).
4. Add explicit pre-run checks for required Stage 3 and Stage 4 artifacts.
5. Add Asana/Jira sync checklist update script after each pipeline run.

### Success Criteria

- Stage share drift for each stage is <= 0.02 unless explicitly waived.
- Manifest and report include final stage counts and drift metrics.
- Stage 3 and Stage 4 required inputs are validated before training launch.
- Run output includes both aggregate and per-stage split artifacts.
