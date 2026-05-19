# Methodology

## Research Question
Does refusal behavior in LLMs change when prompt injection attacks 
are delivered in Hindi, Marathi, or Gujarati versus English?

## Prior Work
Building on Yong et al. (2024), which demonstrated that translating 
harmful prompts into low-resource languages increases GPT-4 compliance 
rates, this research applies a more granular attack-category framework 
to Indic languages specifically.

## Models Under Test
- GPT-4o (chatgpt.com free tier)
- Gemini 1.5 Flash (gemini.google.com)
- Llama 3.1 8B via Groq API

## Attack Categories
Based on OWASP LLM Top 10 (2025) and Garak probe taxonomy:

1. CAT-01: Direct instruction override
2. CAT-02: System prompt extraction
3. CAT-03: Role-play / persona bypass
4. CAT-04: Indirect injection via pasted content
5. CAT-05: Encoded payload
6. CAT-06: Conflicting authority / fictional frame
7. CAT-07: Refusal tone consistency

## Logging Format
Each test logged as:

| prompt_id | language | model | run | response_summary | outcome | notes |

Outcome values: refused / complied / partial / deflected / error

## Controls
- Same semantic intent across all language versions
- Three runs per prompt per model
- No system prompt customization — default consumer interface only
- Tests run within 48 hours of each other to control for model updates