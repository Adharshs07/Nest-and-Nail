# 🏠 Nest & Nail — On-Demand Home Services Marketplace

> **Architected for Reliability. Engineered with Clean Architecture.**  
> *A full-stack, role-based platform connecting clients with verified service professionals for residential repairs, maintenance, and virtual video consultations.*

[![Node.js Version](https://img.shields.io/badge/Node.js-v20%2B-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Next.js](https://img.shields.io/badge/Next.js-16.2.6-black?logo=next.js&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19.1.0-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Express.js](https://img.shields.io/badge/Express.js-4.18-000000?logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose_8.0-47A248?logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Socket.io](https://img.shields.io/badge/Socket.io-4.8-010101?logo=socket.io&logoColor=white)](https://socket.io/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![AWS S3](https://img.shields.io/badge/AWS-S3_Presigned_URLs-FF9900?logo=amazons3&logoColor=white)](https://aws.amazon.com/s3/)
[![Razorpay](https://img.shields.io/badge/Razorpay-v2.9-0C2340?logo=razorpay&logoColor=white)](https://razorpay.com/)
[![Architecture](https://img.shields.io/badge/Architecture-Clean_Architecture_%26_DDD-blueviolet)](#system-architecture)

---

## 📑 Table of Contents

- [1. Project Overview](#1-project-overview)
  - [The Problem](#the-problem)
  - [The Solution](#the-solution)
  - [Core User Personas](#core-user-personas)
  - [High-Level Value Proposition](#high-level-value-proposition)
- [2. Features by User Role](#2-features-by-user-role)
  - [Client Capabilities](#client-capabilities)
  - [Worker Capabilities](#worker-capabilities)
  - [Admin Governance & Moderation](#admin-governance--moderation)
- [3. Technology Stack](#3-technology-stack)
- [4. System Architecture](#4-system-architecture)
  - [High-Level Architecture](#high-level-architecture)
  - [Backend Clean Architecture & Domain-Driven Design](#backend-clean-architecture--domain-driven-design)
  - [Frontend Architecture & Next.js App Router](#frontend-architecture--nextjs-app-router)
  - [End-to-End Request Lifecycle](#end-to-end-request-lifecycle)
- [5. Visual Workflow Diagrams](#5-visual-workflow-diagrams)
  - [1. User Registration & OTP Verification](#1-user-registration--otp-verification)
  - [2. Google OAuth Authentication](#2-google-oauth-authentication)
  - [3. Worker Onboarding & KYC Document Verification](#3-worker-onboarding--kyc-document-verification)
  - [4. Physical Service Execution Lifecycle](#4-physical-service-execution-lifecycle)
  - [5. Tiered Cancellation & Automatic Refund Matrix](#5-tiered-cancellation--automatic-refund-matrix)
  - [6. WebRTC Video Consultation & Socket.io Signaling](#6-webrtc-video-consultation--socketio-signaling)
  - [7. Real-Time Chat & Instant Messaging](#7-real-time-chat--instant-messaging)
  - [8. Real-Time Push Notification Engine](#8-real-time-push-notification-engine)
  - [9. Automated 15-Minute Moderation & Penalization Engine](#9-automated-15-minute-moderation--penalization-engine)
- [6. Database Design](#6-database-design)
  - [Entity-Relationship Diagram](#entity-relationship-diagram)
- [7. Concise API Overview](#7-concise-api-overview)
  - [Authentication & Identity](#authentication--identity)
  - [User & Profile Management](#user--profile-management)
  - [Client Services & Workers](#client-services--workers)
  - [Worker Operations & Schedule](#worker-operations--schedule)
  - [Meetings & Video Consultations](#meetings--video-consultations)
  - [Payments, Wallet & Transactions](#payments-wallet--transactions)
  - [Communication (Chat & Notifications)](#communication-chat--notifications)
  - [Concerns, Reviews & Media](#concerns-reviews--media)
  - [Admin Governance & Operations](#admin-governance--operations)
- [8. Authentication & Security](#8-authentication--security)
  - [Dual-Token Strategy (Access & Refresh)](#dual-token-strategy-access--refresh)
  - [Edge Middleware & Route Protection](#edge-middleware--route-protection)
- [9. Project Directory Structure](#9-project-directory-structure)
- [10. Installation & Setup](#10-installation--setup)
- [11. Environment Variable Configuration](#11-environment-variable-configuration)
  - [Frontend Environment Configuration (.env.example)](#frontend-environment-configuration-envexample)
  - [Backend Environment Configuration (.env.example)](#backend-environment-configuration-envexample)
  - [Configuration & Security Notice](#configuration--security-notice)
- [12. Running the Application](#12-running-the-application)
- [13. Error Handling, Logging & Reliability](#13-error-handling-logging--reliability)
- [14. Roadmap & Future Improvements](#14-roadmap--future-improvements)
- [15. Contributing & License](#15-contributing--license)

---

## 1. Project Overview

### The Problem
Finding dependable, background-verified home service professionals (plumbers, electricians, carpenters, cleaners) remains fragmented, opaque, and risky:
1. **Lack of Trust:** Customers struggle to verify credentials, government identity proofs, and skill certificates of independent service workers.
2. **Scheduling Friction:** Booking physical visits without an initial assessment leads to misdiagnosed problems, wasted travel time, and unpredictable pricing.
3. **Absence & No-Show Risks:** Service workers frequently miss appointments, while clients cancel abruptly without fair recourse for either party.
4. **Scattered Communication:** Using personal phone numbers exposes private details and provides no paper trail for disputes or warranty claims.

### The Solution
**Nest & Nail** is a full-stack marketplace platform built to streamline the entire residential service journey. By combining a **Domain-Driven Clean Architecture** backend with a modern **Next.js 16 App Router** frontend, Nest & Nail provides:
- **Rigorous Admin KYC:** Workers submit government documents and trade certificates reviewed by platform administrators before accepting jobs.
- **Dual Service Modalities:** Clients can book **Physical On-Site Appointments** (Half-Day Morning/Evening or Full-Day) or **Live WebRTC Video Consultations** (15-minute diagnostic triage slots) to troubleshoot and quote jobs remotely.
- **Geospatial Proximity Matching:** MongoDB `2dsphere` indexes pair clients with nearby workers based on coordinates and interactive Leaflet map address selectors.
- **Fair Tiered Cancellation & Wallet Engine:** Automated refund tiers reward punctuality, with instant wallet credits and a full financial audit ledger.
- **Autonomous 15-Minute Moderation Daemon:** An automated background job scans scheduled sessions to detect physical no-shows and virtual meeting absences, applying progressive suspensions and issuing automated refunds without manual intervention.

```
       +-----------------------------------------------------------+
       |                        NEST & NAIL                        |
       |             The Trusted Home Services Platform            |
       +-----------------------------------------------------------+
                     /              |              \
                    /               |               \
        +----------------+  +----------------+  +----------------+
        |     CLIENT     |  |     WORKER     |  |     ADMIN      |
        | Discover, Book |  | Profile, Slots |  | Verify Pros,   |
        | Pay, Chat, Call|  | Jobs, Wallet   |  | Settle Tickets |
        +----------------+  +----------------+  +----------------+
```

### Core User Personas

| Role | Persona Goal | Core Workflows |
|:-----|:-------------|:---------------|
| **Client** | Homeowners needing fast, reliable repairs or installations. | Discover nearby verified workers, check calendar availability, reserve slots, checkout with Razorpay/Wallet, track progress, participate in WebRTC video calls, rate workers, and raise resolution tickets. |
| **Worker** | Skilled technicians seeking consistent, verified job requests. | Complete KYC verification by uploading credentials, configure working hours/block dates, accept job dispatches, start/complete jobs, track earnings, and attend video triage calls. |
| **Admin** | Platform operators managing quality control and safety. | Audit submitted worker identity proofs, manage categories and platform commissions, inspect meetings/chats, arbitrate customer concerns, and oversee transactions. |

### High-Level Value Proposition
- **Enterprise-Grade Clean Architecture:** Strict decoupling between Presentation, Application, Domain, and Infrastructure ensures isolated testability and maintainability.
- **Unified TypeScript Monorepo:** Managed via PNPM workspaces with synchronized domain types and DTO definitions across client and server.
- **Zero-Polling Real-Time Experience:** Socket.io handles instant chat, WebRTC signaling, and system notifications without taxing device battery or network.

---

## 2. Features by User Role

### Client Capabilities
- **Flexible Onboarding:** Email/Password registration with OTP verification, Google OAuth single sign-on, and role switching.
- **Interactive Location Selection:** Interactive Leaflet map with Nominatim OpenStreetMap reverse geocoding to save home and work addresses with precise GPS coordinates.
- **Worker Discovery:** Filter workers by trade categories, proximity, rating, and hourly/daily rates.
- **Dual-Booking Modalities:** Reserve physical visits (Half-Day Morning/Evening or Full-Day) or 15-minute diagnostic WebRTC video consultations.
- **Temporary Slot Locking:** 10-minute slot reservations during checkout to prevent double-booking conflicts.
- **Integrated Payments & Wallet:** Pay using Razorpay or an internal wallet, with automatic transaction tracking and top-ups.
- **Service Tracking:** Real-time visibility into booking statuses (`PENDING`, `CONFIRMED`, `IN_PROGRESS`, `COMPLETED`).
- **Tiered Cancellation:** Automated refund tiers based on the time elapsed since booking.
- **Real-Time Communication:** In-app chat with attachment support and peer-to-peer WebRTC video consultations.
- **Reviews & Concerns:** Rate completed services and submit dispute tickets with image evidence.

### Worker Capabilities
- **KYC Verification:** Upload national identity proofs and trade certificates directly to AWS S3 via presigned URLs for admin approval.
- **Trade & Skill Configuration:** Select authorized service categories and configure specific trade skills.
- **Schedule Management:** Block specific calendar dates or slot windows (`MORNING_HALF`, `EVENING_HALF`, `FULL_DAY`).
- **Job Lifecycle Execution:** View dispatches, view client addresses, transition jobs to `IN_PROGRESS`, and mark as `COMPLETED`.
- **Earnings & Wallet:** Track earnings, receive automatic deposits upon job completion, and review payout history.
- **Worker Dashboard:** View weekly job counts, customer ratings, ongoing tasks, and total revenue.
- **Virtual Consultations:** Attend scheduled 15-minute diagnostic triage calls directly from the browser.

### Admin Governance & Moderation
- **Executive Analytics:** High-level overview of active users, gross booking volume, platform commission, and refund metrics.
- **KYC Verification Queue:** Dedicated interface to review worker credentials and approve or reject applications with feedback.
- **User & Access Management:** View all clients and workers with capabilities to block/unblock accounts and toggle suspensions.
- **Category Management:** Full CRUD operations for service categories with custom icons and active status toggles.
- **Service Auditing:** Complete ledger of all platform bookings, worker assignments, timestamps, and fees.
- **Dispute Resolution:** Review customer and worker concerns, inspect attached evidence photos, and record resolution verdicts.
- **Automated Moderation Daemon:** Background job running every 15 minutes to detect no-shows and meeting absences, applying progressive suspensions and automatic refunds.
- **Transaction Ledger:** Real-time financial audit trail of all platform payments, Razorpay order IDs, credits, and debits.

---

## 3. Technology Stack

Every technology listed below is verified directly within the repository codebase:

| Category | Technology | Version | Purpose in Nest & Nail |
|:---|:---|:---|:---|
| **Frontend Framework** | **Next.js (App Router)** | `16.2.6` | Server-side rendering (SSR), edge routing, layouts, and server actions compiled with Turbopack. |
| **UI Library** | **React** | `19.1.0` | Declarative, concurrent component rendering across all client views. |
| **Styling & Design** | **Tailwind CSS** | `v4.0.0` | Utility-first styling with `@tailwindcss/postcss` and dynamic styling via `clsx` and `tailwind-merge`. |
| **UI Primitives** | **Radix UI** | Multiple | Accessible primitives for dialogs, labels, separators, and responsive navigation menus. |
| **Icons & Visuals** | **Lucide React** / **Heroicons** | `^0.546.0` | SVG icons used across navigation, dashboard widgets, and status badges. |
| **State Management** | **Zustand** | `5.0.8` | Client-side reactive authentication store with localStorage persistence and hydration reconciliation. |
| **HTTP Client** | **Axios** | `1.12.2` | Configured with interceptors for bearer authentication and backend REST communication. |
| **Maps & Geolocation** | **Leaflet** & **React-Leaflet** | `1.9.4` / `5.0.0` | Interactive map rendering, pin placement, and reverse geocoding via OpenStreetMap Nominatim. |
| **Charts & Analytics** | **Recharts** | `3.8.1` | Admin and worker metrics visualization (revenue trends, booking volume, user distribution). |
| **Backend Runtime** | **Node.js** | `>=20.x` | Asynchronous JavaScript execution runtime. |
| **Web Server Framework** | **Express.js** | `4.18.2` | REST API layer handling routing, middlewares, and controller execution. |
| **Language** | **TypeScript** | `5.9.3` | Enforces static typing across both frontend and backend packages. |
| **Database & ODM** | **MongoDB** & **Mongoose** | `8.0.0` | Document database utilized with schemas, discriminators, compound indexes, and 2dsphere geo-indexing. |
| **Real-Time Engine** | **Socket.io** & **Client** | `4.8.3` | Manages live chat, presence tracking, system broadcasts, and WebRTC signaling. |
| **Video Telephony** | **WebRTC (Native)** | Native P2P | Peer-to-peer audio/video streaming negotiated over Socket.io signaling rooms. |
| **Cloud Storage** | **AWS S3 SDK v3** | `3.990.0` | Secure direct-to-S3 uploads and downloads via Presigned URLs (`@aws-sdk/s3-request-presigner`). |
| **Payment Gateway** | **Razorpay Node SDK** | `2.9.6` | Order generation, checkout capture, and HMAC-SHA256 signature verification. |
| **Email Service** | **Nodemailer** | `7.0.10` | SMTP delivery for 6-digit OTP verification codes. |
| **Authentication & Tokens**| **JSONWebToken** & **Jose** | `9.0.2` / `6.1.2` | Access and Refresh token generation, validation, and edge decoding in Next.js middleware. |
| **Password Security** | **Bcrypt.js** | `2.4.3` | Salt generation and cryptographic hashing for secure password storage. |
| **OAuth Integration** | **Google Auth Library** | `10.5.0` | IdToken validation for single sign-on (SSO). |
| **Logging & Auditing** | **Winston** & **Daily Rotate** | `3.18.3` / `5.0.0`| Structured logging with daily rotation, custom formats, and console/file transports. |
| **Form Validation** | **Zod** & **Input-OTP** | `4.1.12` / `1.4.2`| Runtime schema validation and segmented 6-digit pin entry UI components. |
| **Workspace Management** | **PNPM** | `v9+` | Disk-efficient monorepo workspace package manager. |

---

## 4. System Architecture

### High-Level Architecture

The platform follows a multi-tiered architecture where the Next.js frontend and Express backend communicate via RESTful HTTP APIs and persistent WebSocket connections.

```mermaid
graph TB
    subgraph ClientBrowser["User Browser / Client Layer"]
        UI["Next.js 16 UI (React 19)"]
        ZStore["Zustand Client Store"]
        LeafletMap["Leaflet Map Engine"]
        WebRTCClient["WebRTC Media Engine"]
        SocketClient["Socket.io Client"]
    end

    subgraph EdgeRouting["Edge & Server Infrastructure (Port 3000)"]
        NextMiddleware["Next.js Edge Middleware<br/>(Route Guards & Cookie Token Refresh)"]
        ServerActions["Next.js Server Actions<br/>(BFF Layer)"]
    end

    subgraph BackendAPI["Express.js API Layer (Port 4000)"]
        CORSMw["CORS & Cookie Parser"]
        ReqLog["Winston Request Logger"]
        AuthMw["AuthMiddleware<br/>(JWT Verification)"]
        Routes["API Route Handlers"]
        ErrorHandler["Centralized Error Handler"]
    end

    subgraph CleanArch["Clean Architecture Application Core"]
        Controllers["Presentation Layer (Controllers)"]
        UseCases["Application Layer (Use Cases)"]
        Domain["Domain Entities & Contracts"]
        DI["DI Container (Pure DI)"]
    end

    subgraph SocketsEngine["Socket.io Server (Port 4000)"]
        ChatH["ChatHandler"]
        VideoH["VideoCallHandler (Signaling)"]
        PresH["PresenceHandler"]
        RTService["RealtimeService"]
    end

    subgraph Persistence["Database & External Services"]
        MongoDB[("MongoDB Replica Set<br/>(Geo 2dsphere, Compound & TTL Indexes)")]
        AWSS3["AWS S3 Bucket<br/>(Identity Docs, Certs, Proofs)"]
        Razorpay["Razorpay Payment Gateway"]
        GoogleAuth["Google Identity Platform"]
        SMTP["Nodemailer SMTP Server"]
    end

    UI --> NextMiddleware
    NextMiddleware --> ServerActions
    ServerActions --> CORSMw
    UI -->|Socket Connection| SocketClient
    SocketClient <--> SocketsEngine
    WebRTCClient <-->|P2P Media Stream| WebRTCClient
    
    CORSMw --> ReqLog --> AuthMw --> Routes --> Controllers
    Controllers --> UseCases
    UseCases --> Domain
    UseCases --> Persistence
    DI -.->|Injects Dependencies| Controllers
    DI -.->|Injects Dependencies| UseCases

    UseCases --> AWSS3
    UseCases --> Razorpay
    UseCases --> GoogleAuth
    UseCases --> SMTP
    UseCases --> MongoDB
```

---

### Backend Clean Architecture & Domain-Driven Design

The backend strictly implements **Clean Architecture**. The fundamental principle is the **Dependency Inversion Principle**: source code dependencies point only inward toward domain logic.

```mermaid
graph TD
    subgraph PresentationLayer["Presentation Layer (External Driving Adapter)"]
        Routes["Express Routes"]
        Controllers["Controllers (e.g., ClientServiceController)"]
        Middlewares["Middlewares (Auth, Error, Upload)"]
    end

    subgraph ApplicationLayer["Application Layer (Use Cases)"]
        UseCases["Business Use Cases (e.g., BookWorkerUseCase)"]
        DTOs["Data Transfer Objects (DTOs)"]
        Contracts["App Service Contracts (ITokenService, IEmailService)"]
    end

    subgraph DomainLayer["Domain Layer (Enterprise Core)"]
        Entities["Domain Entities (Service, User, Worker, Wallet)"]
        RepoInterfaces["Repository Interfaces (IServiceRepository, IWalletRepo)"]
        DomainErrors["Domain Errors (DomainError, AuthError)"]
        Enums["Core Domain Enums (ServiceStatus, SlotType)"]
    end

    subgraph InfrastructureLayer["Infrastructure Layer (External Driven Adapter)"]
        MongooseModels["Mongoose Schemas & Models"]
        RepoImpls["Repository Impls (ServiceRepository, WalletRepo)"]
        ExternalAdapters["External Adapters (RazorpayGateway, S3Service, Nodemailer)"]
        DISystem["Pure DI Container (DIContainer)"]
    end

    PresentationLayer --> ApplicationLayer
    ApplicationLayer --> DomainLayer
    InfrastructureLayer --> DomainLayer
    InfrastructureLayer --> ApplicationLayer
    DISystem -.->|Wires Implementations into| ApplicationLayer
    DISystem -.->|Wires Implementations into| PresentationLayer
```

#### Layer Responsibilities:
1. **Domain Layer (`backend/src/domain/`)**: Pure business entities (`User`, `Worker`, `Service`, `Wallet`, `Payment`, `Review`, `Concern`), repository contracts, and domain errors with zero dependencies on frameworks or libraries.
2. **Application Layer (`backend/src/application/`)**: Single-responsibility use cases (`BookWorkerUseCase`, `CancelServiceUseCase`, `ProcessModerationActionsUseCase`), DTOs, and application interfaces.
3. **Infrastructure Layer (`backend/src/infrastructure/`)**: Mongoose repository implementations, third-party adapters (`RazorpayGateway`, `S3Service`, `NodemailerEmailService`), and pure dependency injection via `DIContainer`.
4. **Presentation Layer (`backend/src/presentation/`)**: Express controllers, routes, and middlewares (`AuthMiddleware`, `errorHandler`, `RequestLogger`).

---

### Frontend Architecture & Next.js App Router

The frontend uses Next.js App Router conventions with role-based route groups:

```mermaid
graph TD
    subgraph Routing["Next.js App Router Structure"]
        RootLayout["app/layout.tsx (Providers, Toast, SocketContext)"]
        AuthGroup["app/(auth)/ (login, signup, otp)"]
        ClientGroup["app/client/ (home, workers, bookings, meetings, profile)"]
        WorkerGroup["app/worker/ (dashboard, services, schedule, wallet, profile)"]
        AdminGroup["app/admin/ (dashboard, clients, workers, verification, categories)"]
    end

    subgraph StateAndBFF["Client State & Communication"]
        Zustand["Zustand User Store (user-store with localStorage persistence)"]
        Actions["Server Actions (src/app/actions/*)"]
        APIClients["Axios API Clients (src/sources/api/*)"]
    end

    subgraph UIComponents["Reusable Component Library"]
        Atoms["UI Primitives (Input, Button, Modal, Badge)"]
        Containers["Containers (Navbar, Sidebar, Footer)"]
        Features["Feature Components (BookingModal, LeafletMap, VideoCallRoom)"]
    end

    RootLayout --> AuthGroup & ClientGroup & WorkerGroup & AdminGroup
    ClientGroup & WorkerGroup & AdminGroup --> UIComponents
    UIComponents --> Zustand
    UIComponents --> Actions
    Actions --> APIClients
```

---

### End-to-End Request Lifecycle

The diagram below illustrates how an operation travels across architectural boundaries:

```mermaid
sequenceDiagram
    autonumber
    actor Client as Client Browser
    participant UI as BookingModal Component
    participant SA as Server Action (bookWorkerAction)
    participant API as Axios Client (client.api.ts)
    participant Route as Express Router (/api/client/services/book)
    participant Auth as AuthMiddleware.verify
    participant Ctrl as ClientServiceController.bookWorker
    participant UC as BookWorkerUseCase.execute
    participant LockRepo as WorkerScheduleRepository
    participant SvcRepo as ServiceRepository
    participant DB as MongoDB Atlas

    Client->>UI: Selects Dates and Slots and Clicks Confirm
    UI->>SA: bookWorkerAction(bookingPayload)
    SA->>API: POST /api/client/services/book
    API->>Route: HTTP POST with Bearer Cookie
    Route->>Auth: Validates Access Token
    Auth-->>Route: Attaches req.user (clientId)
    Route->>Ctrl: invoke bookWorker(req, res)
    Ctrl->>UC: execute(bookingDTO)
    
    UC->>LockRepo: verifyAndLockSlots(workerId, selectedSlots)
    LockRepo->>DB: findOneAndUpdate({ workerId, date, slotType, isBooked: false })
    DB-->>LockRepo: Slots Locked
    
    UC->>SvcRepo: create(serviceEntity)
    SvcRepo->>DB: ServiceModel.create(...)
    DB-->>SvcRepo: Service Persisted (Status: PENDING)
    
    UC-->>Ctrl: Returns ServiceResponseDTO
    Ctrl-->>API: 201 Created { success: true, payload: service }
    API-->>SA: Response mapped
    SA-->>UI: Updates Booking Status
    UI-->>Client: Displays Booking Confirmation and Payment Prompt
```

---

## 5. Visual Workflow Diagrams

### 1. User Registration & OTP Verification

```mermaid
sequenceDiagram
    autonumber
    actor User as Client / Worker
    participant Frontend as Signup Form
    participant Backend as AuthController
    participant UC as RegisterUserUseCase
    participant OtpUC as SendOtpUseCase
    participant Nodemailer as Nodemailer SMTP
    participant DB as MongoDB (OtpModel)

    User->>Frontend: Enters Name, Email, Role, Password
    Frontend->>Backend: POST /api/auth/register
    Backend->>UC: Validates input & checks email uniqueness
    alt Email Already Exists
        UC-->>Frontend: 400 Bad Request: "User already exists"
    else New Registration
        UC->>OtpUC: Generate 6-digit OTP
        OtpUC->>DB: Save hashed OTP (2-minute TTL)
        OtpUC->>Nodemailer: Send verification email
        Nodemailer-->>User: Delivers 6-digit code
        UC-->>Frontend: 200 OK: "OTP sent to email"
        Frontend->>User: Redirects to /otp verification screen
    end
```

### 2. Google OAuth Authentication

```mermaid
sequenceDiagram
    autonumber
    actor User as User
    participant Frontend as @react-oauth/google
    participant Backend as GoogleAuthController
    participant Google as Google OAuth API
    participant UserRepo as UserRepository
    participant TokenSvc as JwtTokenService

    User->>Frontend: Clicks "Continue with Google"
    Frontend->>Google: Authenticates & receives idToken
    Frontend->>Backend: POST /api/auth/google { credential, role }
    Backend->>Google: Validates credential (OAuth client ID)
    Google-->>Backend: Returns Verified Email, Name, Avatar
    Backend->>UserRepo: findByEmail(email)
    alt User Does Not Exist
        Backend->>UserRepo: Create User (LoginMethod: GOOGLE, isVerified: VERIFIED)
    end
    Backend->>TokenSvc: Generate Access (15m) & Refresh (7d) Tokens
    Backend-->>Frontend: Set HTTP-Only Cookies & return User DTO
    Frontend->>User: Redirects to Dashboard based on Role
```

### 3. Worker Onboarding & KYC Document Verification

```mermaid
sequenceDiagram
    autonumber
    actor Worker as Service Worker
    participant Portal as Worker Profile (/worker/profile)
    participant S3 as AWS S3 (Presigned PUT)
    participant Backend as AdminVerificationController
    actor Admin as Platform Admin
    participant DB as MongoDB (UserModel)

    Worker->>Portal: Fills Trade Categories & Rates
    Worker->>Portal: Selects Government ID & Trade Certificates
    Portal->>Backend: GET /api/media/s3-upload-url (fileName, type)
    Backend-->>Portal: Returns Presigned S3 Upload URL
    Portal->>S3: Direct PUT document to S3 bucket
    S3-->>Portal: 200 OK (Uploaded)
    Portal->>Backend: POST /api/upload/worker/:id/document (S3 URLs)
    Backend->>DB: Update Worker (isVerified: "PENDING", documents: [...])
    
    Note over Admin,Backend: Admin Verification Queue (/admin/verification)
    Admin->>Backend: GET /api/admin/workers?status=PENDING
    Backend-->>Admin: Returns worker details & S3 document URLs
    Admin->>Admin: Inspects credentials & background check
    alt Approved
        Admin->>Backend: PATCH /api/admin/verify/:workerId
        Backend->>DB: Update Worker (isVerified: "VERIFIED", canAcceptBookings: true)
        Backend-->>Worker: Push Notification: "Account Verified! You are now live."
    else Rejected
        Admin->>Backend: PATCH /api/admin/reject/:workerId { reason }
        Backend->>DB: Update Worker (isVerified: "REJECTED")
        Backend-->>Worker: Push Notification: "Verification rejected. Please re-upload."
    end
```

### 4. Physical Service Execution Lifecycle

```mermaid
stateDiagram-v2
    [*] --> PENDING: Client Books Service
    PENDING --> CONFIRMED: Payment Verified
    CONFIRMED --> IN_PROGRESS: Worker Arrives & Clicks "Start Service"
    IN_PROGRESS --> COMPLETED: Worker Completes Job & Clicks "Complete"
    
    CONFIRMED --> CANCELLED_BY_CLIENT: Client Cancels within 6 hours
    CONFIRMED --> CANCELLED_BY_WORKER: Worker Declines / Cancels
    CONFIRMED --> NO_SHOW: 15-min Moderation Daemon Detects No Start
    
    COMPLETED --> REVIEWED: Client Submits Rating & Review
    COMPLETED --> [*]
    REVIEWED --> [*]
    CANCELLED_BY_CLIENT --> [*]
    CANCELLED_BY_WORKER --> [*]
    NO_SHOW --> [*]
```

### 5. Tiered Cancellation & Automatic Refund Matrix

```mermaid
flowchart TD
    Start([Client Requests Cancellation]) --> CalcDiff[Calculate Time Since Booking Creation]
    CalcDiff --> Check6Hr{Elapsed Time > 6 Hours?}
    
    Check6Hr -- Yes --> Reject[Reject Request: Cancellation Window Expired]
    Check6Hr -- No --> Check15Min{Elapsed Time < 15 Minutes?}
    
    Check15Min -- Yes --> Refund100[Apply 100% Refund Tier]
    Check15Min -- No --> Check1Hr{Elapsed Time < 1 Hour?}
    
    Check1Hr -- Yes --> Refund90[Apply 90% Refund Tier]
    Check1Hr -- No --> Refund50[Apply 50% Refund Tier]
    
    Refund100 --> ProcessRefund[Credit Client Wallet & Debit Admin Platform]
    Refund90 --> ProcessRefund
    Refund50 --> ProcessRefund
    
    ProcessRefund --> FreeSlots[Unmark Worker Schedule Slots]
    FreeSlots --> LogTxn[Create Transaction Audit Record]
    LogTxn --> NotifyWorker[Dispatch Real-Time Cancellation Notification]
    NotifyWorker --> Done([Cancellation Complete])
```

### 6. WebRTC Video Consultation & Socket.io Signaling

```mermaid
sequenceDiagram
    autonumber
    actor Client as Client Browser
    participant Signaler as Socket.io Server (VideoCallHandler)
    actor Worker as Worker Browser

    Client->>Signaler: socket.emit("join-room", { roomId, role: "client" })
    Signaler-->>Client: socket.emit("waiting")
    Worker->>Signaler: socket.emit("join-room", { roomId, role: "worker" })
    Note over Signaler: Room participants count == 2
    Signaler-->>Client: socket.emit("start-call")
    
    Client->>Client: Creates RTCPeerConnection & Generates SDP Offer
    Client->>Signaler: socket.emit("offer", { roomId, sdp })
    Signaler-->>Worker: socket.emit("offer", { sdp })
    
    Worker->>Worker: Sets Remote Description & Generates SDP Answer
    Worker->>Signaler: socket.emit("answer", { roomId, sdp })
    Signaler-->>Client: socket.emit("answer", { sdp })
    
    Client->>Signaler: socket.emit("ice-candidate", candidate)
    Signaler-->>Worker: Forward ICE candidate
    Worker->>Signaler: socket.emit("ice-candidate", candidate)
    Signaler-->>Client: Forward ICE candidate
    
    Note over Client,Worker: Direct P2P Audio/Video Media Stream Established
```

### 7. Real-Time Chat & Instant Messaging

```mermaid
sequenceDiagram
    autonumber
    actor Client as Client
    participant Sockets as Socket.io (ChatHandler)
    participant Backend as ChatController & UseCase
    participant DB as MongoDB (ChatMessageModel)
    actor Worker as Worker

    Client->>Sockets: socket.emit("join-chat", chatId)
    Worker->>Sockets: socket.emit("join-chat", chatId)
    
    Client->>Backend: POST /api/chat/send { chatId, receiverId, message, attachmentUrl }
    Backend->>DB: ChatMessageModel.create(...)
    Backend->>Sockets: io.to(chatId).emit("receive-message", messageDTO)
    Sockets-->>Worker: Message Rendered in UI
    Sockets-->>Client: Message Acknowledged & Sent
```

### 8. Real-Time Push Notification Engine

```mermaid
sequenceDiagram
    autonumber
    participant Event as Domain Event (e.g. Booking Confirmed)
    participant UC as SendNotificationUseCase
    participant DB as MongoDB (NotificationModel)
    participant RTSvc as RealtimeService
    participant Sockets as SocketServer (userSocketMap)
    actor User as Client / Worker Tabs

    Event->>UC: execute({ userId, title, message, type, data })
    UC->>DB: Persist Notification (isRead: false)
    UC->>RTSvc: emitToUser(userId, "notification", notificationDTO)
    RTSvc->>Sockets: getSocketIds(userId)
    Note over Sockets: Delivers simultaneously to all active tabs for this user
    Sockets-->>User: socket.emit("notification", notificationDTO)
    User->>User: Toast notification & unread count badge update
```

### 9. Automated 15-Minute Moderation & Penalization Engine

```mermaid
flowchart TD
    CronStart([15-Minute Background Interval Fires]) --> ScanServices[Scan Database for Past Unstarted Services & Consultations]
    
    ScanServices --> CheckPhysical{Case 1: Physical Service Confirmed but Never Started?}
    CheckPhysical -- Yes --> ActionCase1[1. Mark Service NO_SHOW<br/>2. Issue 100% Refund to Client Wallet<br/>3. Suspend Worker from New Bookings for 3 Days<br/>4. Send Push Alerts]
    CheckPhysical -- No --> CheckVideoWorker{Case 2: Video Call Scheduled, Client Joined but Worker Absent?}
    
    ActionCase1 --> CheckVideoWorker
    
    CheckVideoWorker -- Yes --> ActionCase2[1. Mark Meeting WORKER_ABSENT<br/>2. Issue 100% Refund to Client Wallet<br/>3. Suspend Worker for 1 Day<br/>4. Send Push Alerts]
    CheckVideoWorker -- No --> CheckVideoClient{Case 3: Video Call Scheduled, Worker Joined but Client Absent?}
    
    ActionCase2 --> CheckVideoClient
    
    CheckVideoClient -- Yes --> ActionCase3[1. Mark Meeting CLIENT_ABSENT<br/>2. Disallow Refund<br/>3. Restrict Client from Booking This Worker for 1 Day<br/>4. Send Push Alerts]
    CheckVideoClient -- No --> LogAudit[Log Audit Summary in Winston Logger]
    
    ActionCase3 --> LogAudit
    LogAudit --> Sleep([Sleep Until Next 15-Minute Interval])
```

---

## 6. Database Design

### Entity-Relationship Diagram

```mermaid
erDiagram
    USER ||--o{ ADDRESS : embeds
    USER ||--o{ CATEGORY : "belongs to (Worker)"
    USER ||--o{ WORKER_SCHEDULE : "manages (Worker)"
    USER ||--o{ SERVICE : "books (Client) / performs (Worker)"
    USER ||--o{ PAYMENT : "makes (Client)"
    USER ||--|| WALLET : "owns"
    WALLET ||--o{ WALLET_TRANSACTION : contains
    SERVICE ||--o{ REVIEW : has
    SERVICE ||--o{ CONCERN : generates
    SERVICE ||--o{ CHAT_MESSAGE : associates
    USER ||--o{ NOTIFICATION : receives
    USER ||--o{ CLIENT_WORKER_RESTRICTION : constrained

    USER {
        string userId PK
        string name
        string email UK
        number phone
        string role "client | worker | admin"
        string isVerified "NOT_VERIFIED | PENDING | VERIFIED | REJECTED"
        boolean isBlocked
        boolean isSuspended
    }

    ADDRESS {
        string addressId
        string label "HOME | WORK | OTHER"
        Point location "2dsphere [lng, lat]"
    }

    CATEGORY {
        ObjectId _id PK
        string name UK
        boolean isActive
    }

    SERVICE {
        string serviceId PK
        string clientId FK
        string workerId FK
        string category
        date scheduledDate
        string status "PENDING | CONFIRMED | IN_PROGRESS | COMPLETED | CANCELLED | NO_SHOW"
        string paymentStatus "PENDING | SUCCESS | FAILED | REFUNDED"
    }

    WORKER_SCHEDULE {
        ObjectId _id PK
        string workerId FK
        date date
        string slotType "MORNING_HALF | EVENING_HALF | FULL_DAY | VIDEO_SLOTS"
        boolean isBooked
        boolean isAvailable
    }

    WALLET {
        string walletId PK
        string userId FK
        number balance
    }

    WALLET_TRANSACTION {
        string transactionId PK
        string userId FK
        number amount
        string type "CREDIT | DEBIT"
    }

    PAYMENT {
        ObjectId _id PK
        string serviceId FK
        number amount
        string status "CREATED | SUCCESS | FAILED"
    }

    CONCERN {
        string concernId PK
        string serviceId FK
        string status "OPEN | RESOLVED | REJECTED"
    }

    REVIEW {
        string reviewId PK
        string serviceId FK,UK
        number rating
    }

    OTP {
        string email
        string otp
        date expiresAt "TTL: 120s"
    }
```

---

## 7. Concise API Overview

The backend exposes a structured RESTful API mounted under `/api`. Below is a concise overview of the core endpoints grouped by module.

### Authentication & Identity
*Handles user signups, credentials verification, OTP lifecycle, token refreshes, and Google single sign-on.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `POST` | `/api/auth/register` | Register a new client or worker account | Public |
| `POST` | `/api/auth/login` | Authenticate with credentials and receive cookies | Public |
| `POST` | `/api/auth/send-otp` | Request a new 6-digit verification OTP | Public |
| `POST` | `/api/auth/verify-otp` | Verify submitted OTP code | Public |
| `POST` | `/api/auth/refresh` | Exchange refresh token for fresh access token | Cookie |
| `GET` | `/api/auth/validate` | Validate current session and user status | Bearer / Cookie |
| `POST` | `/api/auth/google` | Authenticate using Google OAuth idToken | Public |

### User & Profile Management
*Manages client and worker user profiles, role toggling, addresses, and skills.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `PATCH`| `/api/users/mode` | Switch active role profile (e.g., Client <-> Worker) | Bearer / Cookie |
| `PUT` | `/api/users/user/:userId/profile` | Update user profile and avatar | Bearer / Cookie |
| `PATCH`| `/api/users/:userId/skills` | Update worker skills list | Bearer / Cookie |
| `POST` | `/api/users/:userId/addresses` | Add a new address with GPS coordinates | Bearer / Cookie |
| `DELETE`| `/api/users/:userId/addresses/:addressId` | Delete a saved address | Bearer / Cookie |

### Client Services & Workers
*Handles worker discovery, slot availability queries, slot reservation, and booking cancellations.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `GET` | `/api/client/workers` | Discover workers with geospatial/category filters | Bearer / Cookie |
| `GET` | `/api/client/workers/:id` | View public worker profile and ratings | Bearer / Cookie |
| `GET` | `/api/client/workers/:id/availability` | Fetch booked and available calendar slots | Bearer / Cookie |
| `POST` | `/api/client/services/lock-slots` | Temporarily lock slots for 10 minutes | Bearer / Cookie |
| `POST` | `/api/client/services/book` | Confirm service booking | Bearer / Cookie |
| `GET` | `/api/client/services/ongoing` | Get active/in-progress services | Bearer / Cookie |
| `PATCH`| `/api/client/services/:serviceId/cancel` | Cancel booking (triggers tiered refund matrix) | Bearer / Cookie |

### Worker Operations & Schedule
*Powers the worker dashboard, calendar blocking, and job status transitions.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `GET` | `/api/worker/dashboard` | Fetch worker KPI metrics and earnings | Worker Only |
| `POST` | `/api/worker/slot/block-dates` | Block calendar dates and time slots | Worker Only |
| `GET` | `/api/worker/services` | List all assigned jobs | Worker Only |
| `PATCH`| `/api/worker/services/:serviceId/start` | Mark service as started (`IN_PROGRESS`) | Worker Only |
| `PATCH`| `/api/worker/services/:serviceId/complete` | Mark service as finished (`COMPLETED`) | Worker Only |

### Meetings & Video Consultations
*Facilitates scheduling, history retrieval, and session management for 15-minute video calls.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `GET` | `/api/client/meetings/scheduled` | List upcoming client video consultations | Client Only |
| `GET` | `/api/worker/meetings/scheduled` | List upcoming worker video consultations | Worker Only |
| `POST` | `/api/video-call/join/:serviceId` | Join video consultation room | Bearer / Cookie |
| `POST` | `/api/video-call/leave/:serviceId` | Leave video consultation room | Bearer / Cookie |
| `POST` | `/api/video-call/end/:serviceId` | End video consultation session | Bearer / Cookie |

### Payments, Wallet & Transactions
*Handles payment gateway orders, signature verification, internal wallet balances, and audit logs.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `POST` | `/api/payment/create-order` | Create Razorpay order for booking | Bearer / Cookie |
| `POST` | `/api/payment/verify` | Verify Razorpay HMAC signature and confirm payment | Bearer / Cookie |
| `POST` | `/api/payment/wallet` | Complete payment using internal wallet balance | Bearer / Cookie |
| `GET` | `/api/wallet/balance` | Get authenticated user's wallet balance | Bearer / Cookie |
| `POST` | `/api/wallet/recharge/create-order` | Create order to top up wallet | Bearer / Cookie |
| `GET` | `/api/transactions/client` | View client transaction history | Client Only |
| `GET` | `/api/transactions/worker` | View worker earnings and transaction history | Worker Only |

### Communication (Chat & Notifications)
*Provides endpoints for conversation history, message persistence, and notifications.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `POST` | `/api/chat/send` | Persist and send chat message | Bearer / Cookie |
| `GET` | `/api/chat/:chatId` | Get message history for a conversation | Bearer / Cookie |
| `GET` | `/api/notifications` | Fetch user notifications | Bearer / Cookie |
| `PATCH`| `/api/notifications/:notificationId/read` | Mark a notification as read | Bearer / Cookie |

### Concerns, Reviews & Media
*Allows raising dispute tickets, submitting ratings, and requesting secure AWS S3 upload URLs.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `POST` | `/api/concerns` | Raise a support/dispute concern with image evidence | Bearer / Cookie |
| `GET` | `/api/concerns` | Retrieve my submitted concerns and status | Bearer / Cookie |
| `POST` | `/api/review/:serviceId` | Submit customer star rating and review | Client Only |
| `GET` | `/api/media/s3-upload-url` | Generate presigned AWS S3 PUT URL for direct upload | Bearer / Cookie |

### Admin Governance & Operations
*Platform governance, worker KYC auditing, dispute resolution, and category management.*

| Method | Endpoint | Description | Auth |
|:---|:---|:---|:---:|
| `GET` | `/api/admin/dashboard` | Fetch platform KPIs and revenue analytics | Admin Only |
| `GET` | `/api/admin/workers` | List all workers with verification status filters | Admin Only |
| `PATCH`| `/api/admin/verify/:userId` | Approve worker KYC verification | Admin Only |
| `PATCH`| `/api/admin/reject/:userId` | Reject worker KYC verification | Admin Only |
| `PATCH`| `/api/admin/access/:userId` | Block or unblock a user account | Admin Only |
| `GET` | `/api/admin/categories` | List all service categories | Admin Only |
| `POST` | `/api/admin/categories` | Create a new service category | Admin Only |
| `PATCH`| `/api/admin/concerns/:id/resolve` | Settle and resolve customer/worker dispute | Admin Only |
| `POST` | `/api/admin/moderation/process` | Manually trigger 15-minute moderation audit check | Admin Only |

---

## 8. Authentication & Security

### Dual-Token Strategy (Access & Refresh)
The platform uses a dual-token authentication flow:
- **Access Token:** Short-lived (15 minutes / 900 seconds), stored in an HTTP-only cookie or passed in the Authorization header.
- **Refresh Token:** Long-lived (7 days / 604,800 seconds), stored in a secure HTTP-only cookie, used exclusively to request a new access token.

```mermaid
sequenceDiagram
    autonumber
    actor Client as User Browser
    participant Edge as Next.js Edge Middleware
    participant Backend as Express Backend
    participant TokenSvc as JwtTokenService

    Client->>Backend: POST /api/auth/login { email, password }
    Backend->>TokenSvc: Generate Access Token (15m) & Refresh Token (7d)
    Backend-->>Client: Set HTTP-Only Cookies (accessToken, refreshToken)
    
    Note over Client,Edge: User navigates to protected page (/client/bookings)
    Client->>Edge: Request Page (Sends cookies)
    Edge->>Edge: verifyAccessToken(accessToken)
    alt Access Token is Valid
        Edge-->>Client: Allow Navigation
    else Access Token Expired
        Edge->>Backend: POST /api/auth/refresh (Sends refreshToken)
        alt Refresh Token is Valid
            Backend->>TokenSvc: Issue New Access Token
            Backend-->>Edge: Set-Cookie: fresh accessToken
            Edge-->>Client: Redirect to destination with fresh cookie
        else Refresh Token Expired / Invalid
            Edge-->>Client: Clear Cookies & Redirect to /login
        end
    end
```

### Edge Middleware & Route Protection
- **Edge Route Guards (`frontend/src/middleware.ts`):** Evaluates cookies on incoming requests before rendering. Unauthorized visits to `/client/*`, `/worker/*`, or `/admin/*` automatically redirect to `/login`.
- **Role Isolation:** Clients attempting to view `/admin` or `/worker` routes are immediately redirected to their corresponding home dashboard.
- **Cookie Security:** Cookies are issued with `httpOnly: true`, `sameSite: "lax"`, and conditional `secure: true` in production environments.

---

## 9. Project Directory Structure

```text
Nest & Nail/
├── package.json                    # Monorepo root configuration & dev script
├── pnpm-workspace.yaml             # PNPM workspace definition (backend, frontend)
├── pnpm-lock.yaml                  # Monorepo lockfile
├── README.md                       # Comprehensive project documentation
│
├── backend/                        # Express.js Clean Architecture API
│   ├── package.json                # Backend dependencies and scripts
│   ├── tsconfig.json               # TypeScript configuration
│   ├── Dockerfile.dev              # Container configuration for development
│   ├── src/
│   │   ├── index.ts                # Application bootstrap, CORS, sockets, 15-min cron
│   │   ├── config/
│   │   │   └── env.ts              # Type-safe environment variable loader
│   │   ├── domain/                 # Layer 1: Domain Entities & Repository Interfaces
│   │   │   ├── entities/           # User, Worker, Service, Wallet, Payment, Review
│   │   │   ├── errors/             # DomainError, AuthenticationError, UserBlockedError
│   │   │   ├── gateways/           # IPaymentGateway contract
│   │   │   └── repositories/       # Repository interfaces (IServiceRepository, etc.)
│   │   ├── application/            # Layer 2: Business Use Cases & Contracts
│   │   │   ├── contracts/          # ITokenService, IEmailService, IOtpService
│   │   │   ├── dtos/               # Request/Response Data Transfer Objects
│   │   │   ├── interfaces/         # Use Case abstract contracts
│   │   │   ├── mappers/            # Domain-to-DTO entity mappers
│   │   │   └── use-cases/          # Business workflows (BookWorker, CancelService, etc.)
│   │   ├── infrastructure/         # Layer 3: Adapters, Repositories & Sockets
│   │   │   ├── adapters/           # RazorpayGateway, S3Service, Nodemailer, Bcrypt
│   │   │   ├── database/           # Mongoose schemas/models & DB connection
│   │   │   ├── di/                 # DIContainer, controllers.di, usecases.di, infra.di
│   │   │   ├── logger/             # Winston daily rotating logger implementation
│   │   │   ├── repo/               # Mongoose repository implementations
│   │   │   └── socket/             # Socket.io handlers (Chat, VideoCall, Presence)
│   │   ├── presentation/           # Layer 4: Express Controllers, Routes & Middleware
│   │   │   ├── controllers/        # Express controllers (Client, Worker, Admin)
│   │   │   ├── middlewares/        # AuthMiddleware, ErrorHandler, RequestLogger, Multer
│   │   │   └── routes/             # Express routes grouped by domain module
│   │   └── shared/                 # Enums (ServiceStatus, SlotType), responses
│   └── logs/                       # Winston daily log rotation directory
│
└── frontend/                       # Next.js 16 App Router Application
    ├── package.json                # Frontend dependencies and scripts
    ├── next.config.ts              # Next.js configuration
    ├── tsconfig.json               # TypeScript path aliases (@/* -> ./src/*)
    ├── src/
    │   ├── middleware.ts           # Next.js Edge Route Guard & token refresher
    │   ├── app/                    # App Router Layouts and Pages
    │   │   ├── (auth)/             # Authentication views (login, signup, otp)
    │   │   ├── actions/            # Next.js Server Actions (BFF data layer)
    │   │   ├── admin/              # Admin dashboard, verification, users, categories
    │   │   ├── client/             # Client views (home, workers, bookings, meetings)
    │   │   ├── worker/             # Worker dashboard, services, calendar, wallet
    │   │   ├── layout.tsx          # Root layout with context providers
    │   │   └── globals.css         # Tailwind CSS v4 styling rules
    │   ├── components/             # Reusable UI component library
    │   │   ├── containers/         # Responsive Navbars, Sidebars, Footers
    │   │   ├── modals/             # BookingModal, AddressModal, ReviewModal
    │   │   └── ui/                 # Buttons, Dialogs, Badges, Inputs
    │   ├── lib/                    # Helper utilities and validation schemas
    │   ├── shared/                 # Shared enums, types, and mappers
    │   ├── sources/                # Axios API clients & route definitions
    │   ├── store/                  # Zustand stores (useUserStore with persistence)
    │   └── utils/                  # Razorpay script loader, date-time formatters
    └── public/                     # Static media assets, icons, and illustrations
```

---

## 10. Installation & Setup

### Prerequisites
- **Node.js:** `v20.19.0` or higher
- **Package Manager:** `pnpm` (v9 or higher recommended)
  ```bash
  npm install -g pnpm
  ```
- **MongoDB:** Local MongoDB community server or active MongoDB Atlas connection URI

### Step-by-Step Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/nest-and-nail.git
   cd "Nest & Nail"
   ```

2. **Install Dependencies:**
   Install all dependencies across both backend and frontend workspaces in one step:
   ```bash
   pnpm install
   ```

3. **Configure Environment Files:**
   Create `.env.local` in `frontend/` and `.env` in `backend/` as outlined in Section 11.

---

## 11. Environment Variable Configuration

### Frontend Environment Configuration (`.env.example`)

Create a `.env.local` file in the `frontend/` directory based on the following template:

```env
NEXT_PUBLIC_FRONTEND_URL=http://localhost:3000
NEXT_PUBLIC_API_URL=http://localhost:4000

NEXT_PUBLIC_GOOGLE_CLIENT_ID=your_google_client_id

NEXT_PUBLIC_MAX_AGE_ACCESS_TOKEN=your_access_token_expiry
NEXT_PUBLIC_MAX_AGE_REFRESH_TOKEN=your_refresh_token_expiry

NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
NEXT_PUBLIC_CLOUDINARY_API_KEY=your_cloudinary_api_key

NEXT_PUBLIC_RAZORPAY_KEY=your_razorpay_public_key
```

### Backend Environment Configuration (`.env.example`)

Create a `.env` file in the `backend/` directory based on the following template:

```env
# Server Configuration
PORT=4000
NODE_ENV=development
FRONTEND_URL=http://localhost:3000

# Database
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/nest_nail

# JWT Secrets & Expiry
ACCESS_TOKEN_SECRET=your_access_token_secret
REFRESH_TOKEN_SECRET=your_refresh_token_secret
ACCESS_TOKEN_MAX_AGE=900
REFRESH_TOKEN_MAX_AGE=604800

# Google OAuth (Backend Verification)
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

# SMTP Email Service (Nodemailer OTP delivery)
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_email_app_password

# AWS S3 Storage (Direct Presigned URLs)
AWS_REGION=ap-south-1
AWS_BUCKET_NAME=your_bucket_name
AWS_ACCESS_KEY_ID=your_aws_access_key_id
AWS_SECRET_ACCESS_KEY=your_aws_secret_access_key

# Razorpay Payment Gateway
RAZORPAY_KEY=your_razorpay_key_id
RAZORPAY_SECRET=your_razorpay_key_secret

# Logging
LOG_RETENTION_DAYS=14
```

### Configuration & Security Notice

> [!IMPORTANT]
> **Environment Configuration Required:** You must configure your own valid environment variables in both `frontend/.env.local` and `backend/.env` before running the application.

> [!CAUTION]
> **Credential Security:** Never expose backend secrets—such as `GOOGLE_CLIENT_SECRET`, `RAZORPAY_SECRET`, `ACCESS_TOKEN_SECRET`, `REFRESH_TOKEN_SECRET`, or `AWS_SECRET_ACCESS_KEY`—via `NEXT_PUBLIC_` variables or in client-side code. All variables prefixed with `NEXT_PUBLIC_` are bundled into client-side JavaScript.

---

## 12. Running the Application

### Development Mode

Run both the frontend and backend servers concurrently from the monorepo root:

```bash
pnpm run dev
```

*Or run them in separate terminals:*

```bash
# Terminal 1: Express Backend (Port 4000)
cd backend
pnpm run dev

# Terminal 2: Next.js Frontend (Port 3000)
cd frontend
pnpm run dev
```

### Production Build & Execution

```bash
# 1. Build and start the backend
cd backend
pnpm run build     # Compiles TypeScript to dist/
pnpm run start     # Executes node dist/index.js

# 2. Build and start the frontend
cd ../frontend
pnpm run build     # Generates optimized Next.js production bundle
pnpm run start     # Starts Next.js production server
```

---

## 13. Error Handling, Logging & Reliability

### Centralized Exception Handling
The backend implements a unified error-handling pipeline that maps domain exceptions directly to structured HTTP status codes:

```mermaid
flowchart LR
    DomainErr[Domain Layer Exception] --> Handler[Express errorHandler Middleware]
    Handler --> MapStatus{Error Type}
    
    MapStatus -- AuthenticationError --> Res401[401 Unauthorized]
    MapStatus -- UserNotFoundError --> Res404[404 Not Found]
    MapStatus -- ValidationError --> Res400[400 Bad Request]
    MapStatus -- DomainError --> Res400b[400 Bad Request]
    MapStatus -- AppError --> ResCustom[Custom Status Code]
    MapStatus -- Unknown --> Res500[500 Internal Server Error]
```

### Structured Winston Logging
The backend uses Winston with `winston-daily-rotate-file`:
- **Console Transport:** Colorized timestamps and stack traces for real-time development inspection.
- **`logs/error-%DATE%.log`:** Dedicated error-level log stream with stack traces.
- **`logs/application-%DATE%.log`:** General operational logging with automatic 14-day archiving and compression (`zippedArchive: true`).
- **HTTP Request Logger:** `RequestLogger.ts` logs incoming HTTP methods, URLs, client IPs, response codes, and latency in milliseconds.

---

## 14. Roadmap & Future Improvements

### Existing Capabilities
- [x] Multi-factor authentication (Email/Password, 6-digit OTP, Google SSO).
- [x] Role-Based Access Control (Client, Worker, Admin).
- [x] Worker KYC document submission and admin verification.
- [x] Geospatial worker discovery with 2dsphere indexing and Leaflet maps.
- [x] Half-day, full-day, and 15-minute video consultation booking slots.
- [x] Real-time slot locking to prevent concurrent double-booking.
- [x] Native Razorpay payment gateway integration and internal wallet system.
- [x] Tiered cancellation policy with automatic wallet refunds.
- [x] Peer-to-peer WebRTC video consultations with Socket.io signaling.
- [x] Real-time chat with attachment handling.
- [x] Real-time push notification engine across multiple browser tabs.
- [x] 15-minute automated moderation daemon for physical and virtual no-shows.

### Planned Enhancements
- [ ] **Native Mobile Application:** React Native / Expo client sharing domain types.
- [ ] **AI-Powered Issue Triage:** Computer vision model to diagnose home damage from uploaded client photos.
- [ ] **Multi-Worker Dispatch:** Booking multi-worker teams for large renovation projects.
- [ ] **Escrow Milestone Payouts:** Phased release of funds based on client sign-off.
- [ ] **Redis Caching & Pub/Sub:** Distributed caching for worker listings and multi-node Socket.io scaling.

---

## 15. Contributing & License

### Contributing
Contributions to Nest & Nail are welcome. Please adhere to the following workflow:
1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/NewFeature`).
3. Commit your changes with clear messages (`git commit -m 'feat: Add NewFeature'`).
4. Push to the branch (`git push origin feature/NewFeature`).
5. Open a well-documented Pull Request.

### License
This project is licensed under the **ISC License**. Refer to the project license files for details.

---

<p align="center">
  Built with ❤️ for homeowners and skilled trade professionals.
</p>
