# Multi-Agent Conversational Architectures for Automated Prompt Engineering

Code for my MSc research project on using multi-agent LLM systems to automate prompt optimisation.

This project studies whether structured multi-agent interaction can improve prompts for downstream tasks more effectively than standard prompting baselines. It evaluates three architectures:

- **Authoritarian**
- **Market-Based**
- **Hierarchical**

The frameworks optimise prompts for benchmark tasks by assigning agents distinct roles, prompting principles, and evaluation responsibilities.

## Overview
The project explores whether conversational coordination between agents can produce stronger prompts and reveal useful prompt-engineering strategies.

Benchmarks used in this project include:
- **GSM8K** for mathematical reasoning
- **SST-2** for sentiment analysis
- **HumanEval** for code generation

Generated prompts are evaluated with:
- **GPT-3.5-Turbo**
- **Mistral-v0.3-7B**
- **Llama-3.1-8B**

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

## What this repo contains
- framework implementations for prompt optimisation
- evaluation workflows for multiple benchmarks
- conversation logs for analysing agent behaviour
- raw outputs used in the project analysis
- utilities for testing and significance analysis

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

### 3. Configure API keys
Create a `.env` file and add the required provider keys.

Example:
```bash
OPENAI_API_KEY=...
ANTHROPIC_API_KEY=...
```

## Running the frameworks
The optimisation workflows are implemented in notebooks under `src/algorithms/`.

Typical workflow:
1. choose a task
2. define the base prompt and success criteria
3. select the multi-agent architecture
4. run optimisation
5. evaluate the resulting prompt on the target benchmark

To adapt the framework to a new task:
- add or modify agents in `agent_suite.py`
- define the new task prompt and optimisation criteria
- update the relevant notebook to use the new configuration

## Evaluation
Evaluation notebooks are in `src/tests/`.

- **HumanEval**: use the HumanEval evaluation workflow
- **GSM8K / SST-2**: use the PromptBench-based workflow
- **Conversation analysis**: use the conversational-analysis notebook to inspect optimisation logs

## Outputs
The `src/outputs/` directory contains:
- raw outputs from model evaluations
- selected high-performing agent conversations
- result visualisations used in the project analysis

## Main findings
This project supports three main conclusions:
- prompt optimisation effectiveness depends on both the multi-agent architecture and the inference model
- structured agent interaction can improve prompts for reasoning, sentiment, and code tasks relative to standard baselines in selected settings
- conversation logs from high-performing runs provide useful evidence about how agents critique, refine, and validate prompts

## Scope and limitations
This repository is research code produced for an MSc project. It is intended to support experimentation and analysis rather than provide a polished general-purpose package.

## Related work
This repository accompanies the MSc thesis:

**Multi-Agent Conversational Architectures to Automate Prompt Engineering**
