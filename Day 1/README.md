## 📅 Day 1: Creating a Multi-Agent Workflow

### 📝 Objective
Use Crew AI to **create agents that research and write an article collaboratively**.

### 🧩 Steps

1. **Create Agents**
   - Define role (e.g., Researcher, Writer)
   - Define goal (e.g., "Search for latest papers on X")
   - Provide a backstory to give agents context
   - Set options: `allow_delegation`, `verbose`, etc.

2. **Define Tasks**
   - Add a clear `description` of what each task entails
   - Define the `expected_output`
   - Assign each task to the appropriate agent

3. **Create Your Crew**
   - Initialize a crew by combining the agents
   - Pass in the list of tasks

4. **Run the Crew**
   - Execute the crew to see agents collaborating and completing tasks

---

Stay tuned for more updates as we explore advanced agent behaviors, delegation, memory sharing, and LLM integrations!
