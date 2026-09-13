# My Project Portfolio

## 1. TripKnot
**AI-Assisted Social Travel Platform**  
*Product Manager | April 2026 - Present | One of 5 Founding Team Members | One of 3 Full-Stack Engineers*
**Production Releases:** [Google Play Store](https://play.google.com/store/apps/details?id=com.tripknot.app&pcampaignid=web_share) | [Apple App Store](https://apps.apple.com/in/app/tripknot/id6781707127)

### Company & Product Context
The company is a product-first technology startup founded in 2026 around this AI-assisted travel platform as its core idea and first product. The platform supports personalized day-by-day itineraries, destination and hidden-gem discovery, curated escapes, map-based exploration, and group travel.

The full product ecosystem includes the traveler mobile application, partner-facing business portal, internal admin console, public website, backend services, and the destination-data platform that supports discovery and itinerary generation.

### Founding Team & Delivery Context
I am one of five founding team members and one of three full-stack engineers. The team consists of three full-stack engineers, one UI/UX developer, and one frontend developer. We formed the company around this product idea and coordinated the product, design, data, engineering, and release work as one founding team.

We built the platform from the ground up and released it within five months of beginning development. The work started with product definition and destination data and progressed through the backend, consumer mobile application, business portal, admin console, public website, deployment pipeline, and production operations.

### Project Overview
The platform combines a FastAPI backend, Next.js admin and business interfaces, and an Expo and React Native mobile application to turn travel preferences into personalized itineraries and connect planning with discovery, local experiences, and group travel. My role combines product management with hands-on full-stack engineering across requirements, prioritization, technical tradeoffs, delivery coordination, release, and iteration.

### Technical Architecture & Decisions
*   **AI Itinerary Engine:** Designed and implemented a place-scoring and diversity algorithm that curates a high-quality place pool from user preferences and budgets. It blends log-scaled popularity with rating counts, landmark designations, trending signals, and hidden-gem flags. It uses seed jitter of twelve to eighteen percent to ensure repeat requests generate distinct plans, an anchor mechanism to guarantee top landmarks are included, and round-robin category filling.
*   **LLM Orchestration:** Developed an LLM layer that handles structuring and scheduling over the curated place pool. Gemini uses a Pydantic-derived JSON schema and response validation; Groq Llama 3 is the automatic fallback, receiving the schema in its prompt before downstream normalization. Token cost and latency are tracked on every request.
*   **Trust and Identity Verification:** Owned the primary implementation and built the Aadhaar and KYC identity-verification system end to end for strangers trips where participants join travelers they do not already know, spanning trip and user data models, backend validation, the traveler-facing mobile flow, and the administrative review UI.
*   **Standalone Scoring Service Context:** Collaborated around the platform's one purpose-specific microservice, which was led elsewhere on the founding team and calculates trending and popularity rankings in dependency order across places, destinations, and states using time-decay math with a forty-eight-hour half-life and fully tunable thresholds. I worked with its outputs in the broader product while directly owning other areas. The main backend remains a FastAPI monolith; ETL and image-processing work are supporting tools rather than additional production microservices.
*   **DevOps and CI/CD:** Deployed containerized backend services on Google Cloud Run in the asia-south1 region. Configured GitHub Actions CI/CD with automated staging deployment, manual-gated production promotion, and GCP Workload Identity Federation, eliminating long-lived cloud credentials; integrated Sentry monitoring across mobile and backend.
*   **ETL and Data Ingestion:** Supported the API-mediated validation and ingestion workflow for an ETL tool that processes destination data from spreadsheets and CSVs, including slug generation, geocoding, image parsing, and watermark and quality screening. The tool uses authenticated backend APIs, dry runs, and duplicate detection instead of direct MongoDB writes, helping the team process over 7,500 place records into the production database.
*   **Mobile Personalization and Controls:** Built location-aware home and discovery behavior that distinguishes GPS-derived location from a manually selected city, preventing background sync from overwriting user intent. Added region-filterable state exploration and notification preferences with master and per-category controls.
*   **B2B Monetization and Partner Portal:** Served as the sole contributor to the partner-facing business portal, carrying it from product requirements and workflow design through data modeling, backend integration, interface implementation, and iteration. Built a tiered subscription model featuring Free, Essential, and Growth plans paired with a commission-only, pay-as-you-earn alternative. Gated listing visibility, analytics depth, campaign quotas, and AI itinerary priority to corresponding tiers. Developed multi-step, vertical-specific onboarding flows for hotels, restaurants, and travel agencies.
*   **B2B Commission Ledger:** Programmed an automated commission-billing ledger for the pay-as-you-earn model that transparently separates the company's commission, the payment-gateway pass-through, and the platform fee. For hotels and travel agencies, booking commissions decrease from roughly 15% on Free to roughly 5% on Growth; restaurants remain subscription-led.

### Technology Stack
*   **Backend:** FastAPI, Python, MongoDB Beanie ODM, Redis, Pydantic, Streamlit proof of concept
*   **Frontend & Mobile:** Next.js, React, TypeScript, Expo, React Native, Tailwind CSS, shadcn UI
*   **Infrastructure:** GCP Cloud Run, Google Cloud Storage, Workload Identity Federation, GitHub Actions, Docker, Sentry, SQS-style tasks

### Key Highlights
*   Helped take the travel platform from its founding idea and raw destination data to a complete production ecosystem within five months, spanning the backend, traveler mobile app, business portal, admin console, and public website.
*   Engineered an AI itinerary engine that curates a place pool and generates personalized, budget-aware day-by-day plans in about 10 seconds.
*   Designed and built an Aadhaar and KYC identity-verification system for trips with unfamiliar participants, spanning backend data models and an admin review console.
*   Integrated discovery and recommendation workflows with a standalone scoring service led elsewhere on the founding team, preserving its time-decayed, configurable ranking signals as shared product architecture.
*   Built the admin console and backend endpoints for content moderation and analytics, replacing hard deletes with a soft-cancel, audit-logged moderation workflow.
*   Shipped mobile features spanning location-aware personalization, a region-browsable search feature, and notification preferences in React Native and Expo.
*   Set up CI/CD and cloud deployment for the backend using GitHub Actions and GCP Cloud Run, cutting deployment time to about three minutes with Sentry monitoring.
*   Supported the geocoding ETL and a photo-quality pipeline led elsewhere on the founding team, including API-mediated ingestion and a vision classifier used across 22,000+ photos and 7,500+ place records.
*   Solely built the partner-facing business portal and shaped its monetization model end to end, pairing tiered subscriptions with a commission-only alternative and vertical-specific onboarding for local partners.
*   Integrated sponsored search rankings and priority recommendations in the AI itinerary engine, aligning paid business tiers with scoring and placement results.

---

## 2. Auromics
**Garment Manufacturing Inventory & Production Management System**  
*Freelance Software Engineer | August 2026 - Present | Freelance Engagement*

### Project Overview
This cloud-based inventory, workflow, and production management system was built with solo end-to-end ownership for a garment manufacturer. I directly managed the client relationship with non-technical stakeholders to gather raw requirements, design the schema, implement the database, APIs, and application services, build the frontend, and deploy the system. The production solution is in active use, and I continue to develop and support it. The platform replaces manual registers and spreadsheet-based tracking with a unified source of truth for orders, thread inventory, contractor assignments, contractor staff management, piece-rate wage calculation, and payroll processing.

### Technical Architecture & Decisions
*   **Given-and-Receive Workflow:** Modeled a production ledger where raw materials are issued to contractors or internal workers, and returned pieces are recorded against the same entry. The system supports partial receipts, mid-job reallocations between workers, and automatic fifteen-day overdue flags.
*   **Order Review and Rework Workflow:** Modeled a review state where contractor-completed work is approved into completion or rejected with a reason, reopening the work for correction and notifying the contractor. Made overdue notifications idempotent so recurring checks do not create duplicate alerts.
*   **Thread Inventory & Stock Deduction:** Programmed a real-time inventory manager tracking total, allocated, and available thread stock. Implemented a double-deduction guard using a special inventory transaction key to prevent duplicate stock deductions when order records are re-saved.
*   **Two-Tier Role and Access Model:** Built a secure authorization model splitting the application between an Admin role with full CRUD permissions and a limited Contractor Portal. Contractors log in via a mobile-first, PWA-ready interface to view and update only their assigned orders and manage their own staff roster, including multi-item assignments across workers.
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

## 3. [KittyKat AI](https://kittykat.ai/)
**Multi-Agent Brand and Campaign Management Platform**  
*AI Backend Developer | October 2023 - March 2026 | Greenfield Client Product Built at [YUVABE](https://yuvabe.com/)*

### Project Overview
This enterprise creative platform supports brand-aware marketing and campaign production. It uses an AI-powered CMO agent to bring strategy, campaign planning, content, channel decisions, and visual generation into a single brand workspace. Specialist agents handle different parts of the workflow, while a multi-model approach and human creative review help teams keep outputs useful and consistent with their brand.

The wider product includes a fashion-focused product-to-model workflow that turns ordinary product photographs into realistic model visuals through data preprocessing, model optimization, and hierarchical image refinement. This is the business and creative setting around the product-extraction, asset-search, generation-routing, and campaign-orchestration components I worked on. My direct scope included hands-on frontend development for the conversational experience alongside backend and AI workflows.

This was a client engagement, and the complete digital product was built by the delivery organization as a greenfield team effort. I was involved from the beginning, when the client contract was signed and the engagement moved into product definition. I worked through early requirements, architecture, implementation, and product iteration, giving me continuity across the product build rather than only a later maintenance phase. I did this as part of the wider delivery team, with my own scope centered on the work documented below. The product had 500+ total B2B users during my time; this is a cumulative user figure, not a daily-active-user metric.

### Product Problem & Workflow
Brand and marketing teams needed more than an isolated image generator. They needed a repeatable path from brand context and campaign briefs to moodboards, prompts, images, videos, and reusable assets without moving between disconnected tools or re-explaining the brand on every request. I helped turn that multi-step process into one conversational workspace backed by specialized agent nodes and swappable generation providers.

### Technical Architecture & Decisions
*   **Early Product Involvement:** Helped shape the implementation from the opening stage of the client engagement, connecting the initial campaign workflow and user needs to the conversational interface, agent graph, provider-routing design, and supporting SaaS services.
*   **Multi-Agent LangGraph Framework:** Built the backend conversational assistant on LangGraph as a router-driven multi-agent graph across six specialized nodes. Individual nodes act as domain-specific specialists handling branding, campaign brief generation, moodboard assembly, prompt construction, and asset generation.
*   **Multi-Provider Generation Routing:** Architected a provider-agnostic image and video generation router across OpenAI and Replicate. Used a discriminated union pattern so new generative models could plug in without hardcoded model-specific logic, supporting the product's broader multi-model approach.
*   **CLIP-Based Moodboard Pipeline:** Built a semantic asset-search and reference-image auto-fill engine using CLIP-based vector embeddings, allowing designers to locate brand assets without manual tag entry.
*   **Product Extraction Pipeline:** Integrated a product-extraction model that detects and isolates product assets from brand photography, preparing them for programmatic campaign generation.
*   **Conversational Frontend:** Worked hands-on on the frontend that translated the agent graph into a single guided conversation for non-technical marketing users, keeping specialist routing and state changes behind the interface.
*   **SaaS Infrastructure:** Designed the backend for multi-tenant SaaS scale, introducing credit-tracking limits, Firebase Authentication, and real-time client updates over Server-Sent Events.
*   **Model & Prompt Quality:** Extended model-evaluation workflows with fine-tuning and prompt engineering, improving assistant response quality by roughly 35% across evaluated campaign templates.

### Technology Stack
*   **Core Backend:** FastAPI, Python, MongoDB, Pydantic, Server-Sent Events
*   **AI & Agents:** LangGraph, LangChain, OpenAI API, Replicate API, CLIP Vector Search, Hugging Face
*   **Databases & Cloud:** MongoDB, Firebase Auth, Google Cloud Platform

### Key Highlights
*   Worked on the creative platform from the start of the client engagement, helping build the complete digital product from early product definition and architecture through implementation and iteration.
*   Shaped the conversational campaign interface for a multi-agent AI platform, translating a LangGraph backend into a single conversational workspace for non-technical marketing teams.
*   Routed image and video generation across OpenAI and Replicate using a discriminated union pattern, allowing instant model swaps without blocking product delivery.
*   Layered CLIP-based vector search into the moodboard pipeline, enabling automatic reference-image auto-fill without manual tagging.
*   Built a product-extraction pipeline that isolates brand assets from photographs into a structured, reusable media library.
*   Designed the multi-tenant SaaS architecture with credit-tracking limits, Firebase Authentication, and real-time updates over Server-Sent Events.
*   Improved response quality by roughly 35% across evaluated campaign templates through model evaluation, fine-tuning, and prompt engineering.
*   Helped automate campaign operations through the conversational multi-agent workflow, contributing to a 40% improvement in campaign engagement.

---

## 4. [AuroGurukul](https://aurogurukul.com/)
**AI-Driven Adaptive Learning Management System**  
*Lead Full-Stack Developer | October 2023 - March 2026 | Greenfield Client Product Built at [YUVABE](https://yuvabe.com/)*

### Project Overview
This education platform is rooted in integral learning and built around concept clarity, structured practice, assessment, feedback, mentoring, and learner development. Its programs serve classes 6-12 across board and competitive-exam preparation. Its school-integrated programs combine regular tests, AI-assisted analysis, weak-area targeting, performance dashboards, interactive learning, and online and campus delivery in Pondicherry.

Within that education setting, I worked on an AI-driven learning management platform designed to move beyond a single linear course path through adaptive assessments and immediate study-assistant feedback. I worked hands-on across its Next.js frontend, FastAPI backend, MongoDB data layer, authentication, test-management workflows, analytics, and AI-assisted learning features.

This was a client engagement, and the complete digital product was built by the delivery organization as a greenfield team effort. I was involved from the beginning, when the client contract was signed and the engagement moved into requirements and solution evaluation. I helped assess whether an existing LMS could support the product, participated in the decision to build a custom platform, and continued through architecture, implementation, and iteration, giving me continuity across the greenfield build rather than only a later maintenance phase.

### Learning & Assessment Context
The core product challenge was to support different participants and feedback loops in one system: students needed guided learning, assessments, results, and study support; teachers and administrators needed question banks, test creation, grading, cohort analytics, and controlled access. I translated those needs into role-aware workflows and data models rather than treating the LMS as a static course catalogue.

### Technical Architecture & Decisions
*   **Early Product Involvement:** Worked from the opening stage of the client engagement, translating the initial learning, assessment, and user-role requirements into the build-vs-buy evaluation and the architecture of the custom platform.
*   **Build-vs-Buy Evaluation:** Evaluated Frappe LMS against the product's requirements. After concluding that the open-source option fell short on adaptive learning, AI integration, and custom API support, I led a custom platform build on Next.js, FastAPI, and MongoDB.
*   **Pinecone-Backed RAG Study Assistant:** Engineered an on-demand AI study assistant using a Retrieval-Augmented Generation pipeline backed by a Pinecone vector database, reducing incorrect responses by about 80% across a fifty-query internal benchmark.
*   **Adaptive Assessment Engine:** Coded the logic for assessments that dynamically adjust question difficulty based on real-time student performance, ensuring personalized student pace and learning curves.
*   **Test Management Module:** Built a comprehensive evaluation framework supporting test creation, question bank categorization, automated grading, result submission, and cohort performance analytics.
*   **Security & Auth:** Configured email verification, password reset, and role-based access controls separating student profiles from administrative and teaching staff.

### Technology Stack
*   **Frontend:** Next.js, React, Tailwind CSS, shadcn UI
*   **Backend:** FastAPI, Python, MongoDB, Pydantic, Pinecone Vector DB
*   **Authentication:** Firebase Auth

### Key Highlights
*   Worked on the adaptive-learning platform from the start of the client engagement, helping move the complete digital product from initial requirements and build-vs-buy evaluation into a custom platform.
*   Evaluated open-source learning systems, then led a custom, from-scratch build on Next.js, FastAPI, and MongoDB after concluding existing options fell short.
*   Engineered a Pinecone-backed RAG study assistant, reducing incorrect assistant responses by about 80% across a fifty-query internal benchmark.
*   Designed adaptive assessments and analytics dashboards that adjust question difficulty and track learner progress in real time across cohorts.
*   Developed a complete Test Management Module covering test creation, automated grading, result submission, and performance analytics.
*   Rolled out secure student and staff authentication flows including email verification and role-based access controls.

---

## 5. Finmo
**Repository:** [Finance-Monitor](https://github.com/Keerthu-k/Finance-Monitor)

**Full-Stack Expense Tracker**  
*Independent Project | Solo Build*

### Project Overview
This full-stack expense tracker was built solo to log, manage, and review financial data with an emphasis on monetary correctness and reliable writes. The application pairs a Next.js interface with a FastAPI and MongoDB backend for a focused personal-finance workflow.

### Technical Architecture & Decisions
*   **Financial-Data Integrity:** Modeled monetary amounts as Python `Decimal` values, validating positive inputs and rounding them to two decimal places before persistence to avoid floating-point errors.
*   **Idempotent Write Path:** Implemented client-generated UUID idempotency keys and a unique MongoDB index so retried expense-creation requests return the existing record instead of creating duplicates.
*   **Validated REST API:** Built FastAPI CRUD endpoints with Pydantic validation, category filtering, predictable date ordering, CORS configuration, and serialized API responses.
*   **Typed Frontend:** Developed the expense-entry, list, and category-summary experience in Next.js and TypeScript, including safe amount parsing, monthly filtering, and category-level totals.
*   **Automated Verification:** Added backend API and model tests to verify validation, persistence, and response behavior.

### Technology Stack
*   **Frontend:** Next.js 14, React, TypeScript
*   **Backend:** Python, FastAPI, Pydantic, Motor
*   **Database & Testing:** MongoDB, pytest

### Key Highlights
*   Built the complete expense-tracking application solo across frontend, backend, database design, and tests.
*   Designed a Decimal-based money model and idempotent MongoDB write path to make financial records resilient to floating-point and retry-related errors.
*   Shipped a typed expense-management interface with category summaries, monthly filtering, and a validated REST API.

---

## 6. OfferTracker
**Repositories:** [Web application](https://github.com/Keerthu-k/Offertracker) · [Backend service](https://github.com/Keerthu-k/Offertracker-Backend)

**Job Search Career-Intelligence Platform**  
*Independent Project*

### Project Overview
This professional career-intelligence web application was built on the principle that a job search deserves more than a standard Kanban board. Most trackers merely log status; this system analyzes outcomes, tracking resume versions against response rates and capturing structured post-interview reflections.

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
*   Implemented a low-friction data entry flow requiring only the company name and role to log an application.

---

## 7. Soulfy
**Mood-Based Music Application**  
*Independent Project*

### Project Overview
This independent project explores client-side audio rendering and state synchronization. It introduces real-time WebAssembly-based processing inside a modern web application, optimizing playback queues based on local device hardware constraints.

### Key Highlights
*   Implemented browser-side media processing with WebAssembly FFmpeg, keeping audio preparation on the client rather than sending it to a backend processing service.
*   Developed Zustand-based player state for responsive playback queues within the application session.

---

## 8. Semantic Search Demo
**Repository:** [Text-Embeddings](https://github.com/Keerthu-k/Text-Embeddings)

**Embedding Cosine-Similarity Evaluator**  
*Independent Project*

### Project Overview
A compact, highly targeted showcase of semantic document retrieval. It demonstrates the vector-space mathematics that underpin modern Retrieval-Augmented Generation pipelines using the required Sentence Transformers and PyTorch dependencies.

### Key Highlights
*   Developed a standalone Python evaluator utilizing the all-MiniLM-L6-v2 Sentence Transformer model to encode text data into high-dimensional vector spaces.
*   Calculated semantic document relevance directly using PyTorch cosine-similarity math, establishing a baseline to measure search precision without a database wrapper.
