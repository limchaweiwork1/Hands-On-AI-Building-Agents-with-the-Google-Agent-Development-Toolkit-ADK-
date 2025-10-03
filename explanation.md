# How to Run the Agentic AI Examples

This repository contains a series of Jupyter notebooks that demonstrate how to build various types of agents using the Google Agent Development Toolkit (ADK). This guide will walk you through the steps to get started.

## 1. Environment Setup

Before running the examples, you need to set up your environment.

### a. Install Dependencies

The primary dependency is the `google-adk` package. You can install it using pip:

```bash
pip install google-adk --quiet
```

### b. Configure Environment Variables

To use the public Gemini API, you need to set an environment variable. This is done within the notebooks themselves, but it's good to be aware of it:

```python
import os
os.environ["GOOGLE_GENAI_USE_VERTEXAI"] = "False"
```

## 2. Running Your First Agent

The `01_03.ipynb` notebook is a great place to start. It walks you through the basics of creating and running a simple "greeting" agent.

To run the notebook:

1.  Open the `01_03.ipynb` file in a Jupyter environment (like VS Code with the Jupyter extension, or JupyterLab).
2.  Execute the cells in order. The notebook will:
    *   Install the necessary packages.
    *   Define a simple agent.
    *   Provide a function to interact with the agent.
    *   Run several test cases to show the agent's behavior.