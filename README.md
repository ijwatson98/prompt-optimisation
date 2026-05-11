# Multi-Agent Conversational Architectures for Automated Prompt Engineering

Research code for an MSc project on using multi-agent LLM systems to automate prompt optimisation.

## Overview
This repository investigates whether structured conversational coordination between agents can improve prompt performance relative to standard prompting baselines.

The project evaluates three prompt-optimisation architectures:
- **Authoritarian**
- **Market-Based**
- **Hierarchical**

The frameworks are applied to benchmark tasks in:
- **mathematical reasoning**
- **sentiment analysis**
- **code generation**

using:
- **GSM8K**
- **SST-2**
- **HumanEval**

Generated prompts are evaluated with:
- **GPT-3.5-Turbo**
- **Mistral-v0.3-7B**
- **Llama-3.1-8B**

## Research question
Can structured multi-agent prompt optimisation improve prompt performance relative to standard prompting approaches, and do the effects depend on the optimisation architecture and inference model?

## Main findings
- Prompt optimisation effectiveness depended on both the multi-agent architecture and the inference model.
- Structured agent interaction could improve prompts relative to standard baselines, though effectiveness depended strongly on the optimisation architecture, benchmark task, and inference model.
- Conversation logs from high-performing runs provided useful evidence about how agents critique, refine, and validate prompts.

## What this repo contains
- implementations of three multi-agent prompt-optimisation frameworks
- evaluation workflows for multiple benchmarks
- conversation logs for analysing agent behaviour
- raw outputs and artefacts used in the project analysis
- notebooks for testing and significance analysis

## Repository structure

```text
.
├── diagrams/               # Diagrams of the optimisation frameworks
├── human-eval/             # Forked HumanEval repository
├── promptbench/            # Forked PromptBench repository
├── src/
│   ├── algorithms/         # Notebooks implementing each framework
│   ├── conversations/      # Conversation logs from optimisation runs
│   ├── outputs/            # Raw evaluation outputs and selected analyses
│   ├── prompts/            # Base prompts, optimised prompts, and criteria
│   ├── tests/              # Evaluation and significance-testing notebooks
│   └── agent_suite.py      # Agent definitions used by the frameworks
├── Dockerfile
├── requirements.txt
└── README.md
```

## Setup

### 1. Clone the repository
```bash
git clone https://github.com/ijwatson98/prompt-optimisation.git
cd prompt-optimisation
```

### 2. Create an environment
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 3. Configure required credentials
Create a local `.env` file and add the required provider keys.

Example:
```bash
OPENAI_API_KEY=...
ANTHROPIC_API_KEY=...
```

## Running the code
The optimisation workflows are implemented in notebooks under `src/algorithms/`.

Typical workflow:
1. choose a task
2. define the base prompt and optimisation criteria
3. select the multi-agent architecture
4. run the optimisation notebook
5. evaluate the resulting prompt on the target benchmark

To adapt the framework to a new task:
- add or modify agents in `agent_suite.py`
- define the task prompt and optimisation criteria
- update the relevant notebook configuration

## Evaluation
Evaluation notebooks are in `src/tests/`.

- **HumanEval**: HumanEval-based evaluation workflow
- **GSM8K / SST-2**: PromptBench-based evaluation workflow
- **Conversation analysis**: notebooks for inspecting optimisation logs and selected high-performing runs

## Outputs
The `src/outputs/` directory contains:
- raw outputs from model evaluations
- selected high-performing agent conversations
- result visualisations used in the project analysis

## Scope
This repository is research code produced for an MSc project. It is intended to support experimentation and analysis rather than provide a polished general-purpose package.

## Related output
This repository accompanies the MSc thesis:

**Multi-Agent Conversational Architectures to Automate Prompt Engineering**
