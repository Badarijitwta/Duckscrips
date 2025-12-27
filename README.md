# 🤖 DuckScrips: Financial News Automation Agent

> **A Multi-Agent Orchestrator built on n8n that transforms unstructured PDF magazines into structured, persona-driven business insights.**

![n8n](https://img.shields.io/badge/Orchestrator-n8n-ff6e5c?style=for-the-badge&logo=n8n)
![Mistral](https://img.shields.io/badge/Vision-Mistral_OCR-f5a623?style=for-the-badge)
![Gemini](https://img.shields.io/badge/Analyst-Gemini_1.5-4285F4?style=for-the-badge&logo=google)
![Claude](https://img.shields.io/badge/Persona-Claude_3.5-d97757?style=for-the-badge&logo=anthropic)

## 🎥 Live Demo
**Watch the full automation in action (60s):**

[![Watch the Demo](https://cdn.loom.com/sessions/thumbnails/955aeb6f2421431bac32a22fe024b7f3-with-play.gif)](https://www.loom.com/share/955aeb6f2421431bac32a22fe024b7f3)

---

## 🚀 The Problem
PGDM students and business executives are flooded with dense PDF reports daily. Manually extracting domain-specific insights (Marketing, HR, Ops) from 50+ page magazines is inefficient and time-consuming.

**DuckScrips** is an autonomous agent pipeline that solves this by:
1.  **Ingesting** raw PDF binaries via Telegram.
2.  **Validates** content relevance using semantic guardrails.
3.  **Analyzes** text using a strict Academic Framework.
4.  **Re-contextualizes** insights into a "Gen-Z" relatable persona for maximum engagement.

---

## ⚙️ System Architecture (How It Works)

The system utilizes a **Chain-of-Thought (CoT)** flow where multiple LLMs hand off context to perform specialized tasks.

```mermaid
graph TD
    %% INGESTION LAYER
    subgraph "Ingestion & Validation"
        Start((Telegram Trigger)) -->|Incoming PDF| CheckFormat{Is PDF?}
        CheckFormat -- No --> Error1[❌ Reject: Invalid Format]
        CheckFormat -- Yes --> Vision[👁️ Mistral OCR]
    end

    %% GUARDRAIL LAYER
    subgraph "Semantic Guardrails"
        Vision -->|Raw Markdown| GuardAgent[🛡️ Content Filter Agent]
        GuardAgent -->|Decision: VALID/INVALID| TrafficCop{Is Business Content?}
        TrafficCop -- No --> Error2[❌ Reject: 'Not a Magazine']
    end

    %% INTELLIGENCE LAYER
    subgraph "Cognitive Processing"
        TrafficCop -- Yes --> AnalystAgent[🎓 Gemini 1.5: 'The Professor']
        AnalystAgent -->|Structured 5-Domain Analysis| PersonaAgent[😎 Claude 3.5: 'The Cool Senior']
        PersonaAgent -->|HTML Formatted Summary| Output
    end

    %% DELIVERY LAYER
    subgraph "Delivery"
        Output[🚀 Telegram Broadcast]
    end


The Step-by-Step Logic
1. Vision Layer (Mistral OCR)
Unlike standard text extractors, this agent uses Mistral's Vision capabilities to parse complex magazine layouts. It preserves the hierarchy of headlines, sidebars, and charts, converting the PDF into structured Markdown for the LLMs to understand.

2. Guardrail Agent (Gemini 1.5 Flash)
Role: The Gatekeeper.

Logic: It performs a binary classification on the OCR output to determine if the document is a valid "Business Magazine" or irrelevant noise (e.g., recipes, receipts).

Outcome: This "Traffic Cop" node prevents the system from wasting compute resources or hallucinating on irrelevant files.

3. Analyst Agent (Gemini 1.5 Pro)
Role: The "Professor".

Task: It applies a strict PGDM Academic Framework to the text. It ignores tone and focuses purely on extracting strategic facts across 5 domains:

📢 Marketing & Branding: Positioning, campaigns, consumer behavior.

👥 HR & Org Behavior: Culture, leadership styles, talent management.

⚙️ Operations: Supply chain, logistics, efficiency.

🤖 Systems & IT: AI implementation, tech stacks.

🌍 ESG: Sustainability and corporate governance.

4. Persona Agent (Claude 3.5 Sonnet)
Role: The "Peer Mentor".

Task: Takes the dry, academic output from Gemini and rewrites it using a "Student-Friendly" persona.

Features:

Jargon Buster: Automatically identifies and defines complex corporate terms.

HTML Formatting: Renders bold headers and italicized notes for perfect mobile readability on Telegram.

Analogies: Converts corporate concepts into real-world examples (e.g., "This strategy is giving Nokia vibes").

🛠️ Installation & Setup
Prerequisites
n8n (Self-hosted or Cloud)

Telegram Bot Token (via BotFather)

API Keys: Mistral AI, Google Gemini, Anthropic (Claude)

Quick Start
Clone the Repo:

Bash

git clone [https://github.com/YOUR_USERNAME/DuckScrips.git](https://github.com/YOUR_USERNAME/DuckScrips.git)
Import Workflow:

Open n8n Dashboard.

Click "Import from File" and upload Duckscrips.json (included in this repo).

Configure Credentials:

Enter your API keys for Telegram, Mistral, Gemini, and Anthropic in the n8n credential manager.

Activate:

Toggle the workflow to Active.

Send a PDF to your Telegram Bot to start the pipeline.

🔮 Roadmap (Phase 2)
Python Listener Service: I am currently integrating a Telethon based Python script (see news_bridge.py) to autonomously scrape private Telegram channels for "English Editorials" and pipe them into this n8n webhook.

Vector Database: Adding Pinecone for RAG (Retrieval-Augmented Generation) to allow users to query past magazines.
