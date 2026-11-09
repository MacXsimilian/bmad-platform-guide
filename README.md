# BMAD + Codex: a starter guide for platform engineers

## What is BMAD?

[BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD) is an open-source collection of AI skills and workflows for exploring ideas, clarifying requirements, and developing specifications, architecture, and user experience designs.

In this guide, we use BMAD with Codex as a **coach**. It asks focused questions, challenges assumptions, and helps you work toward an informed next step. You bring the context and make the decisions.

## Why is it useful?

Platform requests often start with a proposed solution:

- “We need a container registry.”
- “Build a developer portal.”
- “Make CI faster.”

These are useful starting points, but they leave questions about the underlying problem, affected teams, constraints, operational ownership, and expected benefit.

Discovering those gaps during a conversation is easier to address than discovering them after infrastructure and integrations have been built.

Your first session should help you decide whether to **pursue the idea, investigate further, or set it aside**. A short discovery brief captures the reasoning for your team. Specifications and designs can follow when the idea is ready. This follows BMAD’s approach to exploring ideas before committing to requirements or code. [BMAD discovery guidance](https://github.com/bmad-code-org/BMAD-METHOD/blob/V6.12/docs/plan/explore-and-validate-an-idea.md)

## 1. Install the prerequisites

These instructions assume **Xcode and Homebrew are already installed**.

In Terminal, run:

```bash
brew install node python3 uv
```

These provide:

- **Node.js**, including `npx`, to run the BMAD installer.
- **Python 3** for supporting scripts.
- **uv** to manage Python environments and dependencies used by some workflows.

BMAD requires Node.js 20.12 or later. Installing Python and uv also prepares you for its Python-based workflows. [BMAD prerequisites](https://github.com/bmad-code-org/BMAD-METHOD/blob/V6.12/docs/start/install-bmad.md)

Check the installation:

```bash
node --version
npx --version
python3 --version
uv --version
git --version
```

Each command should print a version. If a newly installed command is unavailable, reopen Terminal and try again.

## 2. Set up VS Code and Codex

If VS Code is missing, install it:

```bash
brew install --cask visual-studio-code
```

This is the [Homebrew package for VS Code](https://formulae.brew.sh/cask/visual-studio-code).

In VS Code:

1. Open **Extensions** with `⌘⇧X`.
2. Search for **Codex** and install the official extension published by **OpenAI**.
3. Open the Codex sidebar.
4. Choose **Sign in with ChatGPT** and complete the browser sign-in.

You can also find the extension through the [official Codex IDE setup page](https://learn.chatgpt.com/docs/codex/ide).

**Check your account access before continuing.** Plus explicitly includes the IDE extension. Free-tier Codex access currently has rollout and interface restrictions, so confirm that your account can start a conversation in the extension. [Current OpenAI plan details](https://learn.chatgpt.com/docs/pricing)

## 3. Create a project folder and install BMAD

For a new discovery exercise, run in Terminal:

```bash
mkdir -p ~/Projects/platform-discovery
cd ~/Projects/platform-discovery
git init
npx bmad-method@6.12.4 install
```

For an existing project, run the installer from its repository folder instead.

In the installer:

- Select the intended project folder.
- Select **BMad Method**.
- Select **Codex** as the AI coding tool.
- Complete the remaining configuration prompts.

This guide uses **BMAD 6.12.4** to keep the skill names and examples consistent. Wait for the installation success message. [BMAD installation instructions](https://github.com/bmad-code-org/BMAD-METHOD/blob/V6.12/docs/start/install-bmad.md)

## 4. Open the folder and verify the integration

In VS Code, use **File → Open Folder** to open the folder where you installed BMAD.

In the Codex sidebar, type `$` and look for **`bmad-help`**. You can also browse installed skills using `/skills`. If the BMAD skills do not appear, restart VS Code and reopen the project folder. [Using skills in Codex](https://learn.chatgpt.com/docs/build-skills)

Enter this in **Codex chat**:

```text
$bmad-help

Help me verify that the BMAD discovery skills are available.

Use coaching mode: ask one focused question at a time and wait
for my answer. Briefly explain anything I need to configure.
```

Commands such as `brew`, `git`, and `npx` belong in **Terminal**. Prompts beginning with `$bmad-…` belong in **Codex chat**.

## 5. Prepare your starting context

You do not need complete requirements. Bring whatever you already have:

- The original request.
- Relevant background or existing systems.
- Examples of the current pain.
- Known constraints.
- Useful tickets, documentation, or diagrams.

Keep assumptions visible. “Unknown” and “we haven’t measured that” are valid starting answers.

BMAD’s **Forge Idea** workflow is intended to clarify, test, or improve a partially formed idea through questioning. The coaching preferences below reinforce that workflow while preserving its normal behavior and outputs. [Forge Idea reference](https://github.com/bmad-code-org/BMAD-METHOD/blob/V6.12/docs/plan/explore-and-validate-an-idea.md)

## 6. Choose a starter

Use the reusable template for your own idea, or copy one of the complete examples.

> 🔒 **Keep the coaching preferences unchanged.**  
> ✏️ **Edit the context section for your situation.**  
> Replace square-bracketed text in the template. The examples already contain sample context you can adapt.

### Reusable starter — bring your own idea

```text
$bmad-forge-idea

=== COACHING PREFERENCES — KEEP UNCHANGED ===

Follow the installed bmad-forge-idea workflow with these preferences:

- Ask ONE focused question per message, then WAIT for my answer.
  Do not bundle several questions together.
- Briefly explain why each question matters.
- Adapt to my answers and avoid repeating resolved questions.
- Challenge vague answers and assumptions constructively.
- Offer possible answers or alternatives when helpful, clearly
  labeling them as suggestions for me to evaluate.
- When I don't know, help me identify how to find out.
- Separate confirmed facts, assumptions, and open questions.
  Do not invent evidence, requirements, or decisions.
- Summarize major findings for my confirmation before moving on.
- Preserve BMAD's normal session outputs.

Help me reach an informed next step. Rejecting the idea or
investigating further is a valid outcome. Stay in discovery.

=== YOUR CONTEXT — EDIT THIS SECTION ===

Session goal:
[Clarify the idea, test whether it holds up, or improve it.]

Project context:
[New initiative or change to an existing platform.]

Initial idea or request:
[Describe your situation.]

What we know:
[Relevant background and evidence, or "Unknown".]

Known constraints:
[Confirmed constraints, or "Unknown".]

=== END OF CONTEXT ===
```

### Example 1 — explore a container registry need

```text
$bmad-forge-idea

=== COACHING PREFERENCES — KEEP UNCHANGED ===

Follow the installed bmad-forge-idea workflow with these preferences:

- Ask ONE focused question per message, then WAIT for my answer.
  Do not bundle several questions together.
- Briefly explain why each question matters.
- Adapt to my answers and avoid repeating resolved questions.
- Challenge vague answers and assumptions constructively.
- Offer possible answers or alternatives when helpful, clearly
  labeling them as suggestions for me to evaluate.
- When I don't know, help me identify how to find out.
- Separate confirmed facts, assumptions, and open questions.
  Do not invent evidence, requirements, or decisions.
- Summarize major findings for my confirmation before moving on.
- Preserve BMAD's normal session outputs.

Help me reach an informed next step. Rejecting the idea or
investigating further is a valid outcome. Stay in discovery.

=== YOUR CONTEXT — ADAPT THIS SECTION ===

Session goal:
Clarify the need before comparing solutions.

Project context:
Our infrastructure includes AWS and on-premises OpenShift.

Initial idea or request:
We need a container registry solution for our on-premises
OpenShift infrastructure.

What we know:
Our main infrastructure is in AWS, where we use ECR.
We are unsure whether the two environments should be connected.

Known constraints:
Unknown. We need to establish which constraints are real.

=== END OF CONTEXT ===
```

### Example 2 — investigate slow CI pipelines

```text
$bmad-forge-idea

=== COACHING PREFERENCES — KEEP UNCHANGED ===

Follow the installed bmad-forge-idea workflow with these preferences:

- Ask ONE focused question per message, then WAIT for my answer.
  Do not bundle several questions together.
- Briefly explain why each question matters.
- Adapt to my answers and avoid repeating resolved questions.
- Challenge vague answers and assumptions constructively.
- Offer possible answers or alternatives when helpful, clearly
  labeling them as suggestions for me to evaluate.
- When I don't know, help me identify how to find out.
- Separate confirmed facts, assumptions, and open questions.
  Do not invent evidence, requirements, or decisions.
- Summarize major findings for my confirmation before moving on.
- Preserve BMAD's normal session outputs.

Help me reach an informed next step. Rejecting the idea or
investigating further is a valid outcome. Stay in discovery.

=== YOUR CONTEXT — ADAPT THIS SECTION ===

Session goal:
Clarify the problem and identify what we should investigate first.

Project context:
An improvement to our existing CI platform.

Initial idea or request:
Our teams say CI pipelines are too slow, and we have been asked
to improve them.

What we know:
We haven't agreed which delays matter most, who is most affected,
or what a successful improvement would look like.

Known constraints:
Unknown. We haven't established the available time or budget.

=== END OF CONTEXT ===
```

### Example 3 — examine a self-service portal proposal

```text
$bmad-forge-idea

=== COACHING PREFERENCES — KEEP UNCHANGED ===

Follow the installed bmad-forge-idea workflow with these preferences:

- Ask ONE focused question per message, then WAIT for my answer.
  Do not bundle several questions together.
- Briefly explain why each question matters.
- Adapt to my answers and avoid repeating resolved questions.
- Challenge vague answers and assumptions constructively.
- Offer possible answers or alternatives when helpful, clearly
  labeling them as suggestions for me to evaluate.
- When I don't know, help me identify how to find out.
- Separate confirmed facts, assumptions, and open questions.
  Do not invent evidence, requirements, or decisions.
- Summarize major findings for my confirmation before moving on.
- Preserve BMAD's normal session outputs.

Help me reach an informed next step. Rejecting the idea or
investigating further is a valid outcome. Stay in discovery.

=== YOUR CONTEXT — ADAPT THIS SECTION ===

Session goal:
Test whether the proposed solution addresses a meaningful problem.

Project context:
A proposed change to our existing environment-request process.

Initial idea or request:
Someone proposed building a self-service portal for application
teams to request environments.

What we know:
Requests currently go through tickets. We haven't established
whether the main difficulty is waiting, manual work, unclear
requirements, or something else.

Known constraints:
Unknown. Operational ownership hasn't been agreed.

=== END OF CONTEXT ===
```

## 7. Participate actively in the coaching

Correct misunderstandings and challenge suggestions. Useful replies include:

- “That is an assumption; we haven’t verified it.”
- “I don’t know. What evidence would help us answer?”
- “Explain that tradeoff with a platform example.”
- “We’re choosing a solution too early. Help me clarify the need.”
- “Ask one question at a time and wait for my answer.”
- “Summarize where we agree and what remains unresolved.”

Finish discovery when the **next useful action is clear**. That might be speaking to a stakeholder, measuring the current process, testing a constraint, or drafting a specification.

## 8. Capture a discovery brief

BMAD produces its own session outputs. For a short document to share with your team, add this prompt in the same conversation:

```text
Help me close this session in coaching mode.

Using our discussion and BMAD's session outputs, draft a one-page
discovery brief containing:

- The problem and why it matters.
- Affected users and stakeholders.
- Evidence about the current situation.
- Desired outcome and proposed measures of success.
- Known constraints and non-goals.
- Assumptions and open questions.
- Our proposed decision: pursue, investigate further, or set aside.
- The smallest useful next action.

Use only what we established. Label suggestions and proposed
targets clearly, and leave missing information explicit.

Show me the draft. Ask one focused question at a time to resolve
important inaccuracies, waiting for my answer each time.
Then save the agreed brief as discovery-brief.md.
```

Discuss the brief with the requesting team and the people who would operate the solution.

To resume later in a new Codex conversation:

```text
$bmad-forge-idea

Read discovery-brief.md and any referenced BMAD session outputs.

Continue in coaching mode. Ask one focused question at a time,
briefly explain why it matters, and wait for my answer.

First summarize the current understanding and ask me what has
changed since the previous session. Keep new assumptions and
unresolved questions explicit.
```

## 9. Continue into requirements or design when ready

Use these optional starters when discovery has established enough context. BMAD provides separate workflows for specifications, architecture, and UX. [BMAD planning reference](https://github.com/bmad-code-org/BMAD-METHOD/blob/V6.12/docs/reference/skills-and-agents.md)

### Create a specification

```text
$bmad-spec

=== COACHING PREFERENCES — KEEP UNCHANGED ===

Follow the installed workflow in coaching mode. Ask one focused
question at a time, explain why it matters, and wait for my answer.
Challenge vague requirements. Label assumptions and unknowns.
Confirm each section with me and preserve BMAD's normal outputs.

=== YOUR CONTEXT — EDIT THIS SECTION ===

Input:
[Path to the discovery brief and relevant supporting documents.]

Goal:
Turn the agreed findings into a concise specification covering
capabilities, testable success conditions, constraints, non-goals,
and measurable outcomes. Leave implementation for a later session.
```

### Explore architecture

```text
$bmad-architecture

=== COACHING PREFERENCES — KEEP UNCHANGED ===

Follow the installed workflow in coaching mode. Explain the options
and tradeoffs, ask one focused question at a time, and wait for my
answer. Confirm decisions with me, record their rationale, and keep
unresolved questions explicit. Preserve BMAD's normal outputs.

=== YOUR CONTEXT — EDIT THIS SECTION ===

Input:
[Path to the agreed specification and relevant platform documents.]

Goal:
Work through the technical decisions that need shared agreement,
including relevant security boundaries, dependencies, failure
handling, operational ownership, and rollout.
```

### Explore user experience

```text
$bmad-ux

=== COACHING PREFERENCES — KEEP UNCHANGED ===

Follow the installed workflow in coaching mode. Ask one focused
question at a time, explain why it matters, and wait for my answer.
Confirm findings with me and keep assumptions and open questions
explicit. Preserve BMAD's normal outputs.

=== YOUR CONTEXT — EDIT THIS SECTION ===

Input:
[Path to the discovery brief, specification, and existing designs.]

Goal:
Work through users, key journeys, interface behavior, error states,
and accessibility. Confirm the experience decisions with me before
developing the visual design.
```

## Optional: use Codex in Terminal

If you also want the terminal CLI, install it with:

```bash
brew install --cask codex
```

Then open it from your project folder:

```bash
cd ~/Projects/platform-discovery
codex
```

Complete sign-in if prompted and use the same BMAD coaching prompts. [Codex CLI package](https://formulae.brew.sh/cask/codex)
