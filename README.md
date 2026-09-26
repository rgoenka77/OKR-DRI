# DRI — objectives, owned

**DRI** is a task-delegation and alignment tool for growing companies, built around a single idea from a conversation with early-stage VC and former founder Jay Zaveri: most teams don't fall apart from a lack of task-tracking software — they fall apart because, as headcount grows, nobody besides the founder is carrying the *why* behind the work, and that context gets dropped every time a task changes hands.

Every mainstream tool (Asana, Linear, Monday, Lattice, Ally.io) tracks whether work got **done**. DRI is built to also track whether the person doing it actually **understood why**, and to make sure that understanding survives when ownership changes hands.

## What makes it different

Existing OKR / task tools all converge on the same shape: an objective, some key results, a list of tasks, a status color. DRI keeps that shape but adds four mechanics that don't exist elsewhere, all in service of one thesis — **alignment, not just tracking**:

1. **Required "why it matters."** You cannot add a task without stating why it matters. This is a hard constraint, not a nice-to-have field, because "can everyone explain why we're doing this" was the single hardest problem described in the founder interview this product is based on.
2. **Alignment Pulse.** Each task owner can mark their own task "Clear ✓" or "Fuzzy ?" — a signal of *understanding*, separate from progress. A task can be on-time and still be marked fuzzy, surfacing confusion before it becomes a missed deadline.
3. **Handoff log.** Click any owner's name to reassign a task. If it already had an owner, you're prompted for a short handoff note (what's done, what's left, blockers) before the reassignment completes. Nothing changes hands silently — every reassignment is logged and visible on the objective.
4. **Workload view.** A dedicated tab shows every owner's open and stalled task count across *every* objective and company at once — the cross-team view a single objective page never gives you, so overload gets caught before someone burns out or drops the ball.

It also includes a **Portfolio view** (roll up ownership health across multiple companies — useful for an investor or a multi-team lead) and an **AI-assisted breakdown** button that proposes new key results and delegable tasks for an objective (only available when running inside Claude, see below).

## How to use it

### Option 1 — just open it
`index.html` is a single, fully self-contained file. Download the repo and double-click `index.html`, or open it directly in any modern browser. No build step, no server, no dependencies to install.

### Option 2 — run it locally with a server (recommended for Google Fonts to load reliably)
```bash
git clone <this-repo-url>
cd <this-repo>
python3 -m http.server 8000
# then open http://localhost:8000 in your browser
```

### Option 3 — GitHub Pages
Enable GitHub Pages on this repo (Settings → Pages → Deploy from branch → `main` → `/root`) and it will be live at `https://<your-username>.github.io/<repo-name>/` with no further setup.

## Using the app

1. **Add an objective** in the left sidebar — give it a name and optionally a company (useful if you're tracking more than one team or portfolio company).
2. **Add key results** under that objective.
3. **Add tasks** under each key result. You must fill in a task name, an owner (the DRI), and *why the task matters* — the app won't let you skip the why.
4. **Track ownership, not just completion:**
   - Check a task off when it's done.
   - Owners mark their own tasks "Clear" or "Fuzzy" to signal whether they actually understand what's expected.
   - Click an owner's name badge to reassign a task — you'll be prompted for a handoff note if it already had an owner.
5. Switch to the **Portfolio** tab to see ownership health rolled up by company.
6. Switch to the **Workload** tab to see every owner's total open/stalled load across everything they own.
7. On any objective, click **"Suggest key results & tasks"** to have Claude propose a breakdown — only available when this page is opened inside a Claude.ai artifact (it calls Claude's built-in `sample` capability; it has no effect and stays hidden in a plain browser).

## Data & privacy

This is a client-only MVP: all data is stored in your browser's `localStorage` (key `dri_state_v1`). Nothing is sent to a server, nothing is shared between browsers or devices, and closing/reopening the tab preserves your data as long as you don't clear site data. This is intentional for the MVP stage — a real multi-user version would move this to a shared backend.

## Tech stack

Plain HTML, CSS and vanilla JavaScript — no framework, no build tooling, no dependencies beyond two Google Fonts (Source Serif 4, Inter) loaded via CDN. This keeps the MVP a single file that's trivial to read, fork, and deploy anywhere.

## Background

This product was designed from a career-journey interview with Jay Zaveri (entrepreneur turned venture capitalist), in which he identified team alignment — communicating what's being built, why, and who owns each piece — as the hardest recurring problem in scaling an early-stage company, and named the OKR + "Directly Responsible Individual" (DRI) framework (used at Google and, per Jay, Apple) as his own playbook for solving it. DRI turns that playbook into software with a specific, defensible point of view: ownership without context is just busywork, and this tool refuses to let that happen silently.
