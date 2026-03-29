🔬 Research Shastra: Stage-Aware Multi-Agent Research System

ResearchShastra is an autonomous, multi-agent AI system designed to reduce literature review time from hours to minutes. Powered by Google Gemini and the ArXiv API, it goes beyond simple keyword matching by understanding the *stage* of your research (Exploration, Incremental, or Innovation) to intelligently route tasks, fetch papers, and synthesize cited reports.

-----

The Problem & Solution

Current search tools treat all queries the same, leading to information overload. A PhD student looking for foundational papers has completely different needs than an engineer looking for state-of-the-art benchmarks.

Research Shastra solves this by implementing a **Coordinator-Worker Architecture** with 10 specialized AI agents. The system doesn't just search; it reasons. It classifies user intent, routes tasks to specific search strategies, cleans the data, and synthesizes a final executive report with direct, verifiable PDF citations.

-----

System Architecture

The workflow is orchestrated by a central "Brain" that manages specialized agents running in parallel.

1. Intent Classification

  * Field Classifier Agent: Detects the domain of the query (e.g., Technology, Healthcare, Agriculture).
  * Stage Classifier Agent: Determines the research phase:
      * Exploration: Triggers broad, recent, and topic-specific searches.
      * Incremental: Triggers classic and benchmark-focused searches.
      * Innovation: Triggers application-focused searches.

2. Parallel Search Execution

  * Classic Search Agent: Finds highly relevant, heavily cited papers.
  * Recent Papers Search Agent: Filters for the newest pre-prints (vital for fast-moving fields like AI).
  * Topic-Based Category Agent: Maps natural language fields to specific ArXiv taxonomy codes (e.g., `cs.AI`).

3. Data Processing pipeline

  * Deduplication Agent: Cleans combined results from the parallel searches, ensuring no overlapping data.
  * Relevance Ranking Agent: Re-ranks papers heuristically based on the detected stage (e.g., prioritizing recency for "Exploration").

4. Synthesis & Output

  * Summary Agent (Gemini-Powered): Synthesizes complex abstracts into a cohesive narrative report.
  * Citation Agent: Maps generated text back to specific ArXiv PDF URLs, ensuring zero hallucinations in references.

5. Continuous Improvement

  * Refinement/Feedback Loop Agent: Allows users to interactively narrow or expand the scope of their query without starting over.

-----

## ⚙️ Key Features

  * Stage-Aware Routing: Dynamic execution paths based on exactly what kind of research you are doing.
  * Parallel Execution: Search agents run concurrently using Python's `ThreadPoolExecutor` for lightning-fast data retrieval.
  * Zero-Hallucination Citations: Every claim in the final report is linked to a real, verifiable ArXiv PDF.
  * Robust Error Handling: System gracefully falls back on alternative agents if an API limit or timeout is reached.

-----

Example Output:-

🤖 STARTING AGENT WORKFLOW for: 'Automated techniques for optimizing large language model inference speed'

[LOG] FieldClassifierAgent | Detected: Technology
[LOG] StageClassifierAgent | Detected: Exploration
[LOG] Coordinator | Routing: Exploration -> Running Recent + Topic Search
[LOG] Coordinator | Search Complete | Fetched 5 papers

========================================
FINAL RESEARCH REPORT
========================================
Detected Field: Technology
Detected Stage: Exploration
----------------------------------------
**Research Report (Exploration Phase)**

We found 5 papers. The top result is 'Learning From Failure: Integrating Negative Examples when Fine-tuning Large Language Models as Agents'. Another key paper is 'Demystifying Instruction Mixing for Fine-tuning Large Language Models'.
----------------------------------------
REFERENCES:
1. **Learning From Failure: Integrating Negative Examples when Fine-tuning Large Language Models as Agents**
   - Link: [Open PDF](https://arxiv.org/pdf/2402.11651v2)
1. **Demystifying Instruction Mixing for Fine-tuning Large Language Models**
   - Link: [Open PDF](https://arxiv.org/pdf/2312.10793v3)
========================================
✅ SYSTEM STATUS: SUCCESS

*Built for the Google Gemini x Kaggle Agents Intensive Competition.*
