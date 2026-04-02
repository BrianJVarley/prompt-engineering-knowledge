# 🧠 Prompt Engineering Cheat Sheet (Engineer Edition)

![AI](https://img.shields.io/badge/AI-Prompt%20Engineering-blue)
![LLM](https://img.shields.io/badge/LLM-Best%20Practices-green)


> **Design principle:**
> Good prompts = **Context + Clear Task + Guided Reasoning + Structured Output**

---

## 🧱 Canonical Prompt Template

```txt id="wl6lze"
You are a [ROLE].

<CONTEXT>
Relevant background, inputs, constraints
</CONTEXT>

<TASK>
Clear, specific instruction
</TASK>

<REASONING>
(Optional) Think step by step or follow a structure
</REASONING>

<CONSTRAINTS>
- Rules, limits, do/don’t
</CONSTRAINTS>

<OUTPUT_FORMAT>
Exact structure (JSON, Markdown, code, etc.)
</OUTPUT_FORMAT>
```

---

## 🏷️ Why Use XML / LLM Tags?

Structured tags improve:

* ✅ Consistency
* ✅ Parsing reliability
* ✅ Model focus (reduced hallucination)

👉 Think of tags like **interfaces for LLMs**

---

## 🧠 Reasoning Patterns (When Things Get Hard)

### Chain-of-Thought (CoT)

```txt id="cot1"
Explain your reasoning step by step before the final answer.
```

### Zero-shot CoT

```txt id="cot2"
Let's think step by step.
```

### Few-shot CoT

```txt id="cot3"
Q: 3 + 2?
A: 3 + 2 = 5

Q: 10 - 4?
A: 10 - 4 = 6

Now:
Q: 7 + 8?
```

### Structured Reasoning

```txt id="cot4"
Break into:
1. Analysis
2. Steps
3. Final answer
```

---

## 🧩 Context Engineering

**Include**

* Inputs (code, logs, data)
* Goal (desired outcome)
* Constraints (stack, limits)

**Avoid**

* Noise
* Ambiguity

---

## 🎯 Task Clarity

Bad:

```txt id="bad1"
Improve this code
```

Good:

```txt id="good1"
Refactor to reduce time complexity from O(n²) to O(n)
```

---

## 🧪 Prompting Strategies

### One-shot

```txt id="one1"
Example:
Input → Output

Now:
Input →
```

### Few-shot (preferred)

* 2–5 examples
* Include edge cases
* Keep format identical

---

## ⚙️ Output Control

```txt id="out1"
Return JSON:
{
  "issue": "...",
  "fix": "...",
  "reason": "..."
}
```

---

## 🔒 Constraints

```txt id="const1"
- Max 100 lines
- No external libraries
- Use TypeScript
```

---

## 🎭 Role Prompting

```txt id="role1"
You are a senior frontend engineer specializing in performance.
```

---

## 🧰 Common Engineering Use Cases

* Debugging → root cause + minimal fix
* Code review → performance, security
* Refactoring → maintainability
* System design → trade-offs

---

## 🅰️ Angular Example (Tagged Prompt in Practice)

A real-world example of using tagged prompts for **modern Angular (v17+) development**, focused on performance and maintainability.

```txt id="angular-tagged-example"
You are an expert in TypeScript, Angular, and scalable web application development.

<CONTEXT>
We are building an Angular dashboard using standalone components and signals.
The app suffers from performance issues due to unnecessary re-renders and inefficient state handling.
</CONTEXT>

<TASK>
Refactor the component to improve performance and align with modern Angular best practices.
</TASK>

<REASONING>
1. Identify sources of unnecessary re-renders
2. Optimize state using signals and computed()
3. Improve change detection strategy
</REASONING>

<CONSTRAINTS>
- Use standalone components (no NgModules)
- Use signals for state management
- Apply ChangeDetectionStrategy.OnPush
- Avoid ngClass/ngStyle (prefer direct bindings)
- Keep component single-responsibility
</CONSTRAINTS>

<OUTPUT_FORMAT>
- Refactored Angular component (TypeScript)
- Brief explanation of improvements
</OUTPUT_FORMAT>
```

💡 **Why this works**

* Specific context → Angular + performance
* Structured reasoning → better refactors
* Strong constraints → modern best practices only
* Tagged format → reusable across tools (Copilot, Cursor)

---

## ⚡ Pro Tips

* Examples > instructions
* Add reasoning only when needed
* Break complex tasks down
* Treat prompts like **API contracts**

---

## 🧪 Production-Ready Prompt

```txt id="prod1"
You are a senior software engineer.

<CONTEXT>
Python service with high memory usage under load.
</CONTEXT>

<TASK>
Identify root causes and propose fixes.
</TASK>

<REASONING>
Analyze step by step (memory leaks, data structures, concurrency).
</REASONING>

<CONSTRAINTS>
Be concise and actionable
</CONSTRAINTS>

<OUTPUT_FORMAT>
Bullet points: Issue → Fix
</OUTPUT_FORMAT>
```

---

## 🤖 Agents & Skills (Advanced)

As you scale prompt engineering, move beyond single prompts into **agent-style workflows**.

### `agents.md`

Defines how an AI agent behaves across tasks:

```md
# Agent: Frontend Performance Engineer

## Responsibilities
- Analyze UI performance
- Suggest optimizations
- Refactor Angular/React code

## Rules
- Prefer modern frameworks (signals, hooks)
- Avoid deprecated patterns
```

👉 Think: **persistent role + behavior system**

---

### Skills (Composable Capabilities)

Skills are reusable prompt modules:

```txt id="skill1"
Skill: Debug Angular Performance

Input: Component code
Output: Bottlenecks + fixes
```

👉 Combine skills like functions:

* Debugging
* Refactoring
* Testing
* Architecture

---

### 🧠 Mental Model

* Prompts = **functions**
* Skills = **reusable modules**
* Agents = **systems of prompts**

---

## 🏁 Rule of Thumb

> Bad output?
> Improve **context, examples, constraints, or reasoning** — not the model.

---

## 📌 License

MIT — use freely in your projects.

---

