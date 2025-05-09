# multi-ai-agent-crewai

This repository documents my learning journey with **Crew AI**, a powerful framework for building and orchestrating multiple AI agents to solve complex tasks in a structured, collaborative way.

## Introduction to Multi-Agent Systems

### What are Agents?
Agents are autonomous AI units with assigned roles and tasks. Each agent can use tools and reasoning to achieve specific objectives.

### Task → Agent → Answer (using Tools)
- **Task** defines the objective
- **Agent** is assigned to complete it
- **Tools** help the agent retrieve or generate information to fulfill the task

### What is a Multi-AI Agent System?
A system where multiple agents collaboratively solve different parts of a larger problem. Each agent can operate independently, focusing on its assigned task.

### Benefits of Multi-Agent Systems
1. Each agent can focus on **a single responsibility**, improving clarity and performance.
2. Agents can run on **different LLMs**, leveraging their respective strengths.

### What is Crew AI?
Crew AI is a framework that:
- Breaks down complex workflows into modular, **simple structures**
- Provides a **standard pattern** to organize agent systems
- Offers **built-in tools and skills** ready for use by agents
- Helps bring multi-agent systems to **production environments**

### Core Components
- **Agents**: Define roles, goals, backstory, delegation rules, and verbosity.
- **Tasks**: Describe the job, expected output, and assign it to an agent.
- **Crew**: A group of agents assigned to complete a workflow of tasks.
