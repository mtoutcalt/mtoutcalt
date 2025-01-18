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
