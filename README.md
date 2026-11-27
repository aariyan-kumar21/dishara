# Dishaara — Bharat Safe Yatra

> **India's Intelligent Union Territory Tourism & Safety Platform** (Smart India Hackathon 2026)
>
> *Discover. Plan. Book. Navigate. Stay Safe.*

 **[Live Website →](https://dishaara.vercel.app/)**
---

## 📖 Table of Contents

1. [Problem Statement](#1--problem-statement)
2. [How Dishaara Solves It](#2--how-dishaara-solves-it)
3. [Features](#3--features)
4. [Tech Stack & Workflow](#4--tech-stack--workflow)
5. [Repository Structure](#5--repository-structure)
6. [Union Territory References](#6--union-territory-references)
7. [API Overview](#7--api-overview)
8. [Data Model](#8--data-model)
9. [Data Integrity & Verification](#9--data-integrity--verification)
10. [Roadmap](#13--roadmap)

---

## 1. Problem Statement

Tourists visiting India's eight Union Territories have no single, reliable place to plan and manage a trip. A typical traveller juggles Google Search for destinations, Google Maps for navigation, booking sites for stays, airline and transport sites, government portals for permits, weather apps, social media for recommendations, separate festival sites, and emergency services that are disconnected from everything else.

This creates six core problems:

| Problem | What it looks like |
|---|---|
| **Fragmented information** | Tourism details are scattered across many platforms |
| **Difficult trip planning** | Travellers research and build itineraries by hand |
| **No contextual intelligence** | Nothing combines destination, weather, route, budget, safety and personal preferences |
| **Safety limitations** | Emergency information is detached from the traveller's location and itinerary |
| **Unreliable information** | Content is often outdated, incomplete or unofficial |
| **Poor connectivity** | Remote destinations (Ladakh, Andaman, Lakshadweep) have unreliable internet |

---

## 2. How Dishaara Solves It

Dishaara is a **single tourism intelligence platform** covering all 8 Union Territories. A tourist can complete the whole journey without leaving the platform:

```text
Discover → Understand → Plan → Modify → See the route → Check live conditions → Book → Navigate → Get emergency help
```

| Problem | Dishaara's answer |
|---|---|
| Fragmented information | One platform for destinations, maps, weather, festivals, bookings and safety |
| Difficult trip planning | **Yatra AI** generates structured itineraries from budget, days, interests and travel style, and users can edit them freely |
| No contextual intelligence | Destination + weather + route + budget + safety + preferences are combined in one engine |
| Safety limitations | A location-aware **SOS** finds the nearest hospital, police and emergency services instantly, and does not depend on AI |
| Unreliable information | A **verified-data-first** model where every record carries its source, last-updated date and verification status |
| Poor connectivity | An offline-friendly design for itineraries, emergency numbers and destination info |

**Core principle:** Dishaara is *data-first, AI-powered*. Verified official data comes first, and AI reasons over it. AI is never the source of truth.

---

## 3. Features

### Discovery & Destination Intelligence
- **Cinematic home page** with a hero carousel of all 8 UTs (weather, best travel period, rating)
- **Universal search** across destinations, attractions, hotels, restaurants, festivals, activities and nearby places, with semantic search planned (e.g. *"peaceful places near Delhi"*)
- **Popular Across Bharat** destination cards (rating, weather, best time, starting cost, Add to Yatra)
- **Union Territory Explorer** with major attractions and activities for each UT
- **Destination pages** covering overview, attractions, experiences, hotels, restaurants, festivals, culture, weather, transport, safety, emergency facilities, best time, budget, suggested itinerary, map, nearby places and advisories

### Yatra AI & Trip Planning
- **Yatra AI assistant**: a tool-using, RAG-grounded travel agent that answers with citations
- **AI trip planner**: input destination, days, travellers, budget, interests, travel style, accommodation and transport preferences
- **Editable, intelligent itinerary**: add, remove, reorder and resize days; route, distance, time and cost are recalculated automatically
- **Dynamic itinerary optimisation**: reacts to weather alerts, proposes alternatives and applies changes only after user approval
- **Itinerary versioning** with preview, confirm and restore
- **Budget planner**: transport, hotels, food, activities, local travel and an emergency buffer
- **Packing assistant**: personalised by destination, weather, duration and activities

### Maps & Navigation
- **Interactive map**: standard, satellite, terrain and 3D views
- **Layers**: destinations, attractions, hotels, restaurants, hospitals, police, emergency facilities, festivals and alerts
- **Automatic route generation** from itineraries with distance, time, elevation, stops, fuel stations, rest areas and safety alerts
- **Yatra Mode**: simplified in-trip view with current location, ETA, remaining distance, weather and alerts

### Live Intelligence
- **Yatra Live** dashboard: weather, traffic, road conditions, flights, trains, ferries, advisories, festivals, local events and safety alerts
- **Festival intelligence**: structured festival database filterable by UT, month, category, distance and date

### Booking
- **Provider-abstracted booking** for hotels, flights, activities, transport and experiences
- **Booking flow**: search → select → availability → price → traveller details → provider checkout → confirmation → My Yatra
- Bookings link automatically to the user's itinerary, and the AI never makes a paid booking without explicit confirmation

### Safety
- **Yatra Safe**: emergency contacts, police stations, hospitals, ambulances, fire stations, tourist assistance, advisories and recommendations
- **One-tap SOS**: finds the user's location, nearest hospital, police, emergency service, current itinerary and emergency contacts
- **Location-based emergency search** (e.g. *hospitals within 5 km*, *emergency services along my route*)
- **Hard safety/rules records** for restricted areas, permits and protected zones

### Local Guide & Personal Tools
- **Culture & local guide**: languages, greetings, etiquette, dress, religious and photography etiquette, useful phrases
- **Food discovery**: local dishes, street food, restaurants, with vegetarian, vegan, Jain-friendly, halal and family-friendly filters
- **User account**: profile, saved destinations, wishlists, trips, bookings, preferences, emergency contacts
- **Yatra Vault**: secure storage for tickets, permits, insurance and confirmations *(planned)*
- **Travel Readiness Score**: e.g. *"Your Yatra is 82% ready"* *(planned)*
- **Share My Yatra**: secure live-location link for trusted contacts *(planned)*
- **Offline mode**: saved itinerary, emergency numbers and map info *(planned)*

### Platform Qualities
- English + Hindi first, with an architecture ready for more languages
- Accessibility: keyboard navigation, screen readers, high contrast, adjustable fonts, reduced motion, clear emergency UI
- Admin dashboard (planned) to manage territories, destinations, festivals, emergency data, alerts, advisories, AI knowledge and booking providers

---

## 4. Tech Stack & Workflow

### 4.1 End-to-end workflow
<img width="2352" height="1233" alt="workflow" src="https://github.com/user-attachments/assets/c270c7f9-1573-440a-a3a3-ad6d753429bc" />


### 4.2 Data workflow (Verified Data → Intelligence → Experience)

```text
Official Sources
      ↓
Research & Source Snapshot
      ↓
Normalisation → Duplicate Check → Fact Check
      ↓
Verification (source URL + status retained)
      ↓
PostgreSQL / PostGIS / pgvector
      ↓
REST API
      ↓
Map · Itinerary · Booking · Safety · Yatra AI
      ↓
User Experience
```

### 4.3 Yatra AI workflow

```text
User request ("Plan a 6-day Ladakh trip for 2 under ₹50,000")
      ↓
Intent detection → parameter extraction (destination, days, travellers, budget)
      ↓
Retrieve destinations & attractions → calculate route → estimate budget → check weather
      ↓
AI planning → structured itinerary JSON
      ↓
Save to database → render in the frontend
```

### 4.4 SOS workflow (deterministic, no AI)

```text
SOS button → browser GPS → Safety API → PostGIS nearest-neighbour query
      ↓
Hospital · Police · Fire · Official contacts → Emergency UI (call, location, navigate)
```

### 4.5 Stack summary

| Layer | Implemented in this repo | Target architecture (design docs) |
|---|---|---|
| **Frontend** | Next.js (App Router), React, TypeScript, Tailwind CSS | + shadcn/ui, Framer Motion, Zustand, TanStack Query |
| **Backend** | Node.js + Express (TypeScript, port 5000) | NestJS modular monolith |
| **API** | REST + JSON, `/api/v1`, 18 domain endpoint groups | Same, extended per the Phase 4 spec |
| **AI** | AI orchestrator + RAG in `backend/src/lib` | OpenAI API, tool calling, structured outputs |
| **Database** | Fixtures / seed data | PostgreSQL + PostGIS + pgvector with Prisma |
| **Cache** | n/a | Redis (weather, routes, search, rate limits) |
| **Maps** | Geocoding and markers endpoints, GIS utilities | Mapbox GL JS + Mapbox Directions |
| **Storage** | n/a | Cloudflare R2 / S3 |
| **Monitoring** | n/a | Sentry + structured logs |
| **Deployment** | Vercel | Vercel + managed backend and database |

> The target architecture comes from the Phase 2–4 design documents. The "Implemented" column reflects the current code.

---

## 5. Repository Structure

```text
SIH-main/
├── frontend/                  # Next.js / React UI client
│   ├── public/                # Static assets & icons
│   ├── src/
│   │   ├── app/               # App Router pages & views
│   │   ├── components/        # Reusable UI components
│   │   ├── services/          # Client API service callers
│   │   ├── css/               # Styling & design system tokens
│   │   ├── js/                # Vanilla / modular scripts
│   │   ├── lib/               # Utilities & providers
│   │   └── types/             # Frontend TypeScript types
│   ├── next.config.ts         # Next.js config with API proxy rewrites
│   ├── tailwind.config.ts     # Tailwind CSS config
│   ├── tsconfig.json          # TypeScript configuration
│   └── package.json
│
├── backend/                   # Node.js & Express API server
│   ├── src/
│   │   ├── server.ts          # Express server entry point (port 5000)
│   │   ├── routes/            # Express route registrations
│   │   ├── api/v1/            # 18 domain API endpoints
│   │   ├── adapter.ts         # Web-standard request/response adapter
│   │   ├── shims/             # Lightweight Next.js server shims
│   │   ├── lib/               # AI orchestrator, RAG, GIS & fixtures
│   │   └── types/             # Backend TypeScript types
│   ├── tsconfig.json
│   └── package.json
│
├── package.json               # Root orchestrator scripts
└── README.md
```

The decoupled `frontend/` and `backend/` projects communicate over REST, and the frontend proxies API calls through Next.js rewrites.

---

## 6. Union Territory References

All tourism data follows a strict **source hierarchy**:

1. **Tier 1:** UT administrations, UT tourism departments, official government portals
2. **Tier 2:** Ministry of Tourism, Incredible India, India.gov.in, National Government Services Portal
3. **Tier 3:** Government tourism corporations (e.g. JKTDC, PTDC)
4. **Tier 4:** Other authoritative sources, only when the above don't provide the data

**Research baseline cut-off: 26 August 2026.**

### 6.1 Official source registry

| # | Union Territory | Canonical ID | Official references |
|---|---|---|---|
| 1 | **Andaman & Nicobar Islands** | `ANDAMAN_NICOBAR` | [tourism.andamannicobar.gov.in](https://tourism.andamannicobar.gov.in/) · [southandaman.nic.in/tourism](https://southandaman.nic.in/tourism/) |
| 2 | **Chandigarh** | `CHANDIGARH` | [chandigarhtourism.gov.in](https://chandigarhtourism.gov.in/) |
| 3 | **Dadra & Nagar Haveli and Daman & Diu** | `DNH_DD` | [ddd.gov.in](https://ddd.gov.in/) · [places-centres](https://ddd.gov.in/places-centres/) · [tourism-2](https://ddd.gov.in/tourism-2/) |
| 4 | **Delhi** | `DELHI` | [delhitourism.gov.in](https://delhitourism.gov.in/) |
| 5 | **Jammu & Kashmir** | `JAMMU_KASHMIR` | [jktdc.co.in](https://www.jktdc.co.in/) · [law.jk.gov.in](https://law.jk.gov.in/) |
| 6 | **Ladakh** | `LADAKH` | [tourism.ladakh.gov.in](https://tourism.ladakh.gov.in/) · [ladakh.gov.in](https://ladakh.gov.in/) |
| 7 | **Lakshadweep** | `LAKSHADWEEP` | [lakshadweep.gov.in](https://lakshadweep.gov.in/) · [epermit.utl.gov.in](https://epermit.utl.gov.in/) · [services.india.gov.in](https://services.india.gov.in/) |
| 8 | **Puducherry** | `PUDUCHERRY` | [tourism.py.gov.in](https://tourism.py.gov.in/) · [pondytourism.py.gov.in](https://pondytourism.py.gov.in/) |

### 6.2 Central government references

| Source | URL |
|---|---|
| Incredible India (Ministry of Tourism) | https://www.incredibleindia.gov.in/ |
| Ministry of Tourism | https://tourism.gov.in/ |
| Tourism Data Portal | https://www.data.tourism.gov.in/ |
| India.gov.in | https://www.india.gov.in/ |

Incredible India also maintains the official list of UT tourism websites: [destinations/states](https://www.incredibleindia.gov.in/content/incredible-india-v2/en/destinations/states.html).

### 6.3 What each source provides

| Union Territory | Data drawn from the official source |
|---|---|
| Andaman & Nicobar | Destinations, activities, itineraries, ferry services, accommodation, water-sports registration, guide directory, policies and restricted-area guidelines. Also a **live availability source** for Cellular Jail Sound & Light Show bookings |
| Chandigarh | Attractions, events, itineraries, travel desk and e-ticketing |
| DNH & DD | Places, tourism department information, accommodation, tourism notices |
| Delhi | Destinations, heritage, museums, gardens, religious tourism, food, shopping, festivals, travel information |
| Jammu & Kashmir | Destinations, hotels, adventure tourism, gardens, lakes, shrines, packages, tourist-trade regulations |
| Ladakh | Destination data and coordinates, experiences, seasonal information, permit/access data, 2026 event calendar |
| Lakshadweep | Destination information, tourism packages, permit requirements, government booking portals |
| Puducherry | Tourism information, PTDC services, travel guidance, accommodation |

### 6.4 Official foreign tourist visits baseline (Ministry of Tourism)

| Union Territory | 2021 | 2022 | 2023 |
|---|---:|---:|---:|
| Andaman & Nicobar Islands | 1,687 | 4,461 | 9,025 |
| Chandigarh | 5,451 | 28,439 | 31,498 |
| DNH & Daman & Diu | 185 | 1,791 | 4,048 |
| Delhi | 100,178 | 815,713 | 1,828,116 |
| Jammu & Kashmir | 1,650 | 19,985 | 55,337 |
| Ladakh | 1,054 | 21,259 | 40,970 |
| Lakshadweep | 4 | 125 | 755 |
| Puducherry | 321 | 862 | 31,214 |

*Source: Ministry of Tourism, Government of India (Lok Sabha answer dated 03 February 2025). These are **foreign tourist visits**, not total tourist arrivals.*

### 6.5 Naming note

Use the current official name **Sri Vijaya Puram** (formerly Port Blair) as the canonical city name for Andaman & Nicobar records.

---

## 7. API Overview

The backend serves REST + JSON under `/api/v1` with a standard response envelope:

```json
{ "success": true, "data": {}, "meta": {}, "error": null }
```

### Endpoints in the current backend

| Domain | Endpoints |
|---|---|
| Health | `GET /health` |
| Territories | `GET /territories`, `GET /territories/:slug` |
| Destinations | `GET /destinations`, `GET /destinations/:slug` |
| Safety & SOS | `POST /safety/sos`, `GET /safety/advisories`, `GET /safety/contacts` |
| AI Companion | `POST /ai/chat`, `POST /ai/itinerary` |
| Itineraries | `GET /itineraries`, `POST /itineraries` |
| Weather & Live | `GET /weather`, `GET /safety/live` |
| Travel & Bookings | `GET /flights`, `GET /hotels`, `GET /festivals` |
| Maps & Geocoding | `GET /maps/geocoding`, `GET /maps/markers` |
| Authentication | `POST /auth/login`, `POST /auth/register` |

### Planned (Phase 4 specification)

- **Search & places:** `/search`, `/places/nearby`, attractions, experiences, restaurants, events, culture, food, transport, permits, rules
- **Itinerary editing:** days and items CRUD, `reorder`, `resize`, `optimize`, `preview-changes`, `confirm-changes`, versions and restore
- **Maps:** `/maps/routes`, `/maps/routes/multi-stop`, `/maps/layers`, `/itineraries/:id/route`
- **AI:** conversations, `/ai/recommend`, `/ai/ask` (with citations)
- **Booking:** search, availability, create, cancel and audit events
- **Safety:** `/safety/emergency/nearby`, `/safety/alerts`, emergency facilities
- **User & trip tools:** preferences, saved places, reviews, emergency contacts, packing, budget, share, live location
- **Admin:** content, safety, verification, knowledge base and data sources (role-based access)

**Conventions:** URL versioning, pagination (`page`, `limit`, `cursor`), whitelisted sorting, server-side filtering, rate limiting, idempotency for bookings and SOS, and consistent errors with a `request_id`.

---

## 8. Data Model

The Phase 3 schema defines **52 tables** (PostgreSQL + PostGIS + pgvector):

| Area | Tables |
|---|---|
| Geography | `union_territories`, `regions` |
| Tourism | `destinations`, `attractions`, `experiences`, `hotels`, `restaurants`, `festivals`, `events` |
| Safety | `emergency_facilities`, `emergency_contacts`, `travel_advisories`, `safety_alerts`, `permits`, `destination_rules` |
| Travel | `itineraries`, `itinerary_days`, `itinerary_items`, `itinerary_transports`, `itinerary_versions`, `routes`, `route_stops` |
| Booking | `booking_providers`, `bookable_listings`, `booking_availability`, `bookings`, `booking_events` |
| AI / RAG | `ai_conversations`, `ai_messages`, `ai_tool_executions`, `knowledge_documents`, `knowledge_chunks`, `ai_citations` |
| Users | `users`, `user_preferences`, `saved_places`, `reviews`, `user_emergency_contacts` |
| Trip tools | `packing_lists`, `packing_items`, `budget_plans`, `budget_items`, `yatra_share_sessions`, `live_location_events` |
| Content & trust | `media`, `data_sources`, `verification_records`, `content_versions`, `weather_snapshots` |
| Local guide | `destination_culture`, `food_items`, `transport_options` |

Key decisions: UUID primary keys, WGS 84 (EPSG:4326) coordinates, GIST spatial indexes for nearest-facility queries, soft deletes on major entities, and provider-specific booking data kept in JSONB so the schema stays provider-independent.

---

## 9. Data Integrity & Verification

- **No invented data.** Unverifiable values are marked `NOT VERIFIED` or stored as `NULL`. Unannounced dates are `TBD`, and dynamic prices are flagged `provider_api_required`.
- **Verification statuses:** `PENDING_REVIEW` · `VERIFIED` · `OUTDATED` · `REJECTED` · `DISABLED`
- **A record is `VERIFIED` only when** the source is authoritative, the data is identifiable and current enough for its type, it matches the record, and the source URL is retained.
- **Time-sensitive data is fetched live, not seeded as fact:** weather, hotel prices, availability, road conditions, festival dates, permits and emergency numbers.
- **AI is not a source of truth.** AI output is kept separate from verified data, and critical information (emergency contacts, permits, regulations, advisories) is never AI-only.
- **User-facing labels** distinguish `Official`, `Verified`, `Updated recently`, `Live`, `Estimated` and `AI Recommendation`.
- The research baseline should be re-synchronised against official sources before production deployment.

---

## 10. Roadmap

**MVP (SIH)**
- [x] All 8 Union Territories
- [x] Destination discovery and intelligence
- [x] AI assistant and itinerary generation
- [x] Interactive map and routes
- [x] Weather and festival information
- [x] Emergency facilities and SOS
- [x] Booking integration architecture
- [x] Responsive web interface

**Should have**
- [ ] Offline itinerary
- [ ] Budget planner and packing assistant
- [ ] Live travel alerts and Yatra Mode
- [ ] Share My Yatra
- [ ] Culture guide, food discovery and readiness score

**Future**
- [ ] Move to the NestJS + PostgreSQL/PostGIS/pgvector target architecture
- [ ] Mobile app and expansion to all Indian states
- [ ] Voice navigation and multilingual voice assistant
- [ ] Advanced personalisation, tourism analytics and AR experiences

---

<p align="center">
  <b>Dishaara — Bharat Safe Yatra</b><br/>
  <i>Discover. Plan. Book. Navigate. Stay Safe.</i> <br>
      Off campus code - 7A6SJU
</p>
