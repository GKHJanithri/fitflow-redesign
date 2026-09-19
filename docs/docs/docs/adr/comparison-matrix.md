# FitFlow Redesign — Technology Comparison Matrix

Consolidated findings from the frontend, backend, database, and
authentication comparisons (Activities 1–2), scored and weighted against
FitFlow's project priorities.

## Criteria Weights

Weights reflect FitFlow's priorities: shipping a redesigned Minimum Lovable
Product quickly, handling sensitive health-adjacent data responsibly, and
supporting real-time social and AI features.

| Criterion | Weight |
|---|---|
| Development speed | 15% |
| Code reusability | 10% |
| Performance | 15% |
| Scalability | 15% |
| Security / compliance | 15% |
| AI/ML support | 10% |
| Real-time capability | 10% |
| Cost (mid-sized team) | 5% |
| Maintainability | 5% |

## Weighted Decision Matrix

Scores are out of 10. `-` = criterion not directly applicable to that layer.

| Technology | Dev Speed | Reuse | Perf. | Scalability | Security | AI/ML | Real-time | Cost | Maint. | **Weighted Score** |
|---|---|---|---|---|---|---|---|---|---|---|
| React Native (frontend) | 9 | 9 | 8 | 7 | 7 | 7 | 8 | 8 | 8 | **8.03** |
| Flutter (frontend) | 8 | 8 | 8 | 7 | 7 | 6 | 7 | 8 | 7 | **7.50** |
| Node.js + Express (backend) | 9 | - | 7 | 8 | 7 | 8 | 9 | 8 | 8 | **7.90** |
| PostgreSQL (database) | 7 | - | 8 | 8 | 9 | 6 | 5 | 8 | 8 | **7.55** |
| Firebase (real-time layer) | 9 | - | 7 | 9 | 7 | 7 | 9 | 8 | 8 | **8.00** |
| Firebase Auth (authentication) | 9 | - | 8 | 8 | 8 | - | 8 | 9 | 8 | **8.20** |

## Recommended Technology Stack

| Layer | Recommended Technology | Weighted Score |
|---|---|---|
| Frontend | React Native (+ React Native Web) | 8.03 / 10 |
| Authentication | Firebase Auth | 8.20 / 10 |
| Real-time / Social layer | Firebase (Firestore + Realtime Database) | 8.00 / 10 |
| Backend API | Node.js + Express | 7.90 / 10 |
| Primary database | PostgreSQL | 7.55 / 10 |

## Supporting Rationale

Every layer in the recommended stack scored above 7.5/10 on the weighted
matrix, with authentication (Firebase Auth) and the real-time layer
(Firebase) scoring highest — reflecting FitFlow's strong reliance on social
and notification features. React Native's high reuse and development-speed
scores directly support the redesign's time-to-market goal, while
PostgreSQL's comparatively lower real-time score (5/10) is an acceptable
trade-off, since it is used specifically for structured, sensitive data
rather than the real-time social feed (handled instead by Firebase). This
combination reflects the same stack direction justified in the original
case study, with the addition of PostgreSQL as a dedicated, auditable store
for sensitive relational data.

See [`tech-stack-summary.md`](./tech-stack-summary.md) for the narrative
justification behind each layer.
