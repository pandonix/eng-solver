# Engineering Solver Workspace

This workspace is for solving engineering-analysis and solution-design problems in a controlled, evidence-first loop.

## Mission
Turn a user problem into a reviewable engineering recommendation by moving through a fixed loop:

INTAKE -> CLARIFY -> PLAN -> DISPATCH -> COLLECT -> CROSS_EXAMINE -> SCORE -> REPORT -> USER_REVIEW -> DONE

Do not skip stages when the problem is still ambiguous or when evidence is thin.

## Core rules
1. Define the problem before proposing a solution.
2. Fix success criteria before comparing options.
3. Collect evidence before promoting a recommendation.
4. Keep alternatives alive until the judge promotes one.
5. Use workspace files as source of truth; do not rely only on chat history.
6. Do not present a final recommendation without a scorecard.
7. Keep risks and open questions visible.

## Standard working files
For each problem instance, use these files as the source of truth:
- `problem.md`
- `success_criteria.yaml`
- `constraints.yaml`
- `judge_policy.yaml`
- `question_log.md`
- `task_graph.json`
- `evidence/*.json`
- `drafts/*.md`
- `scorecards/*.yaml`
- `reports/*.md`
- `decision_log.md`

## Role map
Use the workspace skills for the following roles:
- `chief_orchestrator`: controls stage transitions and file updates
- `clarifier`: clarifies scope, constraints, and success criteria
- `planner`: decomposes the problem into evidence tasks
- `browser_broker`: collects evidence from the web or web UIs
- `skeptic_judge`: checks evidence, constraints, and promotion criteria
- `reporter`: prepares the user-facing draft

## Promotion policy
A candidate may be promoted only when:
- the problem definition is stable enough,
- key constraints are covered,
- evidence is sufficient for the core claims,
- at least one serious alternative has been compared,
- the latest scorecard says `promote`.

If any of the above is missing, iterate or reject.

## User review handling
When the user follows up, first classify the follow-up:
- correction to the problem definition,
- new constraint,
- request for more evidence,
- request for option comparison,
- request for implementation detail.

Then route back to the right stage instead of rewriting everything from scratch.

## Writing style
- Be direct.
- Prefer structured outputs over long prose.
- Surface uncertainty instead of hiding it.
- Keep reports decision-friendly.
