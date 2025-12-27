# 🤖 DuckScrips: Autonomous Market Intelligence Agent

> **A Multi-Agent Orchestrator built on n8n that transforms unstructured PDF magazines into structured, persona-driven business insights.**

![n8n](https://img.shields.io/badge/Orchestrator-n8n-ff6e5c?style=for-the-badge&logo=n8n)
![Mistral](https://img.shields.io/badge/Vision-Mistral_OCR-f5a623?style=for-the-badge)
![Gemini](https://img.shields.io/badge/Analyst-Gemini_1.5-4285F4?style=for-the-badge&logo=google)
![Claude](https://img.shields.io/badge/Persona-Claude_3.5-d97757?style=for-the-badge&logo=anthropic)

## 🎥 Demo
**See the agent in action (60s):**

[![Watch the Demo](https://img.shields.io/badge/▶_Watch-Live_Demo-red?style=for-the-badge&logo=youtube)](https://www.loom.com/share/955aeb6f2421431bac32a22fe024b7f3)

---

## 🚀 Overview
PGDM students and business executives are flooded with dense PDF reports daily. Manually extracting domain-specific insights (Marketing, HR, Ops) is inefficient.

**DuckScrips** is an autonomous agent pipeline that:
1.  **Ingests** raw PDF binaries via Telegram.
2.  **Validates** content relevance using semantic guardrails.
3.  **Analyzes** text using a strict Academic Framework.
4.  **Re-contextualizes** insights into a "Gen-Z" relatable persona for maximum engagement.

---

## ⚙️ System Architecture

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
    ```
