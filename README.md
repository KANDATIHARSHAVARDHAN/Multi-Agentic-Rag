# 📚 Multi-Agentic RAG - College Study Assistant

A **Streamlit-based multi-agent RAG (Retrieval-Augmented Generation) system** for students.  
It helps in **summarization, MCQ generation, note-making, exam preparation, and concept explanations** using uploaded PDFs or live web search.  

---

## 🚀 Features
- **Multiple LLMs Support**  
  - Gemini 2.5 Flash  
  - Gemini 2.5 Flash Lite  
  - Gemini 2.0 Flash  
  - GPT-OSS-120B (via Groq)  

- **Document Handling**  
  - Upload multiple PDFs  
  - FAISS vector store with caching (hash-based re-use)  
  - Automatic text chunking & embeddings  

- **Study Agents**  
  - 📑 **Summarizer** – Summarizes documents in custom length  
  - ❓ **MCQ Generator** – Creates exam-style MCQs (with ASCII diagrams if needed)  
  - 📝 **Notes Maker** – Creates concise side-heading notes  
  - 📅 **Exam Prep Agent** – Builds structured study plan & revision tips  
  - 💡 **Concept Explainer** – Explains topics in simple terms  
  - 🔍 **Search Agent** – Uses Google Custom Search for web knowledge  

- **Dynamic Routing**  
  - Queries automatically classified to best-suited tool  
  - Web search queries routed to subtools (e.g., summarize search results, generate MCQs, etc.)  

---

## 🏗 Project Architecture (Visual Flow)
```bash

                                      ┌───────────────────────────┐
                                      │        User Input         │
                                      └─────────────┬─────────────┘
                                                    │
                                                    ▼
                                      ┌───────────────────────────┐
                                      │          Router           │
                                      │   (Intent Classifier)     │
                                      └─────────────┬─────────────┘
                                                    │
        ┌─────────────────────┬─────────────────────┼─────────────────────┬─────────────────────┐
        │                     │                     │                     │                     │
        ▼                     ▼                     ▼                     ▼                     ▼
   summarizer          mcq_generator           notes_maker         exam_prep_agent       concept_explainer
        │                     │                     │                     │                     │
        │                     │                     │                     │                     │
        └─────────────────────┴─────────────────────┴─────────────────────┴─────────────────────┘
                                                    │
                                                    ▼
                                           search_agent
                                                    │
                                                    ▼
                                      ┌───────────────────────────┐
                                      │      Subtool Router       │
                                      │   (Routes to:             │
                                      │    summarizer, MCQs,      │
                                      │    notes, exam prep, etc.)│
                                      └─────────────┬─────────────┘
                                                    │
        ┌─────────────────────┬─────────────────────┼─────────────────────┬─────────────────────┐
        ▼                     ▼                     ▼                     ▼                     ▼
   summarizer          mcq_generator           notes_maker         exam_prep_agent       concept_explainer
        │                     │                     │                     │                     │
        └─────────────────────┴─────────────────────┴─────────────────────┴─────────────────────┘
                                                    │
                                                    ▼
                                                    END

```



---

## ▶️ Usage
1. Open the app in Streamlit:
```bash
streamlit run multiagenticRag.py
```


Upload your study material (PDFs).

Select your desired language model.

Ask queries like:

"Summarize chapter 3 in 10 lines"

"Generate 20 MCQs for Thermodynamics"

"Make notes on Electrochemistry in 15 lines"

"Explain Ohm's Law in 5 lines"

"Prepare a study plan for Organic Chemistry"

The system will automatically route the query to the best-suited agent or subtool.
