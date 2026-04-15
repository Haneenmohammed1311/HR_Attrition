
┌──────────────────────────────────────────────────────────┐
│                    SARA'S STORE SYSTEM                   │
│                                                          │
│  ┌─────────────────────────────────────────────────┐    │
│  │  n8n (The Orchestrator / Routing Layer)         │    │
│  │  • Triggers workflows on schedule or events     │    │
│  │  • Routes data between agents and apps          │    │
│  │  • Connects to email, Slack, Google Sheets      │    │
│  └──────────────────┬──────────────────────────────┘    │
│                     │ triggers                           │
│  ┌──────────────────▼──────────────────────────────┐    │
│  │  AGENTIC SYSTEM (The Team)                      │    │
│  │                                                 │    │
│  │  ┌──────────────────────────────────────────┐  │    │
│  │  │  Customer Agent  (built with LangChain)  │  │    │
│  │  │  • Reads emails                          │  │    │
│  │  │  • Queries RAG for Sara's policies       │  │    │
│  │  │  • Reasons and writes replies            │  │    │
│  │  │  • Self-checks (agentic loop)            │  │    │
│  │  │  • Sends final email                     │  │    │
│  │  └──────────────────────────────────────────┘  │    │
│  │                                                 │    │
│  │  ┌──────────────────────────────────────────┐  │    │
│  │  │  Report Agent  (built with LangChain)    │  │    │
│  │  │  • Data Agent → Feedback Agent           │  │    │
│  │  │  → Writer Agent → Editor Agent           │  │    │
│  │  │  • Each uses RAG for relevant context    │  │    │
│  │  │  • Agentic loop: reflect and improve     │  │    │
│  │  └──────────────────────────────────────────┘  │    │
│  └──────────────────┬──────────────────────────────┘    │
│                     │ all agents draw from               │
│  ┌──────────────────▼──────────────────────────────┐    │
│  │  RAG + Vector Database (The Knowledge Layer)    │    │
│  │  • Sara's policies, product specs, FAQs        │    │
│  │  • Searched by meaning, not keywords            │    │
│  │  • Always up to date                            │    │
│  └─────────────────────────────────────────────────┘    │
│                                                          │
│  ALL of this is built by an AGENCY                      │
│  using n8n + LangChain + RAG as the building tools      │
└──────────────────────────────────────────────────────────┘
