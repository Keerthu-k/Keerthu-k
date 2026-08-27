# Professional Experience Portfolio

## 1. Founding Engineer | TripKnot - Aneeras LLP
**April 2026 - Present | Pondicherry, India | Hybrid**  
*Early-Stage AI-Assisted Travel-Tech Startup | One of 5 Founding Engineers*  
**Live Apps in Production:** [Google Play Store](https://play.google.com/store/apps/details?id=com.tripknot.app&pcampaignid=web_share) | [Apple App Store](https://apps.apple.com/in/app/tripknot/id6781707127)

### Role & Product Ownership
As a Founding Engineer, the roles of system architecture and product strategy sit under a single unified responsibility. I co-built the social, AI-assisted travel itinerary planning platform end to end. I manage the development of five FastAPI backend microservices, lead database modeling, design multi-vertical merchant onboarding portals, configure keyless deployment pipelines, and engineer the mobile feed interfaces.

### Technical & Product Achievements

#### Building the AI Itinerary Engine
I built the core differentiator of the product: an AI-driven travel recommendation engine.
*   **Itinerary Optimization:** Programmed a place-scoring algorithm that structures personalized day-by-day travel plans, delivering comprehensive itineraries in under nine seconds.
*   **Place Pool Curation:** Blend popularity scores with rating counts, landmark designations, trending signals, and hidden-gem flags to build a high-quality place pool.
*   **Personalization Jitter:** Implement seed jitter of twelve to eighteen percent on every request to prevent repeat queries from returning identical itineraries, while utilizing an anchor mechanism to prioritize top landmarks.
*   **LLM Orchestration:** Developed an LLM layer that structures and schedules the curated place pool, utilizing Google Gemini as the primary model behind a Pydantic-constrained JSON schema, with Groq Llama 3 as an automatic fallback, tracking token cost and latency on every generation.
*   **Streamlit Prototyping:** Validated the itinerary engine with a Streamlit proof of concept featuring geo-clustering and greedy day-ordering to guide the production rewrite.

#### Designing Trust and Identity Verification
*   **Verification Flows:** Designed a database validation system and admin console to verify traveler identities for collaborative trips, ensuring compliance with verification data structures.
*   **Identity Verification Database:** Designed and built an Aadhaar and KYC identity-verification database and administrative review console for group-trip traveler safety.
*   **Storage Authentication Bug Resolution:** Diagnosed and fixed a Google Cloud Storage upload authentication error by transitioning to Firebase service-account-key authentication following a public access error, restoring secure, seamless user-profile photo uploads.

#### Standalone Scoring Service
*   **Popularity Math:** Designed a standalone scoring service that computes trending and popularity rankings in dependency order across places, destinations, and states.
*   **Time-Decayed Popularity Math:** Designed a standalone ranking microservice utilizing time-decay math with a forty-eight-hour half-life and Redis atomic counters to compute trending scores across destinations. Every threshold is configured as a tunable variable rather than a hardcoded constant to ensure scalability.

#### Admin Backend, Business Portal & Monetization
*   **Admin Console:** Built a Next.js web portal and FastAPI admin console supporting destination, place, and state CRUD operations, CSV content ingestion, and real-time operational analytics dashboards.
*   **Compliance-Focused Trip Moderation:** Restructured trip moderation to replace hard deletes with a soft-cancel, audit-logged moderation workflow containing status, reason, and audit fields for compliance.
*   **Monetization & Pricing Strategy:** Designed the platform's commercial architecture, pairing tiered subscriptions with a commission-only, pay-as-you-earn model, gating listings, analytics depth, and AI prioritization based on subscription tier.
*   **Onboarding Flows:** Designed multi-step, vertical-specific onboarding flows for hotels and stays, restaurants and cafes, and travel agencies, covering business registrations, food safety licenses, and tax details.
*   **Automated Commission Billing:** Programmed an automated commission ledger for the pay-as-you-earn plan, calculating and presenting the split of platform commissions and gateway pass-throughs as separate line items for billing transparency.

#### Data Platform, DevOps & Infrastructure
*   **Applied Vision Moderation Pipeline:** Developed a destination-photo quality vetting pipeline, fine-tuning a Hugging Face vision classifier to screen over 22,400 photos for watermarks, low quality, and AI-generated renders.
*   **Geospatial Ingestion ETL:** Contributed to a geospatial data ingestion pipeline that parsed and geocoded over 7,480 place records into MongoDB, resolving duplicates and generating search tags.
*   **CI/CD Pipeline Optimization:** Configured GitHub Actions CI/CD to deploy containerized backend services onto Google Cloud Run, reducing release deployment times to 145 seconds using GCP Workload Identity Federation.

### Scale & Codebase Context
*   The backend codebase consists of approximately 21,000 lines across 185 API endpoints in 23 domain modules.
*   The mobile application comprises roughly 27,480 lines of code.
*   The administrative console represents approximately 17,480 lines of code.

### Key Highlights
*   Sequenced the itinerary engine's roadmap from a prototype to a production rewrite, engineering a place-scoring algorithm that curates customized place pools in under nine seconds.
*   Designed a two-step identity-verification system gating trips between strangers behind manual approval, spanning data models, backend validation, the user app, and the admin review console.
*   Owned end-to-end product decisions as one of five founding engineers, shipping features across mobile, backend, and web interfaces.
*   Shaped the platform's monetization model, pairing tiered subscriptions with a commission-only alternative and vertical-specific onboarding for hotels, restaurants, and travel agencies.
*   Developed a standalone scoring service computing trending and popularity rankings through time-decay, multi-factor models, built to remain stable from pre-launch traffic through scale.
*   Optimized deployment times to a 145-second average by establishing GitHub Actions CI/CD onto GCP Cloud Run with keyless Workload Identity Federation.
*   Built the admin console and backend from CRUD tools to an analytics dashboard, replacing hard deletes with an audit-logged, two-step trip-moderation flow for compliance.

---

## 2. AI Software Engineer | YUVABE
**October 2023 - March 2026 | Auroville, Tamil Nadu | Onsite**  
*Technology studio delivering generative AI and multi-agent SaaS products across three B2B products*

### Role & Systems Ownership
I grew from an engineering intern to full-time AI Software Engineer, taking on ownership of Large Language Model integration strategy, multi-agent conversational design, adaptive learning architectures. I partnered directly with product leads to translate complex business specifications into robust APIs and database structures, serving over five hundred daily active B2B users.

### Technical & Product Achievements

#### Choosing and Integrating LLMs
*   **Structured Evaluation Briefs:** Wrote technical briefs that defined structured evaluation criteria around quality, cost, and API latency to guide production model-selection decisions across OpenAI GPT and Google Gemini.
*   **Fine-Tuning & Accuracy Optimization:** Extended evaluation pipelines to open-source models and conducted fine-tuning and prompt engineering, improving AI assistant response quality by roughly thirty percent across campaign templates.
*   **AI-Assisted Development:** Integrated terminal utility integrations into daily development workflows to automate boilerplate code, reducing average debugging cycles.

#### Multi-Agent Orchestration
*   **State Machine Assistants:** Developed a campaign-driven messaging workspace utilizing LangGraph, coordinating state updates and routing logic across six specialized agent nodes.
*   **Agnostic Model Routing:** Programmed a provider-agnostic model routing pipeline using a discriminated union pattern to allow instant API model swaps without code redeployments.
*   **Semantic Search:** Constructed moodboard search pipelines utilizing vector embeddings to support automatic reference-image matching, and engineered a computer vision product extraction pipeline that detects and isolates product assets from brand photography.

#### Custom LMS Development
*   **LMS Architecture:** Led the development of a custom, from-scratch learning management platform on Next.js, FastAPI, and MongoDB after audits proved existing open-source options lacked custom API support.
*   **Pinecone RAG:** Engineered an on-demand retrieval study assistant utilizing a Pinecone vector database, reducing incorrect responses by eighty percent during evaluation tests.
*   **Adaptive Testing:** Coded database logic for test-taking engines that dynamically adjust question difficulty based on student performance, shipping a full test-management grading module.

#### Shipping and Supporting in Production
*   **Containerized Cloud Deployments:** Deployed containerized microservices on Google Cloud Platform Cloud Run utilizing GitHub Actions CI/CD to maintain continuous delivery pipelines across three live products.
*   **Documentation & Onboarding:** Authored the internal REST API documentation and integration guides, cutting onboarding time for incoming engineers by nine business days.

### Scale & B2B Context
*   Successfully owned LLM integration strategy and backend microservices across three live AI products serving 580+ daily active B2B users.

### Key Highlights
*   Grew from shipping features to owning LLM integration strategy across three live AI products serving five hundred daily active B2B users.
*   Engineered a RAG-based AI assistant on a Pinecone vector search pipeline, cutting incorrect responses by eighty percent across an internal fifty-query benchmark.
*   Directed model-selection evaluations across multiple providers, improving response quality by roughly thirty percent through fine-tuning and prompt engineering.
*   Partnered directly with product leads to translate complex business specifications into robust APIs, reducing developer rework by 28.5%.
*   Evaluated an open-source learning platform against product requirements, then led a from-scratch rebuild on FastAPI, Next.js, and MongoDB after it fell short.
*   Orchestrated multi-agent workflows on a FastAPI microservices backend to automate marketing campaign operations, cutting manual intervention and lifting user engagement by forty percent.
*   Integrated Claude Code into daily terminal development workflows to reduce boilerplate coding times by forty percent.
*   Deployed containerized AI microservices to GCP Cloud Run via GitHub Actions, securing continuous delivery pipelines across three live products serving five hundred daily active B2B users.
*   Ran sprint planning, backlog grooming, and retrospective reviews with product and design to align technical feature scope with user-facing goals on an agile team.
*   Authored the internal REST API documentation and integration guides, cutting frontend onboarding times by nine business days.

---

## 3. AI Software Engineer Intern | YUVABE
**March 2023 - September 2023 | Auroville, Tamil Nadu | Onsite**  
*Focused on baseline core assistant APIs, model benchmarks, and ERP automation workflows*

### Role & Achievements
*   **Asynchronous APIs:** Delivered three production-ready FastAPI endpoints for conversational interfaces, supporting two feature launches within the first three months.
*   **Model Benchmarking:** Evaluated text, image, and video models across Hugging Face and Replicate, producing side-by-side performance reports on latency, quality, and cost that guided provider selection for two major product launches.
*   **API Prompt Optimizations:** Supported model integration for OpenAI GPT and Google Gemini, contributing to prompt tuning and structured Pydantic schemas that improved output quality.
*   **Enterprise ERPNext Rollout:** Led the end-to-end implementation of ERPNext modules as an intern, automating procurement workflows to improve company-wide operational efficiency by reducing average processing times from days to minutes.
*   **Full-Time Conversion:** Converted from an engineering intern to a full-time AI Software Engineer within seven months based on a track record of production-ready deliverables.

### Key Highlights
*   Delivered production-ready backend APIs in FastAPI, powering AI-driven conversational workflows within the first three months.
*   Integrated OpenAI, Gemini, and Hugging Face models into scalable, production-ready generative AI workflows.
*   Benchmarked image and video models across Hugging Face and Replicate, guiding provider choice for two launches.
*   Led ERPNext implementations end to end during her internship, improving operational efficiency by automating manual workflows to reduce average invoice and inventory processing times.
*   Managed backend modules end to end on an agile team and converted to a full-time role within seven months.
