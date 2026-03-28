# CareerAgent - AI Job Application Copilot

## Overview

AI Job Application Copilot is a human-in-the-loop, agentic system that automates and optimizes the job application process. It ingests job listings, retrieves relevant personal experience using Retrieval-Augmented Generation (RAG), and generates tailored resumes and cover letters for user approval before submission.

This project demonstrates real-world application of LLMs, RAG pipelines, and agent-based workflows.

---

## Problem Statement

Applying to jobs is repetitive, time-consuming, and often inefficient:

* Manual CV tailoring for each job
* Generic applications reduce response rate
* Hard to track applications and progress
* Rewriting similar content repeatedly

This project solves these issues by automating the preparation phase while keeping humans in control of final submission.

---

## Key Features

* Job ingestion (manual input, email parsing, APIs)
* Personal knowledge base (CV, projects, skills)
* RAG-based retrieval of relevant experience
* Tailored resume generation
* Cover letter generation
* Job fit scoring and reasoning
* Human-in-the-loop approval workflow
* Application tracking system
* Optional assisted submission

---

## System Architecture

```
Job Source
  -> Job Parser
  -> Requirement Extractor
  -> Retriever (RAG)
  -> Resume Generator
  -> Cover Letter Generator
  -> Evaluator / Reviewer
  -> Approval Interface
  -> Submission Assistant
  -> Application Tracker
```

---

## Tech Stack

### Backend

* Python
* FastAPI

### LLM

* OpenAI / Anthropic / Local LLM

### RAG

* FAISS / Chroma
* Sentence Transformers / OpenAI embeddings

### Orchestration

* LangChain / LangGraph / Custom pipeline

### Frontend

* Streamlit (MVP)
* Next.js (Production)

### Database

* SQLite / PostgreSQL

### Document Generation

* Jinja2 templates + HTML/PDF

---

## Core Components

### 1. Job Ingestion

Sources:

* Manual input (MVP)
* LinkedIn email alerts
* Job APIs (optional)

Extract:

* Title
* Company
* Description
* Requirements
* Application link

---

### 2. Personal Knowledge Base

Structured data about the user:

* Master CV
* Projects
* Skills
* Achievements
* Role-specific variations

Stored as:

* Text chunks
* Embedded vectors

---

### 3. Retrieval (RAG)

Steps:

1. Embed job description
2. Retrieve relevant experience
3. Rank results

Purpose:

* Ground LLM output in real data
* Avoid hallucination

---

### 4. Generation Layer

Produces:

* Tailored resume
* Cover letter
* Job match score
* Explanation of relevance

---

### 5. Evaluation Layer

Checks:

* Skill alignment
* Keyword coverage
* Missing requirements
* Confidence score

---

### 6. Approval Workflow

User sees:

* Job summary
* Match score
* Resume preview
* Cover letter
* Risk notes

Actions:

* Approve
* Edit
* Reject

---

### 7. Submission Assistant

Options:

* Open job application page
* Prefill known fields
* Manual submission

Note: Full automation is not reliable due to varying forms and anti-bot protections.

---

### 8. Application Tracking

Stores:

* Job details
* Status
* Resume version
* Dates

---

## Agent Design

Agents (logical components):

* Job Parser Agent
* Retrieval Agent
* Resume Tailor Agent
* Cover Letter Agent
* Evaluation Agent
* Submission Assistant Agent

---

## MVP Scope

### Features

* Manual job description input
* Knowledge base ingestion
* RAG retrieval
* Resume generation
* Cover letter generation
* Simple approval UI

### Excluded (for MVP)

* Email ingestion
* Full automation
* Advanced analytics

---

## Project Structure

```
project/
│
├── backend/
│   ├── main.py
│   ├── api/
│   ├── services/
│   │   ├── ingestion.py
│   │   ├── retrieval.py
│   │   ├── generation.py
│   │   ├── evaluation.py
│   ├── models/
│   └── db/
│
├── frontend/
│   ├── streamlit_app.py
│
├── data/
│   ├── resumes/
│   ├── projects/
│
├── vector_store/
│
├── prompts/
│
├── templates/
│
├── README.md
└── requirements.txt
```

---

## How It Works (Flow)

1. User inputs job description
2. System extracts requirements
3. Retriever finds relevant experience
4. LLM generates tailored resume
5. LLM generates cover letter
6. System evaluates match
7. User reviews and approves
8. Application is tracked

---

## Evaluation Strategy

* Retrieval relevance score
* Keyword matching score
* Human feedback
* Resume quality comparison

---

## Design Decisions

### Why RAG?

Avoids hallucination and ensures factual consistency.

### Why Human-in-the-loop?

Prevents incorrect submissions and maintains quality.

### Why Not Fully Automated Submission?

Websites vary, and automation is unreliable and risky.

---

## Future Improvements

* Email job ingestion
* Auto job filtering
* Interview preparation generation
* Feedback learning loop
* Multi-role optimization

---

## Demo Ideas

* Input job description
* Show retrieved experience
* Display generated resume
* Show approval interface

