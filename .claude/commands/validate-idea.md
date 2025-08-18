# Validate Idea Command

**Command:** `/validate-idea [optional: initial-idea-description]`

**Description:** Interactive idea validation through a structured 3-round conversation exploring technical, business, user experience, and risk perspectives.

---

## Objective
Validate and refine your AI project idea through an interactive conversation that thoroughly explores feasibility, viability, and potential challenges before proceeding to PRP creation.

---

## How It Works

You'll engage in a structured conversation with Claude across 3 rounds:
1. **Clarifying Questions** - Building deep understanding of your idea
2. **Challenge & Debate** - Stress-testing assumptions and approach
3. **Synthesis & Refinement** - Collaboratively refining the validated concept

Claude will explore your idea from four key perspectives:
- **Technical**: Feasibility, architecture, scalability, implementation complexity
- **Business**: Market opportunity, monetization, competitive landscape
- **User Experience**: User workflows, pain points, value delivery
- **Risk**: Potential blockers, critical assumptions, failure modes

---

## Process

### 1. Start the Session
- If idea provided: Begin with the supplied description
- If not provided: Ask user to describe their idea in 2-3 sentences
- Set up context for the structured validation conversation

### 2. Round 1: Clarifying Questions (3 Cycles)

**Purpose:** Build comprehensive understanding through targeted questions

**Cycle 1 - Foundation:**
Ask 2-3 foundational questions exploring:
- Target users and expected scale
- Core problem being solved
- Basic user workflow

Example: "Who are your target customers and what scale do you envision?"

**WAIT for response before continuing.**

**Cycle 2 - Depth:**
Based on their answers, dig deeper into:
- Technical requirements and constraints
- Business model and monetization
- User pain points and value proposition
- User flow and walkthrough

Example: "Given your target market, how would you monetize this?"

**WAIT for response before continuing.**

**Cycle 3 - Critical Factors:**
Explore crucial aspects:
- Key assumptions and dependencies
- Success metrics and timeline
- Potential integration needs

Example: "What's your biggest assumption that could make or break this?"

**WAIT for response before moving to Round 2.**

### 3. Round 2: Challenge and Debate

**Purpose:** Stress-test assumptions and strengthen the concept

Based on Round 1 responses, present specific challenges:

**Technical Challenges:**
Raise concerns about scalability, complexity, or technical feasibility based on what they've shared.

**WAIT for their defense/refinement.**

**Business Challenges:**
Question market size, competition, or monetization strategy using their specific context.

**WAIT for their response.**

**User & Risk Challenges:**
Challenge adoption barriers, key assumptions, or dependencies they've mentioned.

**WAIT for their adjustments.**

Encourage idea evolution through this constructive debate.

### 4. Round 3: Synthesis and Refinement

**Purpose:** Collaboratively refine the validated concept

**Synthesis:**
Present what you've learned:
- Key strengths identified
- Main challenges to address
- Refined value proposition

"Does this capture your refined vision? What would you adjust?"

**WAIT for feedback.**

**Recommendations:**
Offer specific suggestions for:
- Technical implementation approach
- Go-to-market strategy
- MVP feature prioritization

"How do these align with your vision?"

**WAIT for input.**

**Final Confirmation:**
Summarize the evolved concept and ask:
"Is this ready for PRP creation, or should we refine anything further?"

**WAIT for confirmation.**

### 5. Generate Validated Idea Document

**Only after user confirmation**, create the document.

**Output Location:** `outputs/ideas/[project-name]-validated-[date].md`

**Document Structure:**
```markdown
# [Project Name] - Validated Idea

## Core Concept
[Refined idea description incorporating all conversation insights]

## Value Proposition  
[Clear value statement evolved through the discussion]

## Target Users & Use Cases
[Specific users and use cases discussed in Round 1]

## Technical Approach
[Technical implementation approach refined through challenges]

## Business Model
[Monetization strategy validated through market challenges]

## Key Success Metrics
[Success metrics the user defined during conversation]

## Identified Risks & Mitigation Strategies
[Specific risks discussed and mitigation strategies developed]

## Key Assumptions to Validate
[Critical assumptions identified and discussed]

## Next Steps
[Concrete next steps for PRP creation]

## Validation Summary
- Tech Feasibility: [Assessment based on technical discussion]
- Business Viability: [Assessment based on market discussion] 
- User Desirability: [Assessment based on UX discussion]
- Risk Level: [Assessment based on risk discussion]
- Overall Confidence: [Synthesis of entire conversation]
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

- **Comprehensive exploration:** All four perspectives thoroughly examined
- **Refined concept:** Idea evolved through the conversation
- **Risk awareness:** Key challenges and mitigation strategies identified
- **Clear next steps:** Ready for PRP creation
- **User confidence:** User feels validated direction is solid

---

## Important Notes

**This is an INTERACTIVE conversation:**
- Ask questions and WAIT for responses
- Build each round on actual user input
- Don't make assumptions - use what the user tells you
- Keep the conversation natural and collaborative

**For Users:**
- Your input drives the validation - be specific and detailed
- Defend your ideas thoughtfully but stay open to refinement
- Ask questions if anything needs clarification
- Expect your idea to evolve through the discussion

---

## Next Steps

The validated idea document serves as input for the `/generate-prp` command, ensuring smooth transition to requirements creation.

**Estimated Time:** 30-45 minutes for typical validation session