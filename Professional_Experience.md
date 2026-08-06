# Founding Engineer | TripKnot (Aneeras LLP)
Apr 2026 – Present · Hybrid, Pondicherry

TripKnot (product name Travera) is a social, AI-assisted travel itinerary planning product: a FastAPI backend with an LLM-driven itinerary generator and a trust and safety system, a Next.js admin console, and an Expo/React Native mobile app. I'm one of five founding engineers building it end to end, architecture, product decisions, DevOps, and cloud deployment, alongside my co-founder. Development has been continuous since April 2026.

### Building the AI Itinerary Engine

Co-built the product's core differentiator: an AI-powered itinerary engine that combines user preferences and budget with a place-scoring and diversity algorithm, log-scaled popularity blended with rating count and landmark, trending, and hidden-gem signals, seed jitter on each request so repeat requests don't return identical plans, an anchor mechanism that guarantees top landmarks always show up, round-robin category fill, and budget-tier filtering that relaxes gracefully when strict filters return too few results, to curate a place pool and generate personalized, diverse day-by-day itineraries in about 10 seconds. On top of that pool, an LLM layer handles the structuring and scheduling: Gemini as the primary model behind a Pydantic-constrained JSON schema, with Groq's Llama 3 as an automatic fallback, plus token-cost and latency tracking on every generation. A Streamlit proof of concept (geo-clustering, greedy TSP day-ordering, LLM scheduling) came first and shaped the production rewrite.

### Designing Trust and Identity Verification

Designed and built the Aadhaar/KYC identity-verification system, including a dedicated flow for "strangers trips" where participants are joining people they don't already know, spanning the trip and user data models, backend validation, and the admin review UI staff use to approve or reject submissions. Also did real production auth work here: tracked down and fixed a GCS upload-authentication bug by switching to Firebase service-account-key auth after a UBLA/make_public failure, plus built profile-image upload handling and user-token verification endpoints.

### Admin Backend and Console

Built the admin backend and console together, full stack: destination, place, and state CRUD, CSV import/export, an analytics dashboard with real visualizations, trip moderation including a two-step host-verification approval flow, and a redesign that replaced hard deletes with a soft-cancel-with-audit-trail approach (status, reason, and audit fields) for compliance.

### Analytics, Gamification, and the Scoring Service

Implemented fire-and-forget event tracking that never adds latency to user-facing requests, atomic counters, a trending and popularity recalculation job, public leaderboard endpoints, and badges. Also designed a standalone scoring service that computes trending and popularity rankings in dependency order across places, destinations, and states, using time-decay math (Reddit-style hot ranking with a 48-hour half-life) and a weighted popularity blend of review quality, importance, engagement, and recent momentum. Every threshold is a tunable config value rather than a hardcoded constant, and the normalization approach is built to hold up from pre-launch traffic through much larger scale.

### Mobile App Features

Shipped a location and personalization pipeline for the Expo/React Native app, so the home feed and discover results reflect a user's real location, including a fix that distinguishes GPS-sourced location from a manually picked city so background sync stops overwriting a manual choice. Built a full "Explore India" states feature with region-filterable browsing and state detail pages, a notification-preferences screen with master and per-category toggles, search and category filtering, and a native file-upload fix that routes Android and iOS photo picker uploads through Expo's native upload API instead of a form-data approach that failed on certain URI types.

### Data Platform and DevOps

Built an image-quality vetting pipeline for destination photos, moving from a heavier OCR-plus-frequency-analysis watermark detector to a fine-tuned vision classifier after tuning against real false positives on food photography, along with a companion tool that converts and re-hosts images to WebP on GCS with structured audit logging. Built an ETL tool that ingests destination data from spreadsheets and CSVs into the production data model, handling slug generation, geocoding, and tag and image parsing, pushed through the authenticated backend API with dry-run and duplicate-detection support rather than writing to the database directly, processing 7,000-plus place records into the production database this way. On the infrastructure side, set up GitHub Actions CI and CD for the backend (tests plus Docker build, automatic staging deploy, manual-gated production promotion), deployed on Google Cloud Run in asia-south1, configured GCP Workload Identity Federation so CI never holds a long-lived cloud credential, cutting deployment time down to about 3 minutes, and wired Sentry monitoring into both the backend and the mobile app.

---

## Key Highlights

- Built the AI itinerary engine: a place-scoring and diversity algorithm that curates a place pool and generates personalized, budget-aware day-by-day itineraries in about 10 seconds, with an LLM layer (Gemini primary, Groq fallback) handling structuring and scheduling.
- Designed and built a KYC/Aadhaar identity-verification system for trips with unfamiliar participants, spanning backend data models and an admin review console.
- Built the admin console and backend endpoints for content moderation and analytics, including a two-step verification flow and an audit-logged cancellation system.
- Designed a standalone scoring service computing trending and popularity rankings through time-decay, multi-factor models, tuned to stay stable from launch through scale.
- Shipped mobile features spanning location-aware personalization, a region-browsable "Explore India" feature, and notification preferences in React Native and Expo.
- Set up CI/CD and cloud deployment for the backend (GitHub Actions, Docker, Cloud Run, Workload Identity Federation), cutting deployment time to about 3 minutes, with Sentry monitoring across backend and mobile.
- Built an image-quality vetting pipeline and ETL tooling that processed 7,000-plus place records into the production database.
- [ADD METRIC: user count, itinerary-generation volume, or other real usage numbers, once available]

Scale, for context: backend is roughly 21,000 lines across 185 endpoints in 23 domain modules, the mobile app is roughly 27,000 lines, the admin console is roughly 17,000 lines. Automated test coverage is thin right now (essentially one test file, covering auth), so "shipped production features end to end" is well supported here; a claim like "with strong test discipline" is not, and should stay off any resume drawn from this.

---

# AI Software Engineer | YUVABE
Mar 2023 – Mar 2026 · Auroville, Tamil Nadu

I joined YUVABE as an AI Software Engineer Intern in March 2023 and converted to full time by October that year, growing from shipping early chatbot APIs into owning LLM integration strategy across three live AI products serving 500+ daily active users.

## Bridging Product and Engineering

Most of my work sat at the point where business requirements turn into technical specs. I partnered directly with product leads to translate what stakeholders needed into APIs and data models, which cut rework by around 30 percent by catching misalignment before it reached implementation. I sat in on sprint planning, backlog grooming, and retrospectives regularly enough that AI features shipped on schedule and stayed tied to the actual user-facing goal, not just the technical one.

### Choosing and Integrating LLMs

I drove the integration strategy for OpenAI and Google Gemini, writing technical briefs that defined evaluation criteria around quality, cost, and latency to guide model selection decisions. That work later extended to open source alternatives through Hugging Face, including fine-tuning and evaluation to see where they could realistically replace a paid API. Fine-tuning and prompt engineering work on top of these models improved response accuracy by roughly 35 percent over baseline.

### Shaping AI Products End to End

I contributed to KittyKat AI, a creative platform for brand and campaign management running on a FastAPI and MongoDB backend. The chatbot is built on LangGraph as a router-driven multi-agent graph, with specialist nodes handling branding, campaigns, moodboards, prompting, and generation; I built the chat-driven UX for the brand and campaign management flows. On the generation side, I worked on the image and video generation system: model configuration and routing across providers (OpenAI's GPT Image 1, Replicate's Flux family, and others) through a discriminated union pattern that lets new models plug in without hardcoded per-model logic, along with prompt engineering for generation quality. I built the moodboard pipeline, including CLIP-based vector search that powers reference-image auto-fill and semantic search across the asset library, and the product extraction pipeline that detects and isolates product assets from brand images. I also designed the multi-tenant architecture with credit tracking, Firebase auth, and real-time updates over SSE to support the platform at SaaS scale.

I also built and iterated on AuroGurukul, an AI-driven learning management system with adaptive assessments, analytics dashboards to track progress, and a RAG-based chatbot for real-time learner support backed by a Pinecone vector search pipeline, which cut incorrect responses by 80 percent across a 50-plus query internal benchmark. I evaluated Frappe LMS first and, after concluding it couldn't meet the product's requirements, built a custom platform from scratch on Next.js, FastAPI, and MongoDB, including a full Test Management Module covering test creation, question management, result submission, and performance analytics.

### ERPNext Implementation Work

Alongside the AI engineering work, I also led ERPNext implementations end to end: configuring Sales, Purchase, Accounting, and Inventory modules, customizing workflows, role-based permissions, and automated reports to match how the business actually operated, and managing data migration, UAT, go-live, and team training with clear documentation. Automating repetitive manual workflows this way improved operational efficiency by 60 percent and reduced error rates across departments.

### Shipping and Supporting in Production

I managed containerized deployments on GCP and CI/CD pipelines through GitHub Actions to keep releases reliable and downtime minimal. I also wrote the internal API documentation and integration guides the frontend team relied on, which cut onboarding time for new engineers by an estimated two weeks, and stayed involved after launch, monitoring usage patterns and failure rates on GCP to inform what got prioritized next. I also worked Claude API and Claude Code into my day-to-day development workflow, cutting boilerplate coding time by roughly 40 percent.

### Where It Started

As an intern, I scoped and delivered three plus backend APIs for AI-driven chatbot workflows, supporting two production feature releases within my first three months. I benchmarked generative image and video models across Hugging Face and Replicate, producing evaluation reports that guided model choice for two features, and supported the integration of OpenAI and Gemini into production workflows, contributing to prompt engineering work that improved chatbot response quality.

---

## Key Highlights

- Grew from intern to full time AI Software Engineer, eventually owning LLM integration strategy across three live AI products serving 500+ daily active users.
- Defined evaluation criteria for LLM providers (OpenAI, Gemini, Hugging Face models) that guided real model selection decisions on cost, quality, and latency, and improved response accuracy by roughly 35 percent over baseline through fine-tuning and prompt engineering.
- Used Claude API and Claude Code as part of the daily development workflow, cutting boilerplate coding time by roughly 40 percent.
- Built the chat-driven UX for KittyKat's brand and campaign management flows, on a LangGraph router-driven multi-agent architecture with specialist nodes per domain.
- Worked on KittyKat's image and video generation system: multi-provider model routing (OpenAI's GPT Image 1, Replicate's Flux family) through a discriminated union pattern, plus prompt engineering for generation quality.
- Built KittyKat's moodboard pipeline and CLIP-based vector search for reference-image auto-fill and semantic asset search, plus a product extraction pipeline for isolating product assets from brand images.
- Designed KittyKat's multi-tenant, credit-tracked SaaS architecture.
- Evaluated Frappe LMS, then built AuroGurukul as a custom platform from scratch, including adaptive assessments, a Pinecone-backed RAG support chatbot (80 percent fewer incorrect responses across a 50-plus query internal benchmark), and a full Test Management Module.
- Led ERPNext implementations end to end (Sales, Purchase, Accounting, Inventory), including data migration, UAT, go-live, and team training, alongside the AI engineering work, improving operational efficiency by 60 percent and reducing error rates across departments.
- Set up GCP deployments and CI/CD, and wrote the API documentation that shortened onboarding for new engineers by about two weeks.
- Delivered production chatbot APIs and ran model benchmarking as an intern, before converting to full time within six months.
