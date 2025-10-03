# How to Create Agentic AI with the Google Agent Development Toolkit (ADK)

This document provides a step-by-step guide on how to build agentic AI systems using the materials and examples in this GitHub repository. The process progresses from creating a simple, single-purpose agent to orchestrating a complex, multi-agent system. Each step references the specific notebook where the concept is demonstrated.

---

### Step 1: Create a Basic LLM Agent

The foundation of any agentic system in the ADK is the `Agent`. This is a core LLM agent whose behavior is defined by natural language instructions.

- **What to do:** Define a simple agent by specifying its `name`, the `model` it should use (e.g., `gemini-2.0-flash`), and a detailed `instruction` prompt that tells the agent how to behave.
- **Purpose:** This first step allows you to create a standalone AI that can understand and respond to user queries based on its instructions. It's the fundamental building block for all more complex systems.
- **Relevant Notebooks:**
    - `01_03.ipynb`: Shows the most basic implementation of a "greeting_agent".
    - `02_03.ipynb`: Demonstrates a more practical `packing_list_agent` that follows structured instructions.

---

### Step 2: Empower Your Agent with Tools

To make an agent truly useful, it needs to interact with the outside world. This is done by giving it "tools."

- **What to do:** Add a `tools` parameter to your `Agent` definition. You can use built-in tools, create your own Python functions, or integrate third-party tools.
- **Purpose:** Tools allow your agent to perform actions like searching the web, calling an external API, or running a specific calculation, moving beyond simple text generation.
- **Relevant Notebooks:**
    - `03_01.ipynb`: Demonstrates how to use the built-in `google_search` tool.
    - `03_02.ipynb`: Teaches you how to create custom Python functions (e.g., for a live weather API) and provide them to your agent as tools.
    - `03_03.ipynb`: Shows how to integrate and wrap a third-party tool from the LangChain ecosystem (Tavily Search) for use within ADK.

---

### Step 3: Orchestrate Multiple Agents in a Sequence

For complex tasks, a single agent may not be enough. You can chain agents together to create a workflow where the output of one agent becomes the input for the next.

- **What to do:** Use the `SequentialAgent` to define a list of sub-agents that should run in a specific order. You use `output_key` on a sub-agent to name its output, which can then be referenced in the instruction of the next agent (e.g., `{itinerary}`).
- **Purpose:** This allows you to break down a complex problem into smaller, manageable steps, with each agent specializing in one part of the task.
- **Relevant Notebook:**
    - `02_04.ipynb`: Shows how to create a workflow where an `itinerary_agent` runs first, and its output is then used by a `packing_list_agent`.

---

### Step 4: Run Agents Concurrently for Efficiency

Some tasks don't need to happen in order. You can run multiple agents at the same time to gather information more efficiently.

- **What to do:** Use the `ParallelAgent` to define a list of sub-agents that should run simultaneously. This is often combined with a `SequentialAgent` that waits for all parallel tasks to complete before processing their combined results.
- **Purpose:** This is useful for workflows where you need to gather different types of information independently (e.g., finding events and planning an itinerary) before combining them.
- **Relevant Notebook:**
    - `04_02.ipynb`: Demonstrates running an `itinerary_agent` and a `latest_events_agent` in parallel, and then passing both of their outputs to a final `personalizer_agent`.

---

### Step 5: Build a Stateful Agent with Conversational Memory

To create a natural conversational experience, your agent needs to remember what was said in previous turns.

- **What to do:** Design your custom tools to accept a `tool_context` parameter. Inside the tool, you can read from and write to the `tool_context.state` dictionary. This state is persistent across a user's session.
- **Purpose:** This gives your agent memory, allowing it to handle follow-up questions without the user having to repeat information (e.g., remembering the last city the user asked about).
- **Relevant Notebook:**
    - `04_05.ipynb`: Shows how to create a stateful "Weather Agent" that remembers the user's preferred temperature unit and the last city checked.

---

### Step 6: Create a Coordinator Agent with LLM-Based Routing

This is the most advanced step, where you build a "master" agent that intelligently delegates tasks to other agents.

- **What to do:** Create a top-level "Coordinator Agent". Instead of giving it simple instructions, you provide it with a set of tools that are actually wrapper functions for your other specialized agents. The Coordinator's instructions then guide its LLM to analyze the user's query and decide which sub-agent(s) to call and in what order.
- **Purpose:** This creates a highly flexible and powerful system that can handle a wide variety of user intents. Instead of being locked into a fixed workflow, the Coordinator can dynamically create a plan to solve the user's request.
- **Relevant Notebook:**
    - `04_06.ipynb`: Provides a full implementation of a `wanderwise_coordinator_agent` that orchestrates the itinerary, events, weather, and packing list agents based on the user's needs.