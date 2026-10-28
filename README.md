# AI-Powered Customer Support Assistant

## About the Project

I developed this project as part of my AI Engineer Workshop, with the help of AI tools for learning, understanding concepts, debugging errors, and improving my implementation.

My goal was to build a customer support assistant using **React, FastAPI, Python, Groq, Pydantic, and SQLite**. While developing it, I learned how to connect a frontend to a backend, integrate an LLM, validate structured AI output, and maintain conversation history across multiple chat sessions.

This project helped me gain practical experience in building an AI-powered full-stack application.

## Features I Implemented

- **AI Message Classification:** Classifies customer messages into categories such as payment issues, order tracking, greetings, and general questions.
- **Structured Output Validation:** Uses Instructor and Pydantic to validate the AI-generated classification data before the application processes it.
- **AI Response Generation:** Uses a second Groq LLM call to generate helpful responses in Markdown.
- **Conversation Memory:** Stores conversation history in SQLite so the assistant can respond to follow-up questions using previous messages.
- **Session Management:** Uses unique session IDs to keep separate conversations isolated.
- **REST API:** Uses FastAPI to handle requests between the frontend and backend.
- **Interactive Frontend:** Uses React and Vite to provide a chat interface, conversation sidebar, and AI analysis details.
- **Error Handling:** Handles invalid inputs and AI request failures.
- **Token Estimation:** Estimates input token usage for messages.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Backend development |
| FastAPI | Building REST API endpoints |
| Groq | Accessing the LLM |
| Instructor | Requesting structured LLM output |
| Pydantic | Validating request and AI response data |
| SQLite | Storing conversations and messages |
| React | Building the user interface |
| Vite | Frontend development server and build tooling |
| JavaScript / JSX | Frontend logic and components |
| Git and GitHub | Version control and project hosting |

## How the Application Works

Each message follows this workflow:

1. The user enters a message in the React chat interface.
2. The frontend sends the message and session ID to the FastAPI backend.
3. The backend validates the request.
4. The first LLM call classifies the message and returns structured data.
5. Pydantic validates the classification result.
6. The application estimates token usage and retrieves recent conversation history from SQLite.
7. The second LLM call uses the intent analysis and conversation context to generate a response.
8. The application saves the user's message and the assistant's response in SQLite.
9. The backend returns the result to the frontend, where the response and intent details are displayed.

## Key Concepts I Learned

### 1. Structured AI Output

I learned why AI-generated data should be validated before being used by an application. Pydantic schemas help ensure that the classification result contains the expected fields and allowed values.

### 2. LLM Integration

I learned how to call a hosted LLM through Groq and use separate LLM calls for message classification and response generation.

### 3. Conversation Memory

I learned the difference between stateless API requests and an application that maintains conversation history. The backend retrieves previous messages using a session ID and passes relevant context to the LLM.

### 4. Database Integration

I learned how to use SQLite to store conversations and messages, retrieve chat history, and maintain separate chat sessions.

### 5. Frontend and Backend Integration

I learned how a React application communicates with a FastAPI backend through HTTP requests and displays the returned responses.

### 6. Debugging and Testing

I used AI assistance to understand errors, review code, troubleshoot integration issues, and test API behavior during development.

## Project Structure

```text
AI_powered_customer_support_assistant/
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── config.py
│   │   ├── schemas/
│   │   ├── services/
│   │   └── utils/
│   ├── sql/
│   ├── tests/
│   ├── .env.example
│   └── requirements.txt
├── frontend-react/
│   ├── src/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── lib/
│   │   ├── pages/
│   │   └── styles/
│   ├── package.json
│   └── vite.config.js
└── README.md
```

## How to Run the Project

### Prerequisites

- Python 3.10 or newer
- Node.js 18 or newer
- A Groq API key
- Git

### 1. Set Up the Backend

Open a terminal in the project root:

```powershell
cd backend
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

### 2. Configure the Environment

```powershell
Copy-Item .env.example .env
notepad .env
```

Add your own Groq API key and configure the model:

```env
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=openai/gpt-oss-120b
```

Use a valid model supported by your Groq account. Keep the real `.env` file private and never commit your API key.

### 3. Start the Backend

From the `backend` directory, run:

```powershell
uvicorn app.main:app --reload --port 8000
```

Useful endpoints:

- Health check: `http://127.0.0.1:8000/health`
- API documentation: `http://127.0.0.1:8000/docs`
- Conversations: `http://127.0.0.1:8000/api/conversations`

### 4. Start the Frontend

Open a second terminal in the project root:

```powershell
cd frontend-react
npm install
npm run dev
```

Open `http://localhost:5173` in your browser.

## Important Notes

- The assistant provides customer support guidance; it does not directly access real order or payment systems.
- Token counts are estimates, not exact billing figures.
- Schema validation checks the structure of the AI-generated data, not whether every statement is factually correct.
- Conversation history is limited when preparing context for the LLM.
- The Groq API key must remain private.

## My Development Experience

I built this project as a hands-on learning experience, using AI assistance to understand unfamiliar concepts, troubleshoot problems, and improve my code. Working through the implementation helped me understand how the different parts of an AI-powered full-stack application fit together.

My next goal is to continue improving the application, strengthen my understanding of the underlying code, and apply these concepts to more projects.

## Acknowledgement

I used AI tools as a learning and development assistant during this project. They helped me understand concepts, explore implementation approaches, debug errors, and review my work. I used this assistance as part of my learning process while developing the application.
