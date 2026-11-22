# Build an Autonomous AI Agent from Scratch (Python, Beginner Friendly)

A free course by **David Oluyale | Agentic AI Hub**.

You build a **research agent** in plain Python, with no framework. You give it a goal, like
*"compare 3 laptops under $800"*, and it works on its own: it plans, searches, calculates, takes notes,
and writes a report.

## Open the notebook

- **Colab:** [Open in Colab](https://colab.research.google.com/github/davolu/autonomous-agent-from-scratch/blob/main/Autonomous_Agent_From_Scratch.ipynb)
- `Autonomous_Agent_From_Scratch.ipynb`: the course notebook (no outputs).
- `Autonomous_Agent_From_Scratch_EXECUTED.ipynb`: the same notebook with the outputs from our recorded run.

## What you build

1. A single AI call, to see what a plain chatbot can and cannot do.
2. Four tools: a search over a small laptop catalog, a safe calculator, and read and write file.
3. The agent loop (goal, think, act, observe, repeat) in about 50 lines.
4. Planning (a to-do list the agent writes for itself) and memory (notes).
5. Guardrails: max steps, a budget cap, and human approval for risky tools.
6. An evaluation: 10 tasks whose answers are computed in Python from the catalog, scored automatically.

In our recorded run the agent passed **10 of 10** evaluation tasks, for a total cost of **$0.00527**
(average 2.2 steps and 1.4 s per task). Your numbers may differ slightly, because model replies vary.

## Setup

1. Get an API key for the model provider used in the notebook.
2. On Colab: open **Secrets** (the key icon), add `ANTHROPIC_API_KEY`, and switch on notebook access.
   On your own computer, set the `ANTHROPIC_API_KEY` environment variable instead.
3. Run the cells from top to bottom. The notebook never prints your key.

```bash
pip install -r requirements.txt
jupyter notebook Autonomous_Agent_From_Scratch.ipynb
```

## Data

`data/laptops.json` holds 24 **made-up** laptops (practice data, not real products or prices).
It plays the role of the web, so every run searches the same data and you can check the answers.
To use real web search, replace `search_products` with a call to a search API and keep the same tool schema.

## Safety notes

- File tools only work inside the `workspace/` folder.
- In `policy` mode, `write_file` is only approved for `.md` files in `reports/`. Set `APPROVAL_MODE = "ask"` to approve each write yourself.
- The calculator parses maths safely and never runs code.
