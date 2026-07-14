# Progress Reporting

![Status](https://img.shields.io/badge/status-always%20on-1f883d)
![Type](https://img.shields.io/badge/type-global%20rule-black)
![Scope](https://img.shields.io/badge/scope-all%20agents-blue)

<a href="https://liviogama.github.io/agent-config/redirect.html?url=https://raw.githubusercontent.com/LivioGama/progress-reporting/main/.agent-config/rules/progress-reporting.md"><img src="https://raw.githubusercontent.com/LivioGama/agent-config/main/assets/install-badge-small.jpg" alt="Install progress-reporting global rule" height="40" /></a>

### Honest percentage updates at meaningful milestones

`progress-reporting` is an always-on global rule that requires AI agents to provide honest `Progress: NN/100` updates during non-trivial work. This keeps users informed about completion status without over-promising or substituting for actual verification.

## 🎯 What It Is For

Long-running agent tasks can leave users uncertain about completion status. This rule ensures:

- **Transparent communication**: Regular progress updates at meaningful milestones
- **Honest estimates**: Current completion percentage, not commitments
- **Contextual updates**: What's done, what's happening now, what remains
- **Appropriate frequency**: Updates every ~30 seconds during active work

## 📊 The Rule

For non-trivial work, give honest `Progress: NN/100` updates at meaningful milestones and roughly every 30 seconds while active.

The percentage is a current estimate of user-visible completion, not a plan item, commitment, or substitute for verification.

Each progress update should briefly say:
- What is done
- What is happening now  
- What remains or blocks completion

## 🔄 Example Usage

**Bad example** (vague, no percentage):
```
Working on the feature...
Still working...
Almost done...
```

**Good example** (specific, with percentage):
```
Progress: 25/100
Done: Set up project structure, installed dependencies
Now: Implementing core authentication logic
Remains: UI components, testing, deployment
```

**Another example** (milestone-based):
```
Progress: 60/100
Done: Database schema, API endpoints, basic UI
Now: Integrating payment processing
Blocks: Waiting for API keys from user
```

## 🎯 When to Apply

- **Non-trivial work**: Tasks taking more than 30 seconds
- **Multi-step processes**: Any work with clear phases
- **User-facing operations**: Changes visible to the user
- **Long-running operations**: Builds, tests, deployments

**Do not apply** to:
- Quick one-liners
- Simple file reads
- Instant responses
- Trivial edits

## 📈 Progress Guidelines

### Percentage Estimation

- **0-10%**: Initial setup, planning, environment preparation
- **10-30%**: Core structure, basic implementation
- **30-60%**: Main features, integration work
- **60-80%**: Refinement, testing, bug fixes
- **80-95%**: Final polish, documentation, verification
- **95-100%**: Completion, cleanup, summary

### Update Frequency

- **Milestone-driven**: Update at phase completions
- **Time-based**: Update every ~30 seconds during active work
- **Blocker-driven**: Update immediately when blocked/unblocked
- **User-driven**: Update when user asks for status

### Content Quality

Each update should include:
1. **Done**: What's completed since last update
2. **Now**: What's currently happening
3. **Remains**: What's left to do
4. **Blocks**: Any blockers or dependencies

## 🚀 Agent-First Usage

Install the global rule through the `agent-config` deeplink handler:

<a href="https://liviogama.github.io/agent-config/redirect.html?url=https://raw.githubusercontent.com/LivioGama/progress-reporting/main/.agent-config/rules/progress-reporting.md"><img src="https://raw.githubusercontent.com/LivioGama/agent-config/main/assets/install-badge-small.jpg" alt="Install progress-reporting global rule" height="40" /></a>

Install URL:

```text
https://liviogama.github.io/agent-config/redirect.html?url=https://raw.githubusercontent.com/LivioGama/progress-reporting/main/.agent-config/rules/progress-reporting.md
```

Raw rule URL:

```text
https://raw.githubusercontent.com/LivioGama/progress-reporting/main/.agent-config/rules/progress-reporting.md
```

## 🔐 Important Notes

- **Not a commitment**: Percentages are estimates, not promises
- **Not a substitute**: Progress updates don't replace verification
- **Honesty first**: Report setbacks and blockers immediately
- **User-focused**: Report user-visible completion, not internal metrics
- **Context matters**: Adjust granularity based on task complexity

## 📖 Full Rule

See [progress-reporting.md](.agent-config/rules/progress-reporting.md) for the complete rule definition.

## 🎯 Benefits

- **User confidence**: Transparent progress builds trust
- **Early detection**: Blockers identified and reported quickly
- **Better planning**: Users can estimate remaining time
- **Reduced anxiety**: Regular updates eliminate uncertainty
- **Clear communication**: Structured format prevents ambiguity
