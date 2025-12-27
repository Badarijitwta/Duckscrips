<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DuckScrips - Autonomous Market Intelligence Agent</title>
    <script type="module">
        import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
        mermaid.initialize({ startOnLoad: true });
    </script>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
            line-height: 1.6;
            color: #24292e;
            max-width: 900px;
            margin: 0 auto;
            padding: 40px 20px;
            background-color: #f6f8fa;
        }
        .container {
            background-color: #ffffff;
            padding: 40px;
            border: 1px solid #e1e4e8;
            border-radius: 6px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }
        h1, h2, h3 {
            border-bottom: 1px solid #eaecef;
            padding-bottom: 0.3em;
            margin-top: 24px;
        }
        h1 { font-size: 2em; font-weight: 600; }
        h2 { font-size: 1.5em; font-weight: 600; }
        h3 { font-size: 1.25em; font-weight: 600; }
        
        .badges { margin: 15px 0; }
        .badges img { margin-right: 5px; }

        blockquote {
            color: #6a737d;
            border-left: 0.25em solid #dfe2e5;
            padding: 0 1em;
            margin: 0;
        }

        code {
            padding: 0.2em 0.4em;
            margin: 0;
            font-size: 85%;
            background-color: #f6f8fa;
            border-radius: 6px;
            font-family: SFMono-Regular, Consolas, "Liberation Mono", Menlo, monospace;
        }

        pre {
            padding: 16px;
            overflow: auto;
            font-size: 85%;
            line-height: 1.45;
            background-color: #f6f8fa;
            border-radius: 6px;
        }

        .mermaid {
            text-align: center;
            margin: 30px 0;
        }

        a { color: #0366d6; text-decoration: none; }
        a:hover { text-decoration: underline; }

        .demo-button {
            display: inline-block;
            margin-top: 10px;
        }
    </style>
</head>
<body>

<div class="container">

    <h1>🤖 DuckScrips: Autonomous Market Intelligence Agent</h1>
    
    <blockquote>
        A Multi-Agent Orchestrator built on n8n that transforms unstructured PDF magazines into structured, persona-driven business insights.
    </blockquote>

    <div class="badges">
        <img src="https://img.shields.io/badge/Orchestrator-n8n-ff6e5c?style=for-the-badge&logo=n8n" alt="n8n">
        <img src="https://img.shields.io/badge/Vision-Mistral_OCR-f5a623?style=for-the-badge" alt="Mistral">
        <img src="https://img.shields.io/badge/Analyst-Gemini_1.5-4285F4?style=for-the-badge&logo=google" alt="Gemini">
        <img src="https://img.shields.io/badge/Persona-Claude_3.5-d97757?style=for-the-badge&logo=anthropic" alt="Claude">
    </div>

    <h2>🎥 Demo</h2>
    <p><strong>See the agent in action (60s):</strong></p>
    <a href="https://www.loom.com/share/955aeb6f2421431bac32a22fe024b7f3" target="_blank" class="demo-button">
        <img src="https://img.shields.io/badge/▶_Watch-Live_Demo-red?style=for-the-badge&logo=youtube" alt="Watch Demo">
    </a>

    <h2>🚀 Overview</h2>
    <p>PGDM students and business executives are flooded with dense PDF reports daily. Manually extracting domain-specific insights (Marketing, HR, Ops) is inefficient.</p>
    <p><strong>DuckScrips</strong> is an autonomous agent pipeline that:</p>
    <ol>
        <li><strong>Ingests</strong> raw PDF binaries via Telegram.</li>
        <li><strong>Validates</strong> content relevance using semantic guardrails.</li>
        <li><strong>Analyzes</strong> text using a strict Academic Framework.</li>
        <li><strong>Re-contextualizes</strong> insights into a "Gen-Z" relatable persona for maximum engagement.</li>
    </ol>

    <h2>⚙️ System Architecture</h2>
    <p>The system utilizes a <strong>Chain-of-Thought (CoT)</strong> flow where multiple LLMs hand off context to perform specialized tasks.</p>
    
    <div class="mermaid">
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

        %% STYLING
        classDef agent fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
        classDef guard fill:#fff3e0,stroke:#e65100,stroke-width:2px;
        classDef error fill:#ffebee,stroke:#c62828,stroke-width:2px;
        
        class Vision,AnalystAgent,PersonaAgent agent;
        class GuardAgent,TrafficCop guard;
        class Error1,Error2 error;
    </div>

    <h2>🧠 The Agentic Workflow</h2>

    <h3>1. Vision Layer (Mistral OCR)</h3>
    <p>Unlike standard text extractors, this agent uses <strong>Mistral's Vision capabilities</strong> to parse complex magazine layouts, preserving the hierarchy of headlines and sidebars for accurate context.</p>

    <h3>2. Guardrail Agent (Gemini 1.5 Flash)</h3>
    <p><strong>Role:</strong> The Gatekeeper.</p>
    <ul>
        <li><strong>Logic:</strong> It performs a binary classification on the OCR output to determine if the document is a valid "Business Magazine" or irrelevant noise (e.g., recipes, receipts).</li>
        <li><strong>Outcome:</strong> Prevents the main analyst from hallucinating on bad data.</li>
    </ul>

    <h3>3. Analyst Agent (Gemini 1.5 Pro)</h3>
    <p><strong>Role:</strong> The "Professor".</p>
    <ul>
        <li><strong>Prompt Engineering:</strong> Strictly enforced "PGDM Framework". It ignores tone and focuses purely on extracting facts across 5 domains:
            <ul>
                <li>📢 Marketing & Branding</li>
                <li>👥 HR & Org Behavior</li>
                <li>⚙️ Operations & Supply Chain</li>
                <li>🤖 Systems & IT</li>
                <li>🌍 ESG & Sustainability</li>
            </ul>
        </li>
    </ul>

    <h3>4. Persona Agent (Claude 3.5 Sonnet)</h3>
    <p><strong>Role:</strong> The "Peer Mentor".</p>
    <ul>
        <li><strong>Task:</strong> Takes the dry, academic output from Gemini and rewrites it using a "Student-Friendly" persona.</li>
        <li><strong>Features:</strong>
            <ul>
                <li><strong>Jargon Buster:</strong> Automatically identifies and defines complex terms.</li>
                <li><strong>HTML Formatting:</strong> Renders bold/italic text for mobile readability.</li>
                <li><strong>Analogies:</strong> Converts corporate concepts into real-world examples (e.g., "Netflix vs. Blockbuster").</li>
            </ul>
        </li>
    </ul>

    <h2>🛠️ Installation & Setup</h2>
    
    <h3>Prerequisites</h3>
    <ul>
        <li><a href="https://n8n.io/">n8n</a> (Self-hosted or Cloud)</li>
        <li>Telegram Bot Token</li>
        <li>API Keys: Mistral AI, Google Gemini, Anthropic (Claude)</li>
    </ul>

    <h3>Quick Start</h3>
    <pre><code>1. Clone the Repo:
git clone https://github.com/YOUR_USERNAME/DuckScrips.git

2. Import Workflow:
- Open n8n.
- Select "Import from File" and choose Duckscrips.json.

3. Configure Credentials:
- Set up your API keys in n8n.

4. Activate:
- Toggle the workflow to Active.</code></pre>

    <h2>🔮 Roadmap (Phase 2)</h2>
    <ul>
        <li><strong>Python Listener Service:</strong> Integrating a <code>Telethon</code> based Python script to autonomously scrape private Telegram channels for "English Editorials" and pipe them into the n8n webhook.</li>
        <li><strong>Vector Database:</strong> Adding Pinecone for RAG (Retrieval-Augmented Generation) to allow users to query past magazines.</li>
    </ul>

    <hr>

    <h2>👨‍💻 Author</h2>
    <p><strong>[Your Name]</strong><br>
    <em>Orchestrating AI Agents to solve unstructured data problems.</em><br>
    [LinkedIn Profile] | [Portfolio Link]</p>

</div>

</body>
</html>
