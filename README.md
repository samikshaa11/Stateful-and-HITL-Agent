MetaAgent: Stateful and Human-in-the-Loop (HITL) Agent

MetaAgent is an advanced conversational AI framework built with LangChain and Azure OpenAI, capable of creating and managing multiple agents, maintaining conversation history, and integrating with popular project management tools like Asana, Jira, and ClickUp. It also supports real-time state tracking, human-in-the-loop approval, and notifications via console or email.

Features

Multi-Agent Management: Create, delete, and switch between multiple agents dynamically.

Conversation History: Logs all interactions with timestamps, speakers, and context type.

Human-in-the-Loop Approval: Approve, skip, rephrase, or log human-only messages before sending to AI.

Project Management Tool Integration:

Fetch tasks from Asana projects

Fetch issues from Jira projects

Fetch tasks from ClickUp lists

Real-Time LLM State Tracking: Tracks whether the AI is Listening, Active, or in Error state.

Notifications: Sends alerts via console or email.

Async Input Support: Handles input asynchronously with timeout handling.

Installation

Clone the repository:

git clone <repository-url>
cd metaagent

Install dependencies:

pip install -r requirements.txt

Install additional SDKs for project management APIs:

pip install asana atlassian-python-api requests pydantic langchain langchain-openai
Environment Variables

Create a .env file or set the following environment variables:

# Azure OpenAI
AZURE_OPENAI_API_KEY=<your_openai_key>
AZURE_OPENAI_ENDPOINT=<your_azure_endpoint>
AZURE_OPENAI_DEPLOYMENT_NAME=<your_deployment_name>
OPENAI_API_VERSION=<api_version>

# Project Management Tokens
ASANA_TOKEN=<your_asana_token>
JIRA_URL=<your_jira_url>
JIRA_USER=<your_jira_username>
JIRA_API_TOKEN=<your_jira_api_token>
CLICKUP_TOKEN=<your_clickup_token>

# Email Notifications (optional)
EMAIL_SENDER=<sender_email>
EMAIL_PASSWORD=<email_password>
EMAIL_RECEIVER=<receiver_email>
Usage

Run the main interactive loop:

python metaagent.py
Commands

create agent <name> [with prompt] [with memory] – Creates a new agent.

delete agent <name> – Deletes an existing agent.

use <name>: <message> – Sends a message to a specific agent.

list agents – Lists all created agents.

history – Displays conversation history.

quit – Exits the program.

Human Approval Options

When sending a message to an agent, you can choose:

y – Send the message

n – Skip

r – Rephrase message

c – Cancel

h – Log message as human-only

Architecture

LLM Integration: Uses AzureChatOpenAI via LangChain with streaming and callbacks.

Conversation Models: Stores ConversationEntry and ConversationHistory using Pydantic.

Tool Integration: Supports dynamic tools for Echo, Recall, Asana, Jira, and ClickUp.

MetaAgent Manager: Central controller for managing agents and handling requests.

Notifier: Handles console and email notifications.

Real-Time State: Tracks AI state transitions and prints status updates.

Notes

Agents are initialized with optional memory (ConversationBufferMemory) and optional custom prompt support.

Supports asynchronous input with timeout handling.

Human-in-the-loop ensures safety and relevance of AI responses.

LangChain agent deprecation warnings may appear; consider migrating to LangGraph for future projects.
