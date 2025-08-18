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
- `@code-reviewer` - Code quality, security, and maintainability review
- `@security-agent` - Security vulnerability and compliance checking

**Architecture & Design**
- `@technical-architect-agent` - System architecture and technology stack design
- `@integration-agent` - System integration and compatibility assessment

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

## Directory Structure & Purpose

```
context/            # Existing system documentation (BO, POS, Beep systems)
data/               # Project data like user personas, lists
examples/           # Code patterns and examples for reference
outputs/
├── ideas/          # Stage 1: Validated concepts
├── prps/           # Stage 2: Product Requirements Prompts
└── validations/    # Stage 3-4: Validation reports
.claude/
├── agents/         # Specialized agent definitions (13 agents)
├── commands/       # 5 core workflow commands
└── settings.local.json  # Permissions and tool access
```

## Key Implementation Notes

1. This is a framework, not traditional code - no build/test commands needed
2. Commands and agents are defined in `.claude/` directory structure
3. Agent collaboration follows: Context Research → Architecture Planning → Task Breakdown → Validation
4. Each stage includes human checkpoints for approval
5. Context folder contains existing system descriptions for integration
6. Framework operates through Claude Code's command system with specialized agents

# important-instruction-reminders
Do what has been asked; nothing more, nothing less.
NEVER create files unless they're absolutely necessary for achieving your goal.
ALWAYS prefer editing an existing file to creating a new one.
NEVER proactively create documentation files (*.md) or README files. Only create documentation files if explicitly requested by the User.