# CSV Analysis Agent with LangChain and Groq LLM

This Google Colab notebook implements an intelligent CSV analysis system using LangChain and the Groq LLM (specifically the llama-3.3-70b-versatile model). The system enables natural language-based analysis of salary data, allowing users to query datasets conversationally without writing explicit code.

## Features

- **Natural Language Queries**: Interact with CSV data using plain English questions
- **Automated Analysis**: AI-powered agent for analyzing salary datasets
- **Enhanced Accuracy**: Built-in verification system that:
  - Uses multiple calculation methods for verification
  - Enforces data formatting standards
  - Requires methodology explanations
  - Prevents hallucination through data-based calculations
- **Flexible Interface**: Supports both programmatic Python access and Streamlit web interface
- **Groq LLM Integration**: Leverages the powerful llama-3.3-70b-versatile model
- **Pandas Integration**: Uses Pandas DataFrame agent for robust data manipulation

## Prerequisites

```python
%pip install -qU pyodbc tabulate langchain langchain-community langchain-core langchain-experimental groq
```

You'll also need a Groq API key stored in your Google Colab environment.

## Setup

1. Import required libraries and set up the Groq API key:

```python
from langchain.schema import HumanMessage, SystemMessage
from langchain_groq import ChatGroq
import os
from google.colab import userdata

os.environ["GROQ_API_KEY"] = userdata.get('GROQ_API_KEY')
```

2. Initialize the Groq LLM model:

```python
llm_name = "llama-3.3-70b-versatile"
model = ChatGroq(model=llm_name)
```

## Usage

The notebook supports analysis of salary data through:

1. **Direct Python Interface**:

```python
agent = create_pandas_dataframe_agent(
    llm=model,
    df=df,
    verbose=True,
    allow_dangerous_code=True
)

result = agent.invoke("Your question here")
```

2. **Streamlit Web Interface** (commented out by default):

- Provides a user-friendly web interface
- Shows dataset preview
- Allows interactive question input
- Displays formatted results

## Example Queries

The system can handle complex analytical queries such as:

- Department salary analysis
- Gender pay comparisons
- Grade-based salary analysis

Example query:

```python
QUESTION = "Which department makes the most on average and give the actual amount?"
```

## Custom Prompting

The notebook includes custom prompt engineering:

- Prefix prompts for setting up analysis context
- Suffix prompts for ensuring thorough verification
- Formatting requirements for numerical results
- Requirements for methodology explanations

## Data Requirements

The notebook expects a CSV file (`salaries_2023.csv`) with columns including:

- Department
- Department_Name
- Division
- Gender
- Base_Salary
- Overtime_Pay
- Longevity_Pay
- Grade

## Error Handling

- Built-in parsing error handling
- Multiple calculation method verification
- Result consistency checking
- Clear indication when results are uncertain

## Output Formatting

Results are formatted with:

- Markdown styling
- Comma-separated numbers for readability
- Detailed methodology explanations
- Verification of calculations

## Contributing

Feel free to fork this notebook and adapt it to your needs. If you make improvements, please consider submitting a pull request.

## Note

Remember to handle your API keys securely and never commit them directly in the notebook.
