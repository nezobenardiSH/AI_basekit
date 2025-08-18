# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI_basekit is an AI agent orchestration framework for developing AI-powered applications through a structured 4-stage workflow. The framework validates ideas, creates comprehensive PRPs (Product Requirements Prompts), validates implementation plans, and executes development with continuous validation.

## Core Workflow Commands

### Main Commands
- **`/start-project [optional: idea]`** - Orchestrate complete 4-stage development workflow
- **`/validate-idea`** - Stage 1: Multi-agent idea validation (3-round discussion)
- **`/generate-prp <validated-idea-file>`** - Stage 2: Create comprehensive PRP from validated idea
- **`/validate-prp <prp-file>`** - Stage 3: Quality assessment with scoring (target: >8/10)
- **`/execute-prp <prp-file>`** - Stage 4: Implementation with embedded validation

## Agent Architecture

### Available Agents (/.claude/agents/)

**Validation & Review**
- `@business-validator` - Market opportunity and monetization strategy assessment
- `@code-reviewer` - Code quality, security, and maintainability review
- `@risk-agent` - Risk identification and mitigation planning
- `@security-agent` - Security vulnerability and compliance checking

**Architecture & Design**
- `@technical-architect-agent` - System architecture and technology stack design
- `@tech-agent` - Technical feasibility evaluation
- `@integration-agent` - System integration and compatibility assessment

**User Experience**
- `@user-experience-agent` - User workflow and adoption analysis
- `@moderator-agent` - Orchestrates multi-agent validation discussions

**Task Management**
- `@task-breakdown-agent` - Breaks ideas into implementable phases
- `@context-manager` - Compresses and hands off context between tasks
- `@context-researcher-agent` - Finds relevant documentation and patterns

**Quality Assurance**
- `@context-validator-agent` - Verifies documentation completeness
- `@task-validator-agent` - Ensures logical task progression
- `@technical-validator-agent` - Reviews architecture decisions
- `@completeness-validator-agent` - Checks for gaps and missing requirements
- `@functional-test-agent` - Validates feature correctness and UX
- `@integration-test-agent` - Tests system compatibility and performance

## Project Structure

```
.claude/
├── agents/          # Agent definitions
├── commands/        # Command implementations
outputs/
├── ideas/          # Stage 1: Validated concepts
├── prps/           # Stage 2: Product Requirements Prompts
└── validations/    # Stage 3-4: Validation reports
context/            # Existing system documentation
template/           # PRP templates
```

## Validation Framework

### Confidence Thresholds
- **≥80%**: Automatic progression to next phase
- **<80%**: Manual review required
- **Stage 3 Gate**: PRP quality score must exceed 8/10

### PRP Requirements
Every PRP must include:
1. MUST READ section with critical documentation
2. Task breakdown with specific file operations
3. Embedded validation agents with confidence thresholds
4. Implementation blueprint with pseudocode
5. Validation loops with executable commands


## Workflow Success Criteria

- **Stage 1**: Clear validated idea with stakeholder buy-in
- **Stage 2**: Comprehensive PRP with embedded validation framework
- **Stage 3**: PRP quality score >8/10 with complete specifications
- **Stage 4**: All validation agents report ≥80% confidence

## Key Implementation Notes

1. Commands and agents are defined in `.claude/` directory structure
2. Use `/agents` command to view and manage available agents
3. Agent collaboration follows: Context Research → Architecture Planning → Task Breakdown → Validation
4. Each stage includes human checkpoints for approval
5. Context folder contains existing system descriptions for integration