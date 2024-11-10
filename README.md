# Code Chat

## Code Chat Extension

Code Chat is a Visual Studio Code extension that integrates with a FastAPI backend, utilizing Together AI's Llama models to enable natural language processing (NLP) for coding-related queries. The extension allows developers to interact with AI directly within VS Code, streamlining tasks like code completion, debugging assistance, and general coding inquiries.

### Features

- **Native Language Support**: Interact with the AI in your preferred language, and Code Chat will respond in kind.
- **Multiple AI Models**: Select from a range of powerful Llama models integrated with **TogetherAI** via **Code Chat Server**, including:
  - **Llama-3.2-11B** for comprehensive knowledge and versatility
  - **Meta-Llama-3.1-8B** for faster performance
  - **CodeLlama-34B** for enhanced code-specific support
- **Chat History**: Keep track of past conversations for easy reference.
- **Interactive Sidebar**: Code Chat appears as a sidebar where you can initiate chats, review history, and access saved conversations.
- **Copy Code Functionality**: Easily copy AI-generated code snippets to your clipboard for quick integration.

### Commands

- **Hello** (`codechat.helloWorld`): Displays a simple greeting message.
- **Start Code Chat** (`codechat.startChat`): Opens a new chat session with the AI.


## Code Chat Server

The **Code Chat Server** is a FastAPI-based backend that powers the Code Chat extension. It handles user prompts, interacts with Together AI’s Llama models, detects the language of incoming prompts, and returns appropriate responses.

### Features:
- **Integration with Together AI’s Llama Models**: Includes Llama-3.2-11B, Meta-Llama-3.1-8B, CodeLlama-34B, and others.
- **Language Detection**: Automatically detects the language of the user’s input and processes the request accordingly.
- **AI Model Communication**: Interacts with the models through API calls, enabling real-time, context-aware responses.
- **Scalable and Efficient**: Designed to handle multiple simultaneous requests, ensuring minimal latency during interactions.

### API Endpoints:
- **`GET /`**: Returns the server status.
- **`POST /api/prompt`**: Accepts a JSON payload with user input (`text`), optional model selection (`model`), and previous conversation history (`history`), then returns a response generated by the AI model.


## Running the Extension and Server Together

### 1. Clone the Main Repository with Submodules:

To clone the main repository with the submodules included, run the following command:
```bash
git clone --recurse-submodules https://github.com/ameentalahmeh/codechat
cd codechat
```

This will clone both the **Code Chat Extension** and **Code Chat Server** repositories as submodules, ensuring that the latest versions of both are included.

### 2. Install Dependencies for Both:

- **Code Chat Extension**:
   ```bash
   cd codechat-extension
   npm install
   ```

- **Code Chat Server**:
   ```bash
   cd ../codechat-server
   pip install -r requirements.txt
   ```

### 3. Configure Environment:
- Copy the `.env` template for the server and add your Together AI API key:
   ```bash
   cp dist.env .env
   ```

### 4. Start the Server:
Run the server using Uvicorn:
```bash
uvicorn src.app:app --reload
```
The server will run at `http://127.0.0.1:8000`.

### 5. Run the Extension:
- Open the **Code Chat Extension** project in VS Code.
- Press `F5` to launch the extension in debug mode.

### 6. Test the Integration:
- With both the server and extension running, interact with the extension's sidebar in VS Code.
- The extension will send prompts to the server, which processes them and returns responses based on the detected language.


## Future Work
- **Optimization**: Performance improvements for faster response times.
- **Support for Additional Models**: Expand model support to include more variants.
- **Enhanced UI/UX**: Improve the chat interface and interaction flow in the VS Code extension.
