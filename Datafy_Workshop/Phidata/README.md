# AI Research Assistant: Automated Content Analysis and Summarization

A Google Colab notebook implementing an intelligent research assistant using the Phi framework and Groq's Mixtral-8x7B model for automated information gathering, analysis, and summarization.

## Overview

This notebook creates an AI-powered research assistant capable of:

- Automatically collecting relevant information from multiple web sources
- Processing and analyzing web content to extract key insights
- Generating concise, well-structured summaries
- Providing real-time updates using current web sources

## Key Components

- **Groq Integration**: Leverages Groq's Mixtral-8x7B model for advanced language processing
- **DuckDuckGo Search**: Implements web search functionality for gathering relevant sources
- **Newspaper4k**: Provides web scraping and article extraction capabilities
- **SQLite Storage**: Maintains persistent storage for conversation history and session data

## Prerequisites

The notebook requires the following Python packages:

```python
phidata
yfinance
duckduckgo-search
newspaper4k
lxml_html_clean
groq
```

## Setup Instructions

1. Open the notebook in Google Colab using the provided badge
2. Install required packages:
   ```python
   %pip install -qU phidata yfinance duckduckgo-search newspaper4k lxml_html_clean groq
   ```
3. Set up your Groq API key:
   ```python
   import os
   from google.colab import userdata
   os.environ['GROQ_API_KEY'] = userdata.get('GROQ_API_KEY')
   ```

## Usage

The notebook implements an Agent class with the following features:

- Uses Groq's mixtral-8x7b-32768 model
- Includes DuckDuckGo and Newspaper4k tools for web searching and content extraction
- Implements SQLite storage for maintaining conversation history
- Provides streaming responses for real-time interaction

Example usage:

```python
prompt = "Tell me about the latest advancements in AI."
response = agent.run(prompt, stream=True)
```

## Features

1. **Automated Research**

   - Searches and collects information from multiple web sources
   - Focuses on relevant and current information
2. **Content Analysis**

   - Processes web content to extract key information
   - Analyzes and synthesizes data from multiple sources
3. **Smart Summarization**

   - Generates concise, structured summaries
   - Presents information in bullet points for easy consumption
4. **Real-time Updates**

   - Actively searches current web sources
   - Provides up-to-date information on any topic

## Contributing

Feel free to open issues or submit pull requests to improve the notebook's functionality.
