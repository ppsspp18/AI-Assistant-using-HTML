# AI Assistant

A customizable ChatGPT-like AI Assistant built using **HTML, CSS, JavaScript, Local Storage, and Large Language Model APIs**. The application provides a clean conversational interface that supports multiple chat sessions, custom AI modes, configurable model providers, conversation memory, and persistent storage.

---

# Project Overview

This project is a lightweight AI Assistant designed to provide a flexible interface for interacting with Large Language Models (LLMs).

Unlike traditional chatbot applications that are tightly coupled to a specific provider, this application allows users to:

* Create multiple conversations
* Configure different AI models
* Define custom AI behaviors
* Persist chat history locally
* Connect to different LLM providers
* Switch between specialized AI modes

The application demonstrates practical implementation of:

* Prompt Engineering
* Conversation Management
* Context Window Management
* LLM API Integration
* Frontend State Management
* User Experience Design

---

# Key Features

## Multi-Conversation Support

Users can maintain multiple chat sessions simultaneously.

Each conversation contains:

```json
{
  "id": "chat_123",
  "title": "Machine Learning Discussion",
  "messages": [],
  "createdAt": 123456789
}
```

Features:

* Create new conversations
* Switch between conversations
* Delete conversations
* Automatic chat titles
* Persistent history

---

## AI Modes

One of the most powerful features of this project is the **Mode System**.

Modes modify AI behavior using system prompts.

Default Modes:

### One-Line Mode

Provides concise one-line explanations.

Example:

```text
Explain Quantum Computing
```

Output:

```text
Quantum computing uses quantum mechanics to perform computations much faster for certain problems.
```

---

### ELI5 Mode

Explains complex topics in simple language.

Example:

```text
Explain Blockchain
```

Output:

```text
Imagine a notebook that everyone can see and nobody can erase.
```

---

### Deep Dive Mode

Provides detailed technical explanations.

Useful for:

* Software Engineering
* Machine Learning
* Data Structures
* System Design

---

### Chat Mode

General-purpose conversational assistant.

---

## Custom AI Modes

Users can create unlimited custom modes.

Example:

### Interview Coach

```text
You are an experienced software engineering interviewer.
```

### Code Reviewer

```text
Review code for performance, security, and readability.
```

### Research Assistant

```text
Provide detailed academic explanations with examples.
```

Each mode stores:

```json
{
  "name": "Interview Coach",
  "prompt": "...",
  "placeholder": "Ask interview questions..."
}
```

---

# Architecture

## High-Level Architecture

```text
+----------------+
| User Interface |
+----------------+
         |
         v
+----------------------+
| Conversation Manager |
+----------------------+
         |
         v
+----------------------+
| Prompt Builder       |
+----------------------+
         |
         v
+----------------------+
| LLM API Layer        |
+----------------------+
         |
         v
+----------------------+
| Response Renderer    |
+----------------------+
```

---

# System Components

## 1. User Interface Layer

Responsible for:

* Chat Interface
* Sidebar
* Settings Modal
* Mode Management
* Conversation Navigation

Technologies:

* HTML
* CSS
* JavaScript

---

## 2. Conversation Manager

Handles:

* Chat Creation
* Chat Selection
* Chat Deletion
* Message Storage

Data Structure:

```javascript
{
    role: "user",
    content: "Hello",
    ts: 123456789
}
```

---

## 3. Prompt Builder

Constructs prompts before sending them to the model.

Example:

```javascript
[
    {
        role: "system",
        content: mode.prompt
    },
    {
        role: "user",
        content: "Explain transformers"
    }
]
```

---

## 4. API Layer

Responsible for:

* API Calls
* Authentication
* Model Selection
* Error Handling

Configurable Parameters:

```text
API URL
API Key
Model Name
Context Length
```

---

## 5. Response Renderer

Processes model responses.

Responsibilities:

* Markdown Rendering
* Code Block Formatting
* Hyperlink Rendering
* Response Display

---

# Context Window Management

Sending entire conversation history is expensive.

To solve this problem:

```javascript
const recent = allMsgs.slice(-ctxN);
```

Only recent messages are included.

Benefits:

* Reduced token usage
* Faster responses
* Lower costs
* Improved scalability

---

# Local Storage Persistence

The application uses browser localStorage.

Stored Objects:

```text
Chats
Modes
Settings
Active Conversation
Active Mode
```

Advantages:

* No backend database required
* Instant retrieval
* Offline persistence
* Simple deployment

---

# API Request Flow

## Step 1

User submits a query.

```text
Explain Retrieval-Augmented Generation
```

## Step 2

Conversation context is collected.

## Step 3

System prompt is added.

## Step 4

Request is sent.

```javascript
{
    model: model,
    messages: apiMessages,
    stream: false
}
```

## Step 5

Response is received.

## Step 6

Response is stored.

## Step 7

Response is displayed.

---

# Error Handling

The application handles:

### Missing API Key

```text
Please configure API settings first.
```

### Invalid Endpoint

```text
API request failed.
```

### Network Failure

```text
Connection Error
```

### Invalid Response

```text
Invalid response from API
```

---

# User Interface Features

## Sidebar

Features:

* Conversation History
* New Chat Button
* Settings Access
* Mode Access

---

## Top Navigation

Features:

* Current Chat Title
* Current Mode
* Settings Shortcut

---

## Chat Window

Features:

* User Messages
* AI Responses
* Markdown Support
* Code Blocks

---

## Settings Modal

Allows users to configure:

```text
API URL
API Key
Model Name
Context Size
```

---

## Mode Manager

Allows:

* Create Mode
* Edit Mode
* Delete Mode
* Switch Mode

---

# Technical Challenges

## Challenge 1

Managing multiple conversations without a backend.

### Solution

Store conversations in localStorage using unique chat IDs.

---

## Challenge 2

Supporting multiple AI personalities.

### Solution

Implement a prompt-driven mode system.

---

## Challenge 3

Managing context efficiently.

### Solution

Configurable context window size.

---

## Challenge 4

Supporting multiple model providers.

### Solution

Configurable API endpoint architecture.

---

# What I Learned

This project provided hands-on experience in:

## AI Engineering

* Prompt Engineering
* Context Management
* LLM APIs
* Model Configuration

## Frontend Development

* State Management
* DOM Manipulation
* Responsive Design
* Local Storage

## Software Engineering

* System Design
* Error Handling
* Extensibility
* Scalability Planning

---

# Future Improvements

## Backend Integration

Move storage from localStorage to a database.

---

## User Authentication

Support multiple users.

---

## Streaming Responses

Display tokens as they are generated.

---

## Voice Assistant

Integrate:

* Speech-to-Text
* Text-to-Speech

---

## File Upload Support

Allow:

* PDF Analysis
* Document QA
* Image Understanding

---

## Retrieval-Augmented Generation (RAG)

Support:

* Knowledge Bases
* Embeddings
* Vector Databases

---

# Explanation (2 Minutes)

I developed a customizable AI Assistant application that allows users to interact with Large Language Models through a ChatGPT-like interface. The system supports multiple conversations, configurable AI modes, local persistence, and integration with different AI providers through configurable APIs.

One of the main features is the Mode System, where different system prompts allow the same model to behave as an ELI5 explainer, technical tutor, interview coach, or general assistant. I also implemented context window management to reduce token usage and improve performance.

The project helped me gain practical experience in prompt engineering, conversation management, frontend architecture, API integration, local storage persistence, and user experience design. It also provided insight into how modern AI assistants are built and deployed.

---

# Technologies Used

* HTML5
* CSS3
* JavaScript
* Local Storage
* REST APIs
* Markdown Rendering
* OpenAI-Compatible APIs
* Gemini APIs
* LLM Models

---

# Author

**Prakhar Pathak**

Engineering | AI & Machine Learning | Software Development

---

**If you found this project interesting, feel free to star the repository and connect with me.**
