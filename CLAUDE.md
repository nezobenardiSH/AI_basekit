# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI_basekit is an AI agent orchestration framework for developing AI-powered applications through a structured 4-stage workflow. The framework uses specialized agents to validate ideas, create comprehensive PRPs (Product Requirements Prompts), validate implementation plans, and execute development with continuous validation.

## Key Commands

### Project Development Workflow

1. **`/start-project [optional: initial-idea-description]`** - Complete AI project development workflow from idea validation through implementation
   - Stage 1: Concept Validation with agent debate
   - Stage 2: Requirements Engineering (PRP creation) 
   - Stage 3: PRP Validation with quality scoring
   - Stage 4: PRP Execution with confidence-based validation

2. **`/generate-prp outputs/ideas/[project-name]-validated-[date].md`** - Generate comprehensive PRP from validated idea
   - Reads validated idea from Stage 1
   - Creates detailed implementation blueprint
   - Embeds validation agents with confidence scoring

3. **`/validate-prp outputs/prps/[project-name]-[date].md`** - Validate PRP quality before implementation
   - Orchestrates 4 validation agents
   - Provides quality score (1-10)
   - Generates validation report with recommendations

4. **`/validate-idea`** - Stage 1 command for orchestrated agent validation discussions
   - 3-round structured validation process (Clarify → Challenge → Synthesize)
   - Multi-agent collaboration (moderator, tech, business, UX, risk agents)

5. **`/execute-prp`** - Stage 4 command for PRP implementation with embedded validation

## Architecture & Agents

### Core Agent Types

Located in `/.claude/agents/`:

**Stage 1: Validation Agents**
- **moderator-agent**: Orchestrates 3-round validation discussions
- **tech-agent**: Evaluates technical feasibility
- **business-validator**: Assesses market opportunity with structured validation
- **user-experience-agent**: Analyzes user workflows and adoption
- **risk-agent**: Identifies potential blockers and challenges

**Stage 2: PRP Creation Agents**
- **context-researcher-agent**: Finds relevant docs, patterns, libraries
- **task-breakdown-agent**: Breaks ideas into implementable phases
- **technical-architect-agent**: Designs system architecture for PRPs
- **integration-agent**: Considers existing codebase integration

**Stage 3: PRP Validation Agents**
- **context-validator-agent**: Verifies documentation completeness
- **task-validator-agent**: Ensures implementable task progression
- **technical-validator-agent**: Reviews architecture decisions
- **completeness-validator-agent**: Checks for gaps and completeness

**Stage 4: Implementation Validation**
- **code-review-agent**: Reviews implementation quality
- **integration-agent**: Validates system integration

### Data Resources

- `/context/`: Contains existing system documentation and descriptions for context research
- `/data/`: Optional directory for project-specific data files (personas, user types, etc.)

### Output Structure

```
outputs/
├── ideas/          # Stage 1: Validated concept documents
├── prps/           # Stage 2: Product Requirements Prompts
└── validations/    # Stage 3: PRP validation reports
```

### Templates

- `/template/prp_base.md`: Base template for PRP generation with validation loops
  - Includes context-rich structure with validation agents
  - Requires MUST READ section, task breakdown, and validation framework
  - Progressive success approach: start simple, validate, enhance

## Development Patterns

### PRP Structure Requirements

Every PRP must include:
1. **MUST READ section**: Critical documentation and references
2. **Task breakdown**: Specific CREATE/MODIFY operations with dependencies
3. **Validation agents**: Embedded with ≥80% confidence thresholds
4. **Implementation blueprint**: Pseudocode and architectural patterns
5. **Validation loops**: Executable commands for quality assurance

### Agent Collaboration Flow

1. Context research (existing system analysis)
2. Architecture planning (technical design)
3. Task breakdown (implementation phases)
4. Validation embedding (quality checkpoints)

### Quality Gates

- **Stage 1 Success**: Validated idea with stakeholder buy-in
- **Stage 2 Success**: PRP with embedded validation framework
- **Stage 3 Success**: Quality score >8/10
- **Stage 4 Success**: ≥80% confidence from all validation agents


## Build & Test Commands

### TypeScript Projects
- **Type checking**: `tsc --no-emit` (runs automatically after Write/Edit operations via hooks)
- **No package.json found**: This is a documentation/agent framework project

### Python Projects (when applicable)
- **Linting**: `ruff check [file]` or `ruff check src/`
- **Type checking**: `mypy [file]` or `mypy src/`
- **Testing**: `pytest` or `python -m pytest`
- **Auto-fix**: `ruff check [file] --fix`

## Validation Framework

### Confidence Thresholds
- **≥80% confidence**: Automatic progression to next phase
- **<80% confidence**: Manual human validation required
- **Quality gates**: Stage 3 requires >8/10 score for progression

### Embedded Validation Loops
PRPs include executable validation commands:
```bash
# Level 1: Syntax & Style
ruff check src/new_feature.py --fix
mypy src/new_feature.py

# Level 2: Unit Tests
uv run pytest test_new_feature.py -v

# Level 3: Integration Test
curl -X POST http://localhost:8000/feature
```

## Important Notes

1. Always check `/.claude/commands/start-project.md` for complete workflow details
2. Validation agents require ≥80% confidence for automatic progression
3. PRPs follow the `/template/prp_base.md` structure exactly
4. Each stage has human checkpoints for approval before proceeding
5. Context research uses `/context/` folder for existing system documentation
6. TypeScript type checking runs automatically via post-tool-use hooks