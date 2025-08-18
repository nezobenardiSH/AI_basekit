# Execute PRP

Implement a feature using the PRP file.

**Command:** `/execute-prp [optional: initial-idea-description]`

**Expected Input**: validated prp from stage 3 (e.g., `outputs/validations/prp-validation-[project-name]-[date].md`)

## PRP File: $ARGUMENTS

## Execution Process

1. **Load PRP**
   - Read the specified PRP file
   - Understand all context and requirements
   - Follow all instructions in the PRP and extend the research if needed
   - Ensure you have all needed context to implement the PRP fully
   - Do more web searches and codebase exploration as needed

2. **ULTRATHINK**
   - Think hard before you execute the plan. Create a comprehensive plan addressing all requirements.
   - Break down complex tasks into smaller, manageable steps using your todos tools.
   - Use the TodoWrite tool to create and track your implementation plan.
   - Identify implementation patterns from existing code to follow.

3. **Execute the plan**
   - Execute the PRP
   - Implement all the code
   - Concurrent Task Execution (if applicable) 
      **For tasks marked [CONCURRENT] in PRP:**: 
      **Sub-Agent Coordination:**
      - Assign each [CONCURRENT] task to appropriate specialized sub-agent
      - Execute all concurrent tasks simultaneously
      - Collect results from all sub-agents
      - Synthesize concurrent task results for sequential phase

      **For tasks marked [SEQUENTIAL] or [DEPENDS: TaskX]:**
      - Load compressed context from previous tasks (if any)
      - Assign task to appropriate implementation sub-agent
      - Execute single focused task with compressed context


#### 4.1 Context Compression After Each Task
```markdown
After completing each sequential task:
@context-manager-agent compress the following:
- Task: [completed task name]
- Results: [files created, key functions, integration points]
- Patterns: [coding patterns established]
- Next Task Needs: [what subsequent task requires]
```

#### 4.2 Context Handoff to Next Task
- Provide compressed context (< 500 tokens) to next task
- Include only essential integration points and patterns
- Remove implementation details and verbose explanations

5. **Phase-by-Phase Validation**
   After completing each implementation phase, execute validation agents:
   - **@phase-qa-tester**: Execute predefined test cases for the completed phase
   - **@code-reviewer-agent**: Review code quality and best practices  
   - **@functional-test-agent**: Validate feature correctness and user experience
   - **@integration-test-agent**: Test system compatibility and performance
   - **@security-agent**: Check security vulnerabilities and compliance
   - Fix any issues with confidence < 80%
   - Re-run validation until all agents report ≥ 80% confidence

6. **Complete**
   - Ensure all checklist items done
   - Run final validation suite
   - Report completion status
   - Read the PRP again to ensure you have implemented everything

6. **Reference the PRP**
   - You can always reference the PRP again if needed

Note: If validation fails, use error patterns in PRP to fix and retry.