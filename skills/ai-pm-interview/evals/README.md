# Evaluation Suite

This directory contains behavioral evaluations for the `ai-pm-interview-lab` skill.

The goal is to verify that the skill conducts realistic, interactive AI Product Manager interviews, evaluates candidates consistently, adapts to their responses, and provides actionable feedback.

These evaluations test **observable behavior**, not exact wording. A response can pass while using different phrasing, provided it satisfies the case's expected behaviors.

## Files

- `cases.yaml` — evaluation scenarios, test inputs, and expected behaviors.

## What We Evaluate

The initial suite focuses on six areas:

1. **Interview interaction** — asks one primary interview question at a time and waits for the candidate's response.
2. **Structured assessment** — applies the skill's five scoring dimensions and explicit 0–2 scoring anchors consistently.
3. **AI product judgment** — distinguishes problems that benefit from AI from those better solved with conventional software.
4. **Technical reasoning** — evaluates model selection, retrieval, tools, agents, evaluation, latency, cost, and reliability when relevant.
5. **Adaptive coaching** — adjusts follow-up questions and difficulty based on the candidate's answers.
6. **Actionable feedback** — identifies strengths, gaps, and concrete next steps without inventing evidence.

## Running Evaluations

These cases are written as a portable, human-readable YAML test specification. They are not tied to a particular testing framework or model provider.

To run a case manually:

1. Load `skills/ai-pm-interview-lab/SKILL.md` into the target AI runtime.
2. Start a fresh conversation for the test.
3. Submit the case's `input` as the candidate's message.
4. Continue the interaction using the supplied `follow_up_inputs`, if any.
5. Compare the observed behavior with the case's `expected_behaviors`.
6. Record a pass or fail for each expected behavior, with a short evidence-based note.

For cases that test multiple turns, evaluate the entire interaction rather than a single response.

## Pass Criteria

A case passes when all required expected behaviors are satisfied and no critical failure occurs.

Examples of critical failures include:

- Asking several unrelated interview questions at once when the interview should be interactive.
- Assigning scores without grounding them in the candidate's response.
- Treating every problem as requiring an AI solution.
- Claiming that an evaluation, benchmark, or experiment was run when it was not.
- Providing a final assessment without acknowledging important missing evidence.
- Ignoring an explicit request to stop or change interview mode.

Minor differences in tone, ordering, or wording should not cause a failure unless they undermine the intended behavior.

## Scoring and Reporting

For each case, record:

| Field | Description |
|---|---|
| Case ID | Unique identifier from `cases.yaml` |
| Result | Pass or fail |
| Evidence | Brief quote or description of observed behavior |
| Severity | Critical, major, or minor for each failure |
| Notes | Ambiguities, unexpected behavior, or proposed improvements |

Do not confuse the skill's candidate-scoring rubric with the evaluation suite's pass/fail criteria. The former assesses interview performance; the latter assesses whether the skill behaves correctly.

## Scope and Limitations

This initial suite is a baseline, not proof of production readiness. It covers common interactions and several important edge cases, but it does not establish statistical reliability across models, prompts, or repeated runs.

Before making a release, test the skill across multiple supported runtimes and models. Where practical, repeat cases to identify inconsistent behavior and add regression cases for discovered failures.

