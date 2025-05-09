# Day 2: Multi-agent Customer Support Automation

This notebook demonstrates how to build a **multi-agent AI system** to automate customer support using [CrewAI](https://crewai.com). The system includes role-based agents, task-specific tools, memory integration, and quality assurance through agent cooperation.

---

## Agents

### 1. **Senior Support Representative**

- **Role:** Provides friendly and thorough customer support.
- **Focus:** Deliver full and accurate answers.
- **Cooperation:** Delegation disabled (`allow_delegation=False`) to ensure this agent completes the task independently.

### 2. **Support Quality Assurance Specialist**

- **Role:** Reviews support responses for quality and completeness.
- **Focus:** Ensure standards are met.
- **Cooperation:** Delegation allowed by default (can collaborate if needed).

Agents are defined with:
- **Role, Goal, Backstory** (Role Playing)
- **Defined Tasks** (Focus)
- **Delegation Behavior** (Cooperation)

---

## Tools Used:

```python
search_tool = SerperDevTool()
scrape_tool = ScrapeWebsiteTool()
docs_scrape_tool = ScrapeWebsiteTool(
  website_url="https://docs.crewai.com/how-to/Creating-a-Crew-and-kick-it-off/"
)
```

> **Tool Assignment**
- **Agent-level:** Available on any task the agent performs
- **Task-level:** Only available for specific tasks (overrides agent tools)

---

## Tasks

### 1. Inquiry Resolution

- **Assigned to:** Senior Support Representative
- **Goal:** Respond to a customer inquiry completely and helpfully
- **Tools:** `docs_scrape_tool` (Task-level)
- **Expected Output:** Informative, friendly, and reference-backed response

### 2. Quality Assurance Review

- **Assigned to:** QA Specialist
- **Goal:** Review the draft for completeness, accuracy, and tone
- **Tools:** None
- **Expected Output:** Final improved version, ready to be sent to the customer

---

## Crew Assembly & Memory

```python
crew = Crew(
  agents=[support_agent, support_quality_assurance_agent],
  tasks=[inquiry_resolution, quality_assurance_review],
  verbose=2,
  memory=True  # Enables short-term memory for agents
)
```

>  **Memory** is important to maintain context between agents and across task execution.

---

## Running the Crew

```python
inputs = {
  "customer": "DeepLearningAI",
  "person": "Andrew Ng",
  "inquiry": "I need help with setting up a Crew and kicking it off, specifically how can I add memory to my crew? Can you provide guidance?"
}

result = crew.kickoff(inputs=inputs)
```

This will trigger agent collaboration, resolve the inquiry, and review it with QA. Outputs may vary due to LLM nondeterminism.

---

## Guardrails

Agents operate within predefined roles and tasks, ensuring responses are:
- Friendly yet professional
- Complete and accurate
- Within scope (prevent hallucinations or irrelevant answers)

## Key Concepts Demonstrated

Understanding these core components helps design effective, safe, and collaborative AI agent systems using CrewAI or similar frameworks.

| Element        | Description                                                                 |
|------------------|---------------------------------------------------------------------------------|
| **Role Playing**  | Assigns identity to guide behavior and align with specific goals.              |
| **Focus**         | Narrows the agent’s task scope for higher accuracy and clarity.                |
| **Tools**         | Integrates external capabilities like APIs, file readers, or calculators.      |
| **Cooperation**   | Enables task sharing and delegation across multiple agents.                    |
| **Guardrails**    | Applies rules and constraints to prevent misuse, hallucination, or failure.    |
| **Memory**        | Maintains context across steps for continuity, learning, and smarter output.   |

Each element plays a vital role in making agents more useful, controllable, and capable of solving complex real-world problems collaboratively.
