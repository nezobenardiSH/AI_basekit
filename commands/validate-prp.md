# Validate PRP
**Command:** `/validate-prp [optional: initial-idea-description]`

## PRP file: $ARGUMENTS

Comprehensive PRP validation through specialized validation agents to ensure quality, completeness, and implementation readiness. This command orchestrates multiple validation agents to thoroughly review the PRP from different expertise perspectives.

**Expected Input**: Generated PRP file from Stage 2 (e.g., `outputs/prps/project-name-[date].md`)

Read the PRP file first to understand the feature implementation plan, then coordinate validation agents to provide comprehensive quality assessment.

---

## Stage 3: PRP Validation Process

### 1. Initialize PRP Validation Agents

**Validation Team Assembly**:
- **@context-validator-agent**: Verifies sufficient context and documentation completeness
- **@task-validator-agent**: Ensures implementable, logical task progression and appropriate granularity
- **@technical-validator-agent**: Reviews architecture decisions, technology choices, and integration feasibility
- **@completeness-validator-agent**: Checks for gaps, missing requirements, and overall PRP completeness

### 2. Comprehensive PRP Quality Review

**Multi-Perspective Validation Process**:

**Phase 1: Individual Agent Analysis**
- **@context-validator-agent** analyzes:
  - Documentation completeness and accessibility
  - MUST READ section adequacy and reference quality
  - Context sufficiency for AI implementation
  - Integration requirements and existing system coverage
  
- **@task-validator-agent** analyzes:
  - Task granularity and complexity appropriateness (2-4 hour tasks)
  - Implementation sequence logic and dependency management
  - Phase structure and milestone clarity
  - Task specificity and actionability for AI execution

- **@technical-validator-agent** analyzes:
  - Architecture soundness and design pattern appropriateness
  - Technology stack compatibility and integration feasibility
  - Performance and scalability considerations
  - Security architecture and compliance requirements

- **@completeness-validator-agent** analyzes:
  - Overall PRP structure and required section presence
  - Implementation requirement coverage (functional, technical, operational)
  - Gap identification and missing component analysis
  - End-to-end coverage assessment for successful implementation

**Phase 2: Cross-Agent Validation**
- Agents review findings from other validators for consistency
- Identify conflicting recommendations or assessment discrepancies
- Ensure validation coverage doesn't have blind spots or overlaps
- Synthesize findings into coherent improvement recommendations

### 3. Validation Synthesis and Quality Scoring

**Individual Agent Scoring**:
- Each validation agent provides confidence score (1-10) for their domain
- Specific findings, gaps, and improvement recommendations
- Risk assessment and implementation feasibility evaluation
- Priority ranking for identified issues (Critical/Important/Minor)

**Overall PRP Quality Assessment**:
- **Context Quality**: Documentation and implementation guidance adequacy
- **Task Quality**: Implementation sequence and granularity appropriateness  
- **Technical Quality**: Architecture soundness and technology decisions
- **Completeness Quality**: Comprehensive coverage and gap analysis
- **Overall Readiness**: Combined assessment for implementation success

### 4. Generate Comprehensive Validation Report

**Validation Report Structure**:
```markdown
# PRP Validation Report: [Project Name]

## Executive Summary
**Overall PRP Quality Score**: [X/10] (Average of all agent scores)
**Implementation Readiness**: [Ready/Needs Revision/Major Issues]
**Recommendation**: [Proceed/Revise/Redesign]

## Individual Agent Assessments

### Context Validation (@context-validator-agent)
**Score**: [X/10]
**Key Findings**: [Documentation and context assessment]
**Critical Issues**: [Must-fix problems]
**Recommendations**: [Specific improvements needed]

### Task Validation (@task-validator-agent)  
**Score**: [X/10]
**Key Findings**: [Task structure and sequence assessment]
**Critical Issues**: [Task breakdown problems]
**Recommendations**: [Granularity and sequencing improvements]

### Technical Validation (@technical-validator-agent)
**Score**: [X/10] 
**Key Findings**: [Architecture and technology assessment]
**Critical Issues**: [Technical decision problems]
**Recommendations**: [Architecture and technology improvements]

### Completeness Validation (@completeness-validator-agent)
**Score**: [X/10]
**Key Findings**: [Coverage and gap assessment] 
**Critical Issues**: [Missing components or requirements]
**Recommendations**: [Completeness improvements needed]

## Consolidated Improvement Plan

### Critical Issues (Must Fix)
- [Issues that prevent successful implementation]
- [Required changes for basic viability]

### Important Issues (Should Fix)  
- [Issues that significantly impact implementation quality]
- [Recommended changes for better success probability]

### Minor Issues (Could Fix)
- [Issues that would improve overall quality]
- [Nice-to-have improvements for better experience]

## Final Recommendation
**Decision**: [Proceed with current PRP / Revise PRP / Major redesign needed]
**Reasoning**: [Justification for recommendation based on validation findings]
**Next Steps**: [Specific actions needed before proceeding to implementation]
```

### 5. Quality Gate Decision

**PRP Quality Thresholds**:
- **≥8.0 Overall Score**: "PRP validated successfully. Ready for Stage 4 - PRP Execution? (y/n)"
- **6.0-7.9 Overall Score**: "PRP has minor issues. Address recommendations before proceeding? (y/n)"  
- **<6.0 Overall Score**: "PRP requires significant revision. Return to Stage 2 for improvement? (y/n)"

**Validation Decision Logic**:
- **All agents ≥8.0**: Automatic approval with minor notes
- **Any agent <6.0**: Requires revision before proceeding
- **Mixed scores**: Human review of specific issues and recommendations

---

## Output Files

### Generated Validation Report
- **Location**: `outputs/validations/prp-validation-[project-name]-[date].md`
- **Content**: Comprehensive validation findings from all agents
- **Format**: Structured report with scores, findings, and recommendations

### Updated PRP (if needed)
- **Location**: `outputs/prps/[project-name]-revised-[date].md`  
- **Content**: Revised PRP incorporating validation feedback
- **Changes**: Documented improvements based on agent recommendations

---

## Usage Examples

```bash
# Validate newly generated PRP
/validate-prp outputs/prps/my-saas-tool-2025-08-15.md

# Validate revised PRP after improvements
/validate-prp outputs/prps/my-saas-tool-revised-2025-08-15.md

# Re-validate after addressing specific agent feedback
/validate-prp outputs/prps/feature-auth-system-v2.md
```

---

## Success Criteria

- **Comprehensive Assessment**: All validation aspects thoroughly reviewed by specialized agents
- **Quality Assurance**: PRP meets minimum quality thresholds for successful implementation
- **Gap Identification**: All missing components and improvement opportunities identified
- **Implementation Readiness**: Clear determination of whether PRP is ready for AI execution
- **Actionable Feedback**: Specific, implementable recommendations for any needed improvements
- **Quality Gate**: Clear decision on proceeding to implementation vs requiring revision

**Estimated Time**: 15-30 minutes for comprehensive validation depending on PRP complexity

Your PRP validation ensures comprehensive quality assessment through specialized expertise before proceeding to AI-driven implementation, maximizing the probability of successful feature development.