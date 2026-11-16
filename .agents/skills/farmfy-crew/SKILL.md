---
name: farmfy-crew
description: "Use when coordinating Farmfy Crew work in a Codex session: select the right specialist, apply the repository's plan-to-verify pipeline, and keep changes scoped to the Farmfy project."
---

# Farmfy Crew

Use this skill to coordinate the Farmfy Crew workflow in Codex. The crew is a routing
and quality process, not a claim that Codex has spawned agents. Use multi-agent tools
only when the active Codex session actually provides them; otherwise perform the
stages sequentially yourself and say so.

## Before starting

1. Read the repository's `AGENTS.md` and any relevant local instructions.
2. Identify the task shape and choose one loop only:
   - Clear, multi-file task: team pipeline below.
   - Vague request: clarify scope and acceptance criteria before execution.
   - Single narrow fix: implement directly, then verify.
   - End-to-end build or explicit keep-going request: use the matching available
     workflow, without combining loops.
3. Load `using-superpowers` and the process skill required by the task before domain
   skills. Follow explicit session instructions and repository rules.

## Crew roster

Route by need. One primary specialist is enough; add a second only when the task needs
that distinct check.

| Need | Farmfy role | Codex responsibility |
| --- | --- | --- |
| Planning | Bibit (`omc-planner`) | Create an ordered plan with a check per step. |
| Clarifying requirements | Asah (`omc-analyst`) | Turn ambiguity into checkable acceptance criteria. |
| Root-cause analysis | Jejak (`omc-tracer`) | Trace behavior and compare evidence-backed hypotheses. |
| Architecture | Tata (`omc-architect`) | Resolve boundaries, invariants, and trade-offs before cross-cutting edits. |
| Implementation | Tani (`omc-executor`) | Make the smallest complete change in assigned scope. |
| UI work | Mekar (`omc-designer`) | Handle interface direction, layout, and interaction; apply UI/accessibility rules. |
| Verification | Saring (`omc-verifier`) | Run relevant checks and report evidence, including failures. |
| Code review | Sisir (`omc-code-reviewer`) | Check correctness, regression risk, and maintainability. |
| Security review | Pagar (`omc-security-reviewer`) | Review auth, secrets, network, and data changes. |
| Release | Panen (`omc-release-manager`) | Handle release/PR work only when requested. |
| Coordination | JoniBoy (`omc-lead`) | Scope, route, integrate, and gate the result. |

These are role names from the Farmfy OpenCode configuration. They do not imply that
matching Codex subagents are installed. Do not claim dispatch unless the tools confirm
it.

## Team pipeline

For clear multi-file work, move through these stages in order:

1. **Plan:** map relevant behavior; create ordered steps and checks. Add architecture
   review if boundaries or invariants are contested.
2. **Acceptance criteria:** make the outcome testable. Skip only when criteria are
   already explicit and checkable.
3. **Execute:** implement only the approved scope. Parallelize independent work only
   when real multi-agent support exists and each task has bounded files and checks.
4. **Verify:** run focused checks and the project's appropriate broader check. Add
   security review for auth, secrets, network, or data changes; code review for
   cross-cutting work.
5. **Fix:** address evidenced failures and verify again. Stop after two fix rounds and
   report any remaining blocker.
6. **Ship:** prepare a release or PR only when explicitly requested.

If this repository uses `.omc/handoffs/`, write the stage handoff there before moving
between stages. Keep local tooling artifacts out of commits unless requested.

## Guardrails

- Evidence before completion claims: name the command and observed result.
- For browser-visible behavior, verify in a browser when browser tools are available;
  otherwise state that browser verification was not performed.
- Preserve unrelated user changes. Do not stage, commit, or push unrelated files.
- Keep the diff to the smallest complete change. Do not add dependencies without a
  clear need.
- Do not invent results, people, metrics, or successful checks.
- Report verdict, acceptance criteria with evidence, changed files, and open issues.
