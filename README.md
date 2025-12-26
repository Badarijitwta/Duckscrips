graph TD
    %% SOURCE LAYER
    subgraph "Restricted Source Environment"
        A[🔒 Private Telegram Channel] -->|New PDF Upload| B(Python Listener Script)
        B -->|Regex Check: 'All English Editorials'| C{Match Found?}
        C -- No --> D[Ignore]
        C -- Yes --> E[Download File to Buffer]
    end

    %% BRIDGE LAYER
    E -->|POST Binary Data| F(n8n Webhook Endpoint)

    %% ORCHESTRATION LAYER (n8n)
    subgraph "n8n AI Orchestrator"
        F --> G[👁️ Mistral OCR]
        G --> H[🛡️ Guardrail Agent]
        H -- Invalid --> I[Stop / Log Error]
        H -- Valid --> J[🧠 Analyst Agent\nGemini 1.5 Flash]
        J -->|JSON Handoff| K[🎨 Creative Agent\nClaude 3.5 Sonnet]
    end

    %% DELIVERY LAYER
    K -->|HTML Summary| L[📢 Public Telegram Channel]
    L --> M[Users/Subscribers]

    %% STYLING
    style A fill:#ffdddd,stroke:#333,stroke-width:2px
    style B fill:#e1f5fe,stroke:#333,stroke-width:2px
    style F fill:#e1f5fe,stroke:#333,stroke-width:2px
    style L fill:#dcedc8,stroke:#333,stroke-width:2px
