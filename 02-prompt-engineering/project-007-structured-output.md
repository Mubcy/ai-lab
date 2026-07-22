# Project 007 — Structured Output Prompting

## Date

2026-07-22

## Category

Prompt Engineering

## Difficulty

Advanced

## Focus

Structured Output, JSON Generation, Schema Compliance

---

# Objective

Design a prompt that instructs an AI model to generate structured, machine-readable output. Compare it with an unstructured prompt and evaluate which is more suitable for production systems.

---

# Task

Extract information from a product review.

---

# Product Review

> I bought the NoiseBuds Air Pro last week. The sound quality is excellent, and the battery lasted nearly 30 hours. However, the microphone struggles during phone calls in noisy environments. Overall, I would rate it 4 out of 5 because it's great value for the price.

---

# Prompt A

Extract the important information from the review.

---

# Prompt B

Extract information from the review and return **only** valid JSON using the following schema.

```json
{
  "product_name": "",
  "rating": "",
  "pros": [],
  "cons": [],
  "summary": ""
}
```

Requirements:

- Return valid JSON only.
- Do not include markdown.
- Keep the summary under 30 words.
- Preserve factual accuracy.
- Do not invent information.

---

# Evaluation Criteria

| Criteria | Description |
|----------|-------------|
| Structure | Is the output clearly structured? |
| Schema Compliance | Does it follow the requested JSON schema? |
| Accuracy | Is the extracted information correct? |
| Consistency | Will repeated runs produce similar outputs? |
| Production Readiness | Can downstream systems easily consume the output? |
| Overall Quality | Overall prompt effectiveness |

---

# Prompt Analysis

## Prompt A

### Strengths

- Simple and flexible.
- Easy for users to write.

### Weaknesses

- No output format specified.
- Difficult to automate.
- Responses may vary significantly.
- Hard to validate programmatically.

---

## Prompt B

### Strengths

- Defines a strict schema.
- Produces machine-readable output.
- Easier to validate.
- Suitable for APIs and automation.
- Reduces formatting inconsistencies.

### Weaknesses

- Less flexible.
- Requires the model to strictly follow formatting rules.

---

# Expected Outputs

## Prompt A

Possible output:

> The reviewer liked the sound quality and battery life but disliked the microphone. They rated the product 4/5.

Output varies depending on the model.

---

## Prompt B

Expected output:

```json
{
  "product_name": "NoiseBuds Air Pro",
  "rating": "4/5",
  "pros": [
    "Excellent sound quality",
    "Battery lasts nearly 30 hours",
    "Good value for money"
  ],
  "cons": [
    "Poor microphone performance in noisy environments"
  ],
  "summary": "Strong audio quality and battery life with a weak microphone."
}
```

---

# Comparison

| Category | Prompt A | Prompt B |
|----------|----------|----------|
| Output Format | ❌ | ✅ |
| Machine Readable | ❌ | ✅ |
| Schema Defined | ❌ | ✅ |
| Easy to Validate | ⭐☆☆☆☆ | ⭐⭐⭐⭐⭐ |
| Automation Ready | ⭐☆☆☆☆ | ⭐⭐⭐⭐⭐ |
| Consistency | ⭐⭐☆☆☆ | ⭐⭐⭐⭐⭐ |

---

# Production Use Cases

Structured output prompting is commonly used for:

- Information extraction
- Customer support automation
- Resume parsing
- Invoice processing
- AI agents
- Workflow automation
- Search indexing
- Database population

---

# Prompt Engineering Principles Demonstrated

- Schema design
- Structured outputs
- Constraint writing
- Output validation
- Production-oriented prompting
- Machine-readable formatting

---

# Reflection

## What I Learned

Structured output prompting makes AI responses significantly easier to integrate into software systems. By defining a clear schema and strict formatting requirements, prompts become more reliable, easier to validate, and better suited for automation.

---

## What I'd Do Differently

Experiment with larger and more complex schemas, including nested objects and arrays, to better understand how models handle advanced structured outputs and validation requirements.

---

# Skills Demonstrated

- Prompt Engineering
- Structured Output Design
- JSON Schema Design
- AI Automation
- Data Extraction
- Instruction Design
- Technical Writing

---

# Final Verdict

**Decision:** ✅ Prompt B Recommended

**Reason**

The structured prompt is significantly more suitable for production environments because it generates consistent, machine-readable output that can be validated and consumed by downstream applications with minimal additional processing.
