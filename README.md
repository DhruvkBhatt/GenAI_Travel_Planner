# GenAI Travel Planner 🌍

An AI-powered travel planning assistant that helps users create comprehensive, personalized travel itineraries using agentic workflows and real-time data from the internet.

## Demo

- **Live app**: [https://genai-travel-planner.onrender.com/](https://genai-travel-planner.onrender.com/)
- **Frontend UI**: Streamlit-based interactive chat interface
- **Screenshot**: See the AI Travel Agent in action by asking questions like "Plan a trip to Goa for 5 days"

## Key Features

- 🤖 **AI-Powered Travel Planning**: Uses LangGraph-based agentic workflows to create detailed travel itineraries
- 🌐 **Real-Time Data Integration**: Fetches live weather information, place details, and pricing data
- 💰 **Expense Calculator**: Provides detailed cost breakdowns with currency conversion support
- 🎯 **Dual Itinerary Options**: Offers both popular tourist destinations and off-beat locations
- 🔧 **Multiple Tools Integration**: Weather info, place search, currency converter, and expense calculator
- 📝 **Comprehensive Plans**: Includes day-by-day itinerary, hotels, restaurants, activities, and transportation

## Tech Stack

- **Frontend**: Streamlit (Interactive chat-based UI)
- **Backend**: FastAPI (REST API server)
- **LLM / AI**: 
  - Google Gemini (default)
  - OpenAI GPT
  - Groq
- **AI Framework**: 
  - LangChain (LLM orchestration)
  - LangGraph (Agentic workflow)
  - LangChain Community Tools
- **External APIs**:
  - OpenWeatherMap (Weather data)
  - Google Places API (Location search)
  - Exchange Rate API (Currency conversion)
  - Alpha Vantage API (Financial data)
- **Deployment**: Render (Backend hosting)

## Project Structure

```text
GenAI_Travel_Planner/
├── agent/                      # Agentic workflow implementation
│   ├── __init__.py
│   └── agentic_workflow.py    # LangGraph-based agent builder
├── config/                     # Configuration files
│   └── __init__.py
├── exception/                  # Custom exception handling
│   ├── __init__.py
│   └── exceptiohandling.py
├── logger/                     # Logging utilities
│   ├── __init__.py
│   └── logging.py
├── notebook/                   # Jupyter notebooks for experiments
│   └── experiments.ipynb
├── prompt_library/            # System prompts and templates
│   ├── __init__.py
│   └── prompt.py
├── tools/                     # LangChain tools for the agent
│   ├── __init__.py
│   ├── arthamatic_op_tool.py
│   ├── currency_conversion_tool.py
│   ├── expense_calculator_tool.py
│   ├── place_search_tool.py
│   └── weather_info_tool.py
├── utils/                     # Utility functions
│   ├── __init__.py
│   ├── config_loader.py
│   ├── currency_converter.py
│   ├── expense_calculator.py
│   ├── model_loader.py
│   ├── place_info_search.py
│   ├── save_to_document.py
│   └── weather_info.py
├── main.py                    # FastAPI backend entry point
├── streamlit_app.py          # Streamlit frontend
├── app.py                    # Additional app configurations
├── requirements.txt          # Python dependencies
├── setup.py                  # Package setup configuration
├── pyproject.toml           # Project metadata
└── README.md                # Project documentation
```

## Prerequisites

Before you begin, ensure you have the following installed:

- **Python**: 3.10 or higher
- **pip**: Python package manager
- **Git**: Version control system

### API Keys Required

You'll need to obtain API keys from the following services:

1. **Google AI Studio** (for Gemini) - [Get API Key](https://makersuite.google.com/app/apikey)
2. **Groq** (optional, alternative LLM) - [Get API Key](https://console.groq.com/)
3. **OpenAI** (optional, alternative LLM) - [Get API Key](https://platform.openai.com/api-keys)
4. **OpenWeatherMap** - [Get API Key](https://openweathermap.org/api)
5. **Google Places API** - [Get API Key](https://developers.google.com/maps/documentation/places/web-service/get-api-key)
6. **Exchange Rate API** - [Get API Key](https://www.exchangerate-api.com/)
7. **Alpha Vantage** (optional) - [Get API Key](https://www.alphavantage.co/support/#api-key)

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/DhruvkBhatt/GenAI_Travel_Planner.git
cd GenAI_Travel_Planner
```

### 2. Create a Virtual Environment

```bash
# Using venv
python -m venv venv

# Activate the virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Or install the package in editable mode:

```bash
pip install -e .
```

## Environment Variables Configuration

Create a `.env` file in the root directory of the project with the following variables:

```env
# LLM API Keys (at least one required)
GOOGLE_API_KEY=your_google_api_key_here
GROQ_API_KEY=your_groq_api_key_here
OPENAI_API_KEY=your_openai_api_key_here

# External Service API Keys
OPENWEATHERMAP_API_KEY=your_openweathermap_api_key_here
GPLACES_API_KEY=your_google_places_api_key_here
EXCHANGE_RATE_API_KEY=your_exchange_rate_api_key_here
ALPHAVANTAGE_API_KEY=your_alphavantage_api_key_here
```

### Example `.env` File

```env
GOOGLE_API_KEY=AIzaSyABC123...
GROQ_API_KEY=gsk_ABC123...
OPENAI_API_KEY=sk-proj-ABC123...
OPENWEATHERMAP_API_KEY=abc123def456...
GPLACES_API_KEY=AIzaSyABC123...
EXCHANGE_RATE_API_KEY=abc123def456...
ALPHAVANTAGE_API_KEY=ABC123DEF456
```

## Usage

### Running the Backend (FastAPI)

Start the FastAPI backend server:

```bash
# Using uvicorn directly
uvicorn main:app --reload --host 0.0.0.0 --port 8000

# Or using Python
python main.py
```

The API will be available at `http://localhost:8000`

### Running the Frontend (Streamlit)

In a separate terminal, start the Streamlit frontend:

```bash
streamlit run streamlit_app.py
```

The Streamlit app will open in your browser at `http://localhost:8501`

### Using the Application

1. Open the Streamlit interface in your browser
2. Enter your travel query in the input box, for example:
   - "Plan a trip to Paris for 7 days"
   - "I want to visit Tokyo for 5 days with a budget of $2000"
   - "Create an itinerary for Bali for 10 days"
3. Click "Send" and wait for the AI to generate your personalized travel plan
4. The AI will provide:
   - Day-by-day itinerary
   - Hotel recommendations with prices
   - Places of interest
   - Restaurant suggestions
   - Activities and transportation options
   - Detailed expense breakdown
   - Current weather information

## API Endpoints

### Health Check

```bash
GET /
```

Returns a simple message confirming the API is running.

### Health Status

```bash
GET /health
```

Returns the health status of the API.

### Query Travel Agent

```bash
POST /query
Content-Type: application/json

{
  "question": "Plan a trip to Goa for 5 days"
}
```

**Response:**

```json
{
  "answer": "# AI Travel Plan\n\n## Day 1\n..."
}
```

## Configuration

The model provider can be changed in the `main.py` file:

```python
graph = GraphBuilder(model_provider="gemini")  # Options: "gemini", "groq", "openai"
```

Model configurations are stored in the `config/` directory.

## Development

### Project Architecture

This project uses an **agentic workflow** architecture powered by LangGraph:

1. **Agent**: The main AI agent that processes user queries and decides which tools to use
2. **Tools**: Specialized functions for weather info, place search, calculations, and currency conversion
3. **Graph**: LangGraph orchestrates the flow between the agent and tools
4. **LLM**: Multiple LLM providers supported (Gemini, Groq, OpenAI)

### Adding New Tools

To add a new tool:

1. Create a new tool file in the `tools/` directory
2. Implement the tool using LangChain's tool decorator
3. Add the tool to the agent in `agent/agentic_workflow.py`

## Troubleshooting

### Common Issues

1. **Import Errors**: Make sure all dependencies are installed with `pip install -r requirements.txt`
2. **API Key Errors**: Verify that all required API keys are set in your `.env` file
3. **Connection Errors**: Check that the backend is running before starting the frontend
4. **Rate Limits**: Some APIs have rate limits; consider upgrading to paid tiers for production use

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the MIT License.

## Author

**Dhruv Bhatt**
- Email: bdhruv32@gmail.com
- GitHub: [@DhruvkBhatt](https://github.com/DhruvkBhatt)

## Acknowledgments

- Built with LangChain and LangGraph
- Uses Google Gemini for AI capabilities
- Deployed on Render

---

*This travel plan application was created to make travel planning easier and more comprehensive using the power of AI and real-time data.*