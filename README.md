<div align="center">
https://querymind-ai-api.onrender.com  
# ⚡QueryMind AI

### Ask Your Database Questions in Plain English

QueryMind AI is an AI-powered database assistant that converts natural-language questions into SQL queries using the actual database schema.

It supports **SQLite and PostgreSQL** and uses **Google Gemini** to generate SQL queries, explain them, and return database results.

<p>

![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge\&logo=react)
![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=for-the-badge\&logo=vite)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-v4-38B2AC?style=for-the-badge\&logo=tailwindcss)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge\&logo=fastapi)
![Python](https://img.shields.io/badge/Python-3.14-3776AB?style=for-the-badge\&logo=python)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Supported-4169E1?style=for-the-badge\&logo=postgresql)
![SQLite](https://img.shields.io/badge/SQLite-Supported-003B57?style=for-the-badge\&logo=sqlite)
![Gemini](https://img.shields.io/badge/Gemini-AI-4285F4?style=for-the-badge\&logo=google)

</p>

</div>

---

## 📖 Overview

QueryMind AI provides a simple natural-language interface for interacting with databases.

Instead of writing SQL manually:

```sql
SELECT name, salary
FROM employees
ORDER BY salary DESC
LIMIT 5;
```

you can ask:

> "Show me the 5 highest paid employees."

QueryMind AI reads the database schema and uses it to generate the appropriate SQL query.

---

## ✨ Features

### 🔌 Database Connectivity

* SQLite database support
* PostgreSQL support
* Database connection validation
* Database session management
* SQLAlchemy-based database abstraction

### 🗂️ Schema Intelligence

* Automatic schema extraction
* Table and column discovery
* Schema-aware SQL generation
* Prevents AI from inventing tables or columns

### 🤖 AI SQL Generation

* Natural language → SQL
* Google Gemini integration
* Schema-aware prompting
* SQL explanation
* Confidence score
* Structured AI responses

### 🛡️ SQL Safety

QueryMind AI uses multiple layers of SQL validation.

* AI is instructed to generate read-only SQL
* SQL is parsed using `sqlglot`
* Only a single `SELECT` statement is allowed
* `INSERT`, `UPDATE`, `DELETE`, `DROP`, `ALTER`, `CREATE`, and `TRUNCATE` are blocked
* Multiple SQL statements are rejected
* Manually edited queries are also validated before execution

### ▶️ Query Execution

* Execute generated SQL
* Edit SQL before execution
* Execute queries against SQLite
* Execute queries against PostgreSQL
* Display query results
* Handle query errors

---

## 🔄 How It Works

```text
User
  │
  │ Natural-language question
  ▼
React Frontend
  │
  │ REST API
  ▼
FastAPI Backend
  │
  ├── Database Session
  │
  ├── Schema Extraction
  │
  └── AI Service
          │
          ▼
      Google Gemini
          │
          ▼
      Generated SQL
          │
          ▼
      SQL Safety Check
          │
          ▼
    Database Execution
          │
          ▼
        Results
```

---

## 🧠 AI Architecture

QueryMind AI uses an `AIService` abstraction to separate the AI layer from the API.

```text
AIService
   │
   ├── GeminiService
   │       └── Google Gemini
   │
   └── MockAIService
           └── Automated Tests
```

The AI receives:

```text
User Question
+
Database Schema
+
SQL Rules
```

and returns:

```json
{
  "sql": "SELECT ...;",
  "explanation": "Short explanation.",
  "confidence": 0.95
}
```

---

## 🏗️ Database Architecture

QueryMind AI uses a common database adapter interface.

```text
DatabaseAdapter
      │
      ├── SQLiteAdapter
      │
      └── PostgreSQLAdapter
```

Each adapter handles:

* Database connection
* Schema extraction
* Query execution
* Connection closing

---

## 📡 API

### Create Database Session

```http
POST /database/session
```

Supports SQLite and PostgreSQL connections.

### Get Database Schema

```http
POST /database/schema
```

Returns the schema of the connected database.

### Generate SQL

```http
POST /generate
```

Example:

```json
{
  "session_id": "session-id",
  "question": "Show the highest paid employees"
}
```

### Execute Query

```http
POST /database/execute
```

Example:

```json
{
  "session_id": "session-id",
  "sql": "SELECT name, salary FROM employees;"
}
```

---

## ⚡ Tech Stack

**Frontend**

* React
* Vite
* Tailwind CSS
* JavaScript
* REST API

**Backend**

* Python
* FastAPI
* SQLAlchemy
* Pydantic
* Uvicorn
* sqlglot

**Databases**

* SQLite
* PostgreSQL
* Psycopg 3

**AI**

* Google Gemini
* `google-genai`

**Testing**

* Pytest
* FastAPI TestClient
* HTTPX

**Tools**

* Git
* GitHub
* Postman
* VS Code

---

## 📂 Project Structure

```text
QueryMind AI
│
├── assets
├── client
├── database
│   └── samples
├── scripts
├── server
│   ├── app
│   │   ├── ai
│   │   ├── api
│   │   ├── database
│   │   ├── models
│   │   └── main.py
│   │
│   └── tests
│
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

Install:

* Python 3.12+
* Node.js
* npm
* Git
* Gemini API key

### Clone Repository

```bash
git clone https://github.com/Manaswi-Sagiraju/querymind-ai.git
cd querymind-ai
```

### Backend Setup

```bash
cd server

python -m venv venv
```

#### Windows

```powershell
.\venv\Scripts\Activate.ps1
```

Install dependencies:

```bash
python -m pip install -r requirements.txt
```

### Environment Variables

Create:

```text
server/.env
```

Add:

```env
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-2.5-flash-lite
```

> Never commit `.env` or API keys to GitHub.

### Run Backend

```bash
uvicorn app.main:app --reload
```

Backend:

```text
http://127.0.0.1:8000
```

### Frontend Setup

Open another terminal:

```bash
cd client
npm install
npm run dev
```

Open the URL shown by Vite.

---

## 🧪 Running Tests

From the `server` directory:

```bash
python -m pytest
```

Tests cover:

* API endpoints
* Database connections
* SQLite adapter
* PostgreSQL adapter
* SQL safety validation
* Schema extraction
* Database sessions
* Query execution
* AI generation using `MockAIService`

---

## 🛣️ Future Enhancements

* MySQL and additional database support
* User authentication
* Query history
* Audit logs
* Role-based access control
* Controlled write operations
* Database permissions
* Enterprise deployment

---

## 📄 License

This project is licensed under the MIT License.

---

## 👩‍💻 Author

**Manaswi Sagiraju**

B.Tech Computer Science Engineering
MVGR College of Engineering

GitHub: [Manaswi-Sagiraju](https://github.com/Manaswi-Sagiraju)
