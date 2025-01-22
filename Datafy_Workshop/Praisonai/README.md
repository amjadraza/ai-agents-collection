# AI Job Market Analysis using Automated Web Search with PraisonAI

This Google Colab notebook demonstrates an automated workflow for analyzing AI job market trends in 2024 using PraisonAI. The workflow involves collecting data through web searches and validating the results to ensure completeness and quality.

## Overview

The notebook implements a dual-agent workflow to:

1. **Collect Data**: Perform an internet search using DuckDuckGo to gather information about AI job trends in 2024.
2. **Validate Data**: Automatically validate the search results to ensure they meet specific criteria (e.g., at least 5 results, each containing a title and URL).

The system leverages the PraisonAI framework and Groq's LLM API for processing and analysis. The workflow is designed to automatically retry data collection if the validation criteria are not met, ensuring robust and complete results.

## Features

- **Automated Web Search**: Uses DuckDuckGo to search for AI job trends in 2024.
- **Data Validation**: Ensures the collected data meets predefined criteria.
- **Retry Mechanism**: Automatically retries data collection if validation fails.
- **PraisonAI Integration**: Utilizes PraisonAI agents and tasks to manage the workflow.

## Requirements

To run this notebook, you need the following:

- **Google Colab**: The notebook is designed to run in Google Colab.
- **PraisonAI**: The notebook uses the PraisonAI framework for agent and task management.
- **DuckDuckGo Search**: The notebook uses the `duckduckgo-search` package to perform web searches.
- **Groq API Key**: The notebook uses Groq's LLM API for processing. You need to provide your Groq API key.

## Installation

Before running the notebook, you need to install the required packages:

```bash
%pip install -qU praisonai duckduckgo-search
```

## Setup

1. **Set Environment Variables**:
   - Set your Groq API key and base URL in the environment variables.
   - Specify the model name (e.g., `llama-3.3-70b-versatile`).

```python
import os
from google.colab import userdata

os.environ['OPENAI_API_KEY'] = userdata.get('OPENAI_API_KEY')
os.environ['OPENAI_BASE_URL'] = 'https://api.groq.com/openai/v1'
os.environ['OPENAI_MODEL_NAME'] = 'llama-3.3-70b-versatile'
```

2. **Define the Web Search Tool**:
   - The `internet_search_tool` function performs a search using DuckDuckGo and returns the results.

```python
from duckduckgo_search import DDGS

def internet_search_tool(query: str) -> List[Dict]:
    try:
        results = []
        ddgs = DDGS()
        for result in ddgs.text(keywords=query, max_results=10):
            results.append({
                "title": result.get("title", ""),
                "url": result.get("href", ""),
                "snippet": result.get("body", "")
            })
        return results
    except Exception as e:
        print(f"Error during DuckDuckGo search: {e}")
        return []
```

3. **Create the Data Collection Agent**:
   - The `data_agent` is responsible for performing the internet search.

```python
from praisonaiagents import Agent

data_agent = Agent(
    name="DataCollector",
    role="Search Specialist",
    goal="Perform internet searches to collect relevant information.",
    backstory="Expert in finding and organising internet data.",
    tools=[internet_search_tool],
    self_reflect=False
)
```

4. **Define Tasks**:
   - **Collect Task**: Perform the internet search and return the results.
   - **Validate Task**: Validate the collected data to ensure it meets the criteria.

```python
from praisonaiagents import Task

collect_task = Task(
    description="Perform an internet search using the query: 'AI job trends in 2024'. Return results as a list of title, URL, and snippet.",
    expected_output="List of search results with titles, URLs, and snippets.",
    agent=data_agent,
    name="collect_data",
    is_start=True,
    next_tasks=["validate_data"]
)

validate_task = Task(
    description="""Validate the collected data. Check if:
    1. At least 5 results are returned.
    2. Each result contains a title and a URL.
    Return validation_result as 'valid' or 'invalid' only no other text.""",
    expected_output="Validation result indicating if data is valid or invalid.",
    agent=data_agent,
    name="validate_data",
    task_type="decision",
    condition={
        "valid": [exit],  # End the workflow on valid data
        "invalid": ["collect_data"]  # Retry data collection on invalid data
    },
)
```

5. **Run the Workflow**:
   - The workflow is managed by the `PraisonAIAgents` class, which orchestrates the tasks and agents.

```python
from praisonaiagents import PraisonAIAgents

agents = PraisonAIAgents(
    agents=[data_agent],
    tasks=[collect_task, validate_task],
    verbose=1,
    process="workflow"
)

agents.start()
```

## Output

The notebook will output the search results and the validation result. If the data is valid, the workflow will end. If the data is invalid, the workflow will retry the data collection.

## Example Output

```plaintext
╭─────────────────────────────────────────────────── Response ────────────────────────────────────────────────────╮
│ [{"title": "AI in 2024: Five trends workers need to know - BBC", "url":                                         │
│ "https://www.bbc.com/worklife/article/20240104-ai-in-2024-five-trends-workers-need-to-know", "snippet": "A 2023 │
│ survey conducted by Jobs for the Future's Center for Artificial Intelligence & the Future of Work (JFF) showed  │
│ the majority of respondents believe they will need new skills to compete in an ..."}, ...]                      │
╰─────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
```

## Conclusion

This notebook provides a robust and automated workflow for analyzing AI job market trends in 2024. By leveraging PraisonAI and Groq's LLM API, the system ensures that the collected data is both comprehensive and validated.

---

**Note**: Make sure to replace the placeholder API key with your actual Groq API key before running the notebook.
