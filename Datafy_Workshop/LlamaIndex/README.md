# Building and Testing a ReAct Agent with LlamaIndex

## Overview

This repository contains a Google Colab notebook that demonstrates how to build and test a ReAct (Reasoning and Acting) agent using LlamaIndex. The notebook covers the creation of a ReAct agent with simple tools (e.g., arithmetic operations) and extends its capabilities by integrating QueryEngine tools for querying financial data from Uber and Lyft's 10-K filings.

## Key Features

- **ReAct Agent Setup**: Learn how to create a ReAct agent and integrate it with simple tools like arithmetic operations.
- **QueryEngine Integration**: Extend the agent's capabilities by integrating QueryEngine tools to query financial data from Uber and Lyft's 10-K filings.
- **Hands-On Examples**: Step-by-step examples of how to use the agent to answer complex questions by combining reasoning and tool usage.
- **Prompt Inspection**: Explore the prompts used by the agent to select and interact with tools.

## Installation

To run this notebook, you need to install the following Python packages:

```bash
pip install -qU llama-index llama-index-llms-gemini llama-index-embeddings-huggingface
```

## Usage

1. **Set Up API Keys**: Ensure you have the necessary API keys (e.g., Gemini API key) and configure them in the notebook.
2. **Define Tools**: Start by defining simple tools (e.g., arithmetic operations) and integrate them with the ReAct agent.
3. **Query Financial Data**: Use the QueryEngine tools to query financial data from Uber and Lyft's 10-K filings.
4. **Run Queries**: Test the agent by running queries and observing how it reasons and acts to provide answers.

## Example Queries

- **Simple Arithmetic**: "What is 20 + (2 * 4)? Calculate step by step."
- **Financial Data**: "What is Lyft's core business model, and how does it generate revenue?"
- **Comparative Analysis**: "Compare and contrast the revenue growth of Uber and Lyft in 2021, then give an analysis."

## Notebook Structure

1. **Installation**: Install required Python packages.
2. **Setup API Keys**: Configure API keys for the Gemini model.
3. **Define LLM and Embedding Model**: Set up the language model and embedding model.
4. **Create ReAct Agent**: Build a ReAct agent with simple tools.
5. **QueryEngine Tools**: Integrate QueryEngine tools for financial data querying.
6. **Run Queries**: Test the agent with various queries.

## Dependencies

- Python 3.10+
- LlamaIndex
- Gemini API
- HuggingFace Embeddings

## Acknowledgments

- LlamaIndex for providing the framework to build and test ReAct agents.
- Gemini and HuggingFace for their language models and embeddings.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

---

This README provides an overview of the notebook and its functionality. Feel free to explore the notebook and experiment with the ReAct agent!
Let me know if you need further adjustments!
