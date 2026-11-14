# 🏠 Nest & Nail — On-Demand Home Services Marketplace

> **Architected for Reliability. Engineered with Clean Architecture.**  
> *A high-performance, role-based platform connecting homeowners with vetted professionals for physical repairs, home maintenance, and live virtual consultations.*

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
- [2. Technology Stack](#2-technology-stack)
- [3. System Architecture](#3-system-architecture)
  - [High-Level Architecture](#high-level-architecture)
  - [Backend Clean Architecture & Domain-Driven Design](#backend-clean-architecture--domain-driven-design)
  - [Frontend Architecture & Next.js App Router](#frontend-architecture--nextjs-app-router)
  - [End-to-End Request Lifecycle](#end-to-end-request-lifecycle)
- [4. Visual Workflow Diagrams](#4-visual-workflow-diagrams)
  - [1. User Registration & OTP Flow](#1-user-registration--otp-flow)
  - [2. Google OAuth Authentication](#2-google-oauth-authentication)
  - [3. Password Recovery & Reset Flow](#3-password-recovery--reset-flow)
  - [4. Worker Onboarding & KYC Document Verification](#4-worker-onboarding--kyc-document-verification)
  - [5. Geospatial Worker Discovery & Availability Query](#5-geospatial-worker-discovery--availability-query)
  - [6. Service Booking & Slot Reservation](#6-service-booking--slot-reservation)
  - [7. Payment Processing (Razorpay & Internal Wallet)](#7-payment-processing-razorpay--internal-wallet)
  - [8. Physical Service Execution Lifecycle](#8-physical-service-execution-lifecycle)
  - [9. Tiered Cancellation & Automatic Refund Matrix](#9-tiered-cancellation--automatic-refund-matrix)
  - [10. WebRTC Video Consultation & Socket.io Signaling](#10-webrtc-video-consultation--socketio-signaling)
  - [11. Real-Time Chat & Bidirectional Messaging](#11-real-time-chat--bidirectional-messaging)
  - [12. Real-Time Push Notification Engine](#12-real-time-push-notification-engine)
  - [13. Automated 15-Minute Moderation & Penalization Engine](#13-automated-15-minute-moderation--penalization-engine)
- [5. Feature Matrix by User Role](#5-feature-matrix-by-user-role)
  - [Client Capabilities](#client-capabilities)
  - [Worker Capabilities](#worker-capabilities)
  - [Admin Governance & Moderation](#admin-governance--moderation)
- [6. Database Architecture & Data Modeling](#6-database-architecture--data-modeling)
  - [Entity-Relationship Diagram](#entity-relationship-diagram)
  - [Schema Definitions & Database Specifications](#schema-definitions--database-specifications)
- [7. Comprehensive API Documentation](#7-comprehensive-api-documentation)
  - [Authentication & Identity Routes](#authentication--identity-routes)
  - [User & Profile Routes](#user--profile-routes)
  - [Worker Routes](#worker-routes)
  - [Client & Booking Routes](#client--booking-routes)
  - [Meeting & Video Consultation Routes](#meeting--video-consultation-routes)
  - [Payments & Wallet Routes](#payments--wallet-routes)
  - [Communication Routes (Chat & Notifications)](#communication-routes-chat--notifications)
  - [Concerns & Reviews Routes](#concerns--reviews-routes)
  - [Media & Storage Routes](#media--storage-routes)
  - [Admin Management & Governance Routes](#admin-management--governance-routes)
- [8. Authentication, Authorization & Security](#8-authentication-authorization--security)
  - [JWT Dual-Token Rotation Strategy](#jwt-dual-token-rotation-strategy)
  - [Role-Based Access Control (RBAC) Matrix](#role-based-access-control-rbac-matrix)
  - [Edge Middleware & Server Action Security](#edge-middleware--server-action-security)
- [9. Third-Party Integrations](#9-third-party-integrations)
- [10. Project Directory Structure](#10-project-directory-structure)
- [11. Installation & Local Development Setup](#11-installation--local-development-setup)
- [12. Environment Variable Configuration](#12-environment-variable-configuration)
- [13. Production Deployment Architecture](#13-production-deployment-architecture)
- [14. Error Handling, Logging & Reliability](#14-error-handling-logging--reliability)
- [15. Roadmap & Future Improvements](#15-roadmap--future-improvements)
- [16. Contributing & License](#16-contributing--license)

---

## 1. Project Overview

### The Problem
Finding dependable, background-verified home service professionals (plumbers, electricians, carpenters, cleaners) remains fragmented, opaque, and risky:
1. **Lack of Trust:** Customers struggle to verify the qualifications, identity proofs, and skill certifications of independent service contractors.
2. **Scheduling Inflexibility:** Booking physical visits without an initial assessment often leads to wasted time, misdiagnosed issues, and unpredictable pricing.
3. **Absence & No-Show Risks:** Service workers frequently miss appointments, while clients cancel abruptly without fair recourse for either party.
4. **Disorganized Communications:** Relying on personal phone numbers exposes private details and provides no paper trail for disputes or warranty claims.

### The Solution
**Nest & Nail** is a production-grade full-stack marketplace platform built to streamline the entire residential service journey. By combining a **Domain-Driven Clean Architecture** backend with a modern **Next.js 16 App Router** frontend, Nest & Nail provides:
- **Rigorous Admin KYC:** Workers submit government documents and trade certificates reviewed by platform administrators before accepting jobs.
- **Dual Service Modalities:** Clients can book **Physical On-Site Appointments** (Half-Day Morning/Evening or Full-Day) or **Live WebRTC Video Consultations** (15-minute triage slots) to troubleshoot and quote jobs remotely.
- **Geospatial Discovery:** MongoDB `2dsphere` indexes match clients with nearby workers based on real-time coordinates and interactive Leaflet map address selectors.
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
| **Client** | Homeowners needing fast, reliable repairs or installations. | Discover nearby verified workers, check calendar availability, lock slots, checkout with Razorpay/Wallet, track progress, participate in WebRTC video calls, rate workers, and raise resolution tickets. |
| **Worker** | Skilled technicians seeking consistent, verified job requests. | Complete KYC verification by uploading credentials, configure working hours/block dates, accept job dispatches, start/complete jobs, track earnings, and attend video triage calls. |
| **Admin** | Platform operators managing quality control and safety. | Audit submitted worker identity proofs, manage categories and platform commissions, inspect meetings/chats, arbitrate customer concerns, and oversee transactions. |

### High-Level Value Proposition
- **Enterprise-Grade Clean Architecture:** Strict decoupling between Presentation, Application, Domain, and Infrastructure ensures isolated testability and zero vendor lock-in.
- **Unified TypeScript Monorepo:** Managed via PNPM workspaces with synchronized domain types and DTO definitions across client and server.
- **Zero-Polling Real-Time Experience:** Socket.io handles instant chat, call handshakes, and system notifications without taxing the client battery or network.

---

## 2. Technology Stack

Every technology listed below is verified directly within the repository codebase:

| Category | Technology | Version | Purpose in Nest & Nail |
|:---|:---|:---|:---|
| **Frontend Framework** | **Next.js (App Router)** | `16.2.6` | Powers server-side rendering (SSR), edge routing, layouts, and server actions with Turbopack compilation. |
| **UI Library** | **React** | `19.1.0` | Powers declarative, concurrent component rendering across all client views. |
| **Styling & Design** | **Tailwind CSS** | `v4.0.0` | Utility-first styling with `@tailwindcss/postcss` and dynamic styling via `clsx` and `tailwind-merge`. |
| **Headless UI Primitives** | **Radix UI** | Multiple | Accessible, unstyled primitives for dialogs, labels, separators, and responsive navigation menus. |
| **Icons & Visuals** | **Lucide React** / **Heroicons** | `^0.546.0` | SVG icons used across navigation, dashboard widgets, and status badges. |
| **State Management** | **Zustand** | `5.0.8` | Client-side reactive authentication store with localStorage persistence and hydration reconciliation. |
| **Client HTTP Transport** | **Axios** | `1.12.2` | Configured with interceptors for bearer authentication and backend REST communication. |
| **Maps & Geolocation** | **Leaflet** & **React-Leaflet** | `1.9.4` / `5.0.0` | Interactive map rendering, pin placement, and reverse geocoding via OpenStreetMap Nominatim. |
| **Charts & Analytics** | **Recharts** | `3.8.1` | Admin and worker metrics visualization (revenue trends, booking volume, user distribution). |
| **Backend Runtime** | **Node.js** | `>=20.x` | High-performance asynchronous JavaScript execution runtime. |
| **Web Server Framework** | **Express.js** | `4.18.2` | REST API layer handling routing, middlewares, and controller execution. |
| **Language** | **TypeScript** | `5.9.3` | Enforces static typing across the entire monorepo. |
| **Database & ODM** | **MongoDB** & **Mongoose** | `8.0.0` | Document database utilized with schemas, discriminators, compound indexes, and 2dsphere geo-indexing. |
| **Real-Time Engine** | **Socket.io** & **Client** | `4.8.3` | Manages live chat, presence tracking, system broadcasts, and WebRTC signaling. |
| **Video Telephony** | **WebRTC (Browser Native)** | Native P2P | Peer-to-peer audio/video streaming negotiated over Socket.io signaling rooms. |
| **Cloud Storage** | **AWS S3 SDK v3** | `3.990.0` | Secure direct-to-S3 uploads and downloads via Presigned URLs (`@aws-sdk/s3-request-presigner`). |
| **Payment Gateway** | **Razorpay Node SDK** | `2.9.6` | Order generation, checkout capture, and HMAC-SHA256 signature verification. |
| **Email Service** | **Nodemailer** | `7.0.10` | SMTP delivery for 6-digit OTP verification codes and password recovery emails. |
| **Authentication & Tokens**| **JSONWebToken** & **Jose** | `9.0.2` / `6.1.2` | Access and Refresh token generation, validation, and edge decoding in Next.js middleware. |
| **Password Security** | **Bcrypt.js** | `2.4.3` | Salt generation and cryptographic hashing for secure password storage. |
| **OAuth Integration** | **Google Auth Library** | `10.5.0` | IdToken validation for seamless single sign-on (SSO). |
| **Logging & Auditing** | **Winston** & **Daily Rotate** | `3.18.3` / `5.0.0`| Structured logging with log rotation, custom formats, and console/file transports. |
| **Form & Pin Validation** | **Zod** & **Input-OTP** | `4.1.12` / `1.4.2`| Runtime schema validation and segmented 6-digit pin entry UI components. |
| **Workspace Management** | **PNPM** | `v9+` | Fast, disk-efficient monorepo workspace package manager. |

---

## 3. System Architecture

### High-Level Architecture

The platform follows a distributed, multi-tiered architecture where the Next.js frontend and Express backend communicate via RESTful HTTP APIs and persistent WebSocket connections.

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
        AuthMw["AuthMiddleware<br/>(JWT Verification & RBAC)"]
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

    subgraph Persistence["Database & Cloud Services"]
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

The backend strictly implements the **Clean Architecture** paradigm proposed by Robert C. Martin. The fundamental rule is the **Dependency Rule**: *Source code dependencies must point only inward toward higher-level policies.*

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

#### Detailed Layer Responsibilities:

1. **Domain Layer (`backend/src/domain/`)**:
   - Contains pure business entities (`User`, `Worker`, `Service`, `Wallet`, `Payment`, `Review`, `Concern`).
   - Declares abstract repository interfaces (`IServiceRepository`, `IWalletRepository`, `IWorkerScheduleRepository`) and gateway contracts (`IPaymentGateway`).
   - Defines domain-specific errors (`DomainError`, `AuthenticationError`, `UserBlockedError`, `UserNotFoundError`).
   - Has **zero dependencies** on databases, frameworks, or external packages.

2. **Application Layer (`backend/src/application/`)**:
   - Contains single-purpose business use case classes (`BookWorkerUseCase`, `CancelServiceUseCase`, `ProcessModerationActionsUseCase`, `VerifyPaymentUseCase`).
   - Contains Data Transfer Objects (DTOs) defining strict input and output shapes.
   - Defines application service contracts (`ITokenService`, `IEmailService`, `IOtpService`, `IRealtimeService`).

3. **Infrastructure Layer (`backend/src/infrastructure/`)**:
   - Implements domain repository interfaces using Mongoose models (`ServiceRepository`, `UserRepositoryFactory`, `WalletRepository`).
   - Integrates third-party services via adapter classes (`RazorpayGateway`, `S3Service`, `NodemailerEmailService`, `BcryptPasswordHasher`, `JwtTokenService`).
   - Hosts the Dependency Injection Container (`DIContainer`), which assembles all instances using constructor injection without third-party reflection libraries.

4. **Presentation Layer (`backend/src/presentation/`)**:
   - Contains Express controllers converting HTTP requests into DTOs, invoking use cases, and formatting standardized responses using `ResponseHandler`.
   - Contains Express route definitions and middlewares (`AuthMiddleware`, `RequestLogger`, `errorHandler`, `multerMiddleware`).

---

### Frontend Architecture & Next.js App Router

The frontend uses Next.js App Router conventions with role-based route groups:

```mermaid
graph TD
    subgraph Routing["Next.js App Router Structure"]
        RootLayout["app/layout.tsx (Providers, Toast, SocketContext)"]
        AuthGroup["app/(auth)/ (login, signup, otp, forgot-password)"]
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

To illustrate how data travels across all architectural boundaries, here is the exact trace of a **Service Booking** operation:

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
    participant NotifRepo as NotificationRepository
    participant DB as MongoDB Atlas

    Client->>UI: Selects Dates, Slots & Clicks "Confirm Booking"
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
    
    UC->>NotifRepo: create(workerNotification)
    NotifRepo->>DB: NotificationModel.create(...)
    
    UC-->>Ctrl: Returns ServiceResponseDTO
    Ctrl-->>API: 201 Created { success: true, payload: service }
    API-->>SA: Response mapped
    SA-->>UI: Updates Booking Status
    UI-->>Client: Displays Booking Confirmation & Payment Prompt
```

---

## 4. Visual Workflow Diagrams

### 1. User Registration & OTP Flow

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

### 3. Password Recovery & Reset Flow

```mermaid
sequenceDiagram
    autonumber
    actor User as User
    participant UI as Forgot Password Page
    participant AuthAPI as AuthController
    participant SMTP as Nodemailer
    participant DB as MongoDB (Otp & User)

    User->>UI: Submits registered email
    UI->>AuthAPI: POST /api/auth/forgot-password { email }
    AuthAPI->>DB: Verify user existence
    AuthAPI->>DB: Generate & persist 6-digit OTP (TTL: 120s)
    AuthAPI->>SMTP: Dispatch OTP email
    AuthAPI-->>UI: OTP sent confirmation
    User->>UI: Enters OTP & New Password
    UI->>AuthAPI: POST /api/auth/reset-password { email, otp, newPassword }
    AuthAPI->>DB: Verify OTP match & expiration
    alt Valid OTP
        AuthAPI->>DB: Hash new password with bcrypt & update UserModel
        AuthAPI->>DB: Invalidate/Delete OTP
        AuthAPI-->>UI: 200 OK: "Password successfully updated"
        UI->>User: Redirect to /login
    else Invalid / Expired OTP
        AuthAPI-->>UI: 400 Bad Request: "Invalid or expired OTP"
    end
```

### 4. Worker Onboarding & KYC Document Verification

```mermaid
sequenceDiagram
    autonumber
    actor Worker as Service Worker
    participant Portal as Worker Profile (/worker/profile)
    participant S3 as AWS S3 (Presigned PUT)
    participant Backend as AdminVerificationController
    actor Admin as Platform Admin
    participant DB as MongoDB (UserModel)

    Worker->>Portal: Fills Trade Categories & Hourly/Daily Rates
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

### 5. Geospatial Worker Discovery & Availability Query

```mermaid
sequenceDiagram
    autonumber
    actor Client as Client
    participant DiscoverUI as /client/workers
    participant Backend as ClientWorkerController
    participant Svc as GetAvailableWorkersUseCase
    participant DB as MongoDB Atlas

    Client->>DiscoverUI: Enters Location (GPS / Leaflet) & Category
    DiscoverUI->>Backend: GET /api/client/workers?category=Plumbing&lat=12.97&lng=77.59
    Backend->>Svc: execute(filters, coordinates)
    Svc->>DB: UserModel.aggregate() with $geoNear (2dsphere index)
    Note over Svc,DB: Filters: role: "worker", isVerified: "VERIFIED",<br/>isBlocked: false, isSuspended: false
    DB-->>Svc: Returns ranked workers with distance calculation
    Svc-->>Backend: Worker DTOs with ratings & hourly rates
    Backend-->>DiscoverUI: JSON response
    DiscoverUI->>Client: Renders Worker Cards on interactive Map & List
```

### 6. Service Booking & Slot Reservation

```mermaid
sequenceDiagram
    autonumber
    actor Client as Client
    participant Modal as BookingModal
    participant Backend as ClientServiceController
    participant SchedRepo as WorkerScheduleRepository
    participant DB as MongoDB

    Client->>Modal: Selects Date (e.g., Nov 18) & Slot (MORNING_HALF)
    Modal->>Backend: POST /api/client/services/lock-slots { workerId, slots }
    Backend->>SchedRepo: lockSlots(workerId, slots, clientId)
    SchedRepo->>DB: Upsert WorkerSchedule (lockedUntil = now + 10m)
    DB-->>Backend: Slots temporarily reserved
    Backend-->>Modal: 200 OK (Proceed to Payment)
    Note over Modal,Client: Client has 10 minutes to complete checkout.<br/>If aborted, lock expires automatically.
```

### 7. Payment Processing (Razorpay & Internal Wallet)

```mermaid
sequenceDiagram
    autonumber
    actor Client as Client
    participant Checkout as Payment Screen
    participant Backend as PaymentController
    participant Gateway as RazorpayGateway / WalletRepository
    participant DB as MongoDB (Payment & Transaction)

    Client->>Checkout: Chooses Payment Method (Razorpay / Wallet)
    alt Payment via Razorpay
        Checkout->>Backend: POST /api/payment/create-order { serviceId, amount }
        Backend->>Gateway: razorpay.orders.create({ amount * 100, INR })
        Gateway-->>Backend: Returns orderId
        Backend-->>Checkout: orderId, keyId, amount
        Checkout->>Client: Launches Razorpay Modal Checkout
        Client->>Checkout: Completes Card / UPI Payment
        Checkout->>Backend: POST /api/payment/verify { orderId, paymentId, signature }
        Backend->>Backend: HMAC-SHA256 signature verification
        Backend->>DB: Persist Payment (status: SUCCESS) & update Service
    else Payment via Internal Wallet
        Checkout->>Backend: POST /api/payment/wallet { serviceId, amount }
        Backend->>Gateway: walletRepo.debitBalance(clientId, amount)
        Gateway->>DB: Atomically deduct balance & record Transaction
        Backend->>DB: Update Service (paymentStatus: SUCCESS)
    end
    Backend-->>Checkout: Payment Confirmation & Service Confirmed
```

### 8. Physical Service Execution Lifecycle

```mermaid
stateDiagram-v2
    [*] --> PENDING: Client Books Service
    PENDING --> CONFIRMED: Advance / Full Payment Verified
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

### 9. Tiered Cancellation & Automatic Refund Matrix

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

### 10. WebRTC Video Consultation & Socket.io Signaling

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

### 11. Real-Time Chat & Bidirectional Messaging

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

### 12. Real-Time Push Notification Engine

```mermaid
sequenceDiagram
    autonumber
    participant Event as Domain Event (e.g. Booking Confirmed)
    participant UC as SendNotificationUseCase
    participant DB as MongoDB (NotificationModel)
    participant RTSvc as RealtimeService
    participant Sockets as SocketServer (userSocketMap)
    actor User as Client / Worker Client Tabs

    Event->>UC: execute({ userId, title, message, type, data })
    UC->>DB: Persist Notification (isRead: false)
    UC->>RTSvc: emitToUser(userId, "notification", notificationDTO)
    RTSvc->>Sockets: getSocketIds(userId)
    Note over Sockets: Delivers to all open tabs for this user simultaneously
    Sockets-->>User: socket.emit("notification", notificationDTO)
    User->>User: Toast notification pop-up & unread counter increment
```

### 13. Automated 15-Minute Moderation & Penalization Engine

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

## 5. Feature Matrix by User Role

### Client Capabilities

| Capability | Module / Route | Technical Implementation |
|:---|:---|:---|
| **User Onboarding** | `/(auth)/signup`, `/otp` | Form validation with Zod, bcrypt hashing, 6-digit OTP delivery via Nodemailer. |
| **Google Sign-In** | `/(auth)/login` | `@react-oauth/google` integration, backend ID token validation via `google-auth-library`. |
| **Worker Discovery** | `/client/workers` | MongoDB `$geoNear` query matching categories, location radius, and sorting by rating. |
| **Interactive Map Selector**| `/client/profile` | Leaflet map with Nominatim OpenStreetMap reverse geocoding for precise coordinates. |
| **Availability & Slots** | `/client/workers/[id]` | Real-time query of `WorkerSchedule`, slot locking (Morning/Evening/Full Day & Video slots). |
| **Service Booking** | `/client/workers/[id]` | Transactional multi-slot booking with temporary 10-minute hold to prevent race conditions. |
| **Multi-Gateway Payment** | `/client/bookings` | Native Razorpay checkout modal + internal Wallet deduction with automatic ledger entries. |
| **Booking Tracking** | `/client/bookings` | Real-time status pipeline (`PENDING` -> `CONFIRMED` -> `IN_PROGRESS` -> `COMPLETED`). |
| **Tiered Cancellation** | `/client/bookings` | Programmatic refund tiers: 100% (<15m), 90% (15m-1hr), 50% (1-6hr), locked (>6hr). |
| **Live Consultation** | `/client/video-call/[id]` | WebRTC peer-to-peer audio/video with Socket.io signaling and connection state tracking. |
| **Instant Messaging** | Floating Chat Widget | Socket.io room-based instant chat with read receipts and attachment handling. |
| **Reviews & Feedback** | `/client/bookings` | Star ratings and written reviews saved to `ReviewModel`, updating worker average rating. |
| **Concern Ticketing** | `/client/bookings` | Submit dispute tickets with image upload support for admin arbitration. |

### Worker Capabilities

| Capability | Module / Route | Technical Implementation |
|:---|:---|:---|
| **KYC Verification** | `/worker/profile` | Upload national identity documents and trade certificates directly to S3 via Presigned URLs. |
| **Category Selection** | `/worker/profile` | Map trade skills to admin-defined categories (e.g. Electrician, Carpentry, Plumbing). |
| **Calendar & Blocking** | `/worker/schedule` | Block/unblock individual dates and slot windows (`MORNING_HALF`, `EVENING_HALF`, `FULL_DAY`). |
| **Job Management** | `/worker/services` | View upcoming dispatches, client GPS coordinates, start job, and complete job. |
| **Earnings & Wallet** | `/worker/wallet` | View current balance, automated credit deposits upon job completion, and transaction history. |
| **Worker Dashboard** | `/worker/dashboard` | Visual metrics: weekly job count, customer ratings, ongoing tasks, and total earnings. |
| **Video Consultation** | `/worker/video-call/[id]` | Join scheduled 15-minute diagnostic triage calls directly from the dashboard. |

### Admin Governance & Moderation

| Capability | Module / Route | Technical Implementation |
|:---|:---|:---|
| **Platform Analytics** | `/admin/dashboard` | High-level metrics: user breakdown, gross booking value, refund volume, platform commission. |
| **Worker Verification Queue**| `/admin/verification` | Audit submitted identity documents and certificates with one-click approve/reject actions. |
| **User Access Control** | `/admin/users` | Toggle active/blocked status for any user, invalidating active refresh sessions. |
| **Category Management** | `/admin/categories` | CRUD operations on service categories with custom SVG icons and enable/disable switches. |
| **Service Auditing** | `/admin/services` | Detailed ledger of all platform bookings, worker assignments, timestamps, and fees. |
| **Concern Resolution** | `/admin/concerns` | Review client/worker dispute messages, inspect evidence photos, and record resolution verdicts. |
| **Autonomous Moderation** | `backend/src/index.ts` | 15-minute background worker detecting no-shows, issuing automated wallet refunds and suspensions. |
| **Financial Audit Trail** | `/admin/transactions` | Real-time inspection of all platform payments, Razorpay order IDs, credits, and debits. |

---

## 6. Database Architecture & Data Modeling

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
        string passwordhash
        boolean isBlocked
        boolean isOnline
        string isVerified
        string role "client | worker | admin"
        string loginMethod "EMAIL_PASSWORD | GOOGLE"
        string profilePictureUrl
        string_array skills
        string_array documents
        string_array certificates
        number rating
        number totalRatings
        number weeklyJobCount
        boolean isSuspended
        date suspensionEndDate
        boolean canAcceptBookings
        date createdAt
    }

    ADDRESS {
        string addressId
        string label "HOME | WORK | OTHER"
        string street
        string city
        string state
        string zip
        Point location "2dsphere [lng, lat]"
        boolean isDefault
    }

    CATEGORY {
        ObjectId _id PK
        string name UK
        string description
        string iconUrl
        boolean isActive
    }

    SERVICE {
        string serviceId PK
        string clientId FK
        string workerId FK
        string category
        string title
        string description
        Point location "2dsphere [lng, lat]"
        date scheduledDate
        array selectedSlots
        number numberOfDays
        number pricePerWorker
        number totalAmount
        string status "PENDING | CONFIRMED | IN_PROGRESS | COMPLETED | CANCELLED | NO_SHOW"
        string paymentStatus "PENDING | SUCCESS | FAILED | REFUNDED"
        date startedAt
        date completedAt
        date cancelledAt
        object videoCall "RoomId, Timestamps, JoinedUsers"
    }

    WORKER_SCHEDULE {
        ObjectId _id PK
        string workerId FK
        date date
        string slotType "MORNING_HALF | EVENING_HALF | FULL_DAY | VIDEO_SLOTS"
        boolean isBooked
        boolean isAvailable
        string serviceId FK
        date lockedUntil
    }

    WALLET {
        string walletId PK
        string userId FK
        number balance
        string currency "INR"
    }

    WALLET_TRANSACTION {
        string transactionId PK
        string userId FK
        number amount
        string type "CREDIT | DEBIT"
        string description
        date createdAt
    }

    PAYMENT {
        ObjectId _id PK
        string serviceId FK
        string clientId FK
        number amount
        string currency "INR"
        string orderId
        string paymentId
        string signature
        string status "CREATED | SUCCESS | FAILED"
        date createdAt
    }

    CONCERN {
        string concernId PK
        string serviceId FK
        string userId FK
        string raisedBy "WORKER | CLIENT"
        string message
        string status "OPEN | RESOLVED | REJECTED"
        string_array images
        string resolutionMessage
        date resolvedAt
    }

    REVIEW {
        string reviewId PK
        string serviceId FK,UK
        string clientId FK
        string workerId FK
        number rating
        string review
        date createdAt
    }

    OTP {
        string email
        string otp
        date expiresAt "TTL: 120s"
    }
```

### Schema Definitions & Database Specifications

1. **User Collection (`UserModel.ts`)**:
   - Implements Mongoose Discriminators: Base schema discriminator key is `role`. `WorkerModel` extends `UserModel`.
   - **Geospatial Index:** `UserSchema.index({ "address.location": "2dsphere" })` enables ultra-fast distance queries.
   - Unique constraints on `userId` and `email`.

2. **Service Collection (`ServiceModel.ts`)**:
   - Stores physical bookings and virtual video consultations.
   - **Indexes:**
     - `{ location: "2dsphere" }` for proximity searches.
     - `{ workerId: 1, scheduledDate: 1 }` for fast calendar lookups.
     - `{ clientId: 1 }` for client booking history retrieval.

3. **Worker Schedule Collection (`WorkerScheduleModel.ts`)**:
   - Manages calendar availability and prevents double bookings.
   - **Compound Unique Index:** `{ workerId: 1, date: 1, slotType: 1 }` ensures a worker can never be scheduled twice for the same slot.

4. **OTP Collection (`OtpModel.ts`)**:
   - Stores temporary registration and password reset verification codes.
   - **Automatic TTL Index:** `OtpSchema.index({ expiresAt: 1 }, { expireAfterSeconds: 120 })` guarantees MongoDB automatically purges expired codes after 2 minutes.

5. **Client-Worker Restriction Collection (`ClientWorkerRestrictionModel.ts`)**:
   - Enforces cooling-off periods when a client misses a video consultation.
   - **Indexes:** `{ clientId: 1, workerId: 1 }` and `{ expiresAt: 1 }`.

---

## 7. Comprehensive API Documentation

All endpoints are prefixed with `/api`. Verified against backend route files.

### Authentication & Identity Routes
*Module: `/api/auth`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `POST` | `/api/auth/register` | Register new client or worker account & send OTP | Public |
| `POST` | `/api/auth/login` | Authenticate with email/password; returns JWT cookies | Public |
| `POST` | `/api/auth/send-otp` | Request a new 6-digit OTP code | Public |
| `POST` | `/api/auth/verify-otp` | Verify submitted OTP code | Public |
| `POST` | `/api/auth/forgot-password` | Send password recovery OTP email | Public |
| `POST` | `/api/auth/reset-password` | Reset account password using verified OTP | Public |
| `POST` | `/api/auth/refresh` | Exchange refresh token for fresh access token | Refresh Cookie |
| `GET` | `/api/auth/validate` | Verify access token & account status | Authenticated (Any) |
| `PATCH`| `/api/auth/change-password` | Change account password | Authenticated (Any) |
| `POST` | `/api/auth/google` | Single Sign-On using Google OAuth idToken | Public |

### User & Profile Routes
*Module: `/api/users` & `/api/auth`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `GET` | `/api/users/current/:email` | Retrieve current user profile details | Public / Verified |
| `PATCH`| `/api/users/mode` | Switch active role profile (e.g. client <-> worker)| Authenticated (Any) |
| `PUT` | `/api/users/user/:userId/profile` | Update profile details and avatar image | Authenticated (Any) |
| `PATCH`| `/api/users/:userId/skills` | Update professional skills list | Authenticated (Worker) |
| `POST` | `/api/users/:userId/addresses` | Add new home/work address with GPS coordinates | Authenticated (Client) |
| `PUT` | `/api/users/:userId/addresses/:addressId`| Edit existing saved address | Authenticated (Client) |
| `DELETE`| `/api/users/:userId/addresses/:addressId`| Remove saved address | Authenticated (Client) |

### Worker Routes
*Module: `/api/worker`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `GET` | `/api/worker/dashboard` | Fetch dashboard KPI metrics (earnings, jobs, ratings)| Authenticated (Worker) |
| `POST` | `/api/worker/slot/block-dates` | Block calendar dates and slot windows | Authenticated (Worker) |
| `GET` | `/api/worker/slot/blocked-dates` | Retrieve worker's blocked dates list | Authenticated (Worker) |
| `GET` | `/api/worker/services` | Get all assigned service jobs | Authenticated (Worker) |
| `GET` | `/api/worker/services/active` | Retrieve worker's current active ongoing service | Authenticated (Worker) |
| `GET` | `/api/worker/services/:serviceId` | Get full details of a specific service request | Authenticated (Worker) |
| `PATCH`| `/api/worker/services/:serviceId/start` | Mark service as started (`IN_PROGRESS`) | Authenticated (Worker) |
| `PATCH`| `/api/worker/services/:serviceId/complete`| Mark service as completed (`COMPLETED`) | Authenticated (Worker) |
| `GET` | `/api/worker/meetings/scheduled` | List upcoming video consultation appointments | Authenticated (Worker) |
| `GET` | `/api/worker/meetings/history` | List historical completed/missed meetings | Authenticated (Worker) |
| `GET` | `/api/worker/meetings/:serviceId` | Get meeting details by service ID | Authenticated (Worker) |

### Client & Booking Routes
*Module: `/api/client`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `GET` | `/api/client/workers` | Discover workers with geospatial/category filters | Authenticated (Client) |
| `GET` | `/api/client/workers/:id` | Get public worker profile details & portfolio | Authenticated (Client) |
| `GET` | `/api/client/workers/:id/availability` | Fetch available & booked slots for a worker | Authenticated (Client) |
| `POST` | `/api/client/services/lock-slots` | Temporarily hold slot reservations for 10 minutes | Authenticated (Client) |
| `POST` | `/api/client/services/unlock-slots` | Release held slot reservations | Authenticated (Client) |
| `POST` | `/api/client/services/book` | Create confirmed service booking | Authenticated (Client) |
| `GET` | `/api/client/services/ongoing` | Get active/in-progress service bookings | Authenticated (Client) |
| `GET` | `/api/client/services/history` | Get past service booking history | Authenticated (Client) |
| `GET` | `/api/client/services/:serviceId` | Get specific booking details | Authenticated (Client) |
| `PATCH`| `/api/client/services/:serviceId/cancel` | Cancel booking (triggers tiered refund calculation) | Authenticated (Client/Worker) |

### Meeting & Video Consultation Routes
*Module: `/api/client/meetings` & `/api/video-call`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `GET` | `/api/client/meetings/scheduled` | List upcoming client video consultations | Authenticated (Client) |
| `GET` | `/api/client/meetings/history` | List completed/past video consultations | Authenticated (Client) |
| `GET` | `/api/client/meetings/:serviceId` | Retrieve video consultation room details | Authenticated (Client) |
| `POST` | `/api/video-call/join/:serviceId` | Join video consultation room | Authenticated (Any) |
| `POST` | `/api/video-call/leave/:serviceId`| Leave video consultation room | Authenticated (Any) |
| `POST` | `/api/video-call/end/:serviceId` | End video consultation session | Authenticated (Any) |

### Payments & Wallet Routes
*Module: `/api` & `/api/wallet` & `/api/transactions`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `POST` | `/api/payment/create-order` | Generate Razorpay order for service payment | Authenticated (Client) |
| `POST` | `/api/payment/verify` | Verify Razorpay payment signature & confirm job | Authenticated (Client) |
| `POST` | `/api/payment/wallet` | Pay for service using internal wallet balance | Authenticated (Client) |
| `GET` | `/api/wallet/balance` | Get authenticated user's wallet balance | Authenticated (Any) |
| `GET` | `/api/wallet/transactions` | Get wallet ledger transactions | Authenticated (Any) |
| `POST` | `/api/wallet/recharge/create-order` | Create Razorpay order to top up wallet | Authenticated (Any) |
| `POST` | `/api/wallet/recharge/verify` | Verify wallet recharge payment & credit balance | Authenticated (Any) |
| `GET` | `/api/wallet/admin/:userId/balance` | Admin inspects any user's wallet balance | Admin Only |
| `GET` | `/api/transactions/client` | List client financial transaction ledger | Authenticated (Client) |
| `GET` | `/api/transactions/worker` | List worker earnings and payout ledger | Authenticated (Worker) |
| `GET` | `/api/transactions/admin` | Master audit ledger of all platform transactions | Authenticated (Admin) |

### Communication Routes (Chat & Notifications)
*Module: `/api/chat` & `/api/notifications`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `POST` | `/api/chat/send` | Persist and send chat message | Authenticated (Any) |
| `GET` | `/api/chat/:chatId` | Retrieve chat message history for conversation | Authenticated (Any) |
| `GET` | `/api/notifications` | Fetch unread and read push notifications | Authenticated (Any) |
| `PATCH`| `/api/notifications/:notificationId/read`| Mark notification as read | Authenticated (Any) |

### Concerns & Reviews Routes
*Module: `/api/concerns` & `/api/review`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `POST` | `/api/concerns` | Raise a support/dispute concern with image evidence | Authenticated (Any) |
| `GET` | `/api/concerns` | Retrieve my submitted concerns and status | Authenticated (Any) |
| `POST` | `/api/review/:serviceId` | Submit customer star rating and review | Authenticated (Client) |

### Media & Storage Routes
*Module: `/api/media` & `/api/upload`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `GET` | `/api/media/s3-upload-url` | Generate Presigned AWS S3 PUT URL for direct upload| Public / Authenticated |
| `POST` | `/api/upload/worker/:workerId/profile` | Upload worker profile picture | Authenticated (Worker) |
| `POST` | `/api/upload/worker/:workerId/document`| Upload worker KYC/trade document | Authenticated (Worker) |

### Admin Management & Governance Routes
*Module: `/api/admin`*

| Method | Endpoint | Description | Authentication / Roles |
|:---|:---|:---|:---|
| `GET` | `/api/admin/dashboard` | Fetch aggregated platform KPIs & revenue metrics | Admin Only |
| `GET` | `/api/admin/clients` | List all registered clients with filter & pagination | Admin Only |
| `GET` | `/api/admin/workers` | List all workers with verification status filters | Admin Only |
| `GET` | `/api/admin/users/all` | List all users across the platform | Admin Only |
| `PATCH`| `/api/admin/verify/:userId` | Approve worker KYC verification | Admin Only |
| `PATCH`| `/api/admin/reject/:userId` | Reject worker KYC verification with remarks | Admin Only |
| `PATCH`| `/api/admin/access/:userId` | Block or unblock a user account | Admin Only |
| `PATCH`| `/api/admin/suspend/:userId` | Toggle worker booking suspension | Admin Only |
| `GET` | `/api/admin/categories` | List all categories (active & inactive) | Admin Only |
| `POST` | `/api/admin/categories` | Create new service category | Admin Only |
| `PUT` | `/api/admin/categories/:id` | Edit service category details | Admin Only |
| `PATCH`| `/api/admin/categories/:id/toggle-status`| Enable / disable service category | Admin Only |
| `GET` | `/api/admin/services` | View all platform service requests | Admin Only |
| `GET` | `/api/admin/services/:serviceId` | Inspect deep details of any service | Admin Only |
| `GET` | `/api/admin/meetings/meetings` | View all scheduled and completed video meetings | Admin Only |
| `GET` | `/api/admin/meetings/meetings/:serviceId`| Inspect meeting logs and participant times | Admin Only |
| `GET` | `/api/admin/concerns` | List all customer and worker dispute tickets | Admin Only |
| `PATCH`| `/api/admin/concerns/:id/resolve` | Mark concern as resolved with resolution notes | Admin Only |
| `POST` | `/api/admin/moderation/process` | Manually trigger 15-minute moderation audit check | Admin Only |

---

## 8. Authentication, Authorization & Security

### JWT Dual-Token Rotation Strategy

Nest & Nail implements an industry-standard dual-token authentication pattern designed for security and frictionless session maintenance:

```mermaid
sequenceDiagram
    autonumber
    actor Client as User Browser
    participant Edge as Next.js Edge Middleware
    participant Backend as Express Backend (AuthRoutes)
    participant TokenSvc as JwtTokenService

    Client->>Backend: POST /api/auth/login { email, password }
    Backend->>TokenSvc: Generate Access Token (15 min) & Refresh Token (7 days)
    Backend-->>Client: Set HTTP-Only Cookies (accessToken, refreshToken)
    
    Note over Client,Edge: User navigates to protected page (/client/bookings)
    Client->>Edge: Request Page (Sends accessToken & refreshToken cookies)
    Edge->>Edge: verifyAccessToken(accessToken)
    alt Access Token is Valid
        Edge-->>Client: Allow Navigation to Page
    else Access Token Expired
        Edge->>Backend: POST /api/auth/refresh (Sends refreshToken)
        alt Refresh Token is Valid
            Backend->>TokenSvc: Issue New Access Token (15 min)
            Backend-->>Edge: Set-Cookie: fresh accessToken
            Edge-->>Client: Redirect to requested page with fresh cookie
        else Refresh Token Expired or Invalid
            Edge-->>Client: Clear Cookies & Redirect to /login
        end
    end
```

### Role-Based Access Control (RBAC) Matrix

| Resource / Route Base | Client | Worker | Admin | Unauthenticated |
|:---|:---:|:---:|:---:|:---:|
| `/client/*` | ✅ Granted | ❌ Redirected | ❌ Redirected | ❌ Redirected to `/login` |
| `/worker/*` | ❌ Redirected | ✅ Granted | ❌ Redirected | ❌ Redirected to `/login` |
| `/admin/*` | ❌ 403 Forbidden | ❌ 403 Forbidden | ✅ Granted | ❌ Redirected to `/login` |
| `/api/admin/*` | ❌ 403 Forbidden | ❌ 403 Forbidden | ✅ Allowed | ❌ 401 Unauthorized |
| `/api/client/*` | ✅ Allowed | ❌ 403 Forbidden | ✅ Allowed | ❌ 401 Unauthorized |
| `/api/worker/*` | ❌ 403 Forbidden | ✅ Allowed | ✅ Allowed | ❌ 401 Unauthorized |
| `/api/auth/login`, `/signup` | ❌ Redirected to Home | ❌ Redirected to Dashboard | ❌ Redirected to Admin | ✅ Allowed |

### Edge Middleware & Server Action Security
- **Cookie Security:** Cookies are transmitted with `httpOnly: true`, `secure: true` (in production), and `sameSite: "lax"`.
- **Server Action Protection:** Next.js Server Actions validate caller tokens and reject unauthenticated requests.
- **Role Boundary Enforcement:** Attempts by a client to access `/admin` or `/worker` trigger immediate redirection to their respective home dashboard.

---

## 9. Third-Party Integrations

```mermaid
graph LR
    subgraph NestAndNail["Nest & Nail Application"]
        Core["Application Services"]
    end

    subgraph ExternalServices["Third-Party Providers"]
        S3["AWS S3 Bucket<br/>(File Storage)"]
        Razorpay["Razorpay API<br/>(Payments)"]
        Google["Google Identity<br/>(OAuth 2.0)"]
        OSM["OpenStreetMap Nominatim<br/>(Geocoding)"]
        SMTP["Nodemailer SMTP<br/>(Email Delivery)"]
    end

    Core -->|Presigned PUT/GET URLs| S3
    Core -->|Orders & Webhook HMAC| Razorpay
    Core -->|ID Token Verification| Google
    Core -->|Reverse Coordinates| OSM
    Core -->|Transactional Emails| SMTP
```

1. **AWS S3 (`@aws-sdk/client-s3`, `@aws-sdk/s3-request-presigner`)**:
   - Generates temporary presigned PUT URLs (5-minute expiry) allowing clients to upload heavy files directly to S3 without putting load on the backend server.
   - Generates presigned GET URLs (1-hour expiry) for admins to securely view private KYC proofs and trade certificates.
2. **Razorpay Node SDK (`razorpay`)**:
   - Integrates server-side order generation and client-side modal checkout.
   - Verifies authenticity using HMAC-SHA256 signatures (`crypto.createHmac("sha256", secret).update(orderId + "|" + paymentId)`).
3. **Google Identity Services (`google-auth-library`)**:
   - Authenticates users with Google OAuth 2.0 credentials, verifying tokens securely on the backend before provisioning user accounts.
4. **Nodemailer**:
   - Transports 6-digit verification OTPs and account recovery links using secure SMTP credentials (`EMAIL_USER`, `EMAIL_PASS`).
5. **OpenStreetMap Nominatim API**:
   - Powers reverse geocoding on the Leaflet address selector to automatically convert map pin coordinates into readable street, city, state, and zip code details.

---

## 10. Project Directory Structure

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
│   │   ├── domain/                 # Layer 1: Pure Enterprise Business Logic
│   │   │   ├── entities/           # User, Worker, Service, Wallet, Payment, Review
│   │   │   ├── errors/             # DomainError, AuthenticationError, UserBlockedError
│   │   │   ├── gateways/           # IPaymentGateway contract
│   │   │   └── repositories/       # Repository interfaces (IServiceRepository, etc.)
│   │   ├── application/            # Layer 2: Application Business Logic (Use Cases)
│   │   │   ├── contracts/          # ITokenService, IEmailService, IOtpService
│   │   │   ├── dtos/               # Request/Response Data Transfer Objects
│   │   │   ├── interfaces/         # Use Case abstract contracts
│   │   │   ├── mappers/            # Domain-to-DTO entity mappers
│   │   │   └── use-cases/          # Business workflows (BookWorker, CancelService, etc.)
│   │   ├── infrastructure/         # Layer 3: External Implementations & Frameworks
│   │   │   ├── adapters/           # RazorpayGateway, S3Service, Nodemailer, Bcrypt
│   │   │   ├── database/           # Connection logic & Mongoose schemas/models
│   │   │   ├── di/                 # DIContainer, controllers.di, usecases.di, infra.di
│   │   │   ├── logger/             # Winston daily rotating logger implementation
│   │   │   ├── repo/               # Mongoose repository implementations
│   │   │   └── socket/             # Socket.io handlers (Chat, VideoCall, Presence)
│   │   ├── presentation/           # Layer 4: Driving Adapters (HTTP / REST)
│   │   │   ├── controllers/        # Express controllers (Client, Worker, Admin)
│   │   │   ├── middlewares/        # AuthMiddleware, ErrorHandler, RequestLogger, Multer
│   │   │   └── routes/             # Route declarations grouped by domain
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
    │   │   ├── layout.tsx          # Root HTML layout with context providers
    │   │   └── globals.css         # Tailwind CSS v4 styling rules
    │   ├── components/             # Reusable UI component library
    │   │   ├── containers/         # Responsive Navbars, Sidebars, Footers
    │   │   ├── modals/             # BookingModal, AddressModal, ReviewModal
    │   │   └── ui/                 # Buttons, Dialogs, Badges, Inputs
    │   ├── lib/                    # Helper libraries and validation schemas
    │   ├── shared/                 # Monorepo shared enums, types, and mappers
    │   ├── sources/                # Axios API clients & route definitions
    │   ├── store/                  # Zustand stores (useUserStore with persistence)
    │   └── utils/                  # Razorpay script loader, date-time formatters
    └── public/                     # Static media assets, icons, and illustrations
```

---

## 11. Installation & Local Development Setup

### Prerequisites
- **Node.js:** `v20.19.0` or higher
- **Package Manager:** `pnpm` (v9 or higher recommended)
  ```bash
  npm install -g pnpm
  ```
- **Database:** Local MongoDB instance or active MongoDB Atlas cluster URI
- **AWS S3 Bucket:** Configured bucket with CORS enabled for Presigned URLs
- **Razorpay Account:** Test Mode API Key & Secret for payment processing

### Step-by-Step Installation

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/nest-and-nail.git
   cd "Nest & Nail"
   ```

2. **Install Workspace Dependencies:**
   Install dependencies across both backend and frontend in a single step using PNPM:
   ```bash
   pnpm install
   ```

3. **Configure Environment Variables:**
   Create `.env` in the `backend/` directory and `.env.local` in the `frontend/` directory following the tables in Section 12.

4. **Start Development Servers:**
   Run both the Next.js frontend and Express backend concurrently from the root directory:
   ```bash
   pnpm run dev
   ```
   *Alternatively, start them in dedicated terminals:*
   ```bash
   # Terminal 1: Backend API (Port 4000)
   cd backend
   pnpm run dev

   # Terminal 2: Next.js Frontend (Port 3000)
   cd frontend
   pnpm run dev
   ```

5. **Access the Application:**
   - **Frontend Web Portal:** [http://localhost:3000](http://localhost:3000)
   - **Backend REST API:** [http://localhost:4000](http://localhost:4000)

---

## 12. Environment Variable Configuration

### Backend Environment Variables (`backend/.env`)

| Variable | Purpose | Required | Example Placeholder |
|:---|:---|:---:|:---|
| `PORT` | Express server port | Yes | `4000` |
| `NODE_ENV` | Runtime environment mode | Yes | `development` / `production` |
| `MONGO_URI` | MongoDB connection string | Yes | `mongodb+srv://user:pass@cluster.mongodb.net/nest_nail` |
| `FRONTEND_URL` | Client origin for CORS | Yes | `http://localhost:3000` |
| `ACCESS_TOKEN_SECRET` | Secret key for signing access tokens | Yes | `your_access_token_secret_here` |
| `REFRESH_TOKEN_SECRET`| Secret key for signing refresh tokens | Yes | `your_refresh_token_secret_here` |
| `ACCESS_TOKEN_MAX_AGE`| Access token lifetime in seconds | Yes | `900` *(15 minutes)* |
| `REFRESH_TOKEN_MAX_AGE`| Refresh token lifetime in seconds | Yes | `604800` *(7 days)* |
| `GOOGLE_CLIENT_ID` | Google OAuth Client ID | Yes | `your-id.apps.googleusercontent.com` |
| `GOOGLE_CLIENT_SECRET`| Google OAuth Client Secret | Yes | `your-google-oauth-secret` |
| `EMAIL_USER` | SMTP email address for sending OTPs | Yes | `your-email@gmail.com` |
| `EMAIL_PASS` | App password for SMTP account | Yes | `your-app-password` |
| `AWS_REGION` | AWS S3 bucket region | Yes | `ap-south-1` |
| `AWS_BUCKET_NAME` | AWS S3 bucket name | Yes | `nest-and-nail-storage` |
| `AWS_ACCESS_KEY_ID` | AWS IAM Access Key ID | Yes | `AKIAIOSFODNN7EXAMPLE` |
| `AWS_SECRET_ACCESS_KEY`| AWS IAM Secret Access Key | Yes | `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY` |
| `RAZORPAY_KEY` | Razorpay Key ID | Yes | `rzp_test_xxxxxxxxxx` |
| `RAZORPAY_SECRET` | Razorpay Key Secret | Yes | `your_razorpay_secret` |
| `LOG_RETENTION_DAYS` | Daily rotated log retention limit | No | `14` |

### Frontend Environment Variables (`frontend/.env.local`)

| Variable | Purpose | Required | Example Placeholder |
|:---|:---|:---:|:---|
| `NEXT_PUBLIC_FRONTEND_URL` | Base public URL of frontend | Yes | `http://localhost:3000` |
| `NEXT_PUBLIC_API_URL` | Base URL of Express backend API | Yes | `http://localhost:4000` |
| `NEXT_PUBLIC_ACCESS_TOKEN_SECRET`| Shared secret for edge validation | Yes | `your_access_token_secret_here` |
| `NEXT_PUBLIC_REFRESH_TOKEN_SECRET`| Shared secret for edge validation | Yes | `your_refresh_token_secret_here` |
| `NEXT_PUBLIC_GOOGLE_CLIENT_ID` | Public Google OAuth Client ID | Yes | `your-id.apps.googleusercontent.com` |
| `NEXT_PUBLIC_RAZORPAY_KEY` | Public Razorpay Key ID for Checkout | Yes | `rzp_test_xxxxxxxxxx` |

---

## 13. Production Deployment Architecture

```mermaid
graph TB
    subgraph Internet["Public Internet"]
        Users["Web Users / Mobile Browsers"]
    end

    subgraph AWSCloud["AWS Production VPC"]
        subgraph EC2["AWS EC2 Instance (Ubuntu 22.04 LTS)"]
            Nginx["Nginx Reverse Proxy & SSL Termination<br/>(Let's Encrypt Certbot)"]
            
            subgraph PM2Manager["PM2 Process Manager"]
                FrontendApp["Next.js SSR App<br/>(Cluster Mode, Port 3000)"]
                BackendApp["Express Clean Architecture API<br/>(Cluster Mode, Port 4000)"]
            end
        end

        subgraph ManagedCloud["Managed Cloud Services"]
            MongoAtlas[("MongoDB Atlas<br/>Multi-AZ Replica Set")]
            S3Storage["AWS S3 Bucket<br/>(Private Assets with Presigned URLs)"]
        end
    end

    Users -->|HTTPS / WSS (Port 443)| Nginx
    Nginx -->|Proxy Pass /| FrontendApp
    Nginx -->|Proxy Pass /api| BackendApp
    Nginx -->|Upgrade WebSocket /socket.io| BackendApp

    BackendApp <--> MongoAtlas
    BackendApp <--> S3Storage
```

### Production Build & Launch Workflow

1. **Backend Build & Production Run:**
   ```bash
   cd backend
   pnpm run build     # Compiles TypeScript to dist/
   pnpm run start     # Starts node dist/index.js
   ```

2. **Frontend Build & Production Run:**
   ```bash
   cd frontend
   pnpm run build     # Generates optimized Next.js production bundle
   pnpm run start     # Starts Next.js production server
   ```

3. **Process Supervision (PM2 Example):**
   ```bash
   pm2 start "node dist/index.js" --name "nest-backend" --cwd "./backend"
   pm2 start "pnpm run start" --name "nest-frontend" --cwd "./frontend"
   pm2 save
   ```

---

## 14. Error Handling, Logging & Reliability

### Centralized Exception Handling
The platform implements a unified error-handling pipeline that maps domain exceptions directly to structured HTTP status codes:

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

## 15. Roadmap & Future Improvements

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

## 16. Contributing & License

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
