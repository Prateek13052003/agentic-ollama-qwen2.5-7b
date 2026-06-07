# Local Agentic Airline Assistant

## Overview

Local Agentic Airline Assistant is an Agentic AI project that demonstrates how Large Language Models can interact with external tools and databases to perform real-world tasks autonomously.

The project uses Microsoft AutoGen, Ollama, Qwen2.5:7B, and SQLite to create an AI airline assistant capable of understanding user requests, deciding when external information is required, executing Python tools, querying a local database, and generating natural language responses.

Unlike traditional chatbots, the assistant is capable of autonomous tool calling, making it a practical introduction to Agentic AI systems.

---

## Features

* Autonomous tool calling using Microsoft AutoGen
* Local LLM inference through Ollama
* Airline ticket price lookup from SQLite database
* Function registration and execution
* Agent-to-tool communication workflow
* Natural language response generation
* Fully local execution without OpenAI API

---

## System Architecture

User Query

↓

Qwen2.5:7B Agent

↓

Tool Selection

↓

Python Function Execution

↓

SQLite Database Query

↓

Tool Response

↓

Final Natural Language Answer

---

## Technologies Used

### AI Framework

* Microsoft AutoGen (v0.2.40)

### Large Language Model

* Qwen2.5:7B
* Ollama

### Database

* SQLite3

### Programming Language

* Python 3.9

### Supporting Libraries

* autogen-agentchat
* sqlite3
* python-dotenv

---

## Database Structure

### Table: cities

| Column           | Type |
| ---------------- | ---- |
| city_name        | TEXT |
| round_trip_price | REAL |

Sample Data:

| City      | Price |
| --------- | ----- |
| London    | 299   |
| Paris     | 399   |
| Rome      | 499   |
| Madrid    | 550   |
| Barcelona | 580   |
| Berlin    | 525   |

---

## Agent Workflow

1. User asks for a ticket price.
2. The agent analyzes the request.
3. The agent decides to use the `get_city_price()` tool.
4. AutoGen executes the registered Python function.
5. SQLite returns the requested ticket price.
6. The result is passed back to the agent.
7. The agent generates a human-readable response.

---

## Challenges Faced During Development

### Package Version Conflicts

Initially, AutoGen packages were installed across different Python environments which resulted in import failures and package detection issues.

### Python Environment Mismatch

The system contained multiple Python versions:

* Python 3.9.6
* Python 3.10.11
* Python 3.11.x

Packages were installed using one interpreter while Jupyter Notebook was running another interpreter.

### Docker Configuration Error

AutoGen attempted to execute code through Docker by default and generated runtime errors when Docker execution was not properly configured.

### Tool Registration Issues

The agent successfully suggested tool calls but failed to execute them because the function was not registered correctly with the UserProxyAgent.

### Agent Conversation Loops

The assistant repeatedly generated responses because termination conditions and human input modes were not configured properly.

### Function Signature Warnings

Tool functions initially lacked explicit return type annotations, producing AutoGen validation warnings.

---

## Key Learnings

* Understanding Agentic AI architecture
* Function calling using AutoGen
* Local LLM deployment with Ollama
* Tool registration and execution
* SQLite integration with AI agents
* Agent orchestration workflows
* Multi-agent communication fundamentals

---

## Example Query

User:

```text
What is the round trip ticket price for London?
```

Agent:

```text
The round trip ticket price to London is $299.
```

---

## Future Enhancements

* Flight booking functionality
* Multi-agent collaboration
* Live airline APIs
* RAG integration
* Browser automation
* Travel recommendation engine
* Multi-city trip planning

---

## Author

Prateek Choudhary

Built as part of learning Agentic AI, AutoGen, Local LLMs, Tool Calling, and Autonomous AI Workflows.
