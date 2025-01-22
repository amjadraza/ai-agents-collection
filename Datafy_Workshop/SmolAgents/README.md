# SmolAgents - Google Colab Notebook

This repository contains a Google Colab notebook demonstrating the use of **SmolAgents**, a framework for creating and running small, task-specific AI agents. The notebook showcases how to set up and use SmolAgents to perform various tasks, including mathematical calculations, web searches, and data retrieval.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
  - [Basic Example](#basic-example)
  - [Using Predefined Tools](#using-predefined-tools)
  - [Fetching and Visualizing Data](#fetching-and-visualizing-data)
- [System Prompt](#system-prompt)
- [Authorized Imports](#authorized-imports)
- [License](#license)

## Introduction

SmolAgents is a lightweight framework designed to create AI agents that can perform specific tasks using code. The agents can execute Python code, interact with external tools, and provide results based on the task given. This notebook demonstrates how to set up and use SmolAgents in a Google Colab environment.

## Installation

To get started, you need to install the required packages. Run the following command in your Colab notebook:

```bash
%pip install -qU smolagents litellm
```

Additionally, you need to set up your API keys for OpenAI, Tavily, and Hugging Face:

```python
import os
from google.colab import userdata

os.environ['OPENAI_API_KEY'] = userdata.get('OPENAI_API_KEY')
os.environ['TAVILY_API_KEY'] = userdata.get('TAVILY_API_KEY')
os.environ['HF_TOKEN'] = userdata.get('HF_TOKEN')
```

## Usage

### Basic Example

The simplest use case is to perform a basic calculation using the `CodeAgent`:

```python
from smolagents import CodeAgent, HfApiModel

model = HfApiModel()
agent = CodeAgent(tools=[], model=model)

agent.run('What is 24*7?')
```

This will output the result of the calculation.

### Using Predefined Tools

SmolAgents comes with predefined tools like `DuckDuckGoSearchTool` for web searches. Here's how you can use it:

```python
from smolagents import DuckDuckGoSearchTool

agent = CodeAgent(tools=[DuckDuckGoSearchTool()], model=model)

agent.run('what is the result for recently concluded cricket test series between India vs Australia?')
```

This will perform a web search and return the result of the cricket series.

### Fetching and Visualizing Data

You can also use SmolAgents to fetch data and visualize it. For example, fetching Google's stock price from 2020 to 2024 and creating a line graph:

```python
agent.run("fetch the share price of google from 2020 to 2024, and create a line graph from it?")
```

Note: This example may require additional imports like `matplotlib` or `seaborn`, which are not included in the default authorized imports.

## System Prompt

The system prompt for the `CodeAgent` is designed to guide the agent in solving tasks using code. It includes examples and rules for how the agent should operate. You can view the system prompt by running:

```python
print(agent.system_prompt)
```

## Authorized Imports

The `CodeAgent` has a list of authorized imports that it can use in its code execution. By default, it includes modules like `time`, `itertools`, `statistics`, and `math`. You can view the list of authorized imports by running:

```python
agent.authorized_imports
```

If you need to use additional modules, you can pass them as `additional_authorized_imports` when initializing the `CodeAgent`.

Feel free to explore the notebook and experiment with different tasks using SmolAgents! If you have any questions or run into issues, please open an issue in the repository.
