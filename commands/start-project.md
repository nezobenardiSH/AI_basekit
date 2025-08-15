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

2. **Initialize Validation Agents**
   - **@moderator-agent:** Orchestrates validation conversation, manages rounds
   - **@tech-agent:** Evaluates technical feasibility, architecture, scalability
   - **@business-agent:** Assesses market opportunity, monetization, competition
   - **@user-experience-agent:** Analyzes user workflows, pain points, value delivery
   - **@risk-agent:** Identifies potential blockers, challenges, assumptions

3. **3-Round Conversational Validation**
- **Validate idea** `/validate-idea`
   - **Round 1: Clarifying Questions (3 cycles)**
     - Agents ask clarifying questions about scope, users, assumptions
     - User provides detailed answers to build shared understanding
   - **Round 2: Challenge and Debate**
     - Agents challenge assumptions from their expertise areas
     - User defends and refines idea through active discussion
   - **Round 3: Synthesis and Refinement**
     - Agents collaborate to synthesize insights
     - Moderator guides final refinement of core concept

4. **Generate Validated Idea Document**
   - **Location:** `outputs/ideas/[project-name]-validated-[date].md`
   - **Content:** Refined concept, value proposition, success metrics, risk assessment

**Checkpoint:** "Proceed to Stage 2 - Requirements Engineering? (y/n/revise)"

---

## Stage 2: Requirements Engineering (PRP Creation)

### Process
1. **Initialize PRP Creation Agents**
   - **@context-researcher-agent:** Finds relevant docs, patterns, libraries
   - **@task-breakdown-agent:** Breaks idea into implementable phases and tasks
   - **@technical-architect-agent:** Defines system design, tech stack, dependencies
   - **@integration-agent:** Considers existing codebase and constraints

2. **Context Gathering and Analysis**
   - **@context-researcher-agent** scans `context/` folder for existing project information
   - Agents research external documentation and best practices as needed
   - Document critical requirements and constraints from existing system

3. **Generate Comprehensive PRP**
   - **Execute PRP creation:** `/generate-prp outputs/ideas/[project-name]-validated-[date].md`
   - **Output follows `prp_base.md` template structure:**
     - **Header**: Project name and context-rich description with validation loops
     - **MUST READ section**: Include all necessary documentation, examples, and caveats
     - **CRITICAL warnings**: Library requirements, gotchas, and implementation pitfalls
     - **Task breakdown**: Specific MODIFY/CREATE file operations with patterns to follow
     - **Validation requirements**: Embedded confidence scoring agents and testing procedures
   - **PRP Creation agents provide context for each section:**
     - **@context-researcher-agent:** Supplies MUST READ documentation and critical warnings
     - **@task-breakdown-agent:** Creates detailed task breakdown with file operations
     - **@technical-architect-agent:** Defines architecture patterns and technical approach
     - **@integration-agent:** Ensures compatibility with existing system context

4. **PRP Output Generation**
   - **Location:** `outputs/prps/[project-name]-[date].md`
   - **Structure:** Follows `templates/prp_base.md` format exactly:
     ```markdown
     name: "Project Name - Context-Rich with Validation Loops"
     description: |
       Template optimized for AI agents with validation capabilities
     
     # MUST READ - Include these in context window
     # CRITICAL: [Implementation warnings and gotchas]
     # [Task breakdown with file operations]
     # [Validation loops with confidence scoring]
     ```
   - **Content:** Context-rich implementation prompt with embedded validation agents following prp_base structure

**Checkpoint:** "Review generated PRP with embedded validation framework and proceed to Stage 3 - PRP Validation? (y/n/revise)"

---

## Stage 3: PRP Validation

### Process
### Process
1. **Execute PRP Validation Command:** `/validate-prp outputs/prps/[project-name]-[date].md`

2. **The `/validate-prp` command orchestrates comprehensive quality review:**
   - **@context-validator-agent:** Verifies sufficient context and documentation completeness
   - **@task-validator-agent:** Ensures implementable, logical task progression and appropriate granularity
   - **@technical-validator-agent:** Reviews architecture decisions, technology choices, and integration feasibility
   - **@completeness-validator-agent:** Checks for gaps, missing requirements, and overall PRP completeness

3. **Quality Assessment and Scoring:**
   - Each agent provides confidence score (1-10) and detailed findings
   - Cross-agent validation for consistency and coverage
   - Overall PRP quality score calculation and implementation readiness assessment
   - Generate comprehensive validation report with prioritized improvement recommendations

4. **Quality Gate Decision:**
   - **≥8.0 Overall Score:** "PRP validated successfully. Ready for Stage 4 - PRP Execution? (y/n)"
   - **6.0-7.9 Overall Score:** "PRP has minor issues. Address recommendations before proceeding? (y/n)"
   - **<6.0 Overall Score:** "PRP requires significant revision. Return to Stage 2 for improvement? (y/n)"

**Checkpoint:** "PRP validated with quality score [X/10]. Proceed to Stage 4 - PRP Execution? (y/n)"

**Output:** `outputs/validations/prp-validation-[project-name]-[date].md`

---

## Stage 4: PRP Execution

### Process
1. **Pre-Execution Setup**
   - Present validated PRP to user
   - Explain execution approach (recommended: Claude Code or similar)
   - Confirm project structure and dependencies are ready

2. **Phase-by-Phase Execution with Confidence Scoring**
   - Execute PRP in phases as defined in document
   - **After each phase:** Automatically call embedded validation subagents
   - **Validation agents provide confidence scores (0-100%):**
     - Code Review Agent, Functional Test Agent, Integration Agent, Security Agent
   - **Confidence-based decision making:**
     - **≥80% confidence:** "Phase validated successfully. Continue to next phase? (y/n)"
     - **<80% confidence:** "Validation concerns detected. Please review manually before proceeding."

3. **Continuous Validation Loop**
   - Implement phase → Validate with agents → Generate confidence scores
   - High confidence (≥80%): Auto-offer to proceed
   - Low confidence (<80%): Require manual human validation
   - Generate validation reports with confidence scores for each phase

4. **Execution Completion**
   - All phases implemented and validated
   - **Final confidence check:** All agents must score ≥80% confidence
   - Generate comprehensive execution report with confidence history
   - **Deployment readiness:** Only achieved when all agents are confident

**Example Validation Flow:**
```
Phase 1 Implementation Complete
→ @code-review-agent: 85% confident ✓
→ @functional-test-agent: 92% confident ✓  
→ @integration-test-agent: 78% confident ⚠️
→ @security-agent: 88% confident ✓

Result: Manual review required (@integration-test-agent <80%)
Action: "Please review integration concerns before proceeding to Phase 2"
```

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