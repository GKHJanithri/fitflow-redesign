# ADR-001: Adopt a Node.js + React Native + PostgreSQL + Firebase Stack for the FitFlow Redesign

## Status
Accepted

## Context
FitFlow needs a cross-platform (iOS/Android/web) redesign delivered quickly
by a mid-sized team, with strong real-time social features, AI-personalized
workouts, camera-based nutrition logging, and responsible handling of
health-adjacent data.

## Decision
- **Frontend:** React Native for the client (iOS, Android, web via React
  Native Web)
- **Backend:** Node.js + Express for the API layer
- **Database:** PostgreSQL for structured/sensitive data (user accounts,
  workout plans, requirements traceability data)
- **Real-time / Social:** Firebase (Firestore, Realtime Database, Auth) for
  real-time social features, notifications, and authentication
- **AI / ML:** TensorFlow Lite (on-device) plus a cloud ML/computer-vision
  service for AI and food-recognition features
- **Caching:** Redis for session and hot-path data

## Consequences

### Positive
- A single primary language (JavaScript/TypeScript) across frontend and
  backend reduces hiring and context-switching cost.
- Firebase accelerates real-time feature delivery (social feed,
  notifications, presence).
- PostgreSQL gives auditable, compliant storage for sensitive data.

### Trade-offs
- Running both PostgreSQL and Firebase introduces two data stores that must
  be kept in sync for certain user-facing views (e.g., a user's profile
  touches both). The team must define clear ownership boundaries between
  the two stores to avoid data drift.

## Related Documents
- [Tech Stack Summary](../tech-stack-summary.md)
- [Comparison Matrix](../comparison-matrix.md)
- [Architecture Diagram](./architecture-diagram.png)
