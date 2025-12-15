# Intern_assessment_fynd
Fynd AI Intern Assessment

AI-Powered Review Intelligence System

🔗 Live App: https://fynd-ai-intern-5moe.onrender.com

🔗 Admin Dashboard: https://fynd-ai-intern-5moe.onrender.com/admin

Overview

This project explores how prompt engineering choices impact accuracy, reliability, and structured outputs of large language models, and applies those learnings to build a production-style AI feedback dashboard.

The system:

Predicts Yelp star ratings using different prompting strategies

Generates AI responses, summaries, and action items for reviews

Provides a web-based admin dashboard for analysis and decision support

The focus is on prompt design, evaluation rigor, and system correctness, not model training.

Tasks Breakdown
Task 1 — Prompt Engineering & Evaluation

Goal:
Evaluate how different prompt designs affect:

Accuracy (Predicted vs Actual)

JSON validity rate

Reliability and consistency

Prompting Strategies Implemented

Zero-Shot Prompting

Direct instruction without examples

Baseline performance

Few-Shot Prompting

Includes labeled examples to anchor sentiment extremes

Improves prediction consistency

Criteria-Based Prompting (Safe Reasoning)

Internal reasoning based on polarity, intensity, specificity

Prevents chain-of-thought leakage

Produces stable structured outputs

Dataset

Yelp Reviews Dataset

Randomly sampled 100 reviews (rate-limit aware)

Columns used: text, stars

Evaluation Metrics

Accuracy (%)

JSON Validity (%)

Successful-call–aware computation (guards against API failures)

Key Insight

Few-shot prompting improved accuracy by anchoring sentiment extremes, while criteria-based prompting showed better consistency at the cost of slightly longer latency.

Task 2 — AI-Powered Feedback Dashboard

Goal:
Build a web-based system that:

Accepts customer feedback

Generates AI-driven insights

Enables admin-side analysis

System Architecture

Flow

User → FastAPI → LLM (Groq) → MongoDB → Admin Dashboard


Key Design Principles

LLM treated as a stateless inference layer

Backend controls validation, prompting, and persistence

Admin dashboard is read-only (no AI calls on load)

Structured JSON enforced at all stages

Tech Stack
Component	Choice	Reason
Backend	FastAPI	Async, clean API design
LLM	Groq (LLaMA-3.3-70B)	Low-latency inference
Orchestration	LangChain	Prompt control + JSON parsing
Database	MongoDB Atlas	Flexible schema for AI outputs
Frontend	HTML + Tailwind CSS + JS	Lightweight, fast UI
Deployment	Render	Free, reliable hosting
Features
User Dashboard

Submit rating and review

Receive AI-generated response instantly

Admin Dashboard

Fynd-inspired UI

Displays:

Rating

Timestamp (UTC)

Full expandable review

AI summary

Recommended actions

Client-side:

Sorting (date, rating)

Filtering (by star rating)

Security & Best Practices

API keys stored via environment variables

.env excluded from version control

No secrets in code, notebooks, or README

JSON-only LLM outputs enforced

Limitations

API rate limits constrain large-scale evaluation

No authentication or role-based access

No trend analytics or keyword search (yet)

Future Improvements

Sentiment trend dashboards

Keyword-based admin search

Role-based access control

Cost-aware batching and async inference

Automated evaluation pipelines

Conclusion

This project demonstrates:

Practical prompt engineering

Honest evaluation under real-world constraints

Production-oriented system design

Clear separation between AI logic and UI

The emphasis throughout was on correctness, reliability, and clarity, rather than maximizing raw accuracy at the expense of robustness.

Setup (Local)
git clone https://github.com/your-username/fynd-ai-intern-assessment
cd fynd-ai-intern-assessment
pip install -r requirements.txt
uvicorn app.main:app --reload


Set environment variables:

GROQ_API_KEY=your_key
MONGO_URI=your_mongo_uri

