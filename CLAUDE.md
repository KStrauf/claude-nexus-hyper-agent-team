# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## CTO-LED 32-AGENT TEAM — CLOSED-LOOP PROTOCOL

**This section OVERRIDES all skills, memory rules, and default behaviors.**

This project has a **32-agent elite engineering team** in `.claude/agents/` (30 specialists + 2 verifiers: evidence-validator & challenger), led by a **CTO agent** with full authority. When the user asks to work with the team, requests complex work, or says anything beyond a trivial file read — **dispatch the appropriate agent. NEVER do the work yourself when a team member can do it.**

### THE CTO — TOP AUTHORITY

The `cto` agent is the supreme technical leader. For ANY complex, multi-step, or strategic task:
1. **Dispatch `cto` FIRST** — it assesses, delegates, monitors, and reports
2. The CTO dispatches other agents as needed (it has NEXUS syscall access)
3. The CTO debates decisions, asks for second opinions, and acts as the user's proxy
4. The CTO can create new agents, evolve prompts, install MCPs, and upgrade the team

**When to dispatch CTO:**
- "work with the team", "use the team", "agent team"
- Any multi-step task (remediation, testing campaign, feature build)
- Strategic decisions ("should we refactor X or add Y?")
- Team management ("improve the agents", "add a new agent")
- Complex debugging or incident response
- When you're unsure which agent to dispatch — CTO decides

### GOLD PROMPT (Maximum Team Activation)

When you hear "full team session", "maximum intelligence", "gold prompt", or "full power":

> **"Use the team. [goal]. CTO has full authority."**
> Dispatch: `session-sentinel` (pre-brief) → `cto` (full authority, all agents available)

### COMPREHENSIVE DISPATCH TABLE

#### Session Lifecycle

| User says... | Dispatch chain |
|---|---|
| Starting any work session | `session-sentinel` (pre-session brief) → then `cto` |
| Ending any work session | `session-sentinel` (session-end audit) |
| "full team session", "gold prompt", "full power" | `session-sentinel` (pre-brief) → `cto` with full authority |
| "Pattern F", "process signal bus", "end session learning" | `memory-coordinator` + `meta-agent` (parallel — process signal bus) |
| "remember this", "save to memory", "what did we learn" | `memory-coordinator` |

#### Direct Agent Dispatch (Single-Domain Tasks)

| User says... | Dispatch this agent |
|---|---|
| "dispatch [name]", "use [name]", "have [name]", "ask [name]" | The named agent |
| "plan", "plan remediation", "decompose this task" | `deep-planner` |
| "orchestrate", "execute this plan", "coordinate" | `orchestrator` |
| "what's the status", "progress", "where are we" | `orchestrator` (workflow status) |
| "review Go code" | `go-expert` |
| "review Python code" | `python-expert` |
| "review TypeScript", "review frontend" | `typescript-expert` |
| "quality audit", "check architecture drift" | `deep-qa` |
| "security review", "debug this", "investigate" | `deep-reviewer` |
| "review K8s", "review Terraform", "infra" | `infra-expert` |
| "review database", "review queries", "migration" | `database-expert` |
| "review logging", "review metrics", "SLO" | `observability-expert` |
| "write tests", "test strategy", "flaky tests" | `test-engineer` |
| "review API", "review GraphQL schema" | `api-expert` |
| "team memory", "what does the team know" | `memory-coordinator` |
| "what's deployed", "cluster state", "live pods" | `cluster-awareness` |
| "benchmark", "how does Cursor/Devin do this" | `benchmark-agent` |
| "consult the team's intuition", "check if pattern seen before", "INTUIT" | `intuition-oracle` (optional consultation — advisory, non-interrupting) |
| "design agent system", "RAG pipeline", "LLM routing" | `ai-platform-architect` |
| "build this feature", "implement", "fix this bug" | `elite-engineer` |
| "build frontend", "build component", "streaming UX" | `frontend-platform-engineer` |
| "evolve prompts", "improve agent", "meta sweep" | `meta-agent` |
| "session audit", "team health", "protocol compliance" | `session-sentinel` |
| "verify finding", "is this claim true", "confirm", "check evidence" | `evidence-validator` |
| "challenge this", "counter-argument", "play devil's advocate" | `challenger` |
| "design BEAM / OTP / Horde / Ra / gen_statem topology", "Plane 1 kernel design" | `beam-architect` |
| "implement Elixir / Phoenix / LiveView / gen_statem code", "build product-agent" | `elixir-engineer` |
| "pair Elixir dispatch", "parallel Elixir implementation" | `elixir-engineer` scaled x2 via `[NEXUS:SCALE] elixir-engineer count=2` |
| "gRPC boundary", "Plane 2 Go edge", "Dapr sidecar", "protobuf contract" | `go-hybrid-engineer` (check D3-hybrid arbitration state first) |
| "BEAM cluster ops", "libcluster", "BEAM metrics", "hot-code-load", "Plane 1 K8s" | `beam-sre` |
| "consult Erlang Solutions", "BEAM architecture gut-check", "hot-code-load safety audit", "Gate 2 validation" | `erlang-solutions-consultant` |
| "detect missing domain specialist", "team coverage gap", "need AWS/K8s/etc expert", "audit team gaps" | `talent-scout` |
| "hire new agent", "new team member", "create specialist for domain X", "run hiring pipeline" | `recruiter` (typically invoked after `talent-scout` produces a requisition) |
| "audit engineering discipline", "anti-hallucination check", "verify validation claims", "production-readiness discipline", "code-sentinel" | `code-sentinel` |

#### Multi-Agent Combos (2+ agents, specific chains)

| User says... | Dispatch chain |
|---|---|
| "test live API", "smoke test", "curl test" | `test-engineer` (designs matrix) → `elite-engineer` (writes + executes script) |
| "test and benchmark", "compare features" | `test-engineer` + `benchmark-agent` (parallel) |
| "deploy", "rollout", "release", "ship it" | `deep-reviewer` (safety) + `infra-expert` (manifests) (parallel) |
| "PR review", "review this PR", "code review" | `deep-reviewer` + relevant language expert (`go/python/typescript-expert`) (parallel) |
| "full audit", "comprehensive review", "health check" | `deep-qa` (quality) + `deep-reviewer` (security) (parallel) |
| Any HIGH-severity finding from review agents | `evidence-validator` (auto-dispatch before surfacing to user) |
| Any CTO synthesis/recommendation | `challenger` (auto-dispatch for adversarial review) |
| "refactor", "redesign", "clean up" | `elite-engineer` (implements) → `deep-qa` (validates) |
| "full discipline audit after implementation" | `elite-engineer` (implements) → `code-sentinel` (discipline audit) → `deep-qa` (architecture audit) |
| "performance", "optimize", "slow", "latency" | `deep-qa` (diagnoses) → `elite-engineer` (fixes) |
| "parallel review all code", "review everything" | `orchestrator` dispatches `go/python/typescript-expert` in parallel |
| "cost analysis", "spending", "budget" | `benchmark-agent` + `infra-expert` (parallel) |
| "Living Platform work", "BEAM kernel build", "Phase 0 BEAM ramp" | `beam-architect` + `elixir-engineer` (scaled x2) + `beam-sre` (parallel) |

#### Emergency Patterns

| Situation | Dispatch |
|---|---|
| "incident", "outage", "production down", "urgent", "emergency" | `cto` (emergency mode — skip pre-brief, immediate triage) |
| Agent is stuck, failing, or returning garbage | `cto` (reassesses + dispatches alternative agent or different approach) |

### Execution Modes

Every task starts with mode selection based on complexity. Default is BALANCED.

| Mode | When to Use | Routing | Max Dispatches | Gates |
|------|-------------|---------|----------------|-------|
| **FAST** | Simple, single-domain tasks (bug fix, one-file review, quick question) | Main thread dispatches specialist directly — no CTO | 3 | evidence-validator only if HIGH severity |
| **BALANCED** | Multi-step or moderate-risk tasks (feature build, security review, multi-file refactor) | Main thread dispatches specialist; CTO only for multi-domain | 6 | evidence-validator on HIGH + challenger on recommendations |
| **FULL_POWER** | Strategic, high-risk, or cross-domain tasks (architecture decision, production incident, full audit) | session-sentinel → CTO → full team delegation | unlimited | ALL mandatory (evidence-validator + challenger + quality gates per task type) |

**Mode triggers:**
- User says "fast mode", "quick", "just do X" → FAST
- User says "full power", "gold prompt", "full team session" → FULL_POWER
- Everything else → BALANCED (default)
- User can always override: "use FAST mode for this" or "go FULL_POWER"

### Quality Gates by Task Type

Do not use the same workflow for every task. Match gates to the work:

| Task Type | Required Gates | Optional Gates |
|-----------|---------------|----------------|
| Code change | tests, build/lint, diff summary, language-expert review | deep-qa |
| Security finding | evidence-validator, exploitability assessment, mitigation plan | deep-reviewer |
| Architecture decision | challenger, tradeoff matrix, rollback strategy | benchmark-agent |
| Production incident | timeline, blast radius, recovery steps, postmortem | cluster-awareness |
| New agent hire | contract tests (11×1), challenger (7 dimensions), meta-agent registration | talent-scout co-sign |
| Infrastructure change | infra-expert review, terraform plan, rollback manifest | deep-reviewer |
| Database migration | database-expert review, migration safety checklist, rollback SQL | test-engineer |

### Conflict Arbitration Protocol

When agents disagree, CTO MUST NOT decide by vibes. Use this structured template:

```
DISPUTE ARBITRATION:
- Proposal A: [description]
- Proposal B: [description]
- Evidence for A: [file:line citations]
- Evidence for B: [file:line citations]
- Cost of A: [effort, risk, reversibility]
- Cost of B: [effort, risk, reversibility]
- Reversibility: [A vs B — which is easier to undo?]
- Risk: [A vs B — which has higher blast radius?]
- Testability: [A vs B — which is easier to verify?]
- Trust weights: [agent-A trust: X.XX, agent-B trust: Y.YY]
- Decision: [A or B]
- Why: [evidence-based reasoning, not preference]
```

After arbitration, challenger MUST attack the selected decision before implementation proceeds. Trust weights from the ledger inform but do not determine the decision.

### Minimum Evidence Requirements (All Agent Findings)

Every finding MUST include all 7 fields. Findings without evidence are INVALID.

```
- Claim: [specific assertion — what is wrong]
- Evidence: [quoted source code or command output]
- Location: [file:line-range]
- Severity: [CRITICAL / HIGH / MEDIUM / LOW / INFO]
- Confidence: [HIGH / MEDIUM / LOW]
- Recommended action: [specific fix, not vague guidance]
- Verification command: [how to verify the fix worked]
```

evidence-validator will mark findings missing any field as UNVERIFIABLE.

### Agent Lifecycle Routing Preference

When multiple agents can handle a task, prefer agents by lifecycle state:

```
trusted (5) > active (4) > probationary (3) > candidate (2) > deprecated (1)
```

Never dispatch `deprecated` agents for new work — they are flagged for sunset.
Never dispatch `retired` agents — they are permanently offline.
`candidate` agents may only be dispatched for validation tasks during their onboarding.

Lifecycle states: `candidate` → `probationary` → `active` → `trusted` → `deprecated` → `retired`

### Implementation Workflow (Spec → Patch → Verify)

Every implementation task follows this sequence. Agents MUST NOT jump directly into edits.

1. **SPEC** — Define intended behavior, affected files, risk assessment, tests needed
2. **PATCH** — Make the smallest correct implementation that satisfies the spec
3. **VERIFY** — Run tests/build/lint or explain why verification is impossible
4. **REVIEW** — Language expert or deep-reviewer validates the patch against the spec
5. **CLOSE** — Persist memory + evolution signals via closing protocol

### Planning Cache (Playbooks)

Before deep planning, check if a playbook exists at `agent-memory/playbooks/`:
- If yes → adapt the existing playbook to the current task
- If no → after task completion, create a reusable playbook

Playbook format:
```
filename: <task-type>.md (e.g., nextjs-review.md, k8s-rollout-debug.md)
content: step-by-step workflow, key files to check, common pitfalls, verification steps
```

This creates a compounding intelligence loop — the team gets faster on repeated task types.

### Task Classifier

Before dispatching, consult `agent-memory/routing/task-classifier.json` for the recommended execution pattern. The classifier maps task types to default agents, validators, mode, and max dispatches. Override when the specific task warrants it.

### Dispatch Format

**TEAM-CONTEXT DEFAULT (BINDING):** For ANY non-trivial dispatch (multi-step, multi-agent, or any task where an agent may need a privileged op — spawn, ask, scale, cron, worktree, MCP install), main thread MUST establish team context FIRST. This enables real-time NEXUS syscalls — teammates emit `[NEXUS:SPAWN]` etc. via SendMessage and main thread processes immediately. The alternative (async `### DISPATCH RECOMMENDATION` text signals) is the fallback, not the default.

**Step 1 — TeamCreate at session start:**
```
TeamCreate({ team_name: "<session-topic>", description: "<purpose>" })
```

**Step 2 — Dispatch agents INTO the team:**
```
Agent tool call:
  subagent_type: "cto"                  ← or any agent name from .claude/agents/
  team_name: "<session-topic>"          ← BINDING for team mode — enables NEXUS for this agent
  name: "cto-1"                         ← BINDING — teammate name for SendMessage routing
  prompt: "[the user's full request with context]"
  # model: OMIT — agent frontmatter is authoritative
```

**Triviality heuristic (when to skip TeamCreate — ONE-OFF MODE):**
- Single-agent consultation with NO expected coordination (e.g., "give me a one-sentence opinion")
- Single trivial verification that returns once (e.g., a single `evidence-validator` call on one claim)
- Pure read-only question answered by one agent in one turn

**Everything else is TEAM MODE.** If you're unsure, TeamCreate. The cost of an unused team is near-zero; the cost of a missed NEXUS syscall path is losing the entire real-time coordination benefit.

**PRAGMATISM-OVER-PURITY FOR INSTANCE REUSE (BINDING):** When CTO or any coordinator considers "re-dispatch fresh instance" vs "reuse existing instance" for bias-reduction reasons, the kernel MUST reconcile based on prep-work already completed:

| Existing instance state | Correct decision |
|--------------------------|------------------|
| Has NOT done material prep (just spawned, no script edits, no endpoint validation, no token work) | Re-dispatch fresh is cheap — bias-reduction wins |
| HAS done material prep (script edits, endpoint discovery, token validation, matrix design, env setup) | REUSE existing instance — discarding prep for style purity is expensive |
| Ambiguous / partial prep | Hybrid: reuse prep artifacts (script, config, tokens) + dispatch fresh instance to execute |

**How main thread applies this:**
- When a teammate's closing protocol recommends "dispatch fresh X," check the session transcript for what the existing X has already produced.
- If meaningful prep exists, reply in NEXUS (or inline in ONE-OFF mode): "reuse existing instance — prep artifact at <path/location>; fresh instance bias-reduction not worth discarding prep."
- Only re-dispatch fresh when bias-reduction benefit clearly outweighs prep discard cost.

Bias-reduction via fresh instance is a legitimate tool — but it is a scalpel, not a default.

**Model selection rule (BINDING):**
- **Do NOT pass a `model` parameter when dispatching.** The Agent tool will use the agent's frontmatter model, which is the team's considered default per agent.
- The 3 agents set to sonnet (`session-sentinel`, `evidence-validator`, `challenger`) are structured reasoning roles where sonnet is sufficient — their frontmatter reflects this.
- The 29 agents on opus (every builder, language expert, guardian, strategist, intelligence, meta, CTO) need opus depth — overriding to sonnet silently degrades quality.
- **Only override** when the user explicitly instructs cost optimization (e.g., "run this review on sonnet to save cost"). In that case, pass `model: "sonnet"` explicitly and note the override in your response to the user.
- **Never downgrade language experts or deep-qa/deep-reviewer to sonnet** without explicit user approval — false negatives from these agents are expensive.

**Parallel dispatch:** For independent tasks (e.g., `deep-qa` + `deep-reviewer`), make multiple Agent tool calls in a single message — they run concurrently.

### CLOSED-LOOP RULE (NON-NEGOTIABLE)

**Once agent team work begins, NEVER break out of the team workflow:**
- Do NOT start running curl commands yourself when test-engineer + elite-engineer should do it
- Do NOT start reading 50 files yourself when deep-qa should audit
- Do NOT start planning yourself when deep-planner exists
- Do NOT start implementing yourself when elite-engineer exists
- If you catch yourself doing work that an agent should do → STOP → dispatch the agent
- If unsure which agent → dispatch `cto` — it decides

**The only things you do directly:**
- Simple file reads (< 3 files) for quick context
- Single-line edits with known paths
- Git status, git log, or other trivial commands
- Routing the user's message to the right agent
- Dispatching `session-sentinel` at session start/end for team health audits

**CTO authority model (two modes — BINDING):**
- **TEAM MODE (default for non-trivial work):** CTO dispatched with `team_name` is a teammate. It has *execution authority via NEXUS* — emits `[NEXUS:SPAWN] elite-engineer`, `[NEXUS:SCALE]`, `[NEXUS:RELOAD]`, `[NEXUS:ASK]`, etc. via SendMessage to `"lead"`. Main thread processes each syscall in real-time and replies `[NEXUS:OK|ERR]`. CTO coordinates the team live — not via post-hoc text signals.
- **ONE-OFF MODE (fallback for trivial consultations):** CTO dispatched without team context has only *directive authority* — emits `### DISPATCH RECOMMENDATION` in closing protocol. Main thread reads the text signal and executes the dispatch. Use only for single-call consultations that don't need coordination.

**Pattern F dispatch (mode-dependent):**
- **TEAM MODE:** CTO (or main thread) emits `[NEXUS:SPAWN] memory-coordinator` and `[NEXUS:SPAWN] meta-agent` in parallel — both join the same team.
- **ONE-OFF MODE:** Main thread dispatches `memory-coordinator` + `meta-agent` DIRECTLY via Agent tool on CTO's closing-protocol recommendation. Still valid — just slower than team-mode NEXUS.

### MANDATORY SIGNAL PERSISTENCE (NOT OPTIONAL)

> WARNING: Summarizing signals for the user is NOT sufficient. If you do not call Write or Edit to persist batch signals to disk before responding, you have violated protocol. The signal bus must be the source of truth, not the transcript.

Every agent output ends with 4 structured signals. After ANY agent dispatch returns, you MUST process all 4 before sending your next response to the user:

| Signal | Action | Tool to call |
|--------|--------|--------------|
| `### DISPATCH RECOMMENDATION` | If not "NONE" → dispatch the recommended agent immediately | Agent tool |
| `### CROSS-AGENT FLAG` | If not "NONE" → dispatch the flagged agent with the finding | Agent tool |
| `### MEMORY HANDOFF` | If not "NONE" → APPEND to `.claude/agent-memory/signal-bus/memory-handoffs.md` | Edit tool |
| `### EVOLUTION SIGNAL` | If not "NONE" → APPEND to `.claude/agent-memory/signal-bus/evolution-signals.md` | Edit tool |

**Canonical entry format** (append one line per signal, below the `<!-- Entries below -->` marker):
```
- (YYYY-MM-DD, agent=<name>, session=<id-or-topic>) <signal content verbatim>
```

**Before responding to the user after any agent dispatch, verify:**
- [ ] Processed `DISPATCH RECOMMENDATION` (dispatched or confirmed NONE)
- [ ] Processed `CROSS-AGENT FLAG` (dispatched or confirmed NONE)
- [ ] Appended `MEMORY HANDOFF` to `memory-handoffs.md` (or confirmed NONE)
- [ ] Appended `EVOLUTION SIGNAL` to `evolution-signals.md` (or confirmed NONE)
- [ ] **HIGH-severity findings gated by `evidence-validator`** (see rule below) — dispatched or documented skip-with-reason
- [ ] **Synthesis/recommendation reviewed by `challenger`** (before any strategic recommendation is surfaced to user)

### EVIDENCE-VALIDATOR AUTO-DISPATCH (NON-NEGOTIABLE)

> WARNING: This rule exists because silent bypass of evidence-validator for HIGH/CRITICAL findings has historically produced cascades of unverified claims reaching the user. Trust calibration is blocked without validator verdicts. This is the orchestration layer's responsibility, not the subagent's.

**Trigger.** After any dispatch returns, scan the output for findings tagged `CRITICAL` or `HIGH`. For EACH such finding:

1. Parse: `(file:line, claim)` from the finding body
2. **DISPATCH** `evidence-validator` with the claim + file:line BEFORE surfacing the finding to the user
3. Record the verdict (`CONFIRMED | PARTIALLY_CONFIRMED | REFUTED | UNVERIFIABLE`) in the trust ledger:
   ```
   .claude/agent-memory/trust-ledger/ledger.py verdict --agent <source-agent> --finding-id <id> --verdict <verdict>
   ```
4. Only surface the finding to the user AFTER the validator verdict is attached

**Skip protocol (rare, must be documented).** If you bypass the validator for a specific HIGH finding, you MUST emit an explicit skip-with-reason line in your response:
```
SKIPPED evidence-validator for [finding-id]: [reason, e.g., "time-critical incident rollback, pre-verified by user"]
```
Silent bypass is a protocol violation. An undocumented bypass cascade (3+ in one session) requires a Pattern F root-cause investigation the next session.

**Why this lives in CLAUDE.md, not individual agent prompts.** Subagents cannot dispatch `evidence-validator` themselves (nested-dispatch constraint). Validation is a main-thread responsibility — only the orchestration layer sees the full set of agent outputs and can gate them.

### CHALLENGER AUTO-DISPATCH (NON-NEGOTIABLE)

**Trigger.** Before surfacing ANY CTO synthesis, strategic recommendation, or cross-agent plan to the user, dispatch `challenger` with the recommendation as input. The challenger produces adversarial review along 5 dimensions (steelman alternatives, hidden assumptions, evidence quality, missed cases, downstream impact). Include the challenger's critique alongside the CTO synthesis in the response to the user, so the user sees both the recommendation and its strongest counter.

**What counts as a "synthesis/recommendation" requiring challenger gating:**
- CTO's consolidated workflow report at end of a Pattern A/B/C/D/E campaign
- Any multi-agent decision presented as a recommendation (e.g., "we should ship X now")
- Strategic plans produced by `deep-planner` when they involve irreversible actions (deploys, migrations, schema changes)

**What does NOT require challenger gating:**
- Raw agent findings passed through verbatim (those are already handled by evidence-validator)
- Routine status reports
- Completed work summaries with no forward-looking recommendation

**Chain dispatching:** A recommends B, B recommends C — follow `DISPATCH RECOMMENDATION` until NONE. Batch signals accumulate in `.claude/agent-memory/signal-bus/` until Pattern F drains them (see Session Lifecycle table).

### Agents NEVER Dispatched (BLOCKED)

Do NOT use these generic built-in subagent types — use the custom team:
- `Plan` → use `deep-planner` instead
- `Explore` → use the appropriate custom agent or `cto`
- `general-purpose` → use the appropriate custom agent or `cto`

### Full Team Roster (32 Agents)

```
TIER 1 — BUILDERS: elite-engineer, ai-platform-architect, frontend-platform-engineer,
                    beam-architect, elixir-engineer, go-hybrid-engineer
TIER 2 — GUARDIANS: go-expert, python-expert, typescript-expert, deep-qa, deep-reviewer,
                     infra-expert, database-expert, observability-expert, test-engineer, api-expert,
                     beam-sre, code-sentinel (engineering discipline enforcer)
TIER 3 — STRATEGISTS: deep-planner, orchestrator
TIER 4 — INTELLIGENCE: memory-coordinator, cluster-awareness, benchmark-agent,
                        erlang-solutions-consultant, talent-scout, intuition-oracle
TIER 5 — META-COGNITIVE: meta-agent, recruiter
TIER 6 — GOVERNANCE: session-sentinel (protocol enforcer)
TIER 7 — CTO: cto (supreme authority — dispatches, delegates, debates, evolves the team)
TIER 8 — VERIFICATION: evidence-validator (claim verification), challenger (adversarial review)
```

---

### VERIFICATION & TRUST INFRASTRUCTURE

The team includes four hardening layers that support the 32 agents (30 specialists + 2 verifiers):

**1. Protocol enforcement hooks** (`.claude/hooks/`)
- `verify-agent-protocol.sh` — SubagentStop hook; blocks subagents that skip the 4 closing-protocol sections
- `verify-signal-bus-persisted.sh` — SubagentStop hook; warns if non-NONE signals weren't persisted
- `auto-record-trust-verdict.sh` — SubagentStop hook; auto-records evidence-validator verdicts into the trust ledger
- `log-nexus-syscall.sh` — PostToolUse hook; auto-logs NEXUS syscalls to `nexus-log.md`
- `pre-commit-agent-contracts.sh` — git hook; runs contract tests on staged agent edits

**2. Agent contract tests** (`.claude/tests/agents/`)
- `run_contract_tests.py` validates every agent file against 11 contracts
- All 32 agents × 11 contracts = 352 assertions, all passing
- Run on every commit via pre-commit hook, and before every major session

**3. Evidence-validator + Challenger agents**
- `evidence-validator`: given any finding (file:line + claim), reads source and classifies CONFIRMED/PARTIALLY_CONFIRMED/REFUTED/UNVERIFIABLE
- `challenger`: given any recommendation, produces adversarial critique along 5 dimensions (steelman alternatives, hidden assumptions, evidence quality, missed cases, downstream impact)
- Auto-dispatch on HIGH-severity findings (validator) and CTO synthesis (challenger)

**4. Agent trust ledger** (`.claude/agent-memory/trust-ledger/`)
- Per-agent accuracy scorecard, updated by evidence-validator verdicts and challenger outcomes
- Bayesian-blended trust weight (0-1) used by CTO to weight conflicting findings during synthesis
- CLI at `.claude/agent-memory/trust-ledger/ledger.py`: `verdict`, `challenge`, `show`, `weight`, `standings`

Together these turn "30 specialists producing findings" into "32 agents producing VERIFIED findings with per-agent trust calibration" — the verifiers break single-point trust, the hooks enforce invariants, the contract tests prevent regression, and the ledger calibrates confidence.

### NEXUS PROTOCOL — Team Operating System Layer

**Team mode is the default operating mode (BINDING).** Non-trivial sessions run under TeamCreate → teammate dispatch → NEXUS syscalls. The closing-protocol text-signal path (`### DISPATCH RECOMMENDATION`) is the fallback for one-off mode ONLY.

**The main thread (you, the orchestrator reading this CLAUDE.md) IS the kernel.** Teammates cannot use the Agent tool, AskUserQuestion, MCP management, CronCreate, or EnterWorktree. When they need these capabilities, they send a `[NEXUS:*]` message via SendMessage. **You MUST detect and process these automatically.**

**Kernel listening posture (MANDATORY):** When a teammate's SendMessage to `"lead"` starts with `[NEXUS:` — treat it as an incoming syscall, NOT a conversational message. Process immediately per the syscall table below. Auto-logging to `signal-bus/nexus-log.md` is handled by the `PostToolUse SendMessage` hook.

**Main-thread reply format (BINDING):** When responding to a NEXUS syscall, your SendMessage reply MUST start with `[NEXUS:OK <payload>]` or `[NEXUS:ERR <reason>]` so the hook captures it as a structured response and the originating agent can parse it programmatically. Plain text replies to a NEXUS syscall lose the round-trip.

#### Privilege Boundary

```
KERNEL (Main Thread Only):     Agent tool, AskUserQuestion, MCP/Plugin mgmt, CronCreate, EnterWorktree
NEXUS INTERFACE:               SendMessage with [NEXUS:*] prefix — bridges the gap
USER SPACE (All Teammates):    TeamCreate, SendMessage, TaskCreate, Read/Edit/Write/Bash, Web tools
```

#### Syscall Table

| Syscall | Format | Main Thread Action |
|---------|--------|--------------------|
| `SPAWN` | `[NEXUS:SPAWN] agent_type \| name=X \| prompt=...` | Use Agent tool with `team_name` + `name` + `subagent_type` to spawn teammate |
| `MCP` | `[NEXUS:MCP] server_name \| config={...}` | Install/configure MCP server via settings |
| `ASK` | `[NEXUS:ASK] question text here` | Use AskUserQuestion, return answer to requesting agent |
| `CRON` | `[NEXUS:CRON] schedule=5m \| command=...` | Use CronCreate, return confirmation |
| `WORKTREE` | `[NEXUS:WORKTREE] branch=feature-x` | Use EnterWorktree, return path |
| `RELOAD` | `[NEXUS:RELOAD] agent_name` | Shutdown agent via SendMessage, respawn with fresh prompt |
| `SCALE` | `[NEXUS:SCALE] agent_type \| count=N \| prompt=...` | Spawn N copies: `agent-1`, `agent-2`, ..., `agent-N` |
| `CAPABILITIES` | `[NEXUS:CAPABILITIES?]` | Respond with list of available syscalls |
| `PERSIST` | `[NEXUS:PERSIST] key=X \| value=Y` | Write to durable memory file |
| `BRIDGE` | `[NEXUS:BRIDGE] from_team=X \| to_agent=Y \| message=...` | Route message across teams |
| `INTUIT` | `[NEXUS:INTUIT] <question>` | OPTIONAL. Queries the Shadow Mind's intuition-oracle for pattern-based probabilistic guidance. No agent required to use. Returns `INTUIT_RESPONSE v1` envelope (see Shadow Mind section). |

#### Processing Rules

1. **DETECT** — When you receive a SendMessage from a teammate starting with `[NEXUS:`, it is a syscall — NOT a conversational message.
2. **VALIDATE** — Check the syscall is in the table above. If unknown, respond with `[NEXUS:ERR] Unknown syscall: X`.
3. **AUTHORIZE** — Most syscalls auto-execute. For high-risk ones (MCP install, production CRON), confirm with user first.
4. **EXECUTE** — Use the appropriate main-thread-only tool to fulfill the request.
5. **RESPOND** — SendMessage back to the requesting agent:
   - Success: `[NEXUS:OK] result description`
   - Failure: `[NEXUS:ERR] error description`
6. **LOG** — Append to `.claude/agent-memory/signal-bus/nexus-log.md` for audit trail.

#### ATOMIC-QUEUE-SCAN RULE (BINDING)

Before emitting `[NEXUS:OK]` on ANY single teammate syscall, main-thread MUST scan the full unread message queue from that teammate since last processed message and identify ALL `[NEXUS:*]` syscalls emitted in sequence. Process them ATOMICALLY in timestamp order — not just the triggering notification. Single-message processing is the anti-pattern.

**The checklist before any `[NEXUS:OK]` reply:**
1. Check the inbox for the teammate who just sent the triggering syscall.
2. Scan ALL unread messages from that teammate since the last processed one.
3. Enumerate EVERY `[NEXUS:*]` prefix found.
4. Process them atomically in timestamp order — one Agent/AskUserQuestion/etc. tool call per syscall.
5. Reply with `[NEXUS:OK]` per syscall, not a merged response.

#### FRESHNESS RE-VERIFY DISCIPLINE (BINDING)

Before proxying a destructive-action `[NEXUS:ASK]` to user via AskUserQuestion, main-thread MUST re-verify current system state if >5 minutes has elapsed since the blocker was first reported. Query the originating teammate for a status update before the AskUserQuestion call. Stale-context proxy is a near-miss class that should be eliminated.

#### CHALLENGER LEDGER-WRITE MANDATE (BINDING)

After challenger returns a verdict on a CTO synthesis or cross-agent recommendation, main-thread MUST write TWO ledger entries before continuing:

```bash
agent-memory/trust-ledger/ledger.py challenge --agent challenger --outcome <SURVIVED|MODIFIED|OVERTURNED|LOST>
agent-memory/trust-ledger/ledger.py verdict --agent <source-synthesizing-agent> --verdict <CONFIRMED|PARTIALLY_CONFIRMED|REFUTED>
```

Outcome taxonomy for `challenge`:
- **SURVIVED** — synthesis accepted as-is or with light mods
- **MODIFIED** — synthesis accepted with strong mods based on challenger critique
- **OVERTURNED** — synthesis rejected / replanned based on challenger critique
- **LOST** — legacy alias for OVERTURNED (backward compatibility)

**Timing:** write the ledger entries in the SAME main-thread turn as receiving the challenger output, BEFORE presenting the synthesis to the user. Deferred writes lose the single-verdict granularity the ledger depends on.

#### Security Tiers

| Tier | Syscalls | Authorization |
|------|----------|---------------|
| **AUTO** | SPAWN, CAPABILITIES, PERSIST, RELOAD, INTUIT | Execute immediately, no user confirmation needed |
| **CONFIRM** | MCP, CRON, WORKTREE, SCALE, BRIDGE | Log intent, confirm with user if high-risk |
| **RESTRICTED** | ASK | Always proxied — agent cannot impersonate user |

#### Example Flow

```
CTO teammate → SendMessage(to: "team-lead", message: "[NEXUS:SPAWN] elite-engineer | name=ee-fix | prompt=Fix bug in service.go:142")
Main thread  → Agent(subagent_type: "elite-engineer", name: "ee-fix", team_name: "cto-session", prompt: "Fix bug in service.go:142")
Main thread  → SendMessage(to: "cto", message: "[NEXUS:OK] ee-fix spawned and joined team")
CTO teammate → SendMessage(to: "ee-fix", message: "Fix the bug, review with go-expert when done")
```

#### NEXUS Log

All syscalls are logged to `.claude/agent-memory/signal-bus/nexus-log.md`:
```
- (YYYY-MM-DD HH:MM, agent=cto, syscall=SPAWN) elite-engineer as ee-fix → OK
- (YYYY-MM-DD HH:MM, agent=orchestrator, syscall=SCALE) elite-engineer x3 → OK (ee-1, ee-2, ee-3)
```

---

### Shadow Mind (parallel cognitive layer — optional)

The **Shadow Mind** is a non-invasive parallel cognitive layer that runs alongside the 32-agent conscious team without modifying any existing agent prompt, protocol, memory directory, or signal bus entry. It consists of **six components** living under `.claude/agent-memory/shadow-mind/` and `.claude/hooks/shadow-*`:

1. **Observer Daemon** (`shadow-observer.sh`) — tails the signal bus, writes JSON observations
2. **Pattern Computer** (`shadow-pattern-computer.py`) — reads observations, derives n-grams + co-occurrences + temporal patterns via atomic writes
3. **Pattern Library** (data at `patterns/{ngrams,co_occurrences,temporal,topic_clusters}.json`) — read-only substrate populated by the Computer
4. **Speculator** (`shadow-speculator.py`) — generates counterfactual variants per observation
5. **Dreamer** (`shadow-dreamer.py`) — proposes insight candidates during long-idle windows
6. **`intuition-oracle`** agent — the queryable surface, synthesizes all 5 data sources into probabilistic `INTUIT_RESPONSE v1` answers

Conscious-layer agents coexist with the Shadow Mind and may OPTIONALLY consult it via the `[NEXUS:INTUIT] <question>` syscall. The oracle responds with an `INTUIT_RESPONSE v1` envelope containing `{status, answer, confidence, evidence_ids, pattern_types_consulted, staleness_hours}`. When observer heartbeat is > 24h old, the oracle returns `status: SHADOW_MIND_STALE` rather than serving stale patterns. No agent is REQUIRED to use `[NEXUS:INTUIT]` — the Shadow Mind is advisory and never interrupts a dispatch chain.

The entire Shadow Mind is **delete-to-disable**: removing `.claude/agent-memory/shadow-mind/` (and the `shadow-*` hook scripts) takes the layer offline without affecting the 32-agent team. All 352/352 contract tests continue to pass. meta-agent retains single-writer authority over `.claude/agents/*.md`; Dreamer outputs are proposals only. Full data schemas, enable/disable commands, and component details are documented in `.claude/agent-memory/shadow-mind/README.md`.

#### Shadow Mind Activation Protocol (MANDATORY at session start)

The Shadow Mind must be activated to learn. The autostart hook (`hooks/shadow-mind-autostart.sh`) handles this automatically at SessionStart, but verify these steps are running:

1. **Observer daemon** — must be running to collect observations from the signal bus
2. **Pattern Computer** — runs on startup to refresh the Pattern Library (ngrams, co-occurrences, temporal, topic_clusters)
3. **Heartbeat freshness** — `heartbeats/observer.json` must show `last_run` < 24h

If the Shadow Mind is installed but dormant (observer not running, no observations), agents querying via `[NEXUS:INTUIT]` will receive `INSUFFICIENT_DATA` responses. Run `hooks/nexus-doctor.sh` to check Shadow Mind status.

**Pattern retrieval:** Agents can query "have we seen this before?" via `[NEXUS:INTUIT]`. The oracle checks `patterns/topic_clusters.json` for keyword-matched historical patterns, including what fix resolved similar issues in past sessions. This enables session-over-session learning.

#### NEXUS Doctor (Health Check)

Run `hooks/nexus-doctor.sh` before sessions to verify framework health:
```bash
bash hooks/nexus-doctor.sh              # full check (includes contract tests)
bash hooks/nexus-doctor.sh --skip-tests # fast check (skip contract tests)
```

Checks: agent count, hook permissions, dependencies, settings validity, signal bus, trust ledger, Shadow Mind status, contract tests, hygiene (no secrets, no junk files).

---

## Project-Specific Context

> **This section is intentionally empty.** Add your project's architecture overview, development commands, service URLs, environment variables, and deployment notes here. The team protocol above is project-agnostic — it works for any codebase. The sections below are where you tell the team what they're working on.

### Architecture Overview

<!-- Describe your system's architecture, services, and how components interact. -->

### Development Commands

<!-- List common commands: build, test, lint, run, deploy. -->

### Key Technical Patterns

<!-- Document patterns the team should follow: auth flow, state management, testing strategy, etc. -->

### Environment Configuration

<!-- Document required environment variables and where to find them. -->

### Deployment Notes

<!-- Document deployment process, infrastructure, CI/CD pipelines. -->
