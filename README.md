
# Build AI Agents and Automate Workflows with n8n

This project showcases advanced AI-powered workflow automation built using **n8n**. Developed as a capstone for the LinkedIn Learning course *"Build AI Agents and Automate Workflows with n8n,"* this repository demonstrates how to bridge the gap between large language models (LLMs) and everyday business tools. 

By leveraging n8n's low-code interface, this project features a fully functional AI Slackbot capable of natural language understanding, multi-agent coordination, and seamless two-way data synchronization with Google Sheets.

![n8n](https://img.shields.io/badge/n8n-Workflow_Automation-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)
![AI](https://img.shields.io/badge/AI-Agent_Development-412991?style=for-the-badge&logo=openai&logoColor=white)
![Slack](https://img.shields.io/badge/Slack-Bot_Integration-4A154B?style=for-the-badge&logo=slack&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-Data_API-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)

---

## Table of Contents
- [Project Overview](#-project-overview)
- [Key Features](#-key-features)
- [Technical Architecture](#-technical-architecture)
- [Skills Demonstrated](#-skills-demonstrated)
- [Prerequisites & Setup](#-prerequisites--setup)
- [Usage Examples](#-usage-examples)
- [Course Reference](#-course-reference)

---

## Project Overview

Modern business processes require dynamic, context-aware automation. This project utilizes n8n to build an intelligent AI Agent ecosystem. Instead of rigid, rule-based automation, the workflows utilize natural language processing to interpret user intent, route tasks to the appropriate tools, and execute complex data operations.

The core of this project is an **AI-powered Slackbot** that acts as a virtual assistant. Users can chat with the bot in Slack, asking it to retrieve specific data from Google Sheets, filter results, or append new data—all through conversational prompts.

---
## Screenshots

<img width="600" height="300" alt="Screenshot 2026-07-09 at 23 37 10" src="https://github.com/user-attachments/assets/ea62028b-3854-409e-be1c-1d8beddea49a" />

---
## Key Features

- **Natural Language Slackbot:** Users can send messages to a Slack channel or via DM. The AI agent parses the intent (e.g., "Find all pending invoices for Acme Corp") and responds dynamically.
- **Two-Way Google Sheets Integration:** The agent can both read from and write to Google Sheets. It queries data using advanced filters and formats the output for Slack.
- **Multi-Agent Coordination (MCP):** Implemented an MCP (Multi-Channel Processing) server within n8n, allowing multiple AI agents to share context and utilize a collective toolset for complex task execution.
- **Custom Workflow Components:** Utilized sub-workflows to keep automation modular and maintainable. Used filter nodes and custom logic to ensure precise data processing and error handling.
- **Secure Authentication:** Configured OAuth2 and API key authentication safely for Slack, Google Sheets, and the underlying AI models.

---

## Technical Architecture

The automation flow relies on a modular, event-driven architecture:

1. **Trigger (Slack):** A Slack event listener detects a new mention or DM to the bot.
2. **AI Agent Node:** The message is passed to the main AI Agent. The agent is equipped with a system prompt defining its persona and constraints.
3. **Tool Routing:** The Agent decides which tool to use based on the user's request:
    * *Google Sheets Read Tool:* Fetches rows based on query parameters.
    * *Google Sheets Write Tool:* Appends or updates rows.
    * *Sub-workflow Tool:* Triggers a sub-workflow for multi-step data transformations.
4. **MCP Server:** For complex requests, the agent communicates with the MCP server to delegate sub-tasks to specialized secondary agents.
5. **Response Generation:** The agent formats the retrieved data into a human-readable response and sends it back to Slack via the Slack API.

---

## Skills Demonstrated

This project validates proficiency in the following areas:

| Skill | Description |
| :--- | :--- |
| **n8n Workflow Automation** | Designing complex, low-code automated workflows connecting disparate APIs and services. |
| **AI Agent Development** | Configuring AI agents using models from major vendors (OpenAI, Anthropic, etc.) to process natural language and perform reasoning. |
| **External Integrations** | Securely connecting external platforms (Google Sheets, Slack) for comprehensive data management and communication. |
| **Multi-Agent Coordination** | Creating and managing MCP servers within n8n to enable multi-agent tool usage and task delegation. |
| **Custom Workflow Components** | Building modular sub-workflows, utilizing filter nodes for conditional logic, and developing custom tools tailored to specific business needs. |
| **Slackbot Creation & Auth** | Building AI-powered Slackbots, managing Slack app credentials, and ensuring seamless interaction between users, the bot, and external data sources. |

---

## Prerequisites & Setup

To run these workflows in your own n8n environment, follow these steps:

### 1. Environment Requirements
* An active [n8n instance](https://n8n.io/) (Cloud or Self-Hosted).
* API keys for your preferred LLM provider (e.g., OpenAI API key).
* A Google Cloud account with the Google Sheets API enabled.
* A Slack workspace where you have permission to create apps.

### 2. Cloning the Repository
```bash
git clone https://github.com/khanmol/AI-agents-with-n8n.git
cd AI-agents-with-n8n
```

### 3. Importing the Workflow
1. Locate the workflow JSON file in the `/workflows` directory of this repository.
2. Open your n8n dashboard.
3. Click on **Workflows** > **Import from File**.
4. Upload the JSON file.

### 4. Credential Configuration
Once imported, you will need to configure the credentials for the following nodes:
* **Slack Credentials:** Create a Slack App, assign the necessary bot token scopes (`chat:write`, `app_mentions:read`), and connect the OAuth token in n8n.
* **Google Sheets Credentials:** Set up OAuth2 in your Google Cloud Console and connect the credentials in n8n.
* **AI Model Credentials:** Add your OpenAI (or equivalent) API key to the AI Agent node.

### 5. Activate the Workflow
Toggle the workflow to **Active** in n8n. Mention your new Slackbot in a channel to test the connection!

---

## Usage Examples

Once the bot is running, you can interact with it in Slack like this:

**User:** `@AI_Assistant Show me all clients from New York.`
**Bot:** `I found 3 clients from New York: 1. Acme Corp, 2. Globex, 3. Initech.`

**User:** `@AI_Assistant Add a new client named "Soylent Corp" located in California with status "Lead".`
**Bot:** `Success! I have added "Soylent Corp" to the Client Database spreadsheet.`

---

## Course Reference

This project is a practical implementation of the concepts taught in the LinkedIn Learning course:
**[Build AI Agents and Automate Workflows with n8n](https://www.linkedin.com/learning/build-ai-agents-and-automate-workflows-with-n8n/making-ai-agents-work-for-you?contextUrn=urn%3Ali%3AlyndaLearningPath%3A68add9deb2724c2b3e9b8365&resume=false)**

---

*Feel free to fork this repository, adapt the workflows to your specific business needs, and explore the capabilities of AI-driven automation!*
