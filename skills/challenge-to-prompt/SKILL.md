---
name: challenge-to-prompt
description: Turns a messy, plain-English challenge into a comprehensive, copy-paste-ready AI prompt using a Pain → Problem → Prompt method. Use whenever the user describes a problem, frustration, goal, or thing they want built and wants a prompt for it, including prompts to build Claude skills, Claude Project instruction files, Claude Code tasks, research briefs, plans, or reusable workflows. Triggers on "build me a prompt", "write a prompt for", "prompt for a skill", "prompt for a project", "Claude Code prompt", "research prompt", "turn this into a prompt", "generate a prompt", or when the user pastes a challenge and asks for something they can paste into an AI. Also use for refining a prompt produced this way.
---

# Challenge to Prompt

Turn a person's raw description of a challenge into a prompt that gets expert-level work out of an AI. The person should not need any prompt-writing skill: they describe what is going on, and they get back a diagnosis plus a prompt they can paste somewhere else.

The method has three moves, always in this order:

1. **Pain**: what this feels like day to day. This proves the situation was understood and gives the eventual prompt real texture.
2. **Problem**: why they are stuck. The root cause, named precisely, becomes the prompt's target.
3. **Prompt**: a ready-to-paste prompt aimed at that root cause.

The diagnosis matters because a prompt built on the surface request ("write me titles") gets generic output, while a prompt built on the root cause ("there is no permanent record of my voice, so every session starts from zero") gets a solution.

## Choosing a mode

- **Generate (default).** The user gives a challenge. Produce the full result immediately, even if the challenge is one vague line. Do not interrogate first; put unknowns in bracketed placeholders and offer refinement afterwards.
- **Refine.** After a Generate result, the user answers the refinement questions (or volunteers more detail). Rewrite the whole result using their answers.
- **Chat.** The user says they want to talk it through, or asks to be interviewed first. Ask questions one at a time, then deliver the prompt.

This skill runs in a chat window. Ask every question as ordinary chat text. Never depend on special tools, buttons, or forms.

## Generate mode: the output

Produce these parts, in this order, under exactly these headings: YOUR PAIN, YOUR PROBLEM, YOUR PROMPT, EXPECTED RESULT, and WANT IT SHARPER? (the refinement questions).

### YOUR PAIN

Exactly five bullets, written to the user as "You...".

- Each bullet is one concrete moment or consequence, not an abstraction. "You paste in a transcript, get something fine, tweak it by hand anyway, and wonder why you bothered" works. "You experience inconsistency" does not.
- Use every number and specific the user gave (hours, counts, names, tools).
- Extend plausibly beyond what they said: the knock-on costs, the thing they have probably already tried, the opportunity sitting unused. Keep extensions believable for anyone in their situation. If the user gave almost nothing, describe the pain typical of that situation.
- Cover different angles across the five: time lost, quality or inconsistency, the emotional cost, what generic advice gets wrong, what is being left on the table.

### YOUR PROBLEM

Two sentences, no more.

- Sentence one names the root cause as a missing system, a knowledge gap, or a broken process, and links it to the consequence. Useful shapes: "You don't have X, so Y keeps happening." "You have X, but you lack Y, which means Z." "X isn't a [what they assume] problem; it's a [what it really is] problem."
- Sentence two names what they need instead, as a specific thing. Often: "The fix isn't [the obvious patch]; it's [the durable thing this prompt will produce]."
- If the user listed specific failures, the root cause must account for every one of them.

### YOUR PROMPT

Put the entire prompt inside one code block so it can be copied in a single action. Write it in the user's first-person voice ("I am...", "I want you to..."), because they will paste it as their own message.

Build it from four blocks. Labelling them ROLE / CONTEXT / REQUEST / QUESTION is fine and helps long prompts; short prompts can run without labels.

**1. Role.** "You are [expert], [credential], specializing in [the specialty that matters here]."

- Choose the expert before writing anything, then commit. Never change expert mid-prompt.
- Choose by the *domain of the challenge*, not the type of deliverable. A question about YouTube growth gets a YouTube strategist. A burnout question gets the researcher who defined burnout. A "build me a reusable system" request gets someone known for turning messy workflows into systems.
- Prefer a real, widely recognized authority whose actual published framework can shape the answer, and state their real credential (book, framework, body of work). Only state credentials you are confident are true.
- If their fame is in an adjacent field, bridge it: "applied here as a [functional role, e.g. senior Python automation consultant for non-technical creators]".
- If no clear authority exists, describe a specialist role in detail instead of inventing a person.
- Add one sentence giving the expert's operating principle for this job, taken from what the user cares about. Example: a user afraid of breaking working code gets "You treat existing working code as sacred and build every new feature in protected layers."

**2. Context.** Who the user is and what their situation is.

- State everything they told you as plain fact.
- Include their admitted limits in their own terms ("I am not technical. I don't know what a good skill file should contain."). These change how the AI should explain things.
- For each detail the AI will need that they did not give, add a bracketed placeholder in capitals with an example: `[CHANNEL NICHE, e.g., "personal finance for millennials"]`. For a choice, list the options: `[MAC / WINDOWS / LINUX]`.
- Scale placeholders to what is missing: a few for a detailed challenge, as many as eight for a one-line challenge or a technical task where the environment is unknown. Include only details that would change the answer. Never ask for something they already told you.
- If the user has not said whether they are living the problem or studying it, do not assume. Write the pain and context so they hold either way, and ask.
- Always worth capturing if unknown: what they have already tried, and any reference examples of work they consider good.

**3. Request.** What to produce, in enough detail that the result cannot come back generic.

- Open with the deliverable and where it will be used: "Build me a complete, copy-paste ready [thing] that I can [paste into / upload to / run in] [exact destination]", followed by the outcome it must achieve.
- List four to seven named components, each as "Name: what it contains and what it must accomplish". Each component should be something a real expert would insist on. Where the chosen expert has a known framework, structure the components around it.
- Turn the user's words into rules:
  - Every complaint becomes a rule that prevents it. "Ideas come out generic" becomes "every idea must be traceable to specific evidence, quoted". "It repeats topics I've covered" becomes "cross-reference my existing catalog before suggesting anything".
  - Every fear becomes a non-negotiable safety rule. "I'm scared it will break what works" becomes "never modify existing functions, only add; give me a backup step before any change; include a dry-run mode".
  - Every stated limit becomes a format requirement. "I'm not a programmer" becomes "explain every change in plain English before showing code" and "give me a test checklist a non-programmer can follow".
  - Every constraint (time, budget, working alone) becomes a boundary on the solution.
- Specify the output precisely: exact counts ("3 title options, ranked"), the layout, and for recurring outputs a literal template to repeat.
- Tell the AI to use examples from the user's real subject matter, not generic filler.
- Say what to do at the edges: thin evidence, missing information, a case that doesn't fit the usual pattern.
- Check that every deliverable the user asked for appears. If they asked for two things, the request covers both.

**4. Closing question.** End Generate-mode prompts with: "Before proceeding, please ask me any clarifying questions to ensure [the deliverable] is tailored to my specific situation." This lets the receiving AI fill gaps the placeholders missed.

### EXPECTED RESULT

After the code block, one sentence describing what they will have and what changes because of it, with a concrete time or contrast. Example shape: "A [deliverable] you set up once this week, so every [recurring event] takes [short time] instead of [current pain]."

Use the user's own numbers for the time or contrast when they gave any; otherwise use a modest, believable one.

### WANT IT SHARPER?

Finish by offering the refinement questions (below) in the same message, so the user can answer them or simply use the prompt as is. The questions are the one part outside the code block that is allowed to run long.

## Shaping the request by type of deliverable

Use these as starting skeletons. Combine or adapt when a challenge spans types.

**A Claude skill or reusable instruction file.** Components usually include: role definition; the rules or style guide, with "do this / not that" pairs; the repeatable formula or template; exactly what the user pastes in each time; exactly what comes back; a block for real examples of their past work; and notes on keeping it current. If the user is non-technical, ask for a walkthrough of what each section is for before the assembled file. State the destination (a skill file to upload, in Markdown).

**Claude Project instructions.** Components usually include: identity and purpose block; audience profile written as a person, not a demographic; voice and standards guide with examples; the default format or template; named working modes the user can switch between on command (for example brainstorm, outline, draft, punch-up, critique); a quality checklist of non-negotiables; a short start-of-chat routine; and the list of files to upload as project knowledge with what each is for. State that it must be ready to paste into the Project Instructions field.

**A Claude Code or technical change.** Claude Code can read the project's files, so make the first deliverable a read-only discovery report that corrects anything the user described wrongly, and give environment placeholders a "NOT SURE" option. Lead with what already works and must keep working. Add a "safety rules (non-negotiable)" list: back up first, add rather than modify, isolate new code, dry-run before real effects, keep secrets out of the code. Then deliverables: a plain-English plan before any code, a rollback plan, each new capability named separately, a test checklist matched to the user's skill level, and setup steps for their operating system. Use option placeholders for environment facts.

**Research.** Open with "Produce a research report that..." instead of the build-me opener. State what is being investigated and that surface-level answers are not wanted. List four to six named dimensions of analysis, each with one to three pointed questions; these dimensions are the components. Then rules that apply to all dimensions: give specific real-world examples, contrast what succeeds with what fails (a pattern only counts if the successes do it and the failures don't), label each claim as established, likely, or speculative, never invent statistics, and say plainly what could not be verified and what data the user should bring. Finish with an output format that ends in the single highest-leverage finding to act on first. Ask in the refinement questions whether the prompt will be run with web search or Research turned on, since that decides whether the AI looks things up or works from what the user supplies.

**A personal or professional plan.** Structure by time: diagnose first, then what to do this week, then a 30-day or similar protocol, then root-cause fixes, then an early-warning system so the problem doesn't return. Ask for specific wording the user can use in difficult conversations. Capture their constraints: what they can and cannot change.

**A recurring workflow or analysis system.** Define the situation, the AI's standing job each cycle, the rules for scoring or ranking (state any formula explicitly), a literal output template to repeat, hard constraints including how to flag weak evidence and what to do when there isn't enough material, and how each session begins (what the user provides).

## Refinement questions

Offer these after a Generate result. Two groups, numbered continuously, asked as plain chat text.

**Strategic questions (three to five).** Each one must change the prompt depending on the answer. Good territory:

- The primary goal, when several are plausible ("pick the one that matters most").
- Severity or stage, which decides between stabilizing now and restructuring long term.
- What they are actually able to change (their real leverage and constraints).
- Preferred style or approach, as a "choose all that apply".
- Gold-standard examples of their own, or people whose work they want to emulate.

Give most of them three or four lettered options written as full first-person statements ("I can have some conversations with my manager but can't change much structurally"), so answering takes one letter. Where it helps, say in a clause why the answer matters. One or two can be open-ended.

**Fill in the details.** One short question per bracketed placeholder in the prompt, in plain grammatical English.

If a strategic question already covers a placeholder, do not ask it twice.

Tell the user they can skip any question.

## Refine mode: rewriting with answers

Rewrite everything, not just the placeholders.

- **Pain**: still five bullets, now sharper, using their answers (their niche, audience, tools, words).
- **Problem**: restate around the goal and constraints they chose.
- **Prompt**: keep the same expert. Replace every answered placeholder by weaving the answer into natural sentences. Remove placeholders for skipped questions, or keep one only if the prompt is unusable without it. Let strategic answers reshape the request: add or change components, tighten rules, make the output specification exact. The refined prompt is normally more detailed than the first.
- **Closing question**: change to "Before delivering, ask me any final clarifying questions that would make the output more precise."
- **Expected result**: rewrite to match.

Label the result as the final prompt.

## Chat mode

1. Open with one sentence acknowledging why the challenge matters, then say a few questions will make the prompt fit their situation.
2. Ask one question per message, normally four in total, each with example answers in the question so it is easy to respond. A reliable order:
   - Where and in what format this applies (platform, tool, length, setup).
   - Who it is for and what subject matter is involved.
   - What they want the output to look like (offer a few shapes to choose from).
   - Their biggest recurring trouble spot.
3. Begin each next message by reflecting their answer back with one useful insight, then ask the next question.
4. Stop when there is enough. If their first message already answers a question, skip it.
5. Deliver the prompt in a code block, built with the same four-block logic. Because the details are now known: weave them in rather than using placeholders (keep only an input slot such as `[PASTE SCRIPT HERE]`), hardcode their stated trouble spot as the top priority, include a checklist of what to look for, and drop the closing clarifying question.
6. Follow with "Why this prompt works": four or five bullets, each pairing a design choice with the benefit to them.

Pain and Problem sections are optional in Chat mode; include them if the user asks for the full treatment.

## Quality check before sending

- The expert is one coherent choice with a true credential, and the specialty matches the challenge's domain.
- Every specific the user gave appears in the output. Nothing they said is asked for again.
- Every complaint, fear, and limit they mentioned has become a rule or requirement.
- Every deliverable they asked for is covered.
- The prompt reads consistently in the user's voice from start to finish.
- The prompt is in a single code block and could be pasted with no edits other than filling brackets.
- Placeholders are capitalized, bracketed, and carry examples.
- The expected result is concrete, not a slogan.

## Style

Write to the user warmly and directly. The pain bullets can be vivid; the prompt itself should be precise and businesslike. Keep everything outside the code block brief so the prompt is the star.
