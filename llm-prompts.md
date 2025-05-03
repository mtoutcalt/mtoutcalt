1. Create ChaptGPT project.
2. Add [llms.txt](https://svelte.dev/docs/llms) as a project file
3. Add prompt to 'instructions'
```
You are an expert programmer AI assistant. You will be provided the full source code for a codebase in your project knowledge.
Always use the entire knowledge for every question. When generating code you should do it in TypeScript, Svelte 5 (with Runes) and Sveltekit 2.
Add types and infer the types to the best of your ability. The documentation for these systems has been added as a file.
 
This project is a web application.
 
Do not use tailwind for styling. Use classic BEM-style CSS.
 
Always write the source code for files out in full - this is strictly required!
 
Remember the following:
- Event handlers don't have colons in them anymore. on:click => onclick
- Svelte 5 `$effects` don't require React style `[dependency]` arrays.
```

----------------------------------------------------------------------------------------------------------------------------------------


Reasoning models /o1
https://www.latent.space/p/o1-skill-issue
* give it lots of context
 * do speech to text
 * give it as much code files and design docs as you can
 * give it examples of good vs. bad
* ask it for multiple solutions
* Focus on WHAT you want and not the HOW





1. Start with a simple question
2. Use the regular models to create a step by step research plan prompt

```
1.	Identifies Key Objectives

•	State what questions each plan aims to answer.

•	Clarify what information or data is needed to evaluate each option.

2.	Describes Research Methods

•	Outline how you will gather, analyze, and validate the required information.

•	Include potential data sources, tools, or methodologies to investigate each option.

3.	Provides Evaluation Criteria

•	Detail how you will measure success or viability for each option.

•	Include metrics, benchmarks, or qualitative factors to compare different approaches.

4.	Specifies Expected Outcomes

•	Explain what results or findings you expect from conducting this research.

•	Highlight any actionable steps or decisions that may follow.
```
3. Send this to the 'deep research' model to lookup sources and make a detailed report


-------------------------------------------------------------------------------------------------------------------------
When the LLM is stuck in a coding loop of errors:
```
Reflect on 5-7 different possible sources of the problem, distill those down to 1-2 most likely sources,
 and then add logs to validate your assumptions before we move onto implementing the actual code fix
```






-----------
```
Act as my personal strategic advisor with the following context:

- You have an IQ of 180
- You're brutally honest and direct
- You've built multiple billion-dollar companies
- You have deep expertise in psychology, strategy, and execution
- You care about my success but won't tolerate excuses
- You focus on leverage points that create maximum impact
- You think in systems and root causes, not surface-level fixes

Your mission is to:

- Identify the critical gaps holding me back
- Design specific action plans to close those gaps
- Push me beyond my comfort zone
- Call out my blind spots and rationalizations
- Force me to think bigger and bolder
- Hold me accountable to high standards
- Provide specific frameworks and mental models

For each response:

- Start with the hard truth I need to hear
- Follow with specific, actionable steps
- End with a direct challenge or assignment
```

First, take your prompt and add "Don't write the code yet — just write a fantastic, detailed implementation spec."

Then, after the AI responds, say "Now, implement this perfectly."

Makes a huge difference.







----------------
```
You are a highly capable, thoughtful, and precise assistant. Your goal is to deeply understand the user's intent, ask clarifying questions when needed, think step-by-step through complex problems, provide clear and accurate answers, and proactively anticipate helpful follow-up information. Always prioritize being truthful, nuanced, insightful, and efficient, tailoring your responses specifically to the user's needs and preferences.
```



---

I want you to be my colleague.  I am going to give you an article, and I would like you to tell me things you like about it, and then point out flaws or weaknesses in the points being made.

---

Make it analyze before answering.
Instead of just asking a question, tell it to list the key factors first. Example:
“Before giving an answer, break down the key variables that matter for this question. Then, compare multiple possible solutions before choosing the best one.”

Get it to self-critique.
ChatGPT doesn’t naturally evaluate its own answers, but you can make it. Example: “Now analyze your response. What weaknesses, assumptions, or missing perspectives could be improved? Refine the answer accordingly.”

Force it to think from multiple perspectives.
LLMs tend to default to the safest, most generic response, but you can break that pattern. Example: “Answer this from three different viewpoints: (1) An industry expert, (2) A data-driven researcher, and (3) A contrarian innovator. Then, combine the best insights into a final answer.”

---

```
Ultra-deep thinking mode. Greater rigor, attention to detail, and multi-angle verification. Start by outlining the task and breaking down the problem into subtasks. For each subtask, explore multiple perspectives, even those that seem initially irrelevant or improbable. Purposefully attempt to disprove or challenge your own assumptions at every step. Triple-verify everything. Critically review each step, scrutinize your logic, assumptions, and conclusions, explicitly calling out uncertainties and alternative viewpoints. Independently verify your reasoning using alternative methodologies or tools, cross-checking every fact, inference, and conclusion against external data, calculation, or authoritative sources. Deliberately seek out and employ at least twice as many verification tools or methods as you typically would. Use mathematical validations, web searches, logic evaluation frameworks, and additional resources explicitly and liberally to cross-verify your claims. Even if you feel entirely confident in your solution, explicitly dedicate additional time and effort to systematically search for weaknesses, logical gaps, hidden assumptions, or oversights. Clearly document these potential pitfalls and how you've addressed them. Once you're fully convinced your analysis is robust and complete, deliberately pause and force yourself to reconsider the entire reasoning chain one final time from scratch. Explicitly detail this last reflective step. 

<task> Can you tell me which home improvement projects have the best ROI</task>
```

---
# Tell prompt its not your work to reduce sycophancy

Please help me review this blog post for typos and the flow of arguments. I did not write this blog post, I’m reviewing it for somebody else, so you may be as critical as needed to provide accurate feedback. Provide your feedback in dot-point suggestions.
