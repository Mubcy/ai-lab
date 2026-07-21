# Project 004 — Code Review and Quality Evaluation


## Category

AI Evaluation

## Difficulty

Intermediate

## Focus

Code Review, Bug Detection, Maintainability, Best Practices

---

# Objective

Evaluate an AI-generated code solution for correctness, readability, maintainability, efficiency, and adherence to software engineering best practices. Identify weaknesses, explain why they matter, and produce an improved implementation.

---

# Prompt

Write a Python function that returns the second largest number in a list.

Example:

Input:
[3, 8, 2, 5]

Output:
5

---

# AI Response

```python
def second_largest(numbers):
    numbers.sort()
    return numbers[-2]
```

---

# Evaluation Criteria

| Criteria | Description |
|----------|-------------|
| Instruction Following | Does the solution solve the problem? |
| Correctness | Does it always return the correct result? |
| Edge Case Handling | Does it handle unusual inputs correctly? |
| Readability | Is the code easy to understand? |
| Maintainability | Can another developer easily extend or modify it? |
| Efficiency | Is the algorithm efficient? |
| Best Practices | Does it follow Python best practices? |
| Overall Quality | Overall usefulness and reliability |

---

# Issue Identification

## Issue 1

### Observation

The function modifies the original input list.

### Problem

Calling `sort()` changes the user's data. Functions should generally avoid mutating inputs unless clearly documented.

**Severity:** Medium

**Confidence:** High

---

## Issue 2

### Observation

No validation for lists with fewer than two elements.

### Problem

Calling the function with an empty list or a single-element list will raise an IndexError.

**Severity:** High

**Confidence:** High

---

## Issue 3

### Observation

Duplicate values are not considered.

### Problem

If the input is:

```python
[8, 8, 5]
```

the function returns:

```python
8
```

Many interview questions define the second largest **distinct** value, which would be:

```python
5
```

The requirement is ambiguous and should be clarified.

**Severity:** Medium

**Confidence:** Medium

---

## Issue 4

### Observation

The implementation performs an in-place sort.

### Problem

Sorting requires O(n log n) time when the problem can be solved in O(n).

**Severity:** Low

**Confidence:** High

---

# Overall Evaluation

| Category | Score (/5) |
|----------|------------|
| Instruction Following | 4 |
| Correctness | 3 |
| Edge Case Handling | 2 |
| Readability | 4 |
| Maintainability | 3 |
| Efficiency | 3 |
| Best Practices | 2 |
| Overall Quality | 3 |

---

# Improved Solution

```python
def second_largest(numbers):
    if len(numbers) < 2:
        raise ValueError("List must contain at least two numbers.")

    unique = sorted(set(numbers))

    if len(unique) < 2:
        raise ValueError("List must contain at least two distinct numbers.")

    return unique[-2]
```

---

# Why This Version Is Better

- Does not modify the original list.
- Handles invalid input.
- Handles duplicate values.
- Produces predictable errors.
- Easier for another developer to understand.

---

# Reflection

## What I Learned

Correctness alone is not enough when evaluating AI-generated code.
Reviewing side effects, edge cases, efficiency, and maintainability often reveals issues hidden by simple test cases.
Clear assumptions (such as whether values should be distinct) are important when requirements are ambiguous.


---

## What I'd Do Differently

Test the AI solution against a broader set of edge cases before evaluating it.
Consider multiple valid interpretations of ambiguous prompts and mention them explicitly.
Compare alternative implementations to evaluate both correctness and performance.


---

# Skills Demonstrated

- AI Evaluation
- Code Review
- Bug Detection
- Edge Case Analysis
- Software Engineering
- Technical Writing
- Critical Reasoning

---

# Final Verdict

Decision: ⚠️ Accept with Major Revisions

Reason:

The submitted solution works for simple cases but fails to consider several important software engineering concerns, including input validation, side effects, duplicate handling, and algorithmic efficiency. It provides a useful starting point but requires meaningful improvements before being considered production-ready.

