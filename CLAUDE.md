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

## Architecture & Agents

### Core Agent Types

Located in `/agents/`:
- **moderator-agent**: Orchestrates 3-round validation discussions
- **tech-agent**: Evaluates technical feasibility
- **business-agent**: Assesses market opportunity
- **user-experience-agent**: Analyzes user workflows and adoption
- **technical-architect-agent**: Designs system architecture for PRPs

### Data Resources

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


## Important Notes

1. Always check `/commands/start-project.md` for complete workflow details
2. Validation agents require ≥80% confidence for automatic progression
3. PRPs follow the `/template/prp_base.md` structure exactly
4. Each stage has human checkpoints for approval before proceeding