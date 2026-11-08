# claude-autonomous-agent-patterns-skill

A Claude Code skill for designing autonomous coding agents with explicit tool interfaces, permissions, execution loops, and human oversight.

## Overview

This skill provides reusable patterns for agents that can inspect environments, call tools, make decisions, and perform multi-step work. It emphasizes controlled autonomy: every capability should have a defined purpose, permission boundary, and failure strategy.

## Main Topics

- Agent loop architecture.
- Tool and function interface design.
- Permission and approval systems.
- Browser and environment automation.
- Human-in-the-loop workflows.
- State and context management.
- Error handling and recovery.
- Observability and auditability.
- Safe execution boundaries.

## Core Agent Architecture

A typical agent cycle includes:

1. Receive a bounded objective.
2. Inspect relevant context.
3. Choose a permitted action.
4. Validate tool arguments.
5. Execute the action.
6. Inspect the result.
7. Update state and plan.
8. Stop when the objective is met or a boundary is reached.

The loop must have explicit step limits and stop conditions.

## Tool Design

A good tool contract defines:

- A narrow action.
- Required and optional arguments.
- Input validation.
- Permission requirements.
- Expected output structure.
- Failure modes.
- Whether the action has side effects.

Prefer small, composable tools over broad tools that can perform unrelated operations.

## Permission Model

Classify actions by impact:

- Read-only inspection.
- Reversible local changes.
- External communication or publication.
- Destructive or irreversible operations.

Require approval when an action can materially affect users, data, infrastructure, or external systems.

## Installation

```bash
git clone https://github.com/Brajesh31/claude-autonomous-agent-patterns-skill.git ~/.claude/skills/autonomous-agent-patterns
```

## Usage

Invoke the skill when designing an agent runtime or tool system:

```text
/autonomous-agent-patterns
```

Provide the agent's objective, environment, available tools, permission model, and expected operating limits.

## Recommended Workflow

1. Define the agent's job and non-goals.
2. Separate deterministic logic from model decisions.
3. Design tool contracts.
4. Define read/write and approval boundaries.
5. Choose a bounded execution loop.
6. Add state tracking and observability.
7. Implement failure and cancellation behavior.
8. Test normal, adversarial, and interrupted workflows.
9. Review side effects and permissions.
10. Expand autonomy only after successful evaluation.

## Safety Checklist

- Tool access follows least privilege.
- Inputs are validated.
- Destructive actions require approval.
- Execution has step and time limits.
- Browser and shell actions are scoped.
- Secrets are protected.
- State transitions are recorded.
- Errors stop unsafe execution.
- Human override is available.
- Actions can be audited.

## Repository Contents

- `SKILL.md`: Main autonomous agent design patterns.
- `README.md`: Architecture, permissions, and workflow guidance.

## Practical Principle

An agent should be capable enough to complete its assigned task and constrained enough that its mistakes remain understandable and recoverable.
