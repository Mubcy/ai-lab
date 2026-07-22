# Project 008 — Multi-Step Workflow Prompting

## Date

2026-07-22

## Category

Prompt Engineering

## Difficulty

Advanced

## Focus

Multi-Step Prompting, Workflow Design, Task Decomposition

---

# Objective

Design a prompt that guides an AI model through a complex task using a structured, step-by-step workflow. Compare it with a single-step prompt and evaluate which approach is more reliable and suitable for production use.

---

# Task

Summarize a news article and identify its key insights.

---

# Prompt A

Summarize this news article and tell me the important points.

---

# Prompt B

Analyze the news article by completing the following steps in order.

### Step 1

Identify the main topic of the article.

### Step 2

Write a summary in no more than 100 words.

### Step 3

List five key takeaways.

### Step 4

Identify any statistics, dates, or important figures mentioned.

### Step 5

Classify the overall sentiment as:

- Positive
- Neutral
- Negative

### Step 6

Return the results using the following Markdown format.

```markdown
## Topic

...

## Summary

...

## Key Takeaways

- ...

## Important Facts

- ...

## Overall Sentiment

...
```

Requirements:

- Do not include personal opinions.
- Do not invent missing information.
- Base every statement only on the article.

---

# Evaluation Criteria

| Criteria | Description |
|----------|-------------|
| Workflow Design | Is the task broken into logical steps? |
| Clarity | Are the instructions easy to follow? |
| Constraint Compliance | Are measurable requirements included? |
| Reliability | Is the prompt likely to produce consistent outputs? |
| Production Readiness | Is the prompt suitable for automation? |
| Overall Quality | Overall effectiveness |

---

# Prompt Analysis

## Prompt A

### Strengths

- Short and easy to write.
- Flexible for simple summarization tasks.

### Weaknesses

- No defined workflow.
- Important details may be omitted.
- Inconsistent structure.
- Difficult to compare outputs.

---

## Prompt B

### Strengths

- Breaks a complex task into manageable steps.
- Ensures important information is extracted.
- Produces consistent formatting.
- Easy to evaluate and automate.
- Reduces ambiguity.

### Weaknesses

- Longer prompt.
- Requires more tokens.

---

# Comparison

| Category | Prompt A | Prompt B |
|----------|----------|----------|
| Step-by-Step Workflow | ❌ | ✅ |
| Structured Output | ❌ | ✅ |
| Information Coverage | ⭐⭐☆☆☆ | ⭐⭐⭐⭐⭐ |
| Automation Ready | ⭐⭐☆☆☆ | ⭐⭐⭐⭐⭐ |
| Consistency | ⭐⭐☆☆☆ | ⭐⭐⭐⭐⭐ |
| Ease of Evaluation | ⭐⭐☆☆☆ | ⭐⭐⭐⭐⭐ |

---

# Production Applications

Multi-step prompting is commonly used in:

- AI research assistants
- Customer support agents
- Document analysis
- Financial reporting
- Medical summarization
- Legal document review
- Workflow automation
- AI agent systems

---

# Prompt Engineering Principles Demonstrated

- Task decomposition
- Workflow design
- Sequential reasoning
- Constraint writing
- Structured outputs
- Prompt optimization

---

# Reflection

## What I Learned

Breaking a complex task into smaller, ordered steps improves consistency and reduces the likelihood of the AI overlooking important requirements. Multi-step prompting makes outputs easier to validate and integrate into production workflows.

---

## What I'd Do Differently

Test the workflow on different types of documents, such as research papers, legal contracts, and technical documentation, to evaluate whether the prompt generalizes well across domains.

---

# Skills Demonstrated

- Prompt Engineering
- Workflow Design
- Multi-Step Prompting
- Sequential Task Design
- AI Automation
- Technical Writing
- Critical Thinking

---

# Final Verdict

**Decision:** ✅ Prompt B Recommended

**Reason**

The multi-step prompt provides a clear workflow, improves information coverage, and produces structured, repeatable outputs. While it requires more tokens than the simpler prompt, its consistency and production readiness make it the stronger choice for complex AI tasks.
