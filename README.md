# ⚡ PromptMaster AI

> **Learn. Prompt. Practice. Optimize.**  
> A modern, responsive full-stack educational AI web application for learning and mastering **Prompt Engineering**, **Natural Language Processing (NLP)**, **Machine Learning**, and **Large Language Models (LLMs)**.

---

## 📖 1. Project Overview

**PromptMaster AI** is an interactive platform built for software developers, AI practitioners, researchers, and students. The application demystifies generative AI by transforming prompt engineering from intuitive trial-and-error into an empirical engineering discipline.

Students can study foundational transformer architecture, converse with an educational AI chatbot, test and score prompts against automated rubrics, synthesize production-grade prompts using the 4-tier Role-Task-Constraint-Format paradigm, evaluate model completions for hallucination risks, and take topic quizzes.

---

## 🌟 2. Key Features

- **🎓 7 Comprehensive Learning Modules**:
  1. *Prompt Engineering Fundamentals* (Tokens, In-Context Learning, Context Windows, Temperature)
  2. *LLM Models & Architecture* (Transformers, Self-Attention, BPE Tokenization, Model Families)
  3. *Types of Prompts & Applications* (Zero-Shot, One-Shot, Few-Shot, Role-Based, Instruction, Structured JSON, Contextual)
  4. *Effective Prompting Strategies* (Chain-of-Thought, Reflection Loops, Least-to-Most Decomposition)
  5. *Fine-Tuning & Prompt Optimization* (Prompting vs RAG vs Fine-Tuning, Parameter Calibration)
  6. *Evaluation & Bias Mitigation* (Accuracy, Hallucination Risk, Safety, Fairness, Counterfactual Audits)
  7. *Real-World Applications & Case Studies* (Education, Healthcare, Software Engineering, Support, Banking, Hiring)
- **🤖 Modern AI Chatbot Assistant**:
  - Conversational educational tutor adhering strictly to Socratic pedagogy:
    1. Simple Explanation
    2. Technical Concept
    3. Practical Example
    4. When It Is Useful
    5. Important Limitations & Safety
  - Conversation history, message persistence in SQLite, copy response, regenerate, and quick topic pre-fills.
  - Connects to any OpenAI-compatible API (`LLM_API_KEY`, `LLM_BASE_URL`, `LLM_MODEL`).
  - Seamless fallback to PromptMaster's built-in educational engine when no API key is supplied.
- **🧪 Interactive Prompt Practice Lab**:
  - Benchmark challenges (Research Paper Summarizer, Support Triage, Sentiment Classifier, Security Audit, JSON Extractor, plus Custom Challenges).
  - Multi-metric automated evaluation scoring prompts across **Clarity**, **Context**, **Specificity**, **Constraints**, and **Output Format** (Score / 100).
  - Concrete suggestions for improvement, an AI optimized rewrite, and a simulated LLM completion preview.
- **⚡ Production Prompt Generator & Refactorer**:
  - Interactive parameter inputs (Task, Role, Audience, Context, Constraints, Desired Format, Goal).
  - Instant presets (Technical Explainer, JSON Extractor, Executive Briefing).
  - Output copy, automated improvement, and persistence to user's saved templates.
- **📊 AI Response Evaluator**:
  - Audit model outputs on Accuracy, Relevance, Clarity, Completeness, Consistency, Hallucination Risk (Low/Med/High), and Safety Classification (Safe/Caution/Unsafe).
  - Preloaded test cases covering clinical safety, historical fact-checking, and algorithmic performance.
- **⚖️ Bias & Safety Mitigation Playground**:
  - Analysis of bias vectors: pretraining skew, confirmation bias, representation gaps.
  - Interactive side-by-side prompt debiasing comparison (ambiguous hiring & credit prompts vs debiased objective rubrics).
- **📝 Interactive Quiz System**:
  - Topic-by-topic quizzes and a Master Comprehensive Quiz.
  - Multiple choice, True/False, and scenario-based questions.
  - Immediate grading, answer explanations, and recommended study areas.
- **🔐 Secure Authentication & Profile**:
  - PBKDF2 HMAC-SHA256 salted password hashing (zero plain-text storage).
  - JWT token-based authentication.
  - One-click demo access for effortless evaluation.
  - Student profile displaying earned badges, quiz score averages, and saved templates.

---

## 🛠️ 3. Technology Stack

### Frontend
- **React.js 19**
- **Vite 6**
- **Tailwind CSS 3**
- **React Router 7**
- **Axios** (with JWT Bearer interceptor)
- **Lucide React** (modern iconography)

### Backend
- **Python 3.10+** (Tested on Python 3.14)
- **FastAPI**
- **Uvicorn**
- **SQLAlchemy 2.0**
- **PyJWT** (Stateless authentication)
- **HTTPX** (Asynchronous API client)
- **Pydantic 2** (Request/response schema validation)

### Database
- **SQLite** for zero-setup local storage.
- Designed with decoupled SQLAlchemy ORM models ready for one-line migration to **PostgreSQL**.

---

## 📂 4. Project Folder Structure

```text
promptmaster-ai/
├── README.md
├── backend/
│   ├── .env                    # Active environment variables
│   ├── .env.example            # Environment template
│   ├── requirements.txt        # Python dependencies
│   ├── run.py                  # Uvicorn entry point runner
│   ├── test_api.py             # Automated 11-step integration test suite
│   ├── promptmaster.db         # SQLite database (auto-generated)
│   └── app/
│       ├── __init__.py
│       ├── main.py             # FastAPI app, CORS, error handling
│       ├── config.py           # Settings & env loading
│       ├── database.py         # SQLAlchemy engine & session factory
│       ├── models.py           # DB models: User, Conversation, Message, etc.
│       ├── schemas.py          # Pydantic schemas
│       ├── auth.py             # PBKDF2 hashing & JWT utilities
│       ├── services/
│       │   ├── topic_content.py      # Full 7-topic curriculum & quizzes
│       │   ├── llm_service.py        # OpenAI API client & educational fallback
│       │   ├── prompt_evaluator.py   # 5-metric scoring & challenge catalog
│       │   ├── prompt_optimizer.py   # Prompt generator & refactorer
│       │   └── response_evaluator.py # Response quality & safety auditor
│       └── routers/
│           ├── auth.py         # /api/auth (register, login, logout)
│           ├── topics.py       # /api/topics (curriculum & details)
│           ├── chat.py         # /api/chat (conversations & messages)
│           ├── practice.py     # /api/prompt/evaluate & challenges
│           ├── generator.py    # /api/prompt/generate, improve, save
│           ├── evaluation.py   # /api/evaluation/evaluate & samples
│           ├── quiz.py         # /api/quiz/questions, submit, history
│           └── progress.py     # /api/progress & /api/profile
└── frontend/
    ├── index.html
    ├── package.json
    ├── vite.config.js          # Dev server with /api proxy to port 8000
    ├── tailwind.config.js
    ├── postcss.config.js
    └── src/
        ├── main.jsx            # React root & BrowserRouter
        ├── App.jsx             # All route definitions
        ├── index.css           # Tailwind & glassmorphism styles
        ├── api/
        │   └── client.js       # Axios client with JWT interceptor
        ├── context/
        │   └── AuthContext.jsx # Auth state, login, demo student access
        ├── components/
        │   ├── Navbar.jsx      # Top status bar & quick action links
        │   ├── Sidebar.jsx     # Responsive platform navigation
        │   ├── Layout.jsx      # App shell wrapper
        │   ├── TopicCard.jsx   # Curriculum module preview cards
        │   ├── Badge.jsx       # Status and taxonomy badges
        │   ├── CodeBlock.jsx   # Syntax container with copy button
        │   ├── LoadingSpinner.jsx
        │   └── Modal.jsx       # Saved prompt dialog
        └── pages/
            ├── LandingPage.jsx         # / (Hero, showcase, features)
            ├── DashboardPage.jsx       # /dashboard (Student metrics)
            ├── LearnOverviewPage.jsx   # /learn (All 7 modules)
            ├── TopicDetailPage.jsx     # /learn/:topicId (Deep dive & quiz)
            ├── ChatPage.jsx            # /chat (AI Chatbot assistant)
            ├── PracticeLabPage.jsx     # /practice (Prompt evaluator)
            ├── PromptGeneratorPage.jsx # /prompt-generator (Synthesis)
            ├── PromptTypesPage.jsx     # /prompt-types (Taxonomy guide)
            ├── LLMModelsPage.jsx       # /llm-models (Architecture & tokens)
            ├── StrategiesPage.jsx      # /strategies (10 rules & diffs)
            ├── OptimizationPage.jsx    # /optimization (PE vs Fine-tuning)
            ├── EvaluationPage.jsx      # /evaluation (Safety & accuracy)
            ├── BiasMitigationPage.jsx  # /bias (Debiasing playground)
            ├── CaseStudiesPage.jsx     # /case-studies (6 industry cases)
            ├── QuizPage.jsx            # /quiz (Assessment engine)
            ├── LoginPage.jsx           # /login
            ├── RegisterPage.jsx        # /register
            └── ProfilePage.jsx         # /profile (Badges & history)
```

---

## 🚀 5. Installation & Setup

### Prerequisites
- **Python**: Version 3.10 or higher (Python 3.14 fully supported)
- **Node.js**: Version 18.0 or higher (Node.js 24 LTS verified)
- **npm**: Version 9.0 or higher

---

### Step 1: Clone or Navigate to the Project

```bash
cd C:\Users\Abhilash\.gemini\antigravity\scratch\promptmaster-ai
```

---

### Step 2: Configure Environment Variables

Navigate to the `backend/` folder and inspect or modify `.env`:

```env
# AI / LLM Configuration
LLM_API_KEY=your_api_key
LLM_BASE_URL=https://api.openai.com/v1
LLM_MODEL=gpt-4o-mini

# Database
DATABASE_URL=sqlite:///./promptmaster.db

# Authentication
JWT_SECRET=super-secret-key-for-promptmaster-ai-learning-platform
```

> **Note on AI API Key**: If `LLM_API_KEY` is left as `your_api_key` or left blank, PromptMaster AI automatically runs in **Built-in Knowledge Engine Mode**. All educational explanations, chat responses, prompt scores, and evaluations work immediately without external internet API dependencies!

---

### Step 3: Install Backend Dependencies

```bash
cd backend
python -m pip install -r requirements.txt
```

---

### Step 4: Run the Backend Integration Test Suite

Verify that all 11 core subsystems operate properly:

```bash
python test_api.py
```

Expected output:
```text
=== PromptMaster AI Integration Test Suite ===
[PASS] Health Check: {'status': 'healthy', 'app': 'PromptMaster AI', 'version': '1.0.0', 'llm_configured': False}
[PASS] Topics List: 7 topics retrieved
[PASS] Topic Detail: Fundamentals module verified
[PASS] User Registration
[PASS] User Login
[PASS] Profile Retrieval
[PASS] AI Chat: Assistant replied to zero-shot query
[PASS] Prompt Practice Evaluation: Prompt scored 76/100
[PASS] Prompt Generator
[PASS] Saved Prompt
[PASS] Saved Prompts List
[PASS] Response Evaluation
[PASS] Quiz Submission
[PASS] Dashboard Progress: 14.3% completed

ALL 11 TEST SUITES PASSED CLEANLY!
```

---

### Step 5: Start the Backend Server

```bash
python run.py
```
*Backend will be running at:* `http://localhost:8000`  
*Swagger API Docs available at:* `http://localhost:8000/docs`

---

### Step 6: Install Frontend Dependencies & Start Frontend

In a separate terminal:

```bash
cd frontend
npm install
npm run dev
```
*Frontend will be running at:* `http://localhost:5173`

---

## 🌐 6. Application Pages & Route Map

| Route | Page Name | Primary Functionality |
| :--- | :--- | :--- |
| `/` | **Landing Page** | Project hero, live naive vs master prompt preview, feature cards, curriculum preview, workflow overview |
| `/dashboard` | **Student Dashboard** | Overall progress, completed modules, quiz averages, recent chat sessions, and recommended topics |
| `/learn` | **Curriculum Overview** | Grid of all 7 educational modules with live search filtering and direct jump links |
| `/learn/:topicId` | **Topic Deep Dive** | Concept cards, technical explanations, bad/good prompt comparisons, best practices, mistakes, and mini quizzes |
| `/chat` | **AI Chatbot** | Modern assistant UI with conversation history, suggested prompt chips, copy, regenerate, and clear chat |
| `/practice` | **Prompt Practice Lab** | Interactive challenge lab with automated 5-dimension rubric scoring (/100), suggestions, and simulated LLM output |
| `/prompt-generator` | **Prompt Generator** | 4-tier structured prompt synthesis tool with industry presets and saved templates manager |
| `/prompt-types` | **Prompt Types Module** | Interactive taxonomy explorer (Zero-shot, Few-shot, Role-based, Structured JSON, Contextual) |
| `/llm-models` | **LLM Models Module** | High-level architecture explanation, live Tokenizer & Cost Calculator, and neutral model family profiles |
| `/strategies` | **Strategies Module** | 10 prompt engineering rules and interactive Bad vs Improved prompt comparison showcase |
| `/optimization` | **Optimization Module**| Prompt Engineering vs RAG vs Fine-Tuning matrix and interactive hyperparameter simulator (Temp, Top-P, Max Tokens) |
| `/evaluation` | **Response Evaluation**| Multi-dimensional evaluator measuring accuracy, relevance, clarity, hallucination risk, and safety ratings |
| `/bias` | **Bias Mitigation** | Algorithmic bias vectors and interactive before-and-after prompt debiasing comparisons |
| `/case-studies` | **Case Studies** | 6 deep-dive enterprise industry case studies (Healthcare, Education, Code, Banking, Support, Hiring) |
| `/quiz` | **Quiz System** | Topic-filtered and Master comprehensive quizzes with immediate grading, explanations, and review tips |
| `/profile` | **Student Profile** | Badges earned, past quiz/practice attempts, and saved prompt templates management |
| `/login` & `/register` | **Authentication** | Secure salted password authentication with one-click demo student access |

---

## 🤖 7. Example Chatbot Questions to Try

When exploring `/chat`, try asking:
1. *"What is the difference between zero-shot and few-shot prompting?"*
2. *"Can you explain how Chain-of-Thought prompting works with an arithmetic example?"*
3. *"How can I prevent an LLM from hallucinating when summarizing company policies?"*
4. *"When should an engineering team use fine-tuning instead of prompt engineering?"*
5. *"How do I format a prompt to guarantee valid JSON output for my backend API?"*

---

## 🧪 8. Example Prompt Practice Challenges

When practicing in `/practice`:
- **Challenge 1 (Research Paper Summarizer)**:  
  *Goal:* "Write a prompt that asks an AI to summarize a research paper in five bullet points."  
  *Try entering:*  
  `You are a senior academic research assistant. Summarize the key findings of the attached research paper into exactly five bullet points. Focus on: (1) Core hypothesis, (2) Methodology, (3) Main finding, (4) Practical implications, and (5) Limitations. Limit each bullet point to 30 words.`
- **Challenge 2 (Customer Support Triage)**:  
  *Goal:* Classify urgency, extract primary complaints, and draft an empathetic reply in JSON format.
- **Challenge 3 (Few-Shot Sentiment Classifier)**:  
  *Goal:* Provide 2 input-output demonstrations to classify customer feedback into [POSITIVE, NEGATIVE, MIXED] with a 1-sentence rationale.

---

## 🛡️ 9. Security & Error Handling

- **Never Exposes Secrets**: The frontend code contains zero references to `LLM_API_KEY`. All LLM calls and evaluation logic are routed through FastAPI.
- **Password Protection**: Uses standard `hashlib.pbkdf2_hmac` with 100,000 iterations and a cryptographically secure 16-byte random salt.
- **Safe Global Exceptions**: FastAPI intercepts unhandled exceptions to return friendly JSON errors, preventing server stack trace leaks.
- **Prompt Size Bounds**: Request payloads enforce Pydantic string bounds (`max_length=10000`) to mitigate denial-of-service and buffer exhaustion attacks.
- **Defensive Delimiters**: Prompts utilize XML delimiters (`<context>`, `<rules>`) to shield systems against prompt injection attacks.

---

## 🐘 10. Database Migration to PostgreSQL

The database layer utilizes SQLAlchemy ORM models (`app/models.py`). To switch from SQLite to PostgreSQL:

1. Install psycopg2 or asyncpg:
   ```bash
   pip install psycopg2-binary
   ```
2. In `backend/.env`, update the database URL:
   ```env
   DATABASE_URL=postgresql://user:password@localhost:5432/promptmaster
   ```
3. Restart the backend: `Base.metadata.create_all(bind=engine)` will automatically generate all tables in PostgreSQL.

---

## 🔮 11. Future Roadmap

- Real-time token streaming via Server-Sent Events (SSE).
- Multi-model playground comparing side-by-side responses from multiple providers simultaneously.
- DSPy pipeline integration for automated prompt optimization against validation datasets.
- Export prompt templates directly as Python/TypeScript SDK snippets.

---

## 📄 License
MIT License. Built for educational and professional AI development.
