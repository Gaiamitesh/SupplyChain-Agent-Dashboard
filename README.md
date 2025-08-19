
# Self-Healing AI Agent for Supply Chain Dashboards

A Langflow + Python prototype of a **self-healing AI agent** that generates supply chain dashboards (Excel + CSV + charts) for KPIs like **Months on Hand (MoH)**, **OTIF**, and **Logistics**.


- 🔄 The agent **validates outputs** (Excel exists, CSV has rows, required KPI columns, charts embedded).
- ♻️ It **repairs and retries** until success (or a max attempt limit).
- 📁 Saves results to a dynamic **`outputs/`** folder under the user-provided base directory.

## Requirements
- Python 3.10+
- Install packages:
  ```bash
  pip install -r requirements.txt
  ```
  (or `pip install pandas openpyxl xlwings`)
- Langflow 0.6+ (import the flow JSON)
- An LLM API key (e.g., OpenAI) set in Langflow **Settings → API Keys**
- Or use Ollama for local

## Quick Start (Web UI only)
1) Put your input **`.csv`** files (e.g., `inventory.csv`, `sales.csv`, `logistics.csv`) into a folder on your machine.
2) In Langflow, load `flows/agent_flow.json` and provide two text inputs:
   - **Agent Instructions** (there is one defaulted, can change if needed)
   - **Folder Path** (the folder from step 1). The agent will create/use `outputs/` inside it.
3) Start the chat: e.g., “Create a MoH dashboard” / “Build a Logistics dashboard” / “Make an OTIF summary”.
4) The agent runs Python, validates results, and retries automatically.
5) Find the outputs under **`<your-folder>/outputs/`**.

## Notes
- All inputs **must be `.csv`** files.
- Update file paths via the **Folder Path** input — do **not** hard-code paths in the prompt.


## Repo Layout
```
supplychain-agent-dashboard/
├── README.md
├── flows/
│   └── agent_flow.json        
├── examples/
│   ├── screenshots/
│   │   
│   └── README.txt
├── outputs/                   
├── requirements.txt
├── .gitignore
└── LICENSE
```


