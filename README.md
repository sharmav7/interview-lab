# Interview Lab

**An open-source collection of AI-powered interview preparation skills.**

Interview Lab is a community-driven library of reusable, structured skills that help people prepare for job interviews through realistic practice, adaptive questioning, evidence-based feedback, and actionable coaching.

The project aims to make high-quality interview preparation accessible, consistent, and adaptable across AI assistants and interview formats.

## Why This Project?

Traditional interview preparation often relies on static question banks, generic model answers, or unstructured feedback. These approaches can help candidates learn concepts, but they do not always replicate the reasoning, ambiguity, and follow-up questions of a real interview.

This project takes a different approach.

Each skill defines a structured coaching experience with explicit instructions, evaluation criteria, interaction patterns, and completion criteria.

Depending on the interview type, a skill may help candidates:

- Practice realistic mock interviews.
- Answer one question at a time and receive targeted follow-ups.
- Improve structured thinking and communication.
- Receive consistent, evidence-based feedback.
- Identify strengths and development areas.
- Practice at different difficulty levels.
- Work through realistic scenarios and constraints.
- Track progress using portable session summaries.
- Build confidence through deliberate practice.

The goal is not to help candidates memorize ideal answers. It is to help them develop the judgment, communication, and problem-solving skills needed to perform well in real interviews.

## Available Skills

Skills are organized by interview type and professional role.

| Skill | Description | Status |
|---|---|---|
| AI PM Interview | Practice AI Product Manager interviews covering product thinking, AI solution design, evaluation, metrics, prioritization, and risk management. | Experimental |
| System Design Interview | Practice architecture, scalability, reliability, performance, and technical trade-offs. | Planned |

The catalog will evolve as new skills are contributed, tested, and maintained.

A skill's status reflects its maturity in this repository, not a guarantee of interview outcomes.

## How It Works

Each skill is a self-contained set of instructions designed to guide an AI assistant through a particular interview-preparation experience.

A typical session follows this workflow:

1. **Set the context:** Establish the target role, interview format, and desired difficulty.
2. **Start the interview:** Present a relevant question or scenario.
3. **Evaluate the response:** Assess the candidate's reasoning against explicit criteria.
4. **Provide feedback:** Explain what worked, what is missing, and why it matters.
5. **Probe or retry:** Ask a relevant follow-up or give the candidate an opportunity to improve.
6. **Adapt the experience:** Adjust the next question or level of guidance based on demonstrated performance.
7. **Summarize progress:** Provide evidence-backed strengths, development priorities, and recommended exercises.

Not every skill follows the same workflow. Technical, product, and behavioral interviews require different evaluation methods, so each skill defines its own domain-specific behavior.

## Getting Started

### 1. Choose a skill

Browse the [`skills/`](skills/) directory and select the skill relevant to your interview.

Each skill lives in its own directory and contains a `SKILL.md` file with its main instructions.

### 2. Download or clone the repository

Clone the repository:

```bash
git clone <repository-url>
cd interview-prep-skills
```

Replace `<repository-url>` with the URL of this repository.

Alternatively, download the repository archive or obtain the directory for an individual skill.

### 3. Use the skill with a compatible AI assistant

Follow the installation or import instructions for your chosen AI environment.

Depending on the platform, you may be able to install a skill directory directly, configure it as an agent capability, or provide its Markdown instructions to an AI assistant.

Compatibility varies by platform. Refer to the documentation for your AI environment and the individual skill.

For the most portable manual approach, provide the contents of the skill's `SKILL.md` to an AI assistant and ask it to follow the instructions. If the skill uses supporting reference files, provide those as well.

### 4. Start practicing

Specify your target role, interview format, and preferred difficulty when the skill supports those options.

For example:

> Conduct a realistic AI Product Manager mock interview. Ask one question at a time, evaluate my reasoning against an explicit rubric, and provide constructive feedback after each answer. Do not reveal model answers before I attempt the question.

For the best experience, engage with the questions as you would in a real interview rather than jumping directly to example answers.

## Repository Structure

The repository follows a modular, skill-oriented structure.

```text
interview-prep-skills/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── skills/
│   ├── ai-pm-interview-lab/
│   │   ├── SKILL.md
│   │   ├── references/
│   │   ├── assets/
│   │   └── evals/
│   ├── product-sense-interview/
│   │   └── SKILL.md
│   ├── system-design-interview/
│   │   └── SKILL.md
│   └── behavioral-interview/
│       └── SKILL.md
├── templates/
│   └── skill-template/
│       └── SKILL.md
├── schemas/
├── scripts/
├── adapters/
└── .github/
    ├── ISSUE_TEMPLATE/
    └── workflows/
```

Some directories are optional and may be introduced as the project grows.

### Directory conventions

- `skills/`: Canonical definitions of individual interview-preparation skills.
- `references/`: Supporting rubrics, domain guidance, and detailed instructions.
- `assets/`: Templates and other resources used by a skill.
- `evals/`: Representative test cases and expected behaviors.
- `templates/`: Starter files for new contributions.
- `schemas/`: Optional schemas for validating catalogs and evaluation data.
- `scripts/`: Validation, testing, and packaging utilities.
- `adapters/`: Platform-specific setup instructions or integration utilities.
- `.github/`: Contribution templates and automated workflows.

The canonical skill definitions are the source of truth. Any platform-specific packages or release bundles should be generated from these sources rather than maintained as independent copies.

## Skill Format

Skills use a portable Markdown format inspired by the [Agent Skills specification](https://agentskills.io/specification).

A typical skill directory looks like this:

```text
skills/
└── example-interview-skill/
    ├── SKILL.md
    ├── references/
    ├── assets/
    └── evals/
```

The `SKILL.md` file contains YAML frontmatter and the instructions that define the skill's behavior.

Example:

```markdown
---
name: example-interview-skill
description: >
  Help candidates practice a specific interview format
  through structured questions and constructive feedback.
---

# Example Interview Skill

## Purpose

Define the interview-preparation objective.

## When to Use

Describe when the skill should be activated.

## Interaction Protocol

Define how the interview should progress.

## Evaluation Criteria

Explain how responses should be assessed.

## Feedback and Adaptation

Describe how feedback, follow-ups, and difficulty
adjustments should work.

## Completion Criteria

Define the expected end-of-session output.
```

The example above is illustrative rather than a complete interview skill.

### Skill design principles

Every skill should aim to be:

**Self-contained:** Its core instructions should work without undocumented dependencies on other skills.

**Explicit:** Define the expected interaction, evaluation criteria, and completion behavior instead of relying on vague instructions.

**Consistent:** Apply scoring criteria consistently and explain evaluations using observable evidence.

**Adaptive:** Respond to the candidate's actual reasoning rather than following a rigid sequence of generic questions.

**Honest:** Distinguish known facts, assumptions, and unknowns. Avoid inventing scenario details or overstating evaluation confidence.

**Portable:** Avoid unnecessary dependence on a specific AI provider, proprietary tool, or platform-specific feature.

**Testable:** Include representative scenarios and observable criteria for determining whether the skill behaves as intended.

**Maintainable:** Keep core instructions focused and use supporting resources when detailed material would otherwise make the main file difficult to navigate.

## Evaluation and Quality

A well-formatted Markdown file is not necessarily a good interview-preparation skill.

The project therefore encourages testing both structural correctness and coaching quality.

### Structural validation

Automated checks may verify:

- Valid YAML frontmatter.
- Required metadata fields.
- Matching skill names and directory names.
- Valid relative links.
- Required documentation and evaluation files.
- Unique identifiers and catalog entries.

### Behavioral evaluation

Representative conversations should test whether a skill:

- Follows its declared interaction protocol.
- Uses the intended evaluation rubric.
- Asks relevant follow-up questions.
- Handles hints, retries, and interruptions appropriately.
- Accepts defensible alternative answers.
- Avoids revealing answers prematurely when that is part of the intended experience.
- Produces the required session summary.
- Maintains consistency across the interview.

### Coaching quality

Where practical, evaluations should also assess:

- Accuracy and relevance of feedback.
- Consistency of scoring.
- Evidence supporting evaluation decisions.
- Quality of follow-up questions.
- Usefulness of recommended practice exercises.
- Handling of ambiguity and uncertainty.

Evaluation results should be interpreted in context. Different AI models and execution environments may produce different results from the same instructions.

No skill can guarantee an interview offer or a particular hiring outcome.

## Contributing

Contributions are welcome.

You can help by:

- Creating skills for new interview formats or professional roles.
- Improving existing interview workflows.
- Refining evaluation rubrics.
- Adding representative test scenarios.
- Improving documentation and installation instructions.
- Reporting incorrect or inconsistent feedback.
- Testing skills across different AI environments.
- Improving accessibility and the overall candidate experience.

Before contributing, read [CONTRIBUTING.md](CONTRIBUTING.md) and follow the repository's contribution guidelines.

### Expectations for new skills

A proposed skill should include:

1. A clear interview-preparation objective.
2. A valid `SKILL.md` with appropriate metadata.
3. Explicit interaction and evaluation instructions.
4. Defined behavior for common edge cases.
5. Representative test cases or a plan for evaluating the skill.
6. Documentation of any required tools, supporting resources, or platform-specific limitations.

Contributions should focus on helping candidates develop genuine interview skills rather than memorizing rigid scripts or gaming evaluation systems.

### Quality over quantity

The goal is to build a collection of useful, reliable skills.

A small number of well-designed and tested skills is more valuable than a large catalog of overlapping, unvalidated prompts.

## Versioning and Releases

Skills may evolve independently as their instructions, rubrics, and test coverage improve.

Where practical, individual skills should follow semantic versioning:

- **Patch:** Minor corrections and clarifications that do not materially change intended behavior.
- **Minor:** Backward-compatible additions and improvements.
- **Major:** Significant changes to the interaction contract, scoring criteria, or expected outputs.

Repository releases should document meaningful changes, compatibility considerations, and known limitations.

The project may also provide downloadable archives for individual skills and bundles containing multiple skills.

See [CHANGELOG.md](CHANGELOG.md) for release history when available.

## Compatibility

The repository is designed for portability across AI assistants and agent environments.

However, portability of the source format does not guarantee identical behavior across platforms.

Compatibility may depend on:

- How a platform discovers and loads skills.
- Whether supporting files are available to the model.
- Context-window limitations.
- Tool and integration availability.
- Model capabilities and instruction-following behavior.
- Platform-specific restrictions or configuration.

Platform adapters should remain separate from canonical skill definitions whenever possible.

Compatibility claims should be based on actual testing and should distinguish verified support from expected or unverified support.

## Responsible Use

Interview-preparation skills are intended to support learning, practice, and professional development.

Users should treat generated feedback as coaching guidance rather than a definitive prediction of hiring outcomes.

Contributors should:

- Avoid discriminatory or irrelevant evaluation criteria.
- Use transparent, job-relevant scoring rubrics.
- Avoid presenting subjective judgments as objective facts.
- Avoid including confidential interview materials without authorization.
- Avoid publishing personal or sensitive candidate data.
- Identify third-party material and respect its applicable license.
- Document material limitations that could affect a skill's use.

Skills should help candidates improve their reasoning, communication, and professional judgment.

## License

This project is licensed under the [Apache License, Version 2.0](LICENSE).

You may use, reproduce, modify, and distribute the project's original skills and supporting materials in accordance with the license terms.

See the `LICENSE` file for the full license text.

Third-party materials may be subject to separate license terms.

## Acknowledgments

This project builds on the broader ecosystem of reusable agent skills and open-source collaboration.

We welcome contributors who want to make interview preparation more accessible, practical, and effective.

## Get Involved

Explore the skills, try them in your preferred AI environment, report issues, and contribute improvements.

If you find a skill useful, consider sharing feedback or contributing test cases that help make it better for the next candidate.

**The mission is simple: help people become better interview candidates through deliberate practice, structured feedback, and continuous improvement.**
