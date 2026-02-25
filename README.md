# 💸 AI Expense Agent with Azure AI Foundry

An AI-powered expense claim agent built using **Azure AI Foundry**, **GPT-4.1**, and the **agent-framework** library. The agent reads expense data from a file, processes it, and autonomously submits a formatted expense claim email — no manual input required beyond a single prompt.

## 🚀 What It Does

1. Loads expense data from a local `.txt` file
2. Asks the user what to do with it
3. Agent autonomously creates an itemized expense claim
4. Calls a custom tool function to "submit" the claim via email
5. Confirms submission to the user

**Example output:**
```
To: expenses@contoso.com
Subject: Expense Claim
Expense Claim Submission:

Date: 07-Mar-2025
- Taxi: $24.00
- Dinner: $65.50
- Hotel: $125.90

Total: $215.40

# Agent:
Your expense claim has been submitted to expenses@contoso.com with an itemized list and total.
```

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Azure AI Foundry | AI project infrastructure & model deployment |
| GPT-4.1 | Language model powering the agent |
| agent-framework | Microsoft's agent orchestration library |
| AzureCliCredential | Secure Azure authentication |
| Python AsyncIO | Async runtime for agent execution |
| Pydantic | Tool parameter validation |

## 📁 Project Structure

```
ai-expense-agent/
├── agent-framework.py    # Main agent code
├── data.txt              # Sample expense data (CSV format)
├── requirements.txt      # Python dependencies
└── .env                  # Azure credentials (not committed)
```

## ⚙️ Setup & Running Locally

### Prerequisites
- Python 3.12+
- Azure subscription with AI Foundry access
- Azure CLI authenticated (`az login`)

### Install dependencies
```bash
python -m venv labenv
source labenv/bin/activate
pip install -r requirements.txt
```

### Configure environment
Create a `.env` file:
```
PROJECT_ENDPOINT=https://your-project.services.ai.azure.com/api/projects/your-project
MODEL_DEPLOYMENT_NAME=gpt-4.1
```

### Run the agent
```bash
python agent-framework.py
```

## 💡 How It Works

The agent uses a **custom tool function** decorated with `@tool` that simulates sending an email. When the user prompts the agent to submit expenses, the agent:

1. Parses the expense data autonomously
2. Decides to call the `submit_claim` tool
3. Passes structured parameters (to, subject, body) to the tool
4. The tool prints the formatted email and confirms submission

This demonstrates **agentic tool use** — the model doesn't just generate text, it makes decisions and takes actions through function calls.

## 🔗 Related Projects

- [AI Inventory Agent](https://github.com/jar702-shippuden/ai-inventory-agent) — MCP-based inventory management agent

---

*Built with Azure for Students subscription | Spring 2026*
