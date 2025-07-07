# AI Research Assistant Agent

A Python-based AI agent that helps you conduct research on any topic using web search, Wikipedia, and Claude AI. The agent provides structured research outputs and can save findings to text files.

## Features

- 🔍 **Web Search**: Uses DuckDuckGo to search the internet for current information
- 📚 **Wikipedia Integration**: Queries Wikipedia for encyclopedic knowledge
- 🤖 **AI-Powered Analysis**: Uses Claude 3.5 Sonnet to analyze and synthesize information
- 📝 **Structured Output**: Returns research findings in a consistent, structured format
- 💾 **File Saving**: Automatically saves research outputs to text files with timestamps
- 🛠️ **Tool-Based Architecture**: Built with LangChain's agent framework for extensibility

## Project Structure

```
research_assistat_ai_agent/
├── main.py           # Main application entry point
├── tools.py          # Custom tools for search, Wikipedia, and file operations
├── requirements.txt  # Python dependencies
├── sample.env       # Environment variables template
└── README.md        # This file
```

## Setup Instructions

### Prerequisites

- Python 3.8 or higher
- An Anthropic API key (for Claude AI)
- Optional: OpenAI API key (if you want to use OpenAI models)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd research_assistat_ai_agent
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   ```bash
   cp sample.env .env
   ```
   
   Edit the `.env` file and add your API keys:
   ```
   ANTHROPIC_API_KEY="your-anthropic-api-key-here"
   OPENAI_API_KEY="your-openai-api-key-here"  # Optional
   ```

### Getting API Keys

- **Anthropic API Key**: Sign up at [Anthropic Console](https://console.anthropic.com/) and create an API key
- **OpenAI API Key**: Sign up at [OpenAI Platform](https://platform.openai.com/) and create an API key (optional)

## Usage

1. **Run the application**
   ```bash
   python main.py
   ```

2. **Enter your research query** when prompted
   ```
   What can i help you research? How does machine learning work?
   ```

3. **Review the structured output** which includes:
   - Topic summary
   - Key findings
   - Sources used
   - Tools utilized

4. **Find saved results** in the generated `research_output.txt` file

## Example Output

```json
{
  "topic": "Machine Learning Fundamentals",
  "summary": "Machine learning is a subset of artificial intelligence that enables computers to learn and improve from experience without being explicitly programmed...",
  "sources": [
    "https://example.com/ml-guide",
    "Wikipedia: Machine Learning"
  ],
  "tools_used": [
    "search",
    "wikipedia",
    "save_text_to_file"
  ]
}
```

## Available Tools

### Search Tool
- **Function**: Web search using DuckDuckGo
- **Use case**: Finding current information, news, and general web content

### Wikipedia Tool
- **Function**: Queries Wikipedia for encyclopedic information
- **Use case**: Getting authoritative, structured knowledge on topics

### Save Tool
- **Function**: Saves research outputs to text files
- **Use case**: Persistent storage of research findings with timestamps

## Customization

### Adding New Tools

You can extend the agent by adding new tools in `tools.py`:

```python
from langchain.tools import Tool

def your_custom_function(query: str):
    # Your custom logic here
    return "Custom result"

custom_tool = Tool(
    name="custom_tool",
    func=your_custom_function,
    description="Description of what your tool does"
)
```

Then add it to the tools list in `main.py`:
```python
tools = [search_tool, wiki_tool, save_tool, custom_tool]
```

### Changing the AI Model

To use a different model, modify the `llm` variable in `main.py`:

```python
# For OpenAI GPT models
from langchain_openai import ChatOpenAI
llm = ChatOpenAI(model="gpt-4")

# For other Anthropic models
llm = ChatAnthropic(model="claude-3-haiku-20240307")
```

## Dependencies

- **langchain**: Core framework for building AI agents
- **langchain-community**: Community tools and utilities
- **langchain-openai**: OpenAI integration
- **langchain-anthropic**: Anthropic Claude integration
- **python-dotenv**: Environment variable management
- **pydantic**: Data validation and parsing
- **wikipedia**: Wikipedia API wrapper
- **duckduckgo-search**: Web search functionality

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).

## Troubleshooting

### Common Issues

1. **API Key Errors**: Ensure your API keys are correctly set in the `.env` file
2. **Import Errors**: Make sure all dependencies are installed: `pip install -r requirements.txt`
3. **Network Issues**: Check your internet connection for web search functionality

### Getting Help

If you encounter issues:
1. Check the error messages in the console
2. Verify your API keys are valid
3. Ensure all dependencies are properly installed
4. Check the project's GitHub issues page

---

**Happy Researching!** 🚀