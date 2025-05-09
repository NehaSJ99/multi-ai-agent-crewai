## Day 3 : Tools for a Customer Outreach Campaign

### Mental Model for Agent Creation: Goal & Process

When designing an agent in CrewAI, it’s essential to follow a mental model rooted in **clarity of purpose and process**.

### 🎯 Goal
Each agent must have a **specific goal** that defines its purpose in the workflow.
- Example: “Write a friendly support response using accurate and complete information.”

### 🔄 Process
The agent follows a structured process:
1. **Receive the task** (with context, tools, and expected output)
2. **Use tools or memory** to gather information
3. **Reason, format, and generate** a solution
4. **(Optional)** Delegate or collaborate with other agents if allowed

This model ensures that each agent behaves predictably and contributes effectively to the multi-agent system.

---

## 🧰 Key Elements of Agent Tools

### 🔧 Versatile
Tools should work across a wide range of input formats or use cases.
- Example: A search tool should handle both generic and domain-specific queries.
- Why it matters: Flexibility increases reusability and robustness.

### 🛑 Fault-Tolerant
Agents and tools should **fail gracefully**:
- Handle unexpected input or tool failure without crashing
- Use retries or fallback methods
- Example: If a web scraper fails, the agent retries or logs an error for review
- Why it matters: Ensures reliability in real-world applications

### 💾 Cache Memory
For repeated tasks or queries, tools should use cached results when possible:
- Prevents unnecessary API calls or duplicate work
- Reduces token usage in LLM-based tools
- Improves performance and efficiency
- Example: If the same question is asked twice, the tool can serve from memory

---

## 🧱 Creating Tools in CrewAI

### 🔌 Using Built-in Tools

CrewAI provides several built-in tools:

```python
from crewai_tools import DirectoryReadTool, FileReadTool, SerperDevTool

directory_read_tool = DirectoryReadTool(directory='./instructions')
file_read_tool = FileReadTool()
search_tool = SerperDevTool()
