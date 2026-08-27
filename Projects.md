# Projects Portfolio

## 1. TripKnot
**AI-Assisted Social Travel Platform**  
*Founding Engineer | April 2026 - Present | Team of 5*  
**Production Releases:** [Google Play Store](https://play.google.com/store/apps/details?id=com.tripknot.app&pcampaignid=web_share) | [Apple App Store](https://apps.apple.com/in/app/tripknot/id6781707127)

### Project Overview
TripKnot is an AI-assisted travel itinerary planning platform designed to make group trip curation social and seamless. The platform coordinates a FastAPI backend, a Next.js admin and business console, and an Expo and React Native mobile application to deliver personalized day-by-day itineraries.

### Technical Architecture & Decisions
*   **AI Itinerary Engine:** Designed and implemented a place-scoring and diversity algorithm that curates a high-quality place pool from user preferences and budgets. It blends log-scaled popularity with rating counts, landmark designations, trending signals, and hidden-gem flags. It uses seed jitter of twelve to eighteen percent to ensure repeat requests generate distinct plans, an anchor mechanism to guarantee top landmarks are included, and round-robin category filling.
*   **LLM Orchestration:** Developed an LLM layer that handles structuring and scheduling over the curated place pool. It utilizes Google Gemini as the primary model behind a Pydantic-constrained JSON schema, with Groq Llama 3 as an automatic fallback, tracking token cost and latency on every request.
*   **Trust and Identity Verification:** Built an Aadhaar and KYC identity-verification system specifically for strangers trips where participants join travelers they do not already know, managing trip and user data models, backend validation, and the administrative review UI.
*   **Standalone Scoring Service:** Engineered a microservice calculating trending and popularity rankings in dependency order across places, destinations, and states using time-decay math with a forty-eight-hour half-life, with fully tunable configuration thresholds.
*   **DevOps and CI/CD:** Deployed containerized backend services on Google Cloud Run in the asia-south1 region. Configured GitHub Actions CI/CD with GCP Workload Identity Federation, eliminating long-lived cloud credentials, and integrated Sentry monitoring across mobile and backend.
*   **ETL and Data Ingestion:** Supported the development of an ETL tool that validates and ingests destination data from spreadsheets and CSVs, handling slug generation, geocoding, and image parsing, helping process over 7,480 place records into the production database.
*   **B2B Monetization and Partner Portal:** Engineered the business side end to end. Built a tiered subscription model featuring Free, Essential, and Growth plans paired with a commission-only, pay-as-you-earn alternative. Gated listing visibility, analytics depth, campaign quotas, and AI itinerary priority to corresponding tiers. Developed multi-step, vertical-specific onboarding flows for hotels, restaurants, and travel agencies.
*   **B2B Commission Ledger:** Programmed an automated commission-billing ledger for the pay-as-you-earn model that transparently calculates and displays the split: platform category commissions of five to ten percent, platform fees of two percent, and payment gateway pass-throughs as distinct line items.

### Technology Stack
*   **Backend:** FastAPI, Python, MongoDB Beanie ODM, Redis, Pydantic, Streamlit proof of concept
*   **Frontend & Mobile:** Next.js, React, TypeScript, Expo, React Native, Tailwind CSS, shadcn UI
*   **Infrastructure:** GCP Cloud Run, Google Cloud Storage, Workload Identity Federation, GitHub Actions, Docker, Sentry, SQS-style tasks

### Key Highlights
*   Engineered an AI itinerary engine that curates a place pool and generates personalized, budget-aware day-by-day plans in under nine seconds.
*   Designed and built an Aadhaar and KYC identity-verification system for trips with unfamiliar participants, spanning backend data models and an admin review console.
*   Designed a standalone scoring service computing trending and popularity rankings through time-decay, multi-factor models, built to remain stable from pre-launch traffic through scale.
*   Built the admin console and backend endpoints for content moderation and analytics, replacing hard deletes with a soft-cancel, audit-logged moderation workflow.
*   Shipped mobile features spanning location-aware personalization, a region-browsable search feature, and notification preferences in React Native and Expo.
*   Set up CI/CD and cloud deployment for the backend using GitHub Actions and GCP Cloud Run, cutting deployment time to 145 seconds with Sentry monitoring.
*   Supported the geocoding ETL and photo pipeline, co-building a vision classifier that screened 22,400+ photos and helped process over 7,480 records.
*   Shaped the platform's monetization model end to end, pairing tiered subscriptions with a commission-only alternative and vertical-specific onboarding for local partners.
*   Integrated sponsored search rankings and priority recommendations in the AI itinerary engine, aligning paid business tiers with scoring and placement results.

---

## 2. Auromics
**Garment Manufacturing Inventory & Production Management System**  
*Freelance Software Engineer | August 2026 | Freelance Engagement*

### Project Overview
Auromics is a cloud-based inventory, workflow, and production management system built for garment and knitting manufacturers. The platform replaces manual registers and spreadsheet-based tracking with a unified source of truth for orders, thread inventory, contractor assignments, contractor staff management, piece-rate wage calculation, and payroll processing.

### Technical Architecture & Decisions
*   **Given-and-Receive Workflow:** Modeled a production ledger where raw materials are issued to contractors or internal workers, and returned pieces are recorded against the same entry. The system supports partial receipts, mid-job reallocations between workers, and automatic fifteen-day overdue flags.
*   **Thread Inventory & Stock Deduction:** Programmed a real-time inventory manager tracking total, allocated, and available thread stock. Implemented a double-deduction guard using a special inventory transaction key to prevent duplicate stock deductions when order records are re-saved.
*   **Two-Tier Role and Access Model:** Built a secure authorization model splitting the application between an Admin role with full CRUD permissions and a limited Contractor Portal. Contractors log in via a mobile-first, web-ready interface to view and update only their assigned orders and manage their own staff roster.
*   **Automated Payroll Module:** Engineered a payroll processor that computes monthly wages based on piece-rate completions, convenience allowances, incentives, and deductions. It automatically generates formal, print-ready bank payment letters matching State Bank of India formatting.
*   **Reporting Architecture:** Created seven tabbed reporting modules including a Wages Register, Given Report, Receive Report, Inventory Report, Employee Summary, Order Master, and Given Outstanding Report, optimized for both desktop viewing and A4 landscape printing.
*   **Denormalized NoSQL Schema:** Structured the database within Firebase Firestore using a denormalized schema for high-speed reads, balancing historical data preservation against read performance.

### Technology Stack
*   **Frontend:** Next.js 15, React, TypeScript, Tailwind CSS, shadcn UI
*   **Backend & Database:** Firebase Firestore NoSQL, Firebase Authentication, Firebase Cloud Functions
*   **Hosting & Deployment:** Vercel, progressive web application configurations
*   **Print Integration:** Native Browser Print API, CSV blob exports

### Key Highlights
*   Architected a full-stack inventory and payroll system, owning the data model from the first line of code through cloud deployment.
*   Automated monthly payroll calculations, turning piece-rate completions and wage structures into print-ready bank payment letters, cutting manual operations by sixty percent.
*   Scoped a two-tier access model, limiting contractor portals to assigned orders and protecting sensitive financial details.
*   Shipped a mobile-first contractor workflow, allowing external partners to assign staff, log progress, and sync updates to the admin dashboard in real time.
*   Modeled a given-and-receive inventory workflow supporting partial receipts, worker reallocations, and automatic fifteen-day overdue flags.
*   Implemented a denormalized Firestore schema with a double-deduction guard to prevent duplicate inventory stock deductions during re-saves.

---

## 3. KittyKat AI
**Multi-Agent Brand and Campaign Management Platform**  
*AI Backend Developer | October 2023 - March 2026 | Team Project at YUVABE*

### Project Overview
KittyKat AI is an enterprise creative platform for automated brand asset and marketing campaign management. It transforms complex, multi-step marketing workflows into a single conversational interface.

### Technical Architecture & Decisions
*   **Multi-Agent LangGraph Framework:** Built the backend conversational assistant on LangGraph as a router-driven multi-agent graph across six specialized nodes. Individual nodes act as domain-specific specialists handling branding, campaign brief generation, moodboard assembly, prompt construction, and asset generation.
*   **Multi-Provider Generation Routing:** Architected a provider-agnostic image and video generation router across OpenAI and Replicate. Used a discriminated union pattern to let new generative models plug in seamlessly without hardcoded model-specific logic.
*   **CLIP-Based Moodboard Pipeline:** Built a semantic asset-search and reference-image auto-fill engine using CLIP-based vector embeddings, allowing designers to locate brand assets without manual tag entry.
*   **Product Extraction Pipeline:** Integrated a product-extraction model that detects and isolates product assets from brand photography, preparing them for programmatic campaign generation.
*   **SaaS Infrastructure:** Designed the backend for multi-tenant SaaS scale, introducing credit-tracking limits, Firebase Authentication, and real-time client updates over Server-Sent Events.

### Technology Stack
*   **Core Backend:** FastAPI, Python, MongoDB, Pydantic, Server-Sent Events
*   **AI & Agents:** LangGraph, LangChain, OpenAI API, Replicate API, CLIP Vector Search, Hugging Face
*   **Databases & Cloud:** MongoDB, Firebase Auth, Google Cloud Platform

### Key Highlights
*   Shaped the conversational campaign interface for a multi-agent AI platform, translating a LangGraph backend into a single conversational workspace for non-technical marketing teams.
*   Routed image and video generation across OpenAI and Replicate using a discriminated union pattern, allowing instant model swaps without blocking product delivery.
*   Layered CLIP-based vector search into the moodboard pipeline, enabling automatic reference-image auto-fill without manual tagging.
*   Built a product-extraction pipeline that isolates brand assets from photographs into a structured, reusable media library.
*   Designed the multi-tenant SaaS architecture with credit-tracking limits, Firebase Authentication, and real-time updates over Server-Sent Events.

---

## 4. AuroGurukul
**AI-Driven Adaptive Learning Management System**  
*Lead Full-Stack Developer | October 2023 - March 2026 | Project Ownership at YUVABE*

### Project Overview
AuroGurukul is an AI-driven learning management platform designed to deliver personalized educational pathways. It replaces traditional linear course structures with adaptive assessment systems and instant AI tutor feedback.

### Technical Architecture & Decisions
*   **Build-vs-Buy Evaluation:** Evaluated Frappe LMS against the product's requirements. Concluding that open-source alternatives fell short on adaptive learning support and AI integration, led a custom, from-scratch platform build.
*   **Pinecone-Backed RAG Study Assistant:** Engineered an on-demand AI study assistant using a Retrieval-Augmented Generation pipeline backed by a Pinecone vector database, cutting response errors by eighty percent across a fifty-query internal benchmark.
*   **Adaptive Assessment Engine:** Coded the logic for assessments that dynamically adjust question difficulty based on real-time student performance, ensuring personalized student pace and learning curves.
*   **Test Management Module:** Built a comprehensive evaluation framework supporting test creation, question bank categorization, automated grading, result submission, and cohort performance analytics.
*   **Security & Auth:** Configured email verification, password reset, and role-based access controls separating student profiles from administrative and teaching staff.

### Technology Stack
*   **Frontend:** Next.js, React, Tailwind CSS, shadcn UI
*   **Backend:** FastAPI, Python, MongoDB, Pydantic, Pinecone Vector DB
*   **Authentication:** Firebase Auth

### Key Highlights
*   Evaluated open-source learning systems, then led a custom, from-scratch build on Next.js, FastAPI, and MongoDB after concluding existing options fell short.
*   Engineered a Pinecone-backed RAG study assistant, reducing incorrect assistant responses by eighty percent across a fifty-query internal benchmark.
*   Designed adaptive assessments and analytics dashboards that adjust question difficulty and track learner progress in real time across cohorts.
*   Developed a complete Test Management Module covering test creation, automated grading, result submission, and performance analytics.
*   Rolled out secure student and staff authentication flows including email verification and role-based access controls.

---

## 5. OfferTracker
**Job Search Career-Intelligence Platform**  
*Independent Project*

### Project Overview
OfferTracker is a professional career-intelligence web application built on the principle that a job search deserves more than a standard Kanban board. Most trackers merely log status; OfferTracker analyzes outcomes, tracking resume versions against response rates and capturing structured post-interview reflections.

### Technical Architecture & Decisions
*   **Data Funnel Analytics:** Designed a performance dashboard displaying pipeline funnels, resume callback percentages, and salary trends using D3.js.
*   **Low-Friction UI Design:** Configured a minimal-input logging system requiring only the company name and role title to create an entry, ensuring logging takes seconds.
*   **Subtle Gamification:** Structured the social collaboration features including follows, groups, and milestone sharing around a quiet accountability model, intentionally excluding leaderboards and competitive points to keep the user experience professional and supportive.

### Technology Stack
*   **Backend:** FastAPI, Python, PostgreSQL, Supabase
*   **Frontend:** React 19, Vite, Tailwind CSS, D3.js for analytics

### Key Highlights
*   Designed a career-intelligence platform tracking resume versions against outcomes, helping job seekers see which resume versions correlate with callbacks.
*   Developed funnels, response rate trackers, and salary-insight dashboards using FastAPI and D3.js to expose exactly where users lose offers.
*   Designed the social interaction layer around a quiet accountability mechanic of milestone tracking without leaderboards, maintaining a professional user experience.
*   Implemented a low-friction data entry flow requiring only the company name and role to log an application in under five seconds.

---

## 6. Soulfy
**Mood-Based Music Application**  
*Independent Project*

### Project Overview
Soulfy is an independent exploration into client-side audio rendering and state synchronization. It introduces real-time WebAssembly-based processing inside a modern web application, optimizing playback queues based on local device hardware constraints.

### Key Highlights
*   Engineered client-side WebAssembly FFmpeg decoders to preprocess audio file files inside the browser context, eliminating backend processing latency.
*   Developed global state handlers using Zustand to coordinate responsive, thread-safe player queues across concurrent tab windows.

---

## 7. Semantic Search Demo
**Embedding Cosine-Similarity Evaluator**  
*Independent Project*

### Project Overview
A compact, highly targeted showcase of semantic document retrieval. It provides a pure, dependency-free demonstration of the vector-space mathematics that underpin modern Retrieval-Augmented Generation pipelines.

### Key Highlights
*   Developed a standalone Python evaluator utilizing the all-MiniLM-L6-v2 Sentence Transformer model to encode text data into high-dimensional vector spaces.
*   Calculated semantic document relevance directly using PyTorch cosine-similarity math, establishing a baseline to measure search precision without a database wrapper.
