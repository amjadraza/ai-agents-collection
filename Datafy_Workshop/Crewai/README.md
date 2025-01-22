# AI-Powered Research and Content Creation with Gemini and CrewAI

## Overview

This Google Colab notebook demonstrates how to build an AI-powered system for automated research and content creation using Google's Gemini language model and CrewAI. The system is designed to help developers, researchers, and content creators automate complex workflows for discovering trends and generating insightful content.

## Key Features

- Integration with Google's Gemini language model
- Autonomous agents for research and content creation using CrewAI
- Automated trend identification and analysis
- High-quality content generation
- Markdown output formatting
- Customizable workflow for different topics

## Prerequisites

- Google Colab account
- Gemini API key
- Serper API key

## Installation

The notebook requires the following packages:

```python
%pip install -qU crewai crewai_tools langchain-google-genai
```

## Environment Setup

You'll need to set up your environment variables:

```python
import os
from google.colab import userdata
os.environ["GOOGLE_API_KEY"] = userdata.get('GEMINI_API_KEY')
os.environ["SERPER_API_KEY"] = userdata.get('SERPER_API_KEY')
```

## Components

### 1. Agents

The system uses two main agents:

- **Senior Researcher**: Focuses on uncovering groundbreaking technologies
- **Writer**: Crafts compelling narratives based on research findings

### 2. Tasks

Two primary tasks are defined:

- **Research Task**: Identifies trends and analyzes their impact
- **Writing Task**: Creates engaging content based on research findings

### 3. Workflow

The system follows a sequential process:

1. Research agent investigates the specified topic
2. Writing agent creates content based on research findings
3. Output is formatted in markdown

## Usage

1. Configure your API keys in Google Colab
2. Run all cells in sequence
3. Provide a topic when prompted (e.g., "AI in healthcare")
4. System will generate research findings and a well-structured article

## Output

The system produces:

- Comprehensive research analysis
- Well-structured article in markdown format
- Optional output file (new-blog-post.md)

## Customization

You can modify:

- Research parameters
- Writing style and format
- Output file specifications
- Topic focus areas

## Example Output

The system can generate detailed articles on various topics, such as:

- Technology trends
- Industry analyses
- Market research
- Scientific developments

## Limitations

- Requires valid API keys
- Processing time depends on topic complexity
- Output quality depends on available data

## Contributing

Feel free to fork this notebook and adapt it to your needs. Contributions and improvements are welcome.

## License

This project is available for open use and modification. Please check individual component licenses for specific terms.
