# My Professional Experience

## 1. Product Manager | Aneeras LLP
**April 2026 - Present | Pondicherry, India | Hybrid**  
*Product-First Travel-Technology Startup | One of 5 Founding Team Members | One of 3 Full-Stack Engineers*
**Live Apps in Production:** [Google Play Store](https://play.google.com/store/apps/details?id=com.tripknot.app&pcampaignid=web_share) | [Apple App Store](https://apps.apple.com/in/app/tripknot/id6781707127)

### Company & Product Overview
The company is a product-first technology startup founded in 2026 around an AI-assisted travel platform as its core idea and first product. It focuses on building practical digital products around real-world experiences, with travel technology establishing its initial direction.

The platform brings personalized day-by-day itinerary planning, destination and hidden-gem discovery, curated escapes, map-based exploration, and group travel into one connected experience. Its broader product ecosystem includes the traveler mobile application, a partner-facing business portal, an internal admin console, the public website, backend services, and the underlying destination-data platform.

### Founding Team & Delivery Context
I am one of five founding team members and one of three full-stack engineers. The founding team consists of three full-stack engineers, one UI/UX developer, and one frontend developer. We formed the company around the travel-platform idea, coordinated product and engineering decisions closely, and built the product from the ground up rather than inheriting an existing platform.

Within five months of beginning the build, we took the platform from the initial idea and raw destination data to a public production release. The team delivered the data foundation, backend, traveler mobile application, business portal, admin console, public website, and the supporting deployment and operational systems required to run them.

### Role & Product Ownership
My role is Product Manager, and I also contribute directly as a hands-on full-stack engineer. I help turn the product vision into priorities, workflows, system decisions, and released features while coordinating closely with the rest of the founding team. My engineering scope spans the Python and FastAPI backend, database and destination-data workflows, mobile features, the admin console, cloud delivery, and the partner-facing business portal, for which I am the sole contributor. I also work with the output of the purpose-specific scoring microservice led elsewhere on the founding team.

### Technical & Product Achievements

#### Building the AI Itinerary Engine
I built the core differentiator of the product: an AI-driven travel recommendation engine.
*   **Itinerary Optimization:** Programmed a place-scoring algorithm that structures personalized day-by-day travel plans, delivering comprehensive itineraries in about 10 seconds.
*   **Place Pool Curation:** Blend popularity scores with rating counts, landmark designations, trending signals, and hidden-gem flags to build a high-quality place pool; use round-robin category filling and budget-tier filtering that relaxes gracefully when strict filters would return too few places.
*   **Personalization Jitter:** Implement seed jitter of twelve to eighteen percent on every request to prevent repeat queries from returning identical itineraries, while utilizing an anchor mechanism to prioritize top landmarks.
*   **LLM Orchestration:** Developed an LLM layer that structures and schedules the curated place pool: Gemini uses a Pydantic-derived JSON schema and response validation, while Groq Llama 3 is the automatic fallback with the schema embedded in its prompt and downstream normalization; token cost and latency are tracked on every generation.
*   **Streamlit Prototyping:** Validated the itinerary engine with a Streamlit proof of concept featuring geo-clustering and greedy day-ordering to guide the production rewrite.

#### Designing Trust and Identity Verification
*   **Aadhaar/KYC Identity Verification:** Designed and built the platform's Aadhaar/KYC identity-verification system end to end for strangers trips in which participants may join travelers they do not already know. I owned the primary implementation across trip and user data models, verification database structures, backend validation, the traveler-facing mobile flow, and the administrative review console used to approve or reject submissions.
*   **Storage Authentication Bug Resolution:** Diagnosed and fixed a Google Cloud Storage upload authentication error by transitioning to Firebase service-account-key authentication following a public access error, restoring secure, seamless user-profile photo uploads.

#### Standalone Scoring Service
*   **Popularity Math:** Collaborated around a standalone scoring service led elsewhere on the founding team. The service computes trending and popularity rankings in dependency order across places, destinations, and states, and its outputs support the discovery and recommendation experiences I worked on.
*   **Time-Decayed Popularity Math:** Worked with the architecture of this purpose-specific ranking microservice, which uses time-decay math with a forty-eight-hour half-life and Redis atomic counters to compute trending scores across destinations. Its thresholds are tunable configuration rather than hardcoded constants. My direct ownership remained centered on the itinerary engine, verification, admin and business workflows, mobile features, and delivery infrastructure.

#### Admin Backend, Business Portal & Monetization
*   **Admin Console:** Built a Next.js web portal and FastAPI admin console supporting destination, place, and state CRUD operations, CSV import and export, real-time operational analytics dashboards, and a two-step host-verification approval flow.
*   **Business Portal Ownership:** Served as the sole contributor to the partner-facing business portal, carrying it from product requirements and workflow design through data modeling, backend integration, interface implementation, and iteration.
*   **Compliance-Focused Trip Moderation:** Restructured trip moderation to replace hard deletes with a soft-cancel, audit-logged moderation workflow containing status, reason, and audit fields for compliance.
*   **Monetization & Pricing Strategy:** Designed the commercial architecture around three subscription tiers: Free, Essential, and Growth, alongside a commission-only, pay-as-you-earn alternative. The tier model controls listing visibility, analytics-dashboard depth, push-notification campaign quotas, featured-search placement, and AI-itinerary placement priority, so commercial placement is connected to the product's scoring and recommendation workflows rather than handled as a separate manual process.
*   **Vertical-Specific Onboarding Flows:** Designed multi-step onboarding for hotels and stays, restaurants and cafés, and travel agencies. The flows capture shared business and location information, then request the data each vertical actually needs: room types and amenities for stays; cuisine, menus, and FSSAI information for restaurants; and destinations covered and trip categories for agencies. Business-registration, GST, and PAN details are included where applicable, while richer content such as additional photos, full menus, and complete room listings can be gated by subscription tier.
*   **Commission Model & Billing Transparency:** Defined the commission structure by partner type: hotels and travel agencies use a booking-commission model that decreases from roughly 15% on the Free tier to roughly 5% on Growth, while restaurants remain subscription-led because their typical table-reservation flow does not map cleanly to a paid booking commission. Programmed the pay-as-you-earn billing ledger to show the company's commission, the payment-gateway pass-through, and the platform fee as separate line items rather than collapsing them into one opaque charge.

#### Data Platform, DevOps & Infrastructure
*   **Applied Vision Moderation Pipeline:** Supported a destination-photo quality-vetting pipeline primarily led by another founding engineer. The wider pipeline evolved from OCR and frequency-analysis watermark checks to a fine-tuned Hugging Face vision classifier after tuning against false positives on food photography. It screens over 22,000 photos for watermarks, low quality, and AI-generated renders; a companion utility converts and re-hosts approved images as WebP in Google Cloud Storage with structured audit logging.
*   **Geospatial Ingestion ETL:** Supported the authenticated ingestion workflow for a geospatial pipeline that parsed and geocoded over 7,500 place records into MongoDB, resolved duplicates, and generated search tags. I worked with its API-mediated validation, dry-run, and duplicate-detection flow rather than treating direct database writes as the ingestion path.
*   **CI/CD Pipeline Optimization:** Configured GitHub Actions CI/CD to deploy containerized backend services onto Google Cloud Run, with automated staging deployment and manual-gated production promotion. Used GCP Workload Identity Federation to reduce release deployment times to about three minutes without long-lived cloud credentials.
*   **Application Monitoring:** Used Sentry across the backend and mobile application for error and application monitoring.

### Scale & Codebase Context
*   The backend codebase consists of approximately 21,000 lines across 185 API endpoints in 23 domain modules.
*   The mobile application comprises roughly 27,480 lines of code.
*   The administrative console represents approximately 17,480 lines of code.

### Key Highlights
*   Helped take the travel platform from its founding idea and raw destination data to a complete production ecosystem within five months, including the backend, traveler mobile app, business portal, admin console, and public website.
*   Took the AI itinerary workflow from Streamlit proof of concept to production, combining curated place pools, structured LLM output, automatic provider fallback, and per-generation cost and latency tracking.
*   Designed and built the Aadhaar/KYC identity-verification workflow for trips between unfamiliar participants, spanning data models, backend validation, the mobile application, and the admin review console.
*   Shipped product capabilities across FastAPI backend services, React Native mobile interfaces, and Next.js administrative and merchant portals as one of three full-stack engineers on the five-person founding team.
*   Solely built the partner-facing business portal from product requirements and workflow design through backend integration, interface implementation, and iteration.
*   Designed Free, Essential, and Growth subscription tiers, a commission-only alternative, and vertical-specific onboarding for hotels, restaurants, cafés, and travel agencies.
*   Connected merchant visibility, campaign quotas, featured placement, and AI-itinerary priority to subscription and commission rules through explicit product gates and billing workflows.
*   Integrated discovery and recommendation features with the founding team's standalone, configurable, time-decayed scoring service.
*   Built destination-management, analytics, host-verification, and audit-logged trip-moderation workflows across the admin console and backend.
*   Established containerized CI/CD on Google Cloud Run with automatic staging, gated production promotion, keyless Workload Identity Federation, and Sentry application monitoring.

---

## 2. AI Software Engineer | [YUVABE](https://yuvabe.com/)
**October 2023 - March 2026 | Auroville, Tamil Nadu | Onsite**  
*Auroville-based technology studio delivering generative AI and multi-agent systems across three live products, including one B2B platform*

### Organization & Role Context
This Auroville-based organization was founded in 2020 around a **Work, Serve, Evolve** model. Its work combines higher-order skilling and project delivery in areas such as AI and full-stack development, digital marketing, ERP, and sustainability with service to Auroville and its surrounding community. Its multidisciplinary studio brings AI, engineering, design, and marketing together for client and product work. This setting gave me experience where technical delivery, product requirements, creative workflows, and community purpose were closely connected.

I grew from an engineering intern to a full-time AI Software Engineer, taking on ownership of large language model integration strategy, multi-agent conversational design, and adaptive learning architectures. Two of my main assignments were greenfield client engagements whose complete digital products were built by the organization. I was involved from the beginning of both engagements, when each client contract was signed and the work moved into product definition. I stayed involved as the products progressed through architecture, implementation, and iteration, so my experience covers their greenfield builds rather than only a later maintenance phase. Within the delivery team, I partnered directly with product leads to translate complex business specifications into robust APIs and database structures across three live products. The creative-platform product had 500+ total B2B users during my time; this is a cumulative product-user figure, not a daily-active-user metric and not a combined figure for all three products. I also worked hands-on on the frontend interfaces for both greenfield products as part of their cross-stack delivery.

### Technical & Product Achievements

#### Choosing and Integrating LLMs
*   **Structured Evaluation Briefs:** Wrote technical briefs that defined structured evaluation criteria around quality, cost, and API latency to guide production model-selection decisions across OpenAI GPT and Google Gemini.
*   **Fine-Tuning & Accuracy Optimization:** Extended evaluation pipelines to open-source models and conducted fine-tuning and prompt engineering, improving AI assistant response quality by roughly 35% across campaign templates.
*   **AI-Assisted Development:** Added terminal utilities to daily development workflows to automate boilerplate code and shorten average debugging cycles.

#### Multi-Agent Creative Platform
This client product brings campaign planning, content, channel decisions, and visual production into a brand-aware conversational workspace. Its product model centers on a CMO agent, specialist sub-agents, reusable brand context, multi-model generation, and human creative review. The broader fashion workflow turns product photographs into realistic, campaign-ready model visuals through preprocessing, model optimization, and hierarchical refinement. I built backend, AI, and frontend parts of the conversational system within that larger product workflow.

*   **From Contract to Product Build:** Joined the engagement at its beginning, when the client contract was signed and the delivery team began shaping the product. I worked through the early product-definition and architecture stages into implementation and iteration as part of the team building the complete digital product.
*   **State Machine Assistants:** Developed the campaign-driven messaging workspace on LangGraph, coordinating state updates and routing logic across six specialized agent nodes for branding, campaign briefs, moodboards, prompt construction, and asset generation.
*   **Agnostic Model Routing:** Programmed a provider-agnostic image and video generation pipeline using a discriminated union pattern, allowing the team to add or swap OpenAI and Replicate models without rewriting product-level routing logic or redeploying model-specific branches.
*   **Brand Asset Discovery:** Constructed a CLIP-based semantic moodboard search pipeline that matched reference images without relying only on manual tags and supported automatic reference-image filling inside campaign workflows.
*   **Product Extraction:** Integrated a computer vision pipeline that detects and isolates products from brand photography so they can become structured, reusable inputs for downstream visual generation.
*   **Conversational Frontend:** Worked hands-on on the frontend experience that presented the multi-step agent workflow as one conversational workspace for non-technical marketing users.

#### Adaptive Learning Platform
This client product serves learners through structured academic programs, mentoring, regular assessment, feedback, and performance tracking. Its education model spans classes 6-12 and combines exam preparation with integral education, interactive learning, test analysis, and weak-area targeting. I worked on the software foundation for personalized learning and assessment: the Next.js interface, FastAPI services, MongoDB data model, role-based workflows, adaptive testing, and an AI study assistant.

*   **From Contract to Product Build:** Joined the engagement at its beginning, when the client contract was signed and the delivery team began defining the product. I participated in the initial requirements and build-vs-buy work, then continued into architecture, implementation, and iteration as part of the team building the complete digital product.
*   **LMS Architecture:** Evaluated Frappe LMS against the required adaptive-learning and custom-API workflows, then led the development of a custom platform on Next.js, FastAPI, and MongoDB after the open-source option fell short.
*   **Pinecone RAG:** Engineered an on-demand retrieval study assistant using a Pinecone-backed Retrieval-Augmented Generation pipeline, reducing incorrect responses by about 80% across an internal fifty-query benchmark.
*   **Adaptive Testing:** Coded database logic for test-taking workflows that dynamically adjust question difficulty based on student performance, then shipped the complete test-management and grading module.
*   **Learner and Staff Workflows:** Built authentication and role boundaries for students, teachers, and administrators so learning, assessment, and management tasks could operate in one platform without exposing the same controls to every user.

#### Limited Backend Testing
*   **AI-Assisted pytest Support:** Used pytest briefly on the creative-platform and adaptive-learning products during my full-time YUVABE role, with heavy AI assistance, to support backend test creation and execution. This was a small supporting contribution, not ownership of either product's testing strategy or comprehensive test coverage.

#### Shipping and Supporting in Production
*   **Containerized Cloud Deployments:** Deployed containerized microservices on Google Cloud Platform Cloud Run utilizing GitHub Actions CI/CD to maintain continuous delivery pipelines across three live products.
*   **Documentation & Onboarding:** Authored the internal REST API documentation and integration guides, cutting onboarding time for incoming engineers by nine business days.

### Scale & B2B Context
*   Owned LLM integration strategy and backend microservices across three live AI products; the creative-platform product had 500+ total B2B users during my time.

### Key Highlights
*   Worked from the beginning of two greenfield client engagements, taking both complete digital products from definition and architecture through implementation and iteration.
*   Owned LLM integration strategy and backend delivery across three live AI products; the creative-platform product had 500+ total B2B users during my time.
*   Built a six-node LangGraph campaign workflow and provider-agnostic image and video routing for OpenAI and Replicate models.
*   Developed CLIP-based moodboard discovery, product extraction, and a conversational frontend for brand-aware campaign and asset-generation workflows.
*   Improved campaign-template response quality by roughly 35% through structured model evaluation, fine-tuning, and prompt engineering.
*   Improved campaign engagement by 40% through multi-agent campaign workflows that connected briefs, moodboards, prompt construction, and asset generation.
*   Evaluated Frappe LMS against an adaptive-learning product's requirements, then led the custom Next.js, FastAPI, and MongoDB platform build when the open-source option fell short.
*   Built a Pinecone-backed study assistant, reducing incorrect responses by about 80% across an internal fifty-query benchmark.
*   Translated product requirements into API and database specifications, reducing developer rework by roughly 30% through earlier alignment with product leads.
*   Deployed containerized services to Google Cloud Run with GitHub Actions and documented REST APIs and integration workflows for frontend and incoming engineers.

---

## 3. AI Software Engineer Intern | [YUVABE](https://yuvabe.com/)
**March 2023 - September 2023 | Auroville, Tamil Nadu | Onsite**  
*Focused on baseline core assistant APIs, model benchmarks, and ERP automation workflows*

### Role & Achievements
*   **Asynchronous APIs:** Delivered three production-ready FastAPI endpoints for conversational interfaces, supporting two feature launches within the first three months.
*   **Model Benchmarking:** Evaluated text, image, and video models across Hugging Face and Replicate, producing side-by-side performance reports on latency, quality, and cost that guided provider selection for two major product launches.
*   **API Prompt Optimizations:** Supported model integration for OpenAI GPT and Google Gemini, contributing to prompt tuning and structured Pydantic schemas that improved output quality.
*   **Enterprise ERPNext Rollout:** Implemented ERPNext modules end to end during my internship, automating procurement workflows and improving company-wide operational efficiency by reducing average processing times from days to minutes.
*   **Full-Time Conversion:** Converted from an engineering intern to a full-time AI Software Engineer within seven months based on a track record of production-ready deliverables.

### Key Highlights
*   Delivered three production-ready FastAPI endpoints for conversational interfaces, supporting two feature launches within my first three months.
*   Supported generative-AI model integrations through prompt tuning, structured Pydantic schemas, and model-neutral backend API work.
*   Benchmarked text, image, and video models across Hugging Face and Replicate, producing latency, quality, and cost comparisons that guided provider selection for two launches.
*   Implemented ERPNext modules end to end, automating procurement, invoice, and inventory workflows and reducing processing time from days to minutes.
*   Built a track record of production-ready backend, model-evaluation, and ERP delivery and converted from intern to full-time AI Software Engineer within seven months.
