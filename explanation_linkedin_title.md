# Explanation of Notebooks by LinkedIn Learning Course Structure

This document maps the Jupyter notebooks in this repository to the specific chapters and sections of the LinkedIn Learning course, "Hands-On AI: Building Agents with Google's Agent Development Toolkit (ADK)". It provides a clear guide on which notebook corresponds to each part of the course content.

---

## 3. Empowering Agents: Tools and Integrations

### ADK's built-in toolbox: Essential capabilities for your agents
- **Notebook:** `03_01.ipynb`
- **Summary:** This notebook focuses on the practical use of ADK's built-in tools, with `google_search` as the primary example. It demonstrates how to build an agent that can fetch and process live data from the web to find and summarize current events.

### Function tools: Tailoring agent actions with Python
- **Notebook:** `03_02.ipynb`
- **Summary:** This notebook teaches how to create and integrate custom Python functions as tools for an agent. The example builds a "Weather Agent" that uses custom functions to interact with the external OpenWeatherMap API to fetch live weather data.

### Expanding horizons: Integrating third-party tools and live data
- **Notebook:** `03_03.ipynb`
- **Summary:** This notebook demonstrates how to integrate third-party tools into the ADK framework, specifically using the Tavily Search API via LangChain. It shows how to wrap a LangChain tool to make it compatible with an ADK agent for advanced web search capabilities.

### Leveraging Google Cloud: Native ADK integrations and secure services
- **Notebook:** Not available in this repository.
- **Summary:** This topic is discussed in the course but does not have a corresponding hands-on notebook in this repository.

### Tool design: Best practices for reliable and secure ADK agents
- **Notebook:** Not available in this repository.
- **Summary:** This topic is discussed in the course but does not have a corresponding hands-on notebook in this repository.

---

## 4. Orchestrating Multi-Agent Systems and Context

### Hierarchical designs: Delegation, routing, and orchestration
- **Notebooks:** `02_04.ipynb`, `04_02.ipynb`, `04_06.ipynb`
- **Summary:** This concept is demonstrated through several notebooks. `02_04.ipynb` introduces sequential orchestration. `04_02.ipynb` shows how to run agents concurrently. `04_06.ipynb` combines these concepts into a master "Coordinator Agent" that uses LLM-based routing to dynamically delegate tasks to sub-agents.

### Parallel agents: Concurrent execution for enhanced efficiency
- **Notebook:** `04_02.ipynb`
- **Summary:** This notebook introduces the `ParallelAgent`, which allows for the concurrent execution of multiple sub-agents. It demonstrates a workflow where an `itinerary_agent` and a `latest_events_agent` run simultaneously to gather information efficiently.

### Loop agents: Iterative processes and refinement
- **Notebook:** Not available in this repository.
- **Summary:** This topic is discussed in the course but does not have a corresponding hands-on notebook in this repository.

### Conversational blueprint: Understanding session, state, and memory
- **Notebook:** `04_05.ipynb`
- **Summary:** This notebook provides a deep dive into how conversational context is managed in ADK. It explains the roles of session, state, and memory in creating stateful agents that can remember information across multiple turns.

### Context-aware agents: Practical session and state management
- **Notebook:** `04_05.ipynb`
- **Summary:** This notebook demonstrates how to build a stateful "Weather Agent" that uses `tool_context.state` to remember the last city checked and the user's temperature preference. This allows the agent to handle follow-up questions naturally without requiring the user to repeat information.

### Putting it all together: Advanced multi-agent orchestration with a coordinator
- **Notebook:** `04_06.ipynb`
- **Summary:** This capstone notebook integrates all the concepts from the course. It builds a master "Coordinator Agent" that uses LLM-based routing to analyze user queries and dynamically call a suite of specialized sub-agents for itinerary planning, event searching, weather lookups, and packing list generation.

---

## 5. Advanced Agents: Persistent Artifacts and Lifecycle Callbacks

This chapter is discussed in the course but does not have corresponding hands-on notebooks in this repository.
- **Artifacts: Giving agents lasting, versioned memory**
- **Data artifacts: Best practices for naming, versioning, and namespaces**
- **Callbacks: Customizing the agent lifecycle with precision hooks**

---

## 6. Productionizing Agents: Deployment, Evaluation & Responsible AI

This chapter is discussed in the course but does not have corresponding hands-on notebooks in this repository.
- **Deploying agents: Agent Engine, Cloud Run, and GKE**
- **Operational excellence: Security, monitoring, and observability**
- **Agent quality: Trajectory analysis and response evaluation**
- **Responsible agents: Upholding safety, ethics, and trust**