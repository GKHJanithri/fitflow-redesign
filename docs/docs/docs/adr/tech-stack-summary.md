# FitFlow Redesign — Technology Stack Summary

This document summarizes the recommended technology stack for the FitFlow
redesign, based on the comparisons in Activities 1 and 2 of Lab Exercise 05.

## Recommended Stack

| Layer | Technology | Why |
|---|---|---|
| Frontend | **React Native** (+ React Native Web) | Best balance of development speed, ~90% code reuse across iOS/Android, web coverage, and the largest ecosystem for real-time/social/Firebase-based features |
| Backend API | **Node.js + Express** | Single language (JS/TS) across frontend and backend, large hiring pool, strong real-time support (Socket.io) |
| Primary database | **PostgreSQL** | Mature row-level security, encryption, and audit tooling suited to sensitive health-adjacent data (GDPR/HIPAA-style compliance) |
| Real-time / Social layer | **Firebase** (Firestore + Realtime Database) | Purpose-built for low-latency social feeds, presence, and push notifications |
| Authentication | **Firebase Auth** | Very low setup effort, Google-managed reliability, integrates directly with Firestore |
| AI / ML | **TensorFlow Lite** (on-device) + Cloud ML/CV Kit | On-device personalization for adaptive workout plans; cloud computer vision for camera-based nutrition logging |
| Caching | **Redis** | Absorbs read-heavy hot paths (dashboard loads) to protect PostgreSQL under load |

## Frontend Decision (Activity 1)

Flutter, React Native, Kotlin Multiplatform, and Swift/SwiftUI were compared
across development speed, code reusability, performance, ecosystem support,
learning curve, web compatibility, AI/ML integration, real-time features,
maintenance cost, and security.

**Recommendation: React Native.** It offers the best balance of development
speed, code reusability (~90% shared across iOS and Android, with web
coverage via React Native Web), a mature ecosystem for the real-time social
and Firebase-based features FitFlow requires, and a large available talent
pool. Flutter was a close second; native Kotlin/Swift was not recommended
given the higher maintenance cost of separate native UI codebases for a
mid-sized team building an MLP under time pressure.

## Backend / Database / Auth Decision (Activity 2)

Node.js/Express, Python/FastAPI, and Go were compared for the backend;
PostgreSQL, MongoDB, Firebase, and DynamoDB for the database; and Firebase
Auth, AWS Cognito, Auth0, and Supabase Auth for authentication.

**Recommendation: Node.js + Express, PostgreSQL, Firebase, and Firebase Auth.**
This combination:
- Keeps the team working in one primary language (JavaScript/TypeScript)
  end-to-end
- Gives sensitive relational data (user accounts, workout plans) the
  stronger access-control and audit tooling PostgreSQL provides
- Gains Firebase's real-time strengths for the social feed and
  notifications without adopting a heavier, harder-to-hire-for stack

## Full Comparisons

The full criteria-by-criteria comparison tables and the weighted decision
matrix are in [`comparison-matrix.md`](./comparison-matrix.md).

## Architecture

See [`architecture-diagram.png`](./adr/architecture-diagram.png) and
[`ADR-001-technology-stack.md`](./adr/ADR-001-technology-stack.md) for the
high-level system architecture and the formal Architecture Decision Record.
