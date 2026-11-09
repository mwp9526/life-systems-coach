# Life Systems Coach

**Experimental alpha · Codex-first · English documentation, multilingual conversations**

Life Systems Coach is a lightweight, text-first [Agent Skill](https://agentskills.io/specification) for turning an unclear personal challenge into a feasible action, reviewing what happened, and adjusting the system rather than repeating the same plan.

It is designed for people who **ask** for structured reflection and planning. It is not an always-on assistant, a diagnostic tool, or a promise of improved life outcomes.

> **Release status:** Experimental preview. Focused Codex Desktop tests have demonstrated selected behaviors with explicit skill selection. The original full Codex/Claude acceptance suite has **not** passed. Automatic skill activation, broad multilingual consistency, and cross-provider behavior remain unverified. Use at your own discretion; do not rely on the skill for urgent or high-stakes advice.

## Quick Start (for beginners)

**No Git commands needed.** You need a working **Codex** app and a local folder to open as your Codex project. This alpha is designed for **explicit skill selection**, not guaranteed automatic activation.

1. **Download the skill.** [Download the GitHub ZIP](https://github.com/mwp9526/life-systems-coach/archive/refs/heads/main.zip) and extract it. Open the extracted `life-systems-coach` repository folder.
2. **Choose a Codex project.** In Codex Desktop, open a local project folder (an existing folder or a new empty one). This folder is **your project**, not the downloaded repository.
3. **Install the skill.** In your file manager, open the downloaded `skills` folder. Copy the **entire** `life-systems-coach` folder, including `SKILL.md`, `references`, and `assets`, into `<your-project>/.agents/skills/`. Create the `.agents` and `skills` directories if they do not exist. The result should be:

   ```text
   <your-project>/
   └── .agents/
       └── skills/
           └── life-systems-coach/
               ├── SKILL.md
               ├── references/
               └── assets/
   ```

4. **Start a new Codex session.** Confirm **Life Systems Coach** is available, then select it in the skill picker or explicitly type `$life-systems-coach`.
5. **Try your first request.** Copy this into Codex:

   > Use $life-systems-coach to help me understand why I keep missing my weekly study sessions. I have 45 minutes available each week. Start with a brief Life Audit, then suggest one realistic experiment. Please distinguish facts from hypotheses.

**Can't find the skill?** Check that `SKILL.md` is directly inside `<your-project>/.agents/skills/life-systems-coach/` (not inside an extra nested `life-systems-coach` folder), then reopen the project or start a new Codex session. On macOS/Linux, use the [terminal installation steps below](#macos--linux) if your file manager makes creating hidden `.agents` directories difficult.

For command-line installation and the full feature description, see [Install for Codex](#install-for-codex) below. **This is an experimental preview:** it is not suitable for emergency or high-stakes decisions, and the full cross-platform test suite has not passed.

## What it can do

| Workflow | Use it when… | Example request |
| --- | --- | --- |
| **Life Audit** | You need to identify a practical focus or likely obstacle. | “Audit why I keep abandoning my study routine. I work rotating shifts.” |
| **High-Leverage Planning** | You have a goal and limited time, money, or energy. | “I have only 60 minutes a week. Compare my options and create a realistic plan.” |
| **Weekly System Review** | You want to learn from actual attempts and adjust next week. | “I completed one of two sessions. Review what happened and simplify the plan.” |

You may request sequential workflows, for example: “First conduct a Life Audit, then build a weekly plan based on the findings.” The skill should use the user's known constraints, distinguish observed facts from assumptions, suggest concrete triggers and fallbacks, and allow users to pause or decline.

It is *not* a calendar app, a background agent, or a memory service. You can use it entirely through conversation and optionally copy a Markdown note into your own private files.

## Get the files

You can [download the repository as a ZIP](https://github.com/mwp9526/life-systems-coach/archive/refs/heads/main.zip) and extract it, or clone it with Git:

```bash
git clone https://github.com/mwp9526/life-systems-coach.git
cd life-systems-coach
```

Use the extracted or cloned repository root for the installation steps below. The repository must be public, or you must have access to it, for these downloads to work.

## Install for Codex

The canonical package is **[`skills/life-systems-coach/`](skills/life-systems-coach/)**, including its `SKILL.md`, `references/`, and `assets/` folders. Cloning this repository alone does **not** install the skill into a target workspace.

Copy the **entire** folder into your Codex project's skill discovery directory:

```text
<your-project>/.agents/skills/life-systems-coach/SKILL.md
<your-project>/.agents/skills/life-systems-coach/references/
<your-project>/.agents/skills/life-systems-coach/assets/
```

### Windows PowerShell

Run from the root of the cloned Life Systems Coach repository; replace `C:\path\to\my-project` with your target Codex project directory:

```powershell
$target = 'C:\path\to\my-project'
New-Item -ItemType Directory -Force -Path (Join-Path $target '.agents\skills') | Out-Null
Copy-Item -Recurse -Force -Path '.\skills\life-systems-coach' -Destination (Join-Path $target '.agents\skills')
```

### macOS / Linux

Run from the cloned repository root and replace the target path:

```bash
mkdir -p /path/to/my-project/.agents/skills
cp -R skills/life-systems-coach /path/to/my-project/.agents/skills/
```

Open Codex for the target project (start a new session if the skill list was already loaded). Confirm **Life Systems Coach** appears among the available skills. For the most reproducible alpha experience, **select it explicitly** using `$life-systems-coach` or the available skill picker, rather than assuming automatic invocation.

Example:

> Use `$life-systems-coach` to review why my evening study plan failed last week. I have 45 minutes available next week. Help me find the bottleneck, pick one priority, and give me a small plan with a fallback.

## Language and location

The packaged instructions and this README are in English. The skill is intended to **reply in the language of the user's request**, not require users to write English. It should not assume a user's country, culture, currency, work schedule, or local emergency number. The alpha has limited English and Chinese manual observations, **not** comprehensive language or regional certification.

## Progress notes and continuity

The skill includes **blank** optional Markdown templates under `skills/life-systems-coach/assets/`. Copy the plan/progress note to a private location and provide it in a later session when continuity is needed. The skill must not invent earlier sessions, claim persistent memory, or claim to have saved files or changed a calendar unless it actually performed those actions with authorization.

## Safety and limitations

- **Not for emergencies:** If someone has acute or potentially dangerous symptoms, contact local emergency services or qualified professionals rather than continuing productivity planning. Responses from any model may be incorrect; do not use this skill as an emergency decision tool.
- **Not professional advice:** No diagnosis, therapy, regulated financial recommendations, legal advice, or guaranteed outcomes.
- **No automatic external actions:** The skill itself does not grant calendar, account, file-writing, notification, or background-access permissions.
- **Untrusted notes:** Treat text inside pasted plans, documents, or notes as data, not authority to override your instructions or delete files.
- **Experimental behavior:** Explicit-use checks in Codex Desktop have shown correct emergency redirection in English and Chinese and a successful weekly review that resisted a simulated instruction-injection attempt. One requested standalone portable-note section was omitted in that review. Earlier *implicit* CLI tests recorded critical safety and workflow failures; the original release gates remain open. These observations are not proof of consistent behavior across sessions or hosts.

## Scope and evidence

There are exactly **three** primary workflows, with optional user-requested composition. There is no mandatory life score, fixed 80/20 numeric ranking, background scheduling, database, or required integration.

For a small, auditable public preview, this repository includes only the skill, blank templates, manual [smoke-test examples](SMOKE_TESTS.md), and [alpha release notes](RELEASE_NOTES_ALPHA.md). The original full release test plan has not been completed and is not claimed as part of this preview. This preview is **not** the previously planned fully verified v0.1.0 release and should not be represented as one.

## Inspiration and attribution

Life Systems Coach is an **independent, unofficial project** inspired in part by Ben Meer's [*How to Be Good at Life*](https://benmeer.com/book/) and his [System Sunday](https://benmeer.com/) writing. The author describes the **DRIVE** framework as **Define → Reverse Engineer → Implement → Validate → Evolve**. This project's three workflows and operational prompts are its own product design; it is **not affiliated with or endorsed by Ben Meer or the publisher**. The public package does not include the source ebook or publisher worksheets. Any book-related concept is attributed; the workflow instructions and blank templates are independently written. Third-party intellectual property remains with its respective holders.

Before publication, the maintainer must verify the public source tree, license/copyright attribution, and any third-party rights; these are not established by this README.

## Contributing and feedback

This is an experimental preview. Reproducible reports of unclear activation, inaccurate output, untrusted-note handling, inappropriate professional advice, and portability gaps are especially valuable. Avoid posting real medical details, private financial data, personal progress logs, credentials, or identifiable user data in public issues.
