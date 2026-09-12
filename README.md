# Punjab Government Scheme Finder

A citizen-friendly Streamlit MVP that helps people discover relevant Punjab Government support schemes using natural-language needs, semantic retrieval (RAG), and a preliminary eligibility check.

## Final MVP flow

1. Enter basic profile: Age, District, Occupation.
2. Describe the actual need in plain language.
3. The **need drives retrieval**; profile information is primarily used for preliminary eligibility.
4. Semantic search (Sentence Transformers + FAISS) retrieves relevant official scheme records.
5. The app shows preliminary match labels and official source links.
6. Government-service requests such as licenses/certificates are routed to the official Maryam Ki Dastak services page rather than being treated as generic schemes.

## Tech stack

- Python
- Streamlit
- Sentence Transformers (`all-MiniLM-L6-v2`)
- FAISS
- JSON scheme knowledge base
- Optional Groq API for a grounded short explanation
- Streamlit Cloud deployment

## Run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

Optional `.env`:

```text
GROQ_API_KEY=your_key_here
```

The app works without Groq; the retrieval and eligibility logic remain available.

## Important product rules

- Official-source links only.
- Never claim official eligibility.
- If there is no strong match, say so instead of showing a random scheme.
- Maryam Ki Dastak is a government-service platform, not a generic support scheme.
- Scheme criteria and intake status can change; users must verify the current official source.

## Current dataset

The current knowledge base contains 36 verified Punjab Government scheme/initiative records across six user-facing fields: Agriculture, Education, Business, Social Welfare, Energy, and Livestock. Sources are restricted to official Punjab Government departments/portals. Criteria and intake status can change, so the app always directs users to the official source for verification.
