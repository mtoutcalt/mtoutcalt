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
