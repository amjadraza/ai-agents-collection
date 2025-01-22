# AI-Driven Student Support System

A Google Colab notebook implementing an intelligent support system for high school students using the Swarm framework. The system provides personalized guidance through specialized AI agents for motivation, counseling, crisis handling, and therapy.

## Overview

This project creates a comprehensive student support system capable of:

- Providing personalized motivation and emotional support
- Offering academic and career guidance
- Handling crisis situations with appropriate escalation
- Delivering therapeutic support through intelligent conversation

## Key Components

### 1. Agent Types

- **Therapist Agent**:

  - Main entry point for student interactions
  - Analyzes mood patterns and current mental state
  - Routes conversations to appropriate specialized agents
- **Motivator Agent**:

  - Provides stoic motivational quotes
  - Relates quotes to student's personal experiences
  - Offers encouragement and support
- **Counselor Agent**:

  - Delivers academic and career guidance
  - Provides personalized advice based on student data
  - Maintains a supportive and engaging tone
- **Crisis Handler Agent**:

  - Supports students in distress
  - Provides immediate empathy and reassurance
  - Facilitates connection to human counselors when necessary

### 2. Technology Stack

Required Python packages:

```python
swarm
requests
beautifulsoup4
IPython
```

## Setup Instructions

1. Open the notebook in Google Colab using the provided badge
2. Install required packages:
   ```python
   %pip install -qU git+https://github.com/openai/swarm.git requests
   ```
3. Set up your OpenAI API key:
   ```python
   from google.colab import userdata
   import os
   os.environ['OPENAI_API_KEY'] = userdata.get('OPENAI_API_KEY')
   ```

## Features

1. **Real-time Interaction**

   - Terminal-based input/output interface
   - Color-coded message display
   - Dynamic agent switching based on context
2. **Contextual Support**

   - Processes student data including:
     - Personal details
     - Academic information
     - Mood history
     - Professional goals
3. **Intelligent Routing**

   - Automatically directs students to appropriate support agents
   - Seamless transitions between different types of support
   - Maintains conversation context across agent switches

## Usage

The system requires context variables for optimal operation:

```python
context_variables = {
    "student_data": "Student's personal information",
    "mood_history": ["mood1", "mood2", ...],
    "academic_info": "Academic and extracurricular details"
}
```

Start a conversation:

```python
client = Swarm()
messages = []
# Run conversation loop
```

## Implementation Goals

- **Accuracy**: Deliver personalized responses based on individual needs
- **Empathy**: Maintain supportive, non-judgmental communication
- **Scalability**: Support addition of new agent types and functionalities
- **Safety**: Include appropriate escalation protocols for crisis situations

## Contributing

Feel free to open issues or submit pull requests to enhance the system's functionality.

## Safety Note

This system is designed as a supplementary tool and should not replace professional mental health services. Always ensure proper escalation protocols are in place for crisis situations.
