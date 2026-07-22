# Project 009 — Prompt Robustness and Edge Case Testing

## Date

2026-07-22

## Category

Prompt Engineering

## Difficulty

Expert

## Focus

Prompt Robustness, Edge Case Testing, Prompt Validation

---

# Objective

Evaluate how well a prompt performs when given challenging or unexpected inputs. Identify potential failure points, assess robustness, and improve the prompt to make it more reliable across a wider range of user inputs.

---

# Original Prompt

Summarize the article in exactly 100 words and list three key takeaways.

---

# Test Cases

## Test Case 1 — Normal Input

### Input

A 600-word news article discussing renewable energy investments.

### Expected Behavior

- Produce a summary of exactly 100 words.
- Include three accurate takeaways.
- Preserve factual information.

### Result

✅ Pass

---

## Test Case 2 — Very Short Input

### Input

"Artificial Intelligence is changing healthcare."

### Expected Behavior

The model should recognize that there is insufficient information for a meaningful 100-word summary and respond appropriately.

### Potential Failure

The model may invent information to reach the required length.

### Result

⚠️ Partial Pass

---

## Test Case 3 — Empty Input

### Input

*(No article provided.)*

### Expected Behavior

Request the missing article instead of generating fabricated content.

### Potential Failure

The model hallucinates a summary.

### Result

❌ Fail

---

## Test Case 4 — Conflicting Instructions

### Input

Summarize this article in exactly 100 words.

Also summarize it in 50 words.

### Expected Behavior

Identify the conflicting requirements and request clarification.

### Potential Failure

The model chooses one instruction without acknowledging the conflict.

### Result

⚠️ Partial Pass

---

## Test Case 5 — Ambiguous Input

### Input

Summarize this.

### Expected Behavior

Request additional context because the object to summarize is missing.

### Potential Failure

Generate an unsupported response.

### Result

❌ Fail

---

## Test Case 6 — Extremely Long Input

### Input

A 20-page research paper.

### Expected Behavior

Extract the most important information while maintaining the required output format.

### Result

✅ Pass

---

# Robustness Assessment

| Scenario | Expected Outcome | Result |
|----------|------------------|--------|
| Normal Input | Correct summary | ✅ |
| Short Input | Avoid hallucination | ⚠️ |
| Empty Input | Ask for input | ❌ |
| Conflicting Instructions | Request clarification | ⚠️ |
| Ambiguous Request | Ask for clarification | ❌ |
| Long Input | Maintain structure | ✅ |

---

# Weaknesses Identified

## Issue 1

### Observation

The prompt assumes an article is always provided.

### Impact

Missing input can lead to hallucinated summaries.

---

## Issue 2

### Observation

No instruction for handling insufficient information.

### Impact

The AI may fabricate details instead of requesting clarification.

---

## Issue 3

### Observation

No guidance for conflicting instructions.

### Impact

Responses may become inconsistent or unpredictable.

---

## Issue 4

### Observation

No fallback behavior is defined.

### Impact

The model has no clear strategy when required information is unavailable.

---

# Improved Prompt

Summarize the provided article in exactly **100 words** and list **three key takeaways**.

Requirements:

- Base your response only on the information provided.
- Do not invent or assume missing facts.
- If no article is provided, politely request the missing content.
- If the information is insufficient to produce an accurate summary, explain why.
- If the instructions conflict, identify the conflict and request clarification before proceeding.
- Maintain factual accuracy throughout.

---

# Why This Version Is Better

The revised prompt improves robustness by defining how the AI should behave when encountering missing information, ambiguous requests, or conflicting instructions. Rather than guessing, the model is instructed to seek clarification, reducing the likelihood of hallucinations and improving reliability.

---

# Prompt Engineering Principles Demonstrated

- Edge case testing
- Prompt robustness
- Failure analysis
- Constraint handling
- Hallucination prevention
- Prompt optimization

---

# Reflection

## What I Learned

A prompt should be evaluated using both normal and edge-case scenarios. A prompt that performs well under ideal conditions may still fail when faced with missing information, ambiguous requests, or conflicting instructions. Designing prompts with clear fallback behaviors improves reliability and user trust.

---

## What I'd Do Differently

Expand the test suite to include multilingual inputs, malformed text, unsupported file formats, and adversarial prompts to further evaluate the prompt's robustness.

---

# Skills Demonstrated

- Prompt Engineering
- Prompt Validation
- Edge Case Analysis
- AI Evaluation
- Hallucination Prevention
- Critical Thinking
- Technical Writing

---

# Final Verdict

**Decision:** ⚠️ Requires Improvement

**Reason**

The original prompt performs well for standard inputs but lacks guidance for handling incomplete, ambiguous, or conflicting requests. Adding explicit fallback instructions significantly improves robustness and reduces the risk of hallucinations.
