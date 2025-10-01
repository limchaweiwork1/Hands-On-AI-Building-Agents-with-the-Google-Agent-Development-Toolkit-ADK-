# Explanation of Notebooks for "Hands-On AI: Building Agents with Google's Agent Development Toolkit (ADK)"

This document provides a detailed explanation of the Jupyter notebooks included in this repository. Each notebook corresponds to a lesson in the LinkedIn Learning course "Hands-On AI: Building Agents with Google's Agent Development Toolkit (ADK)" and is designed to provide hands-on experience with the concepts taught in the course.

## Notebook Summaries

### `01_03.ipynb`: ADK First Steps: Quickstart

This notebook serves as the entry point into the ADK. It covers the fundamental steps required to get started with building agents.

- **Installation and Setup:** It begins by guiding the user through the installation of the `google-adk` package and verifying the installation.
- **Environment Configuration:** It shows how to configure the environment to use the Gemini API, specifying the model to be used.
- **Agent Definition:** The core of this notebook is the definition of a simple "greeting_agent." This agent is instructed to respond with a warm greeting in the same language as the user's input. This demonstrates the basic structure of an `Agent` object, including its `name`, `model`, `description`, and `instruction`.
- **Agent Interaction:** The notebook introduces a modular function, `run_adk_agent_interaction`, to handle the communication with the agent. This function showcases the use of `Runner` and `InMemorySessionService` to manage agent execution and conversation state.
- **Testing:** Finally, it runs a series of test cases with greetings in different languages to demonstrate the agent's functionality and its adherence to the instructions.

### `02_03.ipynb`: LLM Agents in Google ADK: Packing List & Itinerary Example

This notebook dives deeper into creating more complex and practical agents. It introduces two distinct agents: a `packing_list_agent` and an `itinerary_agent`.

- **`packing_list_agent`:** This agent is designed to generate a detailed packing list for a trip. Its instructions guide it to ask clarifying questions about the user's travel plans (destination, duration, activities) and to format the output in a structured Markdown format.
- **`itinerary_agent`:** This agent takes the concept a step further by integrating a tool: `google_search`. It is instructed to create a travel itinerary, using the search tool to find up-to-date recommendations for attractions, restaurants, and activities. This demonstrates how to equip agents with tools to access external information.
- **Tool Integration:** The notebook explicitly shows how to import and assign the `google_search` tool to the `itinerary_agent`, enabling it to perform web searches to fulfill the user's request.
- **Practical Application:** By running both agents, the notebook illustrates how LLM agents can be used to build powerful, real-world applications like a travel assistant.

### `02_04.ipynb`: Workflow Agents in Google ADK: Itinerary-Driven Packing List Example

Building on the previous notebook, this one introduces the concept of `SequentialAgent` to create a workflow where agents work together in a chain.

- **`SequentialAgent`:** This is the key concept of the notebook. It demonstrates how to create a `SequentialAgent` that chains the `itinerary_agent` and the `packing_list_agent` together.
- **Workflow Logic:** The workflow is designed to first generate a travel itinerary and then use that itinerary as input to generate a tailored packing list. This is achieved by using an `output_key` in the `itinerary_agent` and referencing it in the `packing_list_agent`'s instruction prompt.
- **Agent Orchestration:** This notebook showcases how to orchestrate a multi-agent system where the output of one agent becomes the input for the next, creating a logical and powerful workflow.
- **End-to-End Example:** It provides a complete example of a travel planning assistant that first plans the trip and then helps the user pack for it, all in a single, automated sequence.

### `03_01.ipynb`: ADK's Built-in Toolbox: The Foundation

This notebook focuses on the practical use of ADK's built-in tools, with `google_search` as the primary example. It demonstrates how to build an agent that can fetch and process live data from the web.

- **Tool-Equipped Agent:** The notebook centers around creating a `latest_events_agent`. This agent's purpose is to find and summarize information about current or upcoming events based on a user's query.
- **Detailed Instructions:** It emphasizes the importance of providing detailed and structured instructions to the agent. The instructions for the `latest_events_agent` specify how to identify key information, formulate search queries, prioritize official sources, and format the output in a clean, readable Markdown structure.
- **Handling Ambiguity:** The instructions also guide the agent on how to handle vague user queries (e.g., "what's happening soon?") and what to do if no relevant results are found.
- **Robust Testing:** The notebook includes a comprehensive set of test cases to validate the agent's performance. These tests cover various scenarios, including normal cases, specific queries, vague timeframes, multiple event types, and queries that are expected to yield no results. This highlights the importance of thorough testing for tool-using agents.

### `03_02.ipynb`: Function Tools: Building Custom Actions

This notebook teaches how to create and integrate custom tools, allowing agents to perform actions beyond the built-in capabilities, such as interacting with external APIs.

- **Custom Tool Creation:** It walks through the process of defining a Python function that can be used as a tool by an ADK agent.
- **API Integration:** The example focuses on building a "Weather Agent" that uses custom tools (`get_current_weather_from_openweather` and `get_weather_summary_from_openweather`) to fetch data from the live OpenWeatherMap API. This demonstrates how agents can interact with external services.
- **Flexible Input Handling:** It introduces a helper function, `parse_flexible_date_range`, to interpret natural language date expressions (e.g., "tomorrow," "next weekend"), making the agent more intuitive and user-friendly.
- **Agent Instruction for Tools:** The agent's instructions are crafted to guide it on when to use each specific weather tool based on whether the user is asking for the current weather or a forecast.

### `03_03.ipynb`: Third-Party Tools: Expanding Horizons with Tavily and Google ADK

This notebook demonstrates how to expand an agent's capabilities by integrating third-party tools, specifically using the Tavily Search API through LangChain.

- **Third-Party Library Integration:** It shows how to install and use libraries from the LangChain ecosystem (`langchain_community`, `tavily-python`) within the ADK framework.
- **ADK Tool Wrapper:** It introduces the `LangchainTool` wrapper, a key utility for making tools from other frameworks, like LangChain, compatible with ADK agents.
- **Tavily Search Agent:** The notebook builds a `latest_events_agent` that uses the `TavilySearchResults` tool to perform advanced web searches, providing the agent with powerful, up-to-date information retrieval capabilities.
- **Advanced Agent Instructions:** The agent's instructions are refined to be highly specific, including rules for filtering search results by location and formatting the output, ensuring the agent's responses are accurate and clean.

### `04_02.ipynb`: Parallel Agents in Google ADK: Concurrent Task Execution

This notebook introduces the `ParallelAgent`, which allows for the concurrent execution of multiple sub-agents, making workflows more efficient.

- **`ParallelAgent`:** This is the central concept, showing how to define an agent that runs a list of sub-agents simultaneously.
- **Workflow Composition:** It demonstrates a more complex workflow by composing `ParallelAgent` and `SequentialAgent`. A `gather_info_agent` runs the `itinerary_agent` and `latest_events_agent` in parallel.
- **Data Aggregation:** The outputs from the parallel tasks are then passed to a `personalizer_agent` within a sequential workflow. This agent's job is to synthesize the information from the parallel agents into a single, cohesive output.
- **Efficient Orchestration:** This illustrates a powerful pattern for building multi-agent systems where independent sub-tasks can be performed at the same time before their results are merged and processed.

### `04_05.ipynb`: Conversational Context: Building Stateful Agents

This notebook focuses on creating stateful agents that can remember information across multiple turns in a conversation, leading to more natural and intelligent interactions.

- **Stateful Tools:** It demonstrates how to make custom tools "stateful" by giving them access to a `tool_context.state` object. This allows tools to read and write to a persistent session state.
- **Example Weather Agent:** The "Weather Agent" is enhanced to remember the `last_city_checked_stateful` and the user's preferred temperature unit (`user_preference_temperature_unit`).
- **Contextual Interactions:** The agent can now handle follow-up questions without the user needing to repeat information. For example, after asking "What's the weather in London?", the user can simply ask, "What about tomorrow?" and the agent will remember the city.
- **Agent Instructions for State:** The agent's instructions are updated to guide it on how to use the remembered context and even how to answer direct questions about its memory (e.g., "What was the last city I asked for?").

### `04_06.ipynb`: Putting it all together: LLM-Based Routing with a Coordinator Agent

This notebook is the capstone of the series, demonstrating how to build a master "Coordinator Agent" that uses LLM-based routing to dynamically delegate tasks to a suite of specialized sub-agents.

- **LLM-Based Routing:** Instead of a fixed workflow, this notebook builds a top-level `wanderwise_coordinator_agent`. This agent's LLM is instructed to analyze a user's query and intelligently decide which sub-agent(s) to call and in what order.
- **Sub-Agents as Tools:** The specialized agents from previous notebooks (`itinerary_agent`, `weather_agent`, etc.) are wrapped in functions, turning them into "tools" that the Coordinator can use.
- **Dynamic Orchestration:** The Coordinator is given a high-level instruction set that outlines the logic for handling complex trip-planning requests. It can decide whether to call a single agent for a simple query (e.g., "What's the weather?") or to execute a full sequence of agent calls for a complex query (e.g., "Plan a trip to Paris, find events, and tell me what to pack.").
- **Comprehensive AI System:** This brings all the concepts together to create a flexible and powerful multi-agent system that can handle a wide variety of user intents by intelligently orchestrating its specialized components.