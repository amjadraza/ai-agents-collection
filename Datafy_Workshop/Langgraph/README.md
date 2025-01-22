# LangGraph Integration with LangChain and Groq

## Introduction

This Google Colab notebook demonstrates the integration of LangGraph with LangChain and Groq for building conversational AI applications with advanced search capabilities. It showcases how to create different types of conversation flows using StateGraph, including simple chains and intelligent routing mechanisms.

## Goals

- Set up and configure LangGraph with Groq's LLM
- Implement Tavily search integration for real-time information retrieval
- Demonstrate different conversation flow patterns using StateGraph
- Build both simple chains and complex routing systems
- Show practical examples of weather queries and mathematical operations

## Prerequisites

- Google Colab account
- Groq API key
- Tavily API key

## Installation

Run the following command to install required packages:

```bash
pip install -qU langchain langchain-community langchain_tools tavily-python langgraph langchain_groq
```

## Configuration

The notebook requires two API keys:

1. GROQ_API_KEY - For accessing Groq's LLM services
2. TAVILY_API_KEY - For performing web searches

These keys should be stored in Google Colab's secrets management system.

## Components

### 1. LLM Setup

- Uses ChatGroq with the "llama-3.3-70b-versatile" model
- Configured for versatile conversational tasks

### 2. Search Integration

- Implements Tavily search with the following features:
  - Maximum 5 results per search
  - Includes answers and raw content
  - Supports image results
  - Customizable search depth and domain filtering

### 3. Graph Implementations

The notebook includes three different graph implementations:

#### Simple Chain

- Basic implementation with START → Assistant → END flow
- Suitable for simple conversation patterns

#### Router

- Implements conditional routing based on tool usage
- Flow: START → Assistant → [Tools/END]
- Handles both direct responses and tool-based queries

#### Advanced Router with Feedback

- Implements a feedback loop for tool outputs
- Flow: START → Assistant → Tools → [Assistant/END]
- Suitable for complex queries requiring multiple steps

## Usage Examples

The notebook includes several practical examples:

1. Basic conversation handling
2. Weather queries for specific locations
3. Mathematical operations
4. Complex queries combining search and analysis

## Visualization

The notebook includes Mermaid diagram generation for each graph implementation, helping visualize the flow of conversations and tool usage.

## Note

This is an educational notebook demonstrating LangGraph capabilities. For production use, consider implementing additional error handling and security measures.
