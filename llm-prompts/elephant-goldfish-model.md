# The Elephant-Goldfish Model (EGM) for AI-Assisted Software Engineering

> *A Practical Guide to Design-Driven AI Development, Prompt Protocols, and Context Architecture*
> **Source / Reference:** Dave Rensin (2026) — https://drensin.medium.com/elephants-goldfish-and-the-new-golden-age-of-software-engineering-c33641a48874

---

## Executive Summary & Core Philosophy

As Large Language Models (LLMs) and AI coding assistants become deeply integrated into software development, the traditional role of typing syntax into an IDE is shifting toward **system architecture, intent, and design judgment**.

### Key Software Principles

1. **Design is the New Code** (`sizeof(docs) << sizeof(code)`): Providing context to an LLM via plain English design documents is significantly cheaper, faster, and more reliable than forcing it to read tens or hundreds of thousands of lines of raw code.
2. **Preventing AI "Slop":** Generating code without strict design guardrails mass-produces architectural debt and unmaintainable code. Shifting design decisions into human-reviewed documents *before* writing code keeps systems readable and maintainable.
3. **The Engineer's Role as Agent Manager:** Human review of 100% of machine-generated code becomes impossible as volume expands. The primary artifact humans must own, review, and stand behind is the **Design Document**.

---

## The Elephant-Goldfish Metaphor

The Elephant-Goldfish Model (EGM) separates deep context retention from unbiased testing and auditing:

* **The Elephant:** A long-running, heavily-prompted, context-rich AI session. It holds all institutional knowledge, architectural micro-decisions, and conversation history. Used to co-design features and draft the Design Document.
* **The Goldfish:** A brand-new, completely fresh AI session with zero prior memory. It only knows what is put directly in front of it. Used to strictly test, audit, and validate the Design Document without bias or context leakage.

> **Golden Rule of EGM:** *Feed the Elephant; test it against the Goldfish.*

---

## The 4-Phase EGM Workflow

```
┌──────────────────────────────────────────┐
│      PHASE 1: GROW THE ELEPHANT          │
│  • Load context, explore the problem     │
│  • Run the "no code" interrogation loop  │
│  • Draft a technical proposal in prose   │
└────────────────────┬─────────────────────┘
                     ▼
┌──────────────────────────────────────────┐
│      PHASE 2: TEACH THE ELEPHANT         │
│  • Draft the design doc section by       │
│    section, never in one shot            │
│  • Problem, architecture, alternatives   │
│  • File-by-file implementation plan      │
└────────────────────┬─────────────────────┘
                     ▼
┌──────────────────────────────────────────┐
│      PHASE 3: THE GOLDFISH PROTOCOL      │
│  • Test 1: Comprehension check           │
│  • Test 2: Skeptical technical review    │
│  • Test 3: Implementation readiness      │
└────────────────────┬─────────────────────┘
                     ▼
┌──────────────────────────────────────────┐
│      PHASE 4: IMPLEMENTATION             │
│  • Guardrailed code execution            │
│  • Adversarial "tear it to shreds"       │
│    code review                           │
└──────────────────────────────────────────┘
```

---

### Phase 1: Growing the Elephant (No Code Allowed)

Do not allow the AI to generate code. Engage in a 20–30 minute architectural interview to explore the problem boundaries and challenge assumptions.

#### Step 1: Context Loading

Point the AI at existing documentation or relevant source files. Request a high-level summary of what it learned to verify alignment.

#### Step 2: Enforce the "No Code" Rule

**Prompt — Enforce Design Discussion:**

```text
I do not want you to create code. We are not going to
create code. Resist your impulse to create code.
Instead, we are going to have a design discussion. I am
about to describe a feature. I want you to ask me
clarifying questions and challenge my assumptions. Do
not just accept what I say.
```

If the AI becomes sycophantic or overly agreeable, reset it:

**Prompt — Anti-Sycophancy Reset:**

```text
When you agree with me you are not being helpful. You
are most helpful when you challenge my thinking and
force me to think about the edges of my problem.
```

#### Step 3: First Draft Technical Proposal

Require the AI to propose the technical design first, to surface blind spots before you offer your own solution.

**Prompt — First Draft Technical Proposal:**

```text
Based on your understanding of the codebase and what we
discussed, I would like you to give me a first draft
proposal of a technical implementation to actually make
this feature happen. I'm not looking for code. I want
prose from you that demonstrates your understanding of
my system. Short blocks of pseudocode are fine if you
think that will help, but I would strongly prefer
clearly written text and block diagrams.
```

---

### Phase 2: Teaching the Elephant (Writing the Design Doc)

In the same session, build the Markdown design document iteratively, section by section. Never attempt to one-shot the document.

#### Standard Design Document Structure

1. **The Problem:** 3–5 sentences of plain English business context.
2. **The Technical Plan:** Explanatory prose, component breakdowns, and block diagrams.
3. **Alternatives:** Rejected architectures and trade-offs. This section is your guardrail against future hallucinations.
4. **Detailed Implementation Plan:** Explicitly enumerates **every single file** to be created or modified, with full rationale.

Save this file directly in the repository (e.g. `docs/design/feature-name.md`). It is now your primary source code artifact.

---

### Phase 3: The Goldfish Protocol (Validation Loops)

Open a **brand-new, zero-context session** (the Goldfish) for each validation test. This proves the design document is self-contained and unambiguous.

#### Test 1: Comprehension Check

```text
Read this document and the files it references. Tell me
what it's trying to accomplish, and how my system
currently works as it relates to this feature.
```

If the AI fails to explain the system, add the missing context to the doc and repeat.

#### Test 2: Skeptical Technical Review

```text
Assume the role of an expert technical reviewer. Read
this design doc and all the files it references. Tell
me all the things I missed, all the faulty assumptions,
all the edge cases I'm missing, and things I should
have considered but did not. Every mistake and
ambiguity you find makes you more helpful and useful.
```

Incorporate the valid critiques — typically about 30% are high-value.

#### Test 3: Implementation Readiness Check

```text
You are an experienced software engineer experienced
with our codebase. Read this document and the files it
references and tell me: does it absolutely have all the
information you would require to successfully implement
this feature in your first pass?
```

Answer any remaining questions directly in the document until the AI confirms readiness.

---

### Phase 4: Implementation & Adversarial Review

Hand the finalized design document to an AI session for execution.

#### Step 1: Guardrailed Code Execution

```text
Read this design doc and the files it references.
Implement the feature as described. Follow the plan
exactly.
```

#### Step 2: Adversarial Code Review

After code generation, run a strict quality audit.

```text
I have a strong intuition that this code is of poor
quality. Please tear it to shreds and tell me all the
ways it sucks. Flag any place where there are 10 lines
without comments, missing error handling, poor typing,
or suboptimal performance.
```

---

## Bootstrapping Legacy Codebases ("Peanuts & Hay")

For large repositories or monoliths, do not feed all source code into the LLM at once. Generate hierarchical `README.md` files from the leaf nodes up, via recursive summarization.

```
   [ Root README.md ]      ▲
          ▲                │
   [ Subdir README.md ]    │  aggregate hay
          ▲                │
   [ Leaf README.md ]      │  leaf peanuts
```

### Step-by-Step Protocol

**1. Leaf directories ("peanuts").** Point the AI at leaf folders and generate localized descriptions.

```text
Read the files in this directory and produce a new file
named README.md. This file should:
(a) explain the purpose of this directory and the files
    contained in it, and
(b) enumerate each file in the directory and a short
    description of its function.
```

**2. Human verification.** Have a developer spend 5–10 minutes verifying and correcting the leaf `README.md`.

**3. Parent directories ("hay").** Move up one level and summarize the leaf READMEs along with local files.

```text
Please read all the README.md files in all the
subdirectories below me, then read the code in just
this directory and create a file here named README.md.
Using that information this file should:
(a) explain the purpose of this directory and the files
    contained in it, and
(b) enumerate each file in the directory and a short
    description of its function.
```

**4. Repeat upward.** Continue until you reach the root. You now have a lightweight, compressed context tree — peanuts and hay — that lets any LLM understand the repository instantly without blowing the token budget.

*Once design docs cover 100% of the files in a subsystem, these intermediate READMEs can be archived or deleted.*

---

## Accelerated Team Onboarding Protocol

Use the documented context tree to onboard new engineers or non-engineering contributors such as product managers:

1. **Context container:** Dump all hierarchical `README.md` files and existing design docs into a single workspace or notebook (e.g. NotebookLM).
2. **System scope:** In the system instructions, constrain the workspace to the specific subsystem the new contributor will work on.
3. **The first task:** Have the new team member use that workspace to author an EGM-compliant design document for their first feature request.
4. **Validation gate:** Once their design doc passes human review and the Goldfish readiness test, they can execute the code with AI assistance without introducing architectural slop or burning senior review cycles.

---

## Appendix: EGM Design Document Template

````markdown
# Design Doc: [Feature Name]

## 1. Problem Statement

[3-5 sentences describing the business problem, user
pain point, and objectives.]

## 2. Technical Plan & System Architecture

[Explanatory prose detailing core components, data
flow, and interactions.]

```
[Insert block diagram / ASCII flow here]
```

## 3. Considered Alternatives & Rejected Approaches

* **Alternative A:** [Description]
  **Rejected because:** [Reason]
* **Alternative B:** [Description]
  **Rejected because:** [Reason]

## 4. Detailed Implementation Plan

### Affected Files & Scope

| File Path | Action | Rationale |
| :--- | :--- | :--- |
| `src/auth/session.ts` | Modify | Add JWT refresh |
| `src/auth/types.ts` | Modify | New token types |
| `src/auth/session.test.ts` | Create | Renewal tests |

### Step-by-Step Execution Plan

1. **Step 1:** [Exact logic changes and API signatures]
2. **Step 2:** [Migration or database changes]
3. **Step 3:** [Error handling and boundary conditions]

## 5. Testing & Acceptance Criteria

* [ ] Unit test coverage for edge cases
* [ ] End-to-end integration flow
* [ ] Performance & latency benchmarks
````
