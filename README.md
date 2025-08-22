# AI Code Assistant

A command-line AI assistant powered by Google's Gemini API that helps with coding questions and tasks.

## Features

- Interactive conversation with Google Gemini 2.0 Flash model
- Command-line interface for easy integration into development workflows
- Verbose mode for debugging and token usage monitoring
- Function calling support for extended capabilities
- Configurable maximum iteration limits

## Prerequisites

- Python 3.7+
- Google Gemini API key
- Required Python packages (see Installation)

## Installation

1. Clone this repository or download the source files
2. Install required dependencies:
   ```bash
   pip install google-genai python-dotenv
   ```

3. Create a `.env` file in the project root and add your Gemini API key:
   ```
   GEMINI_API_KEY=your_api_key_here
   ```

4. Ensure you have the following files in your project directory:
   - `main.py` (main application file)
   - `prompts.py` (contains the system prompt)
   - `config.py` (contains configuration like MAX_ITERS)

## Usage

### Basic Usage

```bash
python main.py "your question or prompt here"
```

### Examples

```bash
# Ask a general coding question
python main.py "How do I reverse a list in Python?"

# Provide Answers from system prompt
python main.py "What does the eligibility verification agent (EVA) do?"
```

### Verbose Mode

Use the `--verbose` flag to see additional information including token counts:

```bash
python main.py "Explain recursion" --verbose
```

This will display:
- The user prompt
- Prompt token count
- Response token count

## Configuration

### Environment Variables

- `GEMINI_API_KEY`: Your Google Gemini API key (required)

### Configuration Files

- `config.py`: Contains `MAX_ITERS` setting to limit conversation iterations
- `prompts.py`: Contains the system prompt that defines the AI assistant's behavior

## How It Works

1. **Initialization**: Loads environment variables and initializes the Gemini API client
2. **Input Processing**: Parses command-line arguments to extract the user prompt and flags
3. **Conversation Loop**: 
   - Sends the user prompt to the Gemini API
   - Handles function calls if the model needs to perform actions
   - Continues the conversation until a final response is generated
   - Limits iterations to prevent infinite loops
4. **Output**: Displays the final response to the user

## Function Calling Support

The assistant supports Gemini's function calling capabilities, allowing it to:
- Execute code or tools when needed
- Provide more dynamic and interactive responses
- Handle complex multi-step tasks

## Error Handling

The application includes basic error handling for:
- Missing API keys
- API request failures
- Maximum iteration limits
- General exceptions during content generation

## Limitations

- Requires internet connection for API calls
- Limited by Gemini API rate limits and quotas
- Maximum iteration limit prevents very long conversations
- No conversation history persistence between runs

## File Structure

```
project/
├── main.py          # Main application entry point
├── prompts.py       # System prompt configuration
├── config.py        # Application configuration
├── .env            # Environment variables (create this)
└── README.md       # This file
```

## Troubleshooting

### Common Issues

1. **"GEMINI_API_KEY not found"**
   - Ensure your `.env` file exists and contains the correct API key
   - Verify the key name matches exactly: `GEMINI_API_KEY`

2. **"Maximum iterations reached"**
   - The conversation hit the iteration limit (defined in `config.py`)
   - Try rephrasing your question or breaking it into smaller parts
   - Consider increasing `MAX_ITERS` in the configuration

3. **API Connection Issues**
   - Check your internet connection
   - Verify your API key is valid and has sufficient quota
   - Ensure you have access to the Gemini API

## Development

### Adding New Features

1. Modify `prompts.py` to update the system prompt
2. Adjust `config.py` for new configuration options
3. Extend the main conversation loop in `main.py` as needed

### Contributing

1. Follow Python PEP 8 style guidelines
2. Add appropriate error handling for new features
3. Update documentation for any new functionality

## License

This project is provided as-is for educational and development purposes. Please ensure compliance with Google's Gemini API terms of service.

## Support

For issues related to:
- **Google Gemini API**: Check the [official documentation](https://ai.google.dev/)
- **This application**: Review the troubleshooting section or check the application logs
- **Python dependencies**: Refer to the respective package documentation