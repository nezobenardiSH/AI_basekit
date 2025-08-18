# Start Project Command

**Command:** `/start-project [optional: initial-idea-description]`

**Description:** Complete AI project development workflow from idea validation through implementation. Orchestrates specialized agents across 4 stages with human guidance and validation checkpoints to deliver production-ready code.

---

## Objective
Execute end-to-end AI project development workflow: validate ideas → create comprehensive PRP → validate PRP quality → execute implementation with continuous validation. Transform raw ideas into working, validated implementations.

---

## Workflow Overview

**Stage 1:** Concept Validation → Validated idea description  
**Stage 2:** Requirements Engineering → Context-rich PRP with embedded validation framework  
**Stage 3:** PRP Validation → Quality-assured PRP ready for implementation  
**Stage 4:** PRP Execution → Working implementation with validation history

---

## Stage 1: Concept Validation

### Process
1. **Initialize Idea Session**
   - If provided: Use initial idea description from command args
   - If not provided: Prompt user: "Describe your AI project idea in 2-3 sentences"

2. **Execute Idea Validation**
   - **Command:** `/validate-idea`
   - Orchestrates multi-agent validation through 3 structured rounds
   - See `/validate-idea` command for detailed agent collaboration process

3. **Generate Validated Idea Document**
   - **Location:** `outputs/ideas/[project-name]-validated-[date].md`
   - **Content:** Refined concept, value proposition, success metrics, risk assessment

**Checkpoint:** "Proceed to Stage 2 - Requirements Engineering? (y/n/revise)"

---

## Stage 2: Requirements Engineering (PRP Creation)

### Process
1. **Execute PRP Generation**
   - **Command:** `/generate-prp outputs/ideas/[project-name]-validated-[date].md`
   - Orchestrates specialized agents for comprehensive PRP creation
   - See `/generate-prp` command for detailed agent collaboration process

2. **PRP Output**
   - **Location:** `outputs/prps/[project-name]-[date].md`
   - **Structure:** Follows `templates/prp_base.md` format
   - **Content:** Context-rich implementation prompt with embedded validation framework

**Checkpoint:** "Review generated PRP and proceed to Stage 3 - PRP Validation? (y/n/revise)"

---

## Stage 3: PRP Validation

### Process
1. **Execute PRP Validation**
   - **Command:** `/validate-prp outputs/prps/[project-name]-[date].md`
   - Orchestrates 4 validation agents for comprehensive quality review
   - See `/validate-prp` command for detailed validation process

2. **Quality Gate Decision**
   - **≥8.0 Score:** Ready for execution
   - **6.0-7.9 Score:** Minor issues to address
   - **<6.0 Score:** Requires significant revision

3. **Output**
   - **Location:** `outputs/validations/prp-validation-[project-name]-[date].md`

**Checkpoint:** "PRP validated with quality score [X/10]. Proceed to Stage 4 - PRP Execution? (y/n)"

---

## Stage 4: PRP Execution

### Process
1. **Execute PRP Implementation**
   - **Command:** `/execute-prp outputs/prps/[project-name]-[date].md`
   - Phase-by-phase implementation with embedded validation agents
   - See `/execute-prp` command for detailed execution process

2. **Validation-Driven Progression**
   - **≥80% confidence:** Auto-proceed to next phase
   - **<80% confidence:** Manual review required
   - Validation agents: @phase-qa-tester, @code-reviewer-agent, @functional-test-agent, @integration-test-agent, @security-agent

3. **Output**
   - Implementation code in project structure
   - Validation reports for each phase
   - **Location:** `outputs/validations/phase-[N]-validation.md`

**Checkpoint:** "Implementation complete and validated. Project ready for deployment? (y/n)"

---

## Usage Examples

```bash
# Start new project with initial idea
/start-project "Build a SaaS tool for automated code review using AI agents"

# Start new project with interactive idea input
/start-project

# Resume at specific stage (if workflow was interrupted)
/start-project --resume-stage=2 --project="my-saas-tool"
```

---

## Output Structure

```
outputs/
└── [project-name]/
    ├── idea-description.md           # Stage 1 output
    ├── prp-document.md              # Stage 2 output (with embedded validation subagents)
    ├── validations/
    │   ├── prp-validation.md        # Stage 3 output
    │   ├── phase-1-validation.md    # Stage 4 validation outputs
    │   ├── phase-2-validation.md
    │   └── execution-report.md
    └── implementation/
        └── [generated code and assets from PRP execution]
```

---

## Success Criteria

**Stage 1:** Clear, validated idea with stakeholder buy-in  
**Stage 2:** Comprehensive, context-rich PRP with embedded validation framework  
**Stage 3:** Validated PRP with quality score >8/10 and complete validation specifications  
**Stage 4:** Working implementation with complete validation history and deployment readiness

---

## Key Features

- **Human-in-the-loop:** Decision maker throughout all stages
- **Agent orchestration:** Specialized agents for each stage and validation type
- **Confidence-driven validation:** 80% threshold for automated vs manual review
- **Complete audit trail:** All conversations and decisions documented
- **Resumable workflow:** Can pause/resume at any checkpoint
- **Integration ready:** Works with any AI coding assistant for execution

**Estimated Time:** 2-4 hours for complete workflow (varies by project complexity)