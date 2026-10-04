# Safeguarded Data-Analyst Agent for the Palmer Penguins Dataset

A single, semi-autonomous agent that answers plain-English questions about 344 Antarctic penguins. It plans one to six steps, calls six read-only tools, keeps a four-turn working memory, refuses out-of-scope requests, asks for clarification when a question is ambiguous, and writes an audit log of every decision.

## Contents

- `agentic_system.ipynb`: the agent, example runs, safeguard stress tests, a 28-task evaluation and the notebook summary (executed, outputs included).
- `Agentic_AI_Systems_Analysis_Report.pdf`: the analysis report with architecture diagram, design documentation, evaluation, ethics and references.
- `requirements.txt`: output of `pip freeze` from the environment used.
- `data/`: the dataset and access instructions.
- `figures/`: architecture diagram, pass-rate chart and plots produced by the agent.
- `logs/`: JSON-lines audit logs written during the run.

## Reasoning engine

The planner is an explicit rule-based Python program, fully executed in the notebook. An optional `OpenAIPlanner` is included behind the same interface but was **not executed** because no credentials were available. To try it, run `pip install openai`, set the `OPENAI_API_KEY` environment variable, and pass the planner to the agent. The validator, step budget and read-only tools apply to either planner.

## Results

27 of 28 test tasks passed. The failing task is a paraphrase ("Is there any link between mass and flippers?") that the rule-based planner misreads; it is documented as the failure case in the notebook and report.

## Run

```
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace agentic_system.ipynb
```
