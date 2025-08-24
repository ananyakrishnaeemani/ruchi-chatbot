# Ruchi: Your Culinary Assistant 
Ruchi (రుచి) is a multi-language, AI-powered culinary assistant designed to provide recipes and cooking advice with a special focus on Indian and South Asian cuisine. This application uses a hybrid backend that leverages Ollama for local, private English support and the Gemini API for high-quality Telugu responses.

## Features
- Hybrid Backend: The app intelligently routes requests to the Ollama model for English and the Gemini API for Telugu, maximizing performance and quality for each language.
- Multilingual Support: The app provides separate chat histories for English and Telugu, each with its own tailored system prompt and conversation flow.
- Strict Safety Constraints: The application is designed to avoid providing medical advice and other harmful content, ensuring it remains a helpful informational tool.

## Project Structure
The project is organized into a modular structure for clarity and maintainability:
```
/Ruchi
├── .env                  # Stores environment variables (e.g., API keys)
├── .gitignore            # Excludes sensitive files from Git
├── requirements.txt      # Lists all Python dependencies
├── app.py                # The main Streamlit app file
├── config.py             # Centralized configuration for models and prompts
├── llm_backends.py       # Functions to handle communication with Ollama
```
## Setup and Installation
Follow these steps to get the project up and running on your local machine.

## Prerequisites
- Python 3.8+: Ensure you have a compatible version of Python installed.
- Ollama: Download and install Ollama from the official website.
- Model: Pull the phi3:mini model using the Ollama command line.
- Gemini API Key: Obtain a Gemini API key from Google AI Studio. This is required for the Telugu functionality.
```
ollama pull phi3:mini
```

### Step 1: Clone the Repository
Clone this repository and navigate to the project directory.
```
git clone https://code.swecha.org/ananyakrishna/ruchi-individual-project
cd ruchi-individual-project
```
### Step 2: Install Dependencies
It's highly recommended to use a virtual environment.
Create and activate a virtual environment
```
python -m venv .venv
source .venv/bin/activate  # On Windows, use: .\.venv\Scripts\activate
```
Install the required Python packages
```
pip install -r requirements.txt
```
### Step 3: Configure the Environment
Create a .env file in the root of your project. This file is crucial for securely storing your Gemini API key. .env
Gemini API Key for Telugu responses
```
GEMINI_API_KEY="your_gemini_api_key_here"
```

### Step 4: Run the Application
Pull the Ollama model in a terminal.
```
ollama pull phi3:mini
```
In a new terminal window with your virtual environment activated, run the Streamlit application.
```
streamlit run app.py
```
Your web browser should automatically open to the Swaad landing page. From there, you can select your preferred language and start a conversation with your culinary assistant.