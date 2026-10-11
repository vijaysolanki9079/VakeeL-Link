# VakeelLink ⚖️

**VakeelLink is an AI-powered Indian legal research and consultation platform that helps users understand legal topics, find lawyers, manage cases, and communicate securely with legal professionals.**

The platform combines Retrieval-Augmented Generation (RAG), Indian case law, statutes, lawyer discovery, consultations, secure messaging, and role-based dashboards in one application.

> **Disclaimer:** VakeelLink is a research and assistance platform. AI-generated responses are not a substitute for professional legal advice from a qualified advocate.

---

## ✨ Features

### 🤖 AI Legal Assistant

- Ask questions about Indian law in natural language.
- Search legal case law, statutes, and legal documents.
- Uses Retrieval-Augmented Generation for context-aware responses.
- Provides citations from retrieved legal sources.
- Supports multiple legal domains, including:
  - Constitutional Law
  - Criminal Law
  - Consumer Law
  - Family Law
  - Labour Law
  - Motor Accident Law
- Uses Groq as the primary LLM provider.
- Uses Google Gemini as a fallback provider.
- Supports retrieval-only responses when LLM services are unavailable.
- Displays confidence scores, legal domains, citation sources, and disclaimers.

### 👨‍⚖️ Lawyer Directory

- Browse registered lawyers.
- Search lawyers by specialization and location.
- View lawyer profiles and experience.
- View ratings, reviews, availability, and consultation fees.
- Receive lawyer recommendations based on the legal query domain.

### 📅 Legal Consultations

- Request consultations with lawyers.
- Track consultation status.
- Support for chat-based consultations.
- Schedule consultation details.
- Manage active, pending, completed, and cancelled consultations.

### 💬 Secure Messaging

- Client–lawyer messaging.
- Real-time consultation chat support through WebSockets.
- Message history stored securely.
- Archived consultation conversations.

### 📂 Case and Document Management

- Create and manage legal case records.
- Store case-related documents.
- Archive case documents and consultation records.
- Support for evidence, case briefs, and legal documents.

### 🔐 Authentication and Authorization

- Supabase Authentication integration.
- Role-based access control for:
  - Clients
  - Lawyers
  - Administrators
- Protected dashboards and routes.
- JWT-based authorization.
- Row-Level Security policies for user data protection.

### 🛠️ Admin Features

- Manage users and lawyer profiles.
- Review lawyer applications.
- Handle reported issues.
- Manage notifications.
- Monitor consultations and platform activity.

---

## 🧱 Technology Stack

### Frontend

| Technology | Purpose |
|---|---|
| React 19 | User interface development |
| Vite 8 | Frontend build tool and development server |
| React Router 7 | Client-side routing |
| Framer Motion | Animations and page transitions |
| Lucide React | Icons |
| JavaScript / JSX | Frontend programming language |

### Backend

| Technology | Purpose |
|---|---|
| Python 3.11–3.13 | Backend programming language |
| FastAPI | REST API framework |
| Uvicorn | ASGI server |
| Pydantic | Data validation and settings management |
| SlowAPI | API rate limiting |
| Python-Jose | JWT authentication |
| HTTPX | HTTP client requests |
| Python Multipart | File and form-data handling |

### Database and Authentication

| Technology | Purpose |
|---|---|
| Supabase | Authentication and backend services |
| PostgreSQL | Relational database |
| Supabase Row-Level Security | Database access control |
| SQL | Database schema, indexes, policies, and seed data |

### Artificial Intelligence and Search

| Technology | Purpose |
|---|---|
| Groq | Primary large language model provider |
| Llama 3.3 70B | Primary AI model |
| Llama 3.1 8B | Groq fallback model |
| Google Gemini | Secondary AI provider |
| Qdrant Cloud | Vector database |
| Sentence Transformers | Legal document embeddings |
| `all-MiniLM-L6-v2` | Default embedding model |
| NumPy | Local vector-store fallback |

### Deployment and Infrastructure

| Technology | Purpose |
|---|---|
| Render | Backend deployment |
| Vercel | Frontend deployment |
| WebSockets | Real-time consultation messaging |
| GitHub | Source code management |

---

## 🏗️ System Architecture

```text
User
 │
 ▼
React Frontend
 │
 │ REST API / WebSocket
 ▼
FastAPI Backend
 │
 ├── Supabase Authentication
 ├── PostgreSQL Database
 ├── Lawyer Directory
 ├── Consultation Management
 ├── Messaging System
 └── AI Legal Research Pipeline
       │
       ├── Query Classification
       ├── Sentence Transformer Embeddings
       ├── Qdrant Vector Search
       ├── Local NumPy Vector Store Fallback
       ├── Groq LLM
       ├── Google Gemini Fallback
       └── Citation Generation
```

---

## 🧠 AI and RAG Pipeline

When a user asks a legal question, VakeelLink processes it through the following pipeline:

```text
User Legal Query
      │
      ▼
Legal Domain Classification
      │
      ▼
Query Embedding
      │
      ▼
Vector Search
      │
      ├── Qdrant Cloud
      └── Local NumPy Vector Store
      │
      ▼
Relevant Legal Sections and Cases
      │
      ▼
Context and Citation Preparation
      │
      ▼
Groq LLM Response Generation
      │
      ├── Gemini fallback if Groq fails
      └── Retrieval-only response if both fail
      │
      ▼
Structured Legal Response with Citations
```

The AI response may include:

- Legal analysis
- Summary
- Facts and issues
- Conclusion
- Cited sections
- Cited cases
- Cited acts
- Citation excerpts
- Confidence score
- Legal domain
- Retrieval status
- Recommended lawyers
- Legal disclaimer

---

## 📁 Project Structure

```text
VakeeL-Link/
└── Vakeel-link-main/
    ├── backend/
    │   ├── app/
    │   │   ├── api/
    │   │   │   └── routers/
    │   │   │       ├── auth.py
    │   │   │       ├── ai.py
    │   │   │       ├── lawyers.py
    │   │   │       ├── cases.py
    │   │   │       ├── consultations.py
    │   │   │       ├── messaging.py
    │   │   │       ├── users.py
    │   │   │       ├── chat.py
    │   │   │       └── admin.py
    │   │   ├── core/
    │   │   │   ├── config.py
    │   │   │   ├── limiter.py
    │   │   │   └── Supabase configuration
    │   │   ├── services/
    │   │   │   ├── rag/
    │   │   │   ├── retrieval/
    │   │   │   └── AI services
    │   │   ├── middleware/
    │   │   └── main.py
    │   ├── requirements.txt
    │   ├── requirements-render.txt
    │   ├── .env.example
    │   └── supabase_schema.sql
    │
    ├── frontend/
    │   ├── src/
    │   │   ├── components/
    │   │   ├── pages/
    │   │   │   ├── LandingPage
    │   │   │   ├── Login
    │   │   │   ├── Signup
    │   │   │   ├── AIAssistant
    │   │   │   ├── LawyerDirectory
    │   │   │   ├── LawyerProfile
    │   │   │   ├── UserDashboard
    │   │   │   ├── LawyerDashboard
    │   │   │   ├── CaseSearch
    │   │   │   ├── CaseCurator
    │   │   │   ├── Consultations
    │   │   │   ├── MyCases
    │   │   │   ├── Statutes
    │   │   │   ├── Archive
    │   │   │   └── Profile
    │   │   ├── App.jsx
    │   │   └── main.jsx
    │   ├── package.json
    │   ├── vite.config.js
    │   └── .env.example
    │
    ├── generate_embeddings.py
    ├── upload_to_qdrant.py
    ├── render.yaml
    ├── DEPLOY.md
    └── README.md
```

---

## ✅ Prerequisites

Install the following before running the project:

- Node.js 20 or later
- npm
- Python 3.11, 3.12, or 3.13
- Git
- A Supabase project
- A Groq API key
- A Qdrant Cloud project and API key
- Optional: Google Gemini API key

---

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/vijaysolanki9079/VakeeL-Link.git
cd VakeeL-Link/Vakeel-link-main
```

---

### 2. Configure the backend

```bash
cd backend
```

Create a virtual environment:

#### Windows

```powershell
python -m venv venv
venv\Scripts\activate
```

#### macOS/Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

Install Python dependencies:

```bash
python -m pip install -r requirements.txt
```

Create the environment file:

#### Windows

```powershell
copy .env.example .env
```

#### macOS/Linux

```bash
cp .env.example .env
```

Open `backend/.env` and add your credentials.

---

### 3. Configure the frontend

Open a second terminal:

```bash
cd VakeeL-Link/Vakeel-link-main/frontend
npm install
```

Create the frontend environment file:

#### Windows

```powershell
copy .env.example .env
```

#### macOS/Linux

```bash
cp .env.example .env
```

Set the backend API URL in `frontend/.env`:

```env
VITE_API_URL=http://127.0.0.1:8000
```

---

## 🔐 Environment Variables

### Backend Environment Variables

Create a file at:

```text
Vakeel-link-main/backend/.env
```

Example configuration:

```env
# Application
PROJECT_NAME=VakeelLink API
ENVIRONMENT=development
API_V1_STR=/api/v1

# CORS
CORS_ORIGINS=http://127.0.0.1:5173,http://localhost:5173

# Supabase
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key

# Authentication
JWT_SECRET=your_secure_jwt_secret

# Groq
GROQ_API_KEY=your_groq_api_key

# Google Gemini - optional fallback
GOOGLE_API_KEY=your_google_api_key
GEMINI_API_KEY=your_gemini_api_key

# Qdrant
QDRANT_URL=https://your-qdrant-cluster-url
QDRANT_API_KEY=your_qdrant_api_key

# Embeddings
EMBEDDING_MODEL_NAME=sentence-transformers/all-MiniLM-L6-v2

# Vector store
USE_LOCAL_VECTOR_STORE=true
LOCAL_EMBEDDINGS_DIR=./embeddings
LOCAL_CORPUS_DIR=./corpus

# RAG configuration
RAG_MIN_HITS=3
RAG_SCORE_FLOOR=0.35
RAG_BROADEN=true
RAG_BLEND_LOCAL=true
```

### Frontend Environment Variables

Create a file at:

```text
Vakeel-link-main/frontend/.env
```

```env
VITE_API_URL=http://127.0.0.1:8000
```

> Never commit real API keys, Supabase service-role keys, or private credentials to GitHub.

---

## 🗄️ Database Setup

1. Create a project in Supabase.
2. Open the Supabase SQL Editor.
3. Copy the contents of:

```text
backend/supabase_schema.sql
```

4. Run the SQL script.
5. Confirm that the required tables and policies were created.

The schema includes tables for:

- User profiles
- Lawyers
- Lawyer availability
- Lawyer reviews
- Consultations
- Query history
- AI citations
- Chat sessions
- Chat messages
- Archived chats
- Archived documents
- Notifications
- Reported issues

The database also includes Row-Level Security policies for protecting user-specific data.

---

## ▶️ Running the Application

### Start the backend

From the `backend` directory:

```bash
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
```

Backend URLs:

| Service | URL |
|---|---|
| API | http://127.0.0.1:8000 |
| Health check | http://127.0.0.1:8000/health |
| RAG health check | http://127.0.0.1:8000/health/rag |
| API documentation | http://127.0.0.1:8000/docs |
| ReDoc | http://127.0.0.1:8000/redoc |

### Start the frontend

From the `frontend` directory:

```bash
npm run dev
```

Frontend URL:

```text
http://127.0.0.1:5173
```

---

## 🧪 Available Scripts

### Frontend

```bash
npm run dev
```

Starts the Vite development server.

```bash
npm run build
```

Creates a production build.

```bash
npm run preview
```

Previews the production build locally.

```bash
npm run lint
```

Runs ESLint checks.

### Backend

```bash
python -m uvicorn app.main:app --reload
```

Starts the FastAPI development server.

```bash
python -m pip install -r requirements.txt
```

Installs backend dependencies.

---

## 🔌 API Overview

### Authentication

```text
/api/v1/auth
```

Handles:

- User registration
- User login
- Authentication
- Role management

### Users

```text
/api/v1/users
```

Handles:

- User profiles
- Profile updates
- User information

### Lawyers

```text
/api/v1/lawyers
```

Handles:

- Lawyer listing
- Lawyer profiles
- Lawyer search
- Lawyer recommendations
- Lawyer applications

### AI Legal Research

```text
/api/v1/query
/api/v1/query/ask
```

Example request:

```http
POST /api/v1/query/ask
Content-Type: application/json
```

Example body:

```json
{
  "query": "What are my rights if a company refuses to refund a defective product in India?"
}
```

### Consultations

```text
/api/v1/consultations
```

Handles:

- Consultation requests
- Consultation status
- Scheduling
- Lawyer-client consultation workflows

### Messaging

```text
/api/v1/messages
/api/v1/chat
```

Handles:

- Consultation messages
- AI assistant chat sessions
- Real-time WebSocket communication

### Cases

```text
/api/v1/cases
```

Handles:

- Legal case records
- Case information
- Case management

### Administration

```text
/api/v1/admin
```

Handles:

- Platform administration
- Lawyer verification
- Reported issues
- User and consultation management

---

## 🧭 Frontend Routes

| Route | Description |
|---|---|
| `/` | Landing page |
| `/login` | User login |
| `/signup` | User registration |
| `/lawyers` | Lawyer directory |
| `/lawyers/:id` | Lawyer profile |
| `/dashboard/user` | Client dashboard |
| `/dashboard/lawyer` | Lawyer dashboard |
| `/assistant` | AI legal assistant |
| `/case-search` | Legal case search |
| `/case-curator` | Case curation tools |
| `/statutes` | Legal statutes |
| `/archive` | Archived records |
| `/my-cases` | Lawyer case management |
| `/consultations` | Consultation management |
| `/profile` | User profile |
| `/pricing` | Pricing page |

---

## 📚 Legal Data and Embeddings

VakeelLink supports both cloud and local vector search.

### Qdrant Cloud

Qdrant can be used to store and search legal document embeddings remotely.

Expected legal collection names include:

```text
legal_constitutional
legal_criminal
legal_consumer
legal_family
legal_labour
legal_motor_accident
```

### Local Vector Store

The project also supports a local NumPy-based vector store for development and fallback operation.

Configure it using:

```env
USE_LOCAL_VECTOR_STORE=true
LOCAL_EMBEDDINGS_DIR=./embeddings
LOCAL_CORPUS_DIR=./corpus
```

### Generate Embeddings

```bash
python generate_embeddings.py
```

### Upload Embeddings to Qdrant

```bash
python upload_to_qdrant.py
```

Make sure your Qdrant collection names match the legal domain names expected by the application.

---

## 🚢 Deployment

### Backend Deployment with Render

The repository includes a `render.yaml` configuration file for deploying the FastAPI backend to Render.

Typical settings:

```text
Runtime: Python
Start command: uvicorn app.main:app --host 0.0.0.0 --port $PORT
Health check: /health
```

Add the following environment variables in the Render dashboard:

```text
SUPABASE_URL
SUPABASE_KEY
SUPABASE_SERVICE_ROLE_KEY
JWT_SECRET
QDRANT_URL
QDRANT_API_KEY
GROQ_API_KEY
GOOGLE_API_KEY
CORS_ORIGINS
```

### Frontend Deployment with Vercel

For Vercel deployment:

1. Import the repository into Vercel.
2. Set the project root to:

```text
Vakeel-link-main/frontend
```

3. Add the following environment variable:

```env
VITE_API_URL=https://your-backend-url.com
```

4. Deploy the project.

---

## 🩺 Health Checks

Check whether the backend is running:

```bash
curl http://127.0.0.1:8000/health
```

Expected response:

```json
{
  "status": "ok",
  "service": "VakeelLink API"
}
```

Check the AI and data services:

```bash
curl http://127.0.0.1:8000/health/rag
```

This endpoint provides information about:

- Embedding configuration
- Groq availability
- Gemini availability
- Qdrant connectivity
- Supabase connectivity
- Local vector-store availability
- Degraded service conditions

---

## 🛡️ Security Guidelines

- Never commit `.env` files.
- Never expose the Supabase service-role key in the frontend.
- Keep secret API keys only in backend environment variables.
- Use strong values for `JWT_SECRET`.
- Configure CORS for trusted frontend domains only.
- Rotate API keys if they are accidentally exposed.
- Review Supabase Row-Level Security policies before production use.
- Do not treat AI responses as final legal advice.
- Validate uploaded documents before storing them.
- Apply additional authentication and authorization checks before production deployment.

---

## 🐛 Troubleshooting

### Frontend cannot connect to backend

Verify that:

```env
VITE_API_URL=http://127.0.0.1:8000
```

Also make sure the backend is running on port `8000`.

### AI responses contain no citations

Check:

- Qdrant URL and API key
- Qdrant collection names
- Local embeddings directory
- Legal corpus directory
- Embedding model configuration

### Groq authentication error

If you receive an invalid API key error:

1. Generate a new Groq API key.
2. Update `GROQ_API_KEY` in `backend/.env`.
3. Restart the backend server.

### Supabase connection error

Check:

- `SUPABASE_URL`
- `SUPABASE_KEY`
- `SUPABASE_SERVICE_ROLE_KEY`
- Whether the Supabase project is active
- Whether `supabase_schema.sql` has been executed

### Qdrant connection error

Check:

- `QDRANT_URL`
- `QDRANT_API_KEY`
- Collection names
- Whether the Qdrant cluster is active

### npm command fails

Run the command from the frontend directory:

```bash
cd Vakeel-link-main/frontend
npm install
npm run dev
```

---

## 🔮 Future Improvements

- Improve legal document ingestion and processing.
- Add more Indian legal databases and jurisdictions.
- Add multilingual support for Indian languages.
- Improve AI answer evaluation and citation verification.
- Add online payment support for consultations.
- Add video consultation support.
- Add lawyer document verification workflows.
- Add automated legal document generation.
- Improve admin analytics and reporting.
- Add automated testing and continuous integration.
- Add production-grade logging and monitoring.

---

## 🤝 Contributing

Contributions are welcome and appreciated.

### Contribution Workflow

1. Fork the repository.
2. Create a new branch:

```bash
git checkout -b feature/your-feature-name
```

3. Make your changes.
4. Test the frontend and backend.
5. Commit your changes:

```bash
git add .
git commit -m "Add your feature description"
```

6. Push your branch:

```bash
git push origin feature/your-feature-name
```

7. Open a Pull Request.

### Before submitting a Pull Request

- Run frontend linting:

```bash
npm run lint
```

- Verify the backend starts successfully.
- Check API health endpoints.
- Confirm that no secrets are included.
- Update documentation when adding new features.

---

## 📄 License and Project Status

VakeelLink is currently a hackathon/research prototype for Indian legal assistance workflows.

The project is intended for educational, experimental, and development purposes. It should be reviewed and hardened before being used in a production legal-services environment.

---

## 👨‍💻 Author

Developed as an AI-powered legal technology project focused on improving access to Indian legal information and professional consultations.

---

## ⭐ Support the Project

If you find this project useful:

- Give the repository a star.
- Fork the repository.
- Report bugs through GitHub Issues.
- Suggest new features.
- Contribute improvements through Pull Requests.

---

**VakeelLink — Making legal research and lawyer discovery more accessible with AI.**
