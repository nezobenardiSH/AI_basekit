# Validate Idea Command

**Command:** `/validate-idea [optional: initial-idea-description]`

**Description:** Interactive idea validation through structured conversation with specialized agents across 3 rounds of clarification, challenge, and refinement.

---

## Objective
Validate and refine your AI project idea through multi-agent conversational debate to ensure technical feasibility, business viability, user desirability, and risk awareness before proceeding to PRP creation.

---

## Process

### 1. Initialize Idea Validation Session
- If idea provided: Use initial idea description from command args
- If not provided: Prompt user: "Describe your AI project idea in 2-3 sentences"
- Create conversation context for structured validation rounds

### 2. Initialize Validation Agents
- **Moderator Agent:** Orchestrates validation conversation, manages rounds, ensures all perspectives covered
- **Tech Agent:** Evaluates technical feasibility, architecture, scalability, implementation complexity
- **Business Agent:** Assesses market opportunity, monetization potential, competitive landscape, business model
- **User Experience Agent:** Analyzes user workflows, pain points, value delivery, adoption barriers
- **Risk Agent:** Identifies potential blockers, challenges, assumptions, failure modes

### 3. Round 1: Clarifying Questions (3 Question Cycles)

**Objective:** Build shared understanding of the idea through targeted questions

**Process:**
- Each agent asks 1-2 clarifying questions from their domain expertise
- **Tech Agent examples:**
  - "What's your expected scale - how many users/requests per day?"
  - "Are there any specific technical constraints or existing systems to integrate with?"
- **Business Agent examples:**
  - "Who is your target customer and what's their willingness to pay?"
  - "What's your primary value proposition compared to existing solutions?"
- **UX Agent examples:**
  - "Walk me through a typical user's workflow with your solution"
  - "What's the biggest pain point users face today without your solution?"
- **Risk Agent examples:**
  - "What's your biggest assumption that could make or break this idea?"
  - "What external dependencies or partnerships would you need?"

**Interaction:**
- User answers each agent's questions in detail
- Agents ask follow-up questions based on responses
- 3 cycles of questions ensure thorough understanding
- Moderator ensures all critical areas are covered

### 4. Round 2: Challenge and Debate

**Objective:** Stress-test the idea through constructive challenges and defenses

**Process:**
- **Tech Agent challenges:**
  - "Your proposed architecture might not scale beyond X users because..."
  - "Have you considered the complexity of implementing Y feature?"
  - "What's your plan for handling Z technical risk?"
- **Business Agent challenges:**
  - "The market size for this seems limited because..."
  - "Your monetization strategy has a weakness in..."
  - "Competitors like X already solve this problem - how are you different?"
- **UX Agent challenges:**
  - "Users might not adopt this because their current workflow is..."
  - "The learning curve seems steep - how will you handle onboarding?"
  - "Your value delivery happens too late in the user journey..."
- **Risk Agent challenges:**
  - "Your biggest vulnerability is..."
  - "This assumption seems risky because..."
  - "What happens if Y external factor changes?"

**Interaction:**
- User defends their idea, provides additional context, refines approach
- Agents provide counter-arguments and alternative perspectives  
- Ideas evolve and improve through active debate
- User can ask agents for specific advice on addressing challenges

### 5. Round 3: Synthesis and Refinement

**Objective:** Collaborate to synthesize insights and refine the validated concept

**Process:**
- **Moderator leads synthesis:**
  - "Based on our discussion, here are the key strengths we've identified..."
  - "The main risks/challenges that need addressing are..."
  - "The refined value proposition seems to be..."
- **Agents collaborate to refine:**
  - **Tech Agent:** "The technical approach should focus on..."
  - **Business Agent:** "The go-to-market strategy should prioritize..."
  - **UX Agent:** "The user experience should emphasize..."
  - **Risk Agent:** "The key mitigation strategies should include..."
- **Final refinement:** User and agents work together to polish the core concept

### 6. Generate Validated Idea Document

**Output Location:** `outputs/ideas/[project-name]-validated-[date].md`

**Document Structure:**
```markdown
# [Project Name] - Validated Idea

## Core Concept
[Refined idea description from conversation]

## Value Proposition  
[Clear value statement validated through discussion]

## Target Users & Use Cases
[Defined through UX Agent conversation]

## Technical Approach
[High-level approach validated by Tech Agent]

## Business Model
[Monetization and market approach from Business Agent]

## Key Success Metrics
[Measurable outcomes defined through conversation]

## Identified Risks & Mitigation Strategies
[Risks surfaced by Risk Agent with mitigation plans]

## Key Assumptions to Validate
[Critical assumptions identified during debate]

## Next Steps
[Recommended actions for moving to PRP creation]

## Validation Summary
- Tech Feasibility: [Agent assessment]
- Business Viability: [Agent assessment] 
- User Desirability: [Agent assessment]
- Risk Level: [Agent assessment]
- Overall Confidence: [Moderator synthesis]
```

---

## Usage Examples

```bash
# Start with initial idea
/validate-idea "Build a SaaS tool for automated code review using AI agents"

# Start with interactive idea input
/validate-idea

# Validate existing idea document
/validate-idea --input=outputs/ideas/rough-idea.md
```

---

## Success Criteria

- **Thorough exploration:** All agents have engaged and provided input
- **Refined concept:** Idea has evolved and improved through conversation
- **Risk awareness:** Key risks and mitigation strategies identified
- **Clear next steps:** Ready for PRP creation with solid foundation
- **Stakeholder confidence:** Human feels confident about the validated direction

---

## Conversation Guidelines

- **Stay engaged:** Actively participate in all three rounds
- **Be specific:** Provide detailed answers to agent questions
- **Defend thoughtfully:** Support your idea with reasoning, be open to changes
- **Ask for help:** Use agents as advisors - "How would you approach X?"
- **Iterate:** Ideas should evolve - embrace refinement through discussion

---

## Output Integration

The validated idea document becomes the input for `/create-prp` command, ensuring seamless transition from idea validation to requirements engineering.

**Estimated Time:** 30-60 minutes depending on idea complexity and discussion depth