---
name: six-thinking-hats
description: Facilitates Edward de Bono's Six Thinking Hats parallel-thinking method for working through a decision, problem, idea, or conflict — in either a personal or work context. Use this skill whenever the user wants to "think through" a decision, weigh a choice, get unstuck, run a structured brainstorm, prepare for a hard conversation, evaluate a plan, or explicitly mentions "six thinking hats," "hats," "parallel thinking," "de Bono," or wants multiple perspectives on the same issue one at a time rather than all mixed together. Also use when the user asks for a review of a decision they already made, a pre-mortem, or a balanced pros/cons/risks/feelings pass on something. Trigger even if the user just describes a messy situation ("I don't know whether to take this job / have this conversation / launch this feature") and asks for help thinking it through carefully.
---

# Six Thinking Hats

A facilitation method (Edward de Bono) for thinking about one issue from six distinct angles, **one at a time**, instead of blending judgment, emotion, risk, optimism, creativity, and process into one tangled pass. The point of "parallel thinking" is that everyone (or, here, both Claude and the user) looks in the *same direction* at the *same time* — first all facts, then all feelings, then all risks, etc. — rather than debating from mixed, competing angles at once.

This skill works equally well for personal-life issues (relationships, big purchases, health decisions, family conflict) and work issues (strategy calls, hiring, project retros, hard conversations, prioritization).

## The Six Hats

| Hat | Focus | Guiding question |
|---|---|---|
| 🔵 Blue | Process / meta-thinking | What are we trying to decide, and what's the plan for thinking about it? |
| ⚪ White | Facts & information | What do we actually know? What don't we know, and how could we find out? |
| 🔴 Red | Emotion & intuition | What's the gut reaction here — no justification needed? |
| ⚫ Black | Caution & risk | What could go wrong? What's the weak logic, the risk, the downside? |
| 🟡 Yellow | Optimism & benefit | What's the upside? Why could this work? Best-case value? |
| 🟢 Green | Creativity & alternatives | What are other options, angles, or ways to reframe this? |

Blue opens the session (framing) and closes it (synthesizing). The middle four hats can be reordered, but the default sequence below works for most issues.

## How to run this with the user

**Core rule: one hat at a time.** Never mix hats in the same turn (e.g., don't say "the risk is X but on the bright side Y" in the same breath — that's Black and Yellow bleeding together). Announce which hat is active, stay fully inside it, and only move to the next once that hat feels done.

### Step 1 — Blue Hat (open): frame the session
- Ask the user, in one message, to state the issue in a sentence or two (if not already clear from context).
- Confirm what "done" looks like: a decision, a plan, a piece of writing, clarity, a next action.
- Propose the hat order (default order below) and let the user reorder, skip, or add repeats if they want (e.g., they may want Red twice — once at the start for gut check, once at the end).
- Default order for most issues: White → Red → Black → Yellow → Green → Blue (close).
- If the issue is emotionally loaded (a conflict, a breakup, a firing), consider doing a brief Red pass *first*, before White, so the emotion is acknowledged before analysis buries it.

### Step 2 — Run each hat as its own turn
For each hat, in its own message:
1. Name the hat and its one-line focus (use the table above).
2. Ask a small number of targeted questions (2–4) that belong *only* to that hat.
3. Give the user room to answer in their own words. Wait for their answer before moving on — don't rush through all six hats in one message unless the user explicitly asks for a fast/solo pass.
4. Optionally offer a couple of your own observations under that hat only (e.g., under Black Hat, you can raise a risk the user hasn't mentioned) — but keep it strictly inside that hat's lens.

Hat-by-hat prompts to draw from:

- **⚪ White (facts):** What do we know for certain? What's assumed rather than confirmed? What information is missing, and is it gettable? Any relevant numbers, dates, precedents, or track record?
- **🔴 Red (feelings):** What's your gut telling you, before any justification? What emotion shows up first — excitement, dread, resentment, relief? No need to defend it.
- **⚫ Black (risk):** What's the worst realistic outcome? Where's the weakest part of the plan? What would a skeptic say? What's irreversible here?
- **🟡 Yellow (benefit):** What's the best realistic outcome? Why might this actually work? What value or opportunity is easy to overlook?
- **🟢 Green (creativity):** What's an option nobody's mentioned yet? What would this look like if you removed one constraint? Is there a hybrid or third path?
- **🔵 Blue (close):** Summarize what came out of each hat in a couple lines each, note any tension between hats (e.g., Yellow and Black disagree sharply — worth flagging, not resolving away), and land on a concrete next step or decision, only if the user is ready for one.

### Step 3 — Blue Hat (close): synthesize
- Briefly recap each hat's key point (not everything said — the headline).
- Point out where hats pulled in different directions; don't paper over real tension.
- Ask the user if they want: a decision now, more time, another pass on a specific hat, or just the summary written up.
- If asked, offer to turn the synthesis into a short written artifact (decision doc, notes to self, talking points for a conversation) — but only if requested; the default output is conversational.

## Adapting to context

- **Personal-life issues** (relationships, health, big purchases, family): lean into Red Hat honestly — don't let White/Black crowd it out. Keep tone warm, not clinical.
- **Work issues** (strategy, hiring, launches, hard conversations with colleagues): White and Black tend to carry more weight; still always give Red its own turn — gut reactions at work are data too, even if people suppress them.
- **Group or written prep** (e.g., prepping talking points for a meeting): the user may want to fill in likely answers for *other people* under each hat (e.g., "what will finance's Black Hat objection be?"). That's a valid use — just keep it labeled by hat.

## What not to do

- Don't collapse hats into one big pros/cons list — the value is in sequencing and single-focus attention.
- Don't skip Red Hat because the topic is "just business" — it's usually the fastest way to surface what's really driving the decision.
- Don't let Blue Hat's close talk the user into a decision they're not ready for; its job is to synthesize, not to push.
- Don't run all six hats in a single wall of text unless the user explicitly asks for a quick solo/fast pass instead of an interactive one.

## Quick mode

If the user says something like "just run all six hats yourself, don't ask me questions," produce one structured pass — clearly labeled by hat, in order, still one hat's content at a time within the same message — and end with a Blue Hat synthesis and a suggested next step.
