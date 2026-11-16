# Contributing to ViDo

Thank you for your interest in contributing to ViDo!

ViDo is a collaborative task-management workspace built for focused individuals and transparent teams—designed around the core belief that work is more useful when its progress and history are visible, rather than reduced to a binary checkbox.

ViDo is also built as a transparent, four-phase case study in AI-assisted software engineering. Every contribution helps shape both a dependable product and an educational resource for the developer community.

---

## Current Project Stage

ViDo is currently in the **planning and pre-implementation stage**. The project specifications, core philosophy, and developmental roadmap are outlined in [README.md](./README.md), [Idea.md](./Idea.md), and [tasks.md](./tasks.md).

Application scaffolding and foundational implementation will begin with **Milestone 1**. Because application code and tooling configurations have not yet been committed to the repository, detailed instructions for local environment setup, package management, and running automated tests will be added once those choices are established by the project.

---

## The Four Development Milestones

All contributions should align with the four planned milestones of the ViDo roadmap:

1. **Milestone 1 — Minimal Task Management Core**
   * A focused personal task workspace without authentication.
   * Precise target dates and times for deadlines.
   * Incremental progress tracking from `0%` to `100%`.
   * Timestamped progress checkpoints, comments, blockers, and retained history.
   * Derived views for **Pending**, **Overdue**, and **Completed** tasks.
2. **Milestone 2 — Authentication and Multi-User Support**
   * Email and password authentication with persistent profiles and secure sessions.
   * Relational database integration.
   * Strict user-level data isolation enforced via database access control.
3. **Milestone 3 — Shared Tasks and Team Collaboration**
   * Separation of private `My Tasks` and collaborative `Team Tasks`.
   * Team workspaces, member invitations, and explicit task ownership.
   * Threaded updates, author-attributed checkpoints, and real-time synchronization.
4. **Milestone 4 — Embedded AI Agent and Recommendations (Flagship Milestone)**
   * Context-aware task generation from schedules, goals, and recent history.
   * Follow-up task suggestions, deadline risk detection, and priority recommendations.
   * Explainable assistance with mandatory user approval before altering data.

---

## Welcome Contributions

At this stage of the project, we warmly welcome:

* **Documentation:** Improving clarity, fixing typos, expanding architectural guides, and keeping project documentation in sync with roadmap decisions.
* **Planning & Architecture Discussions:** Refining data models, identifying edge cases in task lifecycles, and reviewing roadmap tasks.
* **Feature Suggestions:** Constructive proposals that align with ViDo's core philosophy (simplicity, transparency, and progress tracking).
* **Code Contributions:** Implementing tasks outlined in [tasks.md](./tasks.md) according to the active milestone priorities once foundational scaffolding is in place.
* **Bug Reports:** As soon as runnable code is introduced, clear reports detailing unexpected behavior and reproducible steps.

---

## Core Architectural Principles

All code and design contributions must adhere to ViDo's established principles:

### 1. Privacy by Default
* Personal tasks belong strictly to their owner and must remain completely isolated from other users.
* Team tasks are strictly scoped to verified workspace members.
* Authorization and access control must be enforced at the database/backend layer (such as PostgreSQL Row-Level Security). Client-side filtering is never treated as a security boundary.

### 2. Derived Task Status
* Task status categories—**Pending**, **Overdue**, and **Completed** (including whether completion occurred after the deadline)—must be computed dynamically from the target deadline and completion timestamp.
* They should not be stored or manually toggled as disconnected, arbitrary status flags.

### 3. Explainable AI and User Approval
* The AI recommendation agent is designed to assist user decision-making, not replace user control.
* Recommendations must be explainable and require explicit user approval before modifying tasks, assignments, or schedules.
* The agent must never perform silent changes to user or team data.

---

## Learning Deliverables

Because ViDo serves as a case study in AI-assisted development, overall project milestones are accompanied by learning assets alongside code:

* **Code Snapshots:** Preserving working code states at major milestone boundaries.
* **Prompt Records:** Documenting significant AI prompts and development techniques used during creation.
* **Demonstrations:** Producing concise video walkthroughs showing completed milestone features in action.
* **Technical Articles:** Publishing standalone written explanations of the architecture, key decisions, and challenges solved.

> **Note for Contributors:** You do **not** need to record videos or write technical articles for individual pull requests! Routine pull requests (such as bug fixes, documentation updates, or specific task implementations) only require clear PR descriptions. Learning deliverables are synthesized at the milestone level, and contributors interested in collaborating on prompts, demonstrations, or educational write-ups are always welcome to help.

---

## Contribution Workflow

ViDo uses a standard GitHub fork-and-pull-request workflow.

### 1. Fork the Repository
Navigate to the upstream ViDo repository on GitHub at https://github.com/vicharanashala/ViDo and click **Fork** to create a copy under your GitHub account.

### 2. Clone Your Fork
Clone your newly created fork to your local development machine:

```bash
git clone https://github.com/<your-username>/ViDo.git
cd ViDo
```

### 3. Verify or Set Up the Upstream Remote
Check your currently configured remotes:

```bash
git remote -v
```

* If `upstream` is already listed and points to https://github.com/vicharanashala/ViDo.git, you are all set and do not need to add it again.
* If `upstream` is not listed, configure it using:

```bash
git remote add upstream https://github.com/vicharanashala/ViDo.git
```

Verify your configuration once more:

```bash
git remote -v
```

### 4. Synchronize Local `main` with Upstream
Ensure your working tree is clean before switching branches and synchronizing with upstream. If you have uncommitted changes, commit or stash them first.

Once your working tree is clean, update your local `main` branch with the latest changes from upstream:

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

### 5. Create a Dedicated Topic Branch
Always make your changes on a separate branch created from the updated `main`. Use clear, descriptive prefixes for your branch names:

* `docs/` — for documentation additions or corrections (e.g., `docs/add-contribution-guidelines`)
* `feature/` — for new features aligned with the roadmap (e.g., `feature/task-checkpoints`)
* `fix/` — for bug fixes (e.g., `fix/deadline-calculation`)

Create and switch to your topic branch:

```bash
git checkout -b <branch-name>
```

Example:

```bash
git checkout -b docs/add-contribution-guidelines
```

### 6. Make Focused Changes and Commit
* Keep commits focused on a single responsibility.
* Write clear, informative commit messages explaining what was changed and why.

### 7. Keep Your Branch Up to Date
If changes have landed in `upstream/main` while you were working, fetch and rebase your topic branch:

```bash
git fetch upstream
git rebase upstream/main
```

### 8. Push to Your Fork
Push your topic branch to your GitHub fork:

```bash
git push -u origin <branch-name>
```

### 9. Open a Pull Request
Go to the upstream repository at https://github.com/vicharanashala/ViDo on GitHub. You will see a banner prompting you to open a pull request from your recently pushed branch against the `main` branch.

---

## Pull Request Expectations

When submitting a pull request, please ensure:

- [ ] **Descriptive Summary:** Clearly explain what changes were made, the rationale behind them, and any alternatives considered.
- [ ] **Roadmap / Issue Reference:** Link to the corresponding item in [tasks.md](./tasks.md) or related issue numbers where applicable.
- [ ] **Focused Scope:** Keep the PR focused on a single objective. Avoid mixing unrelated refactorings or documentation edits into one PR.
- [ ] **Evidence / Verification:** Include screenshots, terminal output, or demonstration notes illustrating the change when applicable.
- [ ] **Respect Pre-Implementation Status:** Avoid adding code that assumes unapproved dependencies or conflicts with current milestone priorities.

---

## Development Setup & Testing

Detailed development setup, local execution, and testing procedures will be documented in this section once the project's tooling, dependency management, and automated test runners are established during Milestone 1.

---

Thank you for helping build ViDo!
