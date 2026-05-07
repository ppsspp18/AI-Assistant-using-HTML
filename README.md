# Vanilla JS AI Chat Interface

A lightweight, fully-featured, vanilla JavaScript chat interface for interacting with OpenAI-compatible Large Language Model (LLM) APIs. 

This project operates entirely on the client side (in-browser), storing chat history, custom modes, and settings using `localStorage`. It is designed to be highly customizable and easily points to any API provider that supports the standard OpenAI chat completions endpoint format.

## 🚀 Features

* **OpenAI-Compatible API Support**: Easily connect to providers like OpenAI, Groq, Together AI, or local instances like LM Studio and Ollama by updating the API URL in settings.
* **Persistent Chat History**: Conversations are automatically saved to your browser's local storage. Switch between past conversations, create new ones, or delete old ones via the sidebar.
* **Custom Modes (Personas)**: Create, edit, and delete custom "Modes" (System Prompts). Tell the AI to act like a Python expert, a pirate, or a code reviewer.
* **Adjustable Context Window**: Configure how many previous messages (`ctxN`) are sent with each new request to save on tokens or expand the AI's memory.
* **Reasoning Model Support**: Automatically parses and strips out `<thought>...</thought>` tags from models that output their chain-of-thought (e.g., DeepSeek-R1).
* **Markdown Rendering**: Parses and renders markdown responses formatting (requires `marked.js` to be included in your HTML).
* **Responsive UI**: Features an auto-resizing text input area, an off-canvas mobile-friendly sidebar, and modal dialogs for settings and mode configuration.

## 🛠️ Getting Started

### Prerequisites
Since this is a vanilla HTML/JS/CSS project, there are no build steps or dependencies to install via npm. 

You simply need a web browser and an API key from an LLM provider.

### Installation & Usage
1. Clone or download this repository.
2. Ensure you have the `index.html` file (which should include the provided JavaScript, your CSS, and a `<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>` tag for markdown).
3. Open `index.html` directly in your web browser.
4. Click the **⚙️ Settings** icon in the UI.
5. Enter your configuration:
   * **API URL**: e.g., `https://api.openai.com/v1/chat/completions` (or your local/custom endpoint)
   * **API Key**: Your authorization token
   * **Model Name**: e.g., `gpt-4o`, `gemma-4-31b-it`, `llama-3-70b`
   * **Context Length**: Number of previous messages to remember (default is 8).
6. Save settings and start chatting!

## 📂 Code Structure Overview

The JavaScript is organized into distinct logical blocks:

* **`Init`**: Bootstraps the application, loads stored data, and binds event listeners.
* **`Chat storage`**: Manages the CRUD operations for conversation histories in `localStorage` (`chats` object, `activeChatId`).
* **`Render sidebar & chat`**: Handles DOM manipulation to display chat lists, render message bubbles, and show "Thinking..." indicators.
* **`Settings`**: Handles the API configuration modal and persistence.
* **`Modes`**: Manages the array of system prompts (personas) available to the user.
* **`Send` (`sendMessage`)**: The core function. Packages the user input, system prompt, and chat history, sends the `POST` request to the API, handles the response, strips thought tags, and updates the UI.
* **`Events`**: Binds all button clicks, keyboard shortcuts (e.g., Enter to send), and modal dismissals.

## 🔒 Privacy & Security

**Important**: Because this is a client-side application, your API keys are stored in your browser's `localStorage` in plain text. Do not use this application on public or shared computers, as anyone with access to the browser developer tools can view your API key.

## 📝 Dependencies

* **Marked.js**: Used in the `appendBubble` function (`marked.parse(content)`) to render markdown. Ensure it is included in your HTML file.

## 🤝 Contributing

Feel free to fork this project, submit pull requests, or open issues to suggest new features (like syntax highlighting for code blocks, streaming responses, or image generation support).
