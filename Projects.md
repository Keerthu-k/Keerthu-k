# Projects

## TripKnot
**FastAPI · MongoDB (Beanie ODM) · Gemini/Groq · Next.js · Expo/React Native · GCP**

A social, AI-assisted travel itinerary planning product: a FastAPI backend with an LLM-driven itinerary generator and a trust and safety system, a Next.js admin console, and an Expo/React Native mobile app. Built end to end as one of two founding engineers, from architecture through product decisions, DevOps, and cloud deployment.

A hand-built place-scoring and diversity algorithm curates a place pool from user preferences and budget, then an LLM layer (Gemini as the primary model, Groq's Llama 3 as an automatic fallback, both constrained to a structured JSON schema) structures it into personalized, diverse day-by-day itineraries in about 10 seconds. Identity verification runs through an Aadhaar/KYC flow with an admin review queue, including a dedicated path for trips where participants don't already know each other. A standalone scoring service ranks places, destinations, and states by trending and popularity using time-decay math, and a companion image pipeline vets destination photos for watermarks and quality before they go live. An ETL pipeline with duplicate detection and validation safeguards fed 7,000-plus place records into the production database. Deployed on Google Cloud Run with GitHub Actions CI/CD (deployment time cut to about 3 minutes) and Sentry monitoring across the backend and mobile app.

## Auromics (ThreadOps): Manufacturing Management System
**Next.js 15 · TypeScript · Firebase (Firestore, Auth) · Tailwind CSS · shadcn/ui**

A solo freelance build, from the first line of code to a deployed product, with full ownership of the architecture, data model, and UI. Built for Auromics, an Auroville-based garment manufacturer that exports and imports globally, replacing the manual registers and spreadsheets the factory was running production on with a single source of truth for orders, thread inventory, client accounts, and payroll.

The core of the system is a given-and-receive workflow: raw goods go out to a contractor or worker, and the return gets logged against that same entry, with support for partial receipts, mid-job reallocation between workers, and automatic overdue flags on anything outstanding for more than 15 days. Orders move through a lifecycle with a built-in review loop: once a contractor marks their assigned work complete, it goes to the admin for review, who can approve it straight through to completed or reject it with a reason, which reopens the order and notifies the contractor. Confirming an order automatically allocates thread from inventory based on each product's per-size configuration. Access is two-tier: an admin role with full control over every module, and a limited contractor portal scoped to that contractor's own assigned work, so external production partners can update progress without seeing anyone else's data or the factory's financials.

The contractor side runs as a mobile-first, PWA-ready interface: contractors log in and see only their own assigned orders, assign local workers to specific items with individual quantities, and push status and progress updates that sync straight to the admin dashboard in real time. Shipped in phases: the first pass covered inventory, orders, products, clients, and contractors end to end; the second refined the order state machine and built out the fuller contractor mobile workflow, including multi-item orders where different workers can be assigned different quantities against different items on the same order.

Payroll runs directly off that production data. At month end, the salary module computes net pay per worker (completed quantity times wage, plus convenience allowance and incentives, minus deductions) and generates a print-ready bank payment letter formatted to match what factories already submit to their bank branch. Workers missing bank details get an amber warning and are left out of that letter specifically, though they still show up in the broader salary summary. Reporting spans seven tabbed views, including a wages register and an outstanding-work report grouped by client, built for print as much as for the screen since factory staff still work off paper.

A few deliberate design calls: notifications are idempotent, so the overdue-check job can run on every dashboard load without spamming duplicate alerts; thread inventory has a double-deduction guard so an order re-save can't accidentally deduct stock twice; and the Firestore data model is denormalized on purpose for read performance, a tradeoff that's documented rather than hidden, since it means master-record edits don't retroactively touch historical entries.

## KittyKat AI Creative Platform
**FastAPI · MongoDB · LangGraph · Next.js · Firebase · GCP**

A creative platform for brand and campaign management, built with a team of engineers. The chatbot is built on LangGraph as a router-driven multi-agent graph, with specialist nodes handling branding, campaigns, moodboards, prompting, and generation. I built the chat-driven UX for the brand and campaign management flows, and worked on the image and video generation system: model configuration and routing across providers (OpenAI's GPT Image 1, Replicate's Flux family, and others) through a discriminated union pattern that lets new models plug in without hardcoded per-model logic, along with prompt engineering for generation quality. I also built the moodboard pipeline, including CLIP-based vector search that powers reference-image auto-fill and semantic search across the asset library, and the product extraction pipeline that detects and isolates product assets from brand images. Multi-tenant by design, with credit tracking, Firebase auth, and real-time updates over server-sent events.

## AuroGurukul LMS Platform
**Next.js · FastAPI · MongoDB · Firebase Auth · Retrieval-Augmented Generation (RAG) · Pinecone · LLMs**

An AI-driven learning management system with adaptive assessments and a RAG-based chatbot, backed by a Pinecone vector search pipeline, that gives learners real-time support instead of making them wait on a human; a 50-plus query internal benchmark showed an 80 percent drop in incorrect responses. Evaluated Frappe LMS first, then built a custom platform from scratch on Next.js, FastAPI, and MongoDB after concluding Frappe couldn't meet the product's requirements, including a full Test Management Module (test creation, question management, result submission, performance analytics). Built the analytics dashboards that track learner progress, along with the full auth flow (email verification, forgot and reset password) and both the frontend and backend end to end.

## OfferTracker
**FastAPI · PostgreSQL · Supabase · React 19 · Vite · Tailwind CSS · D3.js**

A career intelligence platform for job seekers, built on the idea that a job search deserves more than a Kanban board. Most trackers just record what happened; OfferTracker is built to help explain why, tracking resume versions against outcomes, logging structured reflections after each interview stage, and surfacing skill gaps that keep showing up so they can actually be addressed.

The entry point is intentionally minimal (just company name and role title are required) so logging an application takes seconds, not minutes. Beyond the personal tracker, it has a lightweight social layer: follows, groups, and a shared post feed, plus quiet milestone tracking instead of points or leaderboards. The analytics dashboard covers pipeline funnels, response rates, and salary insights, built with D3.js.

## Soulfy
**Next.js · Zustand · React Query · FFmpeg**

A music app exploring mood-based listening, with client-side audio processing via FFmpeg and Zustand for state management.

## Semantic Search Demo
**Python · Sentence Transformers · PyTorch**

A small semantic search tool built on the all-MiniLM-L6-v2 sentence embedding model. Encodes a corpus of documents and a set of queries, then ranks results by cosine similarity, a compact demonstration of embedding-based retrieval outside of a larger RAG system.
