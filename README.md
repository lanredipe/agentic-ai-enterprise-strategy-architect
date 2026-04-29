# The Enterprise Strategy Architect – Autonomous Agentic System

## Overview
The Enterprise Strategy Architect is an autonomous agentic system designed to solve executive-level business problems through structured reasoning, market research, and financial modeling.

The system implements a Plan–Execute–Review loop to decompose complex objectives, retrieve relevant knowledge, perform calculations, and generate a validated strategic roadmap.

---

## Core Features
* **Stateful Orchestration (LangGraph):** Implements a directed graph with a controlled self-correction loop for iterative improvement of outputs.
* **Tri-Memory Architecture:**
    * **Semantic Memory:** Retrieval-Augmented Generation (RAG) using FAISS with curated industry data.
    * **Episodic Memory:** Retains user preferences (e.g., sustainability focus) across the execution flow.
    * **Procedural Memory:** Embedded business analysis rules and best practices guiding agent decisions.
* **Tool-Augmented Reasoning:**
    * **Market_Search:** Real-time data retrieval via Tavily.
    * **Financial_Analyzer:** Deterministic ROI and 5-year projection calculations.
    * **Compliance_Check:** Safety validation for bias and restricted legal/tax advice.
* **Pydantic-Validated Output:** Final strategic reports undergo strict schema validation before delivery, ensuring a consistent structure (Executive Summary, Risk Assessment, Financial Forecast, and Next Steps).
* **Observability & Debugging:** Custom LangChain callbacks provide transparent execution logs, including state transitions, retry handling, and safety validation results.

---

## System Design: Controlled Self-Correction
To ensure reliability and stability, the system uses a bounded cyclic graph:
1. The **Critic Node** evaluates generated outputs against procedural standards.
2. Failed evaluations trigger a return to the **Executor Node** for revision.
3. A strict limit of **MAX_REVISIONS = 3** prevents infinite loops and ensures execution stability under failure conditions.

---

## Example Use Case
**Test Prompt:**
> "Analyze the feasibility of expanding a data center into Nigeria vs. Togo with a 5-year ROI projection based on GreenCompute's low-carbon footprint preference."

**System Output:** A validated JSON report including comparative market analysis, calculated ROI figures, sustainability scoring, and a prioritized strategic roadmap.

---

## Tech Stack
* **Frameworks:** LangGraph, LangChain
* **Models:** Groq LLMs (Primary + Fallback Architecture)
* **Vector Store:** FAISS (HuggingFace Embeddings)
* **Validation:** Pydantic, JSON
* **Language:** Python

---

## Author and Role
**Olanrewaju Stephen Amudipe**
*System Architect & Orchestrator*

Designed the system architecture, agent workflow, memory strategy, and prompt logic. Utilized AI/LLM tools to implement the underlying Python codebase under architectural supervision.

---
