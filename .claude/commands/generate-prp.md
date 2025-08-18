# Create PRP

## Feature file: $ARGUMENTS

Generate a complete PRP for general feature implementation with thorough research and agent collaboration. 
**Command:** `/generate-prp [optional: initial-idea-description]`

**Expected Input**: Validated idea file from Stage 1 (e.g., `outputs/ideas/project-name-validated-[date].md`)

Read the validated idea file first to understand what needs to be created, the validation results from Stage 1, and integration requirements with existing systems.

The AI agent only gets the context you are appending to the PRP and training data. Assume the AI agent has access to the codebase and the same knowledge cutoff as you, so its important that your research findings are included or referenced in the PRP. The Agent has Websearch capabilities, so pass urls to documentation and examples.

## Agent Collaboration Process

1. **Context Research Phase**
   - **@context-researcher-agent**: Analyze existing system descriptions from `context/` folder
   - **@integration-agent**: Assess integration points and compatibility requirements with existing system
   - Document current system constraints and integration requirements

2. **Architecture Planning Phase**
   - **@technical-architect-agent**: Define system architecture, technology stack, and component design
   - **@task-breakdown-agent**: Break down feature into implementable phases and tasks
   - Plan detailed implementation approach with clear dependencies

3. **Research and Validation Phase**
   - Search for similar features/patterns in the codebase
   - Identify files to reference in PRP
   - Note existing conventions to follow
   - Check test patterns for validation approach
   - External research: Library documentation, implementation examples, best practices

## Research Process

1. **Codebase Analysis** 
   - Search for similar features/patterns in the existing codebase
   - Check `examples/` folder for code patterns (may be empty initially - will grow over time)
   - Identify files to reference in PRP for consistency
   - Note existing conventions and patterns to follow
   - Check test patterns for validation approach

2. **External Research** (if needed)
   - Library documentation (include specific URLs)
   - Framework documentation and best practices
   - Common implementation patterns and pitfalls

3. **User Clarification** (if needed)
   - Specific patterns to mirror and where to find them?
   - Integration requirements and where to find them?

## PRP Generation

Using `templates/prp_base.md` as template:

### Critical Context to Include and pass to the AI agent as part of the PRP
- **Documentation**: URLs with specific sections
- **Code Examples**: Real snippets from codebase
- **Gotchas**: Library quirks, version issues, existing system constraints
- **Patterns**: Existing approaches to follow from current system
- **Integration Requirements**: How to connect with existing system components

### Implementation Blueprint
- Start with pseudocode showing approach
- Reference real files for patterns
- Include error handling strategy
- List tasks to be completed to fulfill the PRP in the order they should be completed
- **Integration with existing system**: Specific MODIFY/CREATE operations for seamless connection

### Embedded Validation Agents
Include validation requirements for each implementation phase:

```markdown
## Validation Framework

After each implementation phase, call the following validation agents:

### Phase Validation Requirements
- **@code-review-agent**: Review code quality, best practices, maintainability (Target: ≥80% confidence)
- **@functional-test-agent**: Validate feature correctness and user experience (Target: ≥80% confidence)  
- **@integration-test-agent**: Test system compatibility and performance (Target: ≥80% confidence)
- **@security-agent**: Check security vulnerabilities and compliance (Target: ≥80% confidence)

### Validation Decision Logic
- **≥80% confidence from all agents**: "Phase validated successfully. Continue to next phase? (y/n)"
- **<80% confidence from any agent**: "Validation concerns detected. Please review manually before proceeding."

### Validation Report Format
Each agent should provide:
- Confidence score (0-100%)
- Specific findings and recommendations
- Pass/fail status for phase progression
```

### Validation Checkpoints (Configure Based on Project)
These are commands the AI can run to verify the implementation is working correctly.
**Configure based on your project's tech stack and available tools.**

**Check your project for:**
- **Package files**: `package.json`, `pyproject.toml`, `requirements.txt`, `Gemfile`, etc.
- **Config files**: `.eslintrc`, `pytest.ini`, `tsconfig.json`, etc.  
- **Test directories**: `tests/`, `__tests__/`, `spec/`, etc.
- **Scripts**: Check `package.json` scripts or `Makefile` for existing validation commands

**Include validation commands that work in your project:**

```bash
# Python projects with pytest and ruff
pytest tests/ -v
ruff check --fix .
mypy .

# Node.js projects with npm scripts
npm test
npm run lint
npm run type-check

# Generic commands that often work
# Run existing test suite (if it exists)
make test

# Check if linting is configured
make lint
```

**Instructions for PRP Creation:**
1. **Check what tools are installed** in the target project
2. **Look for existing scripts** in package.json, Makefile, or project config
3. **Only include commands that will actually work** in that environment
4. **If no validation tools exist**, rely on validation agents only

**Fallback**: If no validation checkpoints are available, include this note in the PRP:
```markdown
Note: No automated validation tools configured. Rely on validation agents for quality assurance.
```

*** CRITICAL AFTER YOU ARE DONE RESEARCHING AND EXPLORING THE CODEBASE AND COLLABORATING WITH AGENTS BEFORE YOU START WRITING THE PRP ***

*** ULTRATHINK ABOUT THE PRP AND PLAN YOUR APPROACH THEN START WRITING THE PRP ***

## Agent Integration Summary

Before writing the PRP, ensure you have:
- [ ] **@context-researcher-agent** provided current system understanding
- [ ] **@integration-agent** identified compatibility requirements and integration points  
- [ ] **@technical-architect-agent** defined architecture and technology approach
- [ ] **@task-breakdown-agent** created detailed implementation phases and tasks
- [ ] All agent insights incorporated into PRP structure
- [ ] Validation agents embedded with confidence scoring requirements

## Output
Save as: `outputs/prps/{feature-name}-[date].md`

## Quality Checklist
- [ ] All necessary context included from agent collaboration
- [ ] Current system integration requirements documented
- [ ] Embedded validation agents with ≥80% confidence thresholds
- [ ] References existing patterns from context analysis
- [ ] Clear implementation path with phase-by-phase breakdown
- [ ] Error handling documented
- [ ] Embedded validation agents with ≥80% confidence thresholds
- [ ] Seamless integration approach with existing system

Score the PRP on a scale of 1-10 (confidence level to succeed in one-pass implementation using claude codes with validation checkpoints)

Remember: The goal is one-pass implementation success through comprehensive context and embedded validation framework.