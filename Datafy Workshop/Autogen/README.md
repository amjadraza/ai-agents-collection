# AutoGen Multi-Agent Customer Support System

## Overview

This project implements an advanced customer support automation system using Microsoft's AutoGen framework. The system utilizes multiple specialized AI agents to handle customer inquiries, provide troubleshooting assistance, and manage support escalations efficiently.

## Features

- **Multi-Agent Architecture**: Seven specialized agents working together:
  - Inquiry Agent: Classifies incoming customer issues
  - Response Agent: Generates appropriate automated responses
  - Knowledge Base Agent: Searches for relevant solutions
  - Troubleshooting Agent: Provides step-by-step problem resolution
  - Feedback Agent: Collects customer satisfaction data
  - Escalation Agent: Identifies cases needing human intervention
  - Human Support Agent: Manages handoffs to human representatives

## Prerequisites

- Python 3.8+
- Google Colab environment
- OpenAI API key

## Installation

1. Run the notebook in Google Colab
2. Install required packages:

```bash
%pip install -qU pyautogen dask[dataframe]
```

## Configuration

1. Set up your OpenAI API key in Google Colab:

   - Store your API key in Colab's secrets manager
   - The system will automatically retrieve it using `userdata.get('OPENAI_API_KEY')`
2. LLM Configuration:

```python
llm_config = {
    "model": "gpt-4o-mini",
    "temperature": 0.4,
    "api_key": os.environ["OPENAI_API_KEY"],
}
```

## Usage

1. The system is initialized with a set of specialized agents
2. Customer inquiries are processed through a chain of agents
3. Each agent performs its specific role in the support process
4. The system can handle basic troubleshooting automatically
5. Complex cases are identified and escalated to human support

Example usage:

```python
initial_inquiry = "My internet is not working, and I have already tried rebooting the router."

user_proxy.initiate_chat(
    recipient=inquiry_agent,
    message=initial_inquiry,
    max_turns=2,
    summary_method="last_msg"
)
```

## System Architecture

- Uses nested chats for complex interactions
- Implements automatic workflow management
- Features conditional escalation paths
- Includes feedback collection mechanisms

## Customization

You can customize the system by:

- Modifying agent system messages
- Adjusting the LLM configuration
- Adding new specialized agents
- Changing the conversation flow
- Updating the escalation criteria

## Limitations

- Requires active internet connection
- Depends on OpenAI API availability
- Limited to text-based interactions
- Requires proper API key configuration

## Contributing

Feel free to fork this project and submit pull requests for any improvements.

## Acknowledgments

- Microsoft AutoGen framework
- OpenAI API

## Support

For issues and questions, please open an issue in the repository.
