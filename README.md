<p align="center">
  <img src="assets/logo.png" alt="TernakKu Logo" width="180" />
</p>

<p align="center">
  <em>A digital livestock management system to streamline farm operations, maintain livestock records, and monitor animal health.</em>
</p>

<p align="center">
  <img src="assets/icon/flutter.svg" alt="Flutter" height="20" />
  &nbsp;&nbsp;
  <img src="assets/icon/dart.svg" alt="Dart" height="20" />
  &nbsp;&nbsp;
  <img src="assets/icon/riverpod.png" alt="Riverpod" height="20" />
  &nbsp;&nbsp;
  <img src="assets/icon/nestjs.svg" alt="NestJS" height="20" />
  &nbsp;&nbsp;
  <img src="assets/icon/typescript.svg" alt="TypeScript" height="20" />
  &nbsp;&nbsp;
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/icon/prisma-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="assets/icon/prisma.svg" />
    <img src="assets/icon/prisma.svg" alt="Prisma" height="20" />
  </picture>
  &nbsp;&nbsp;
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/icon/mysql-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="assets/icon/mysql.svg" />
    <img src="assets/icon/mysql.svg" alt="mysql" height="20" />
  </picture>
</p>

## 🌟 Core Features

- **Unified Livestock Inventory & Pedigree Tracking:** Centralizes individual animal profiles, lineage tracking, and key physiological data into an easily searchable database.
- **Real-Time Daily Operational Logs:** Instantly documents critical farm events—including births, illnesses, treatments, and mortality—reducing data fragmentation.
- **Vaccination & Veterinary Medical History:** Manages automated scheduling and tracking of veterinary interventions to ensure compliance and proactive herd health.
- **Flexible Custom Categorization Engine:** Empowers farmers to define custom record-keeping categories tailored to specific livestock breeds and farm operational models.

## 🚀 Key Highlights & Engineering Focus

Designed to digitize livestock management workflows, **TernakKu** showcases end-to-end full-stack development and robust system design:

- **100% Cross-Platform Consistency:** Built with a reactive Flutter client communicating seamlessly with a modular NestJS API.
- **Absolute Type Safety:** Strict static typing enforced across the backend and database boundaries using **TypeScript**, **Prisma**, and **Zod**.
- **Resilient Mobile State Management:** Utilizes **Riverpod** for reactive, testable state management combined with **GoRouter** for declarative deep-link handling.
- **Secure Token Architecture:** Implements encrypted local persistence via `flutter_secure_storage` paired with stateless **JWT** authentication and rate-limiting on sensitive API endpoints.
- **Zero-Redundancy Database Design:** Leverages ACID-compliant relational schemas via Prisma to handle complex parent-offspring pedigree trees and relational medical logs reliably.

## 🛠️ Technology Stack & Architectural Rationale

TernakKu separates the mobile client from its backend API, allowing the application interface, business logic, and persistent data to be managed independently.

### 📱 Mobile Application

- [**Flutter**](https://flutter.dev/): Selected for its high-performance native rendering engine and single-codebase cross-platform deployment.
- [**Riverpod**](https://riverpod.dev/): Delivers compile-safe, robust dependency injection and reactive state management without BuildContext coupling.
- [**GoRouter**](https://pub.dev/packages/go_router): Provides declarative routing, deep-linking support, and secure redirect guards based on authentication states.
- [**Dio**](https://pub.dev/packages/dio): Advanced HTTP client featuring robust interceptors for automated token injection, error handling, and request retries.
- [**Flutter Secure Storage**](https://pub.dev/packages/flutter_secure_storage): Secures sensitive user credentials and session tokens using hardware-backed platform keystores.

### ⚙️ Backend

- [**NestJS**](https://nestjs.com/): Enforces modular architecture and enterprise-grade Object-Oriented Programming (OOP) patterns with native TypeScript support and robust Dependency Injection.
- [**Prisma ORM**](https://www.prisma.io/): Type-safe database toolkit providing autocompletion, bulletproof migration workflows, and automated query sanitization.
- [**MySQL**](https://www.mysql.com/): A fast, reliable, and robust relational database management system capable of handling complex transactional queries for herd tracking.
- [**Zod**](https://zod.dev/): Powers runtime data validation on API payloads, ensuring ironclad data integrity from client inputs down to database persistence.
- [**Day.js**](https://day.js.org/): Lightweight utility for parsing, formatting, and synchronizing timestamps across vaccination schedules and daily logs.

## 🔒 Security Implementation

Security was prioritized at every tier of TernakKu’s architecture:

1. **API Rate Limiting:** Protects authentication endpoints and resource-heavy queries against brute-force attacks and traffic spikes.
2. **Cryptographic Password Hashing:** Secures user credentials using adaptive `bcrypt` password hashing routines.
3. **Stateless JWT Authentication:** Issues securely signed JSON Web Tokens for authorized micro-interactions across protected routes.
4. **Encrypted Client Storage:** Sensitive session identifiers are stored inside device-level secure enclaves (`flutter_secure_storage`) rather than vulnerable plain-text local storage.
5. **Strict DTO Validation & Sanitization:** Incoming client payloads are validated at the API boundary using Zod schemas, while Prisma ORM neutralizes SQL injection vectors by design.

## 📦 Installation & Project Structure

TernakKu consists of two independent applications: a Flutter mobile client and a NestJS backend API. Each component has its own dependencies, configuration, and development workflow.

### 🚀 Getting Started

To install, configure, and run the application locally, follow the README in each directory:

- **[Mobile Readme](./mobile/README.md):** Contains the Flutter application source code, mobile dependencies, and platform-specific configuration.
- **[Backend API Repository](./backend//README.md):** Contains the NestJS backend, Prisma schema, database configuration, and API implementation.

To run the complete application locally, configure and start the backend API and database first, then configure the mobile application to communicate with the API.

### 📁 Repository Structure

```text
TernakKu-IPB/
├── mobile/                  # Flutter mobile application
│   ├── lib/                 # App source code (providers, views, models)
│   ├── assets/              # Images and logo
│   ├── pubspec.yaml         # Flutter dependencies
│   └── README.md            # Mobile app setup and configuration
│
├── backend/                 # NestJS API server
│   ├── prisma/              # Database schema and migration history
│   ├── src/                 # Application modules, controllers, and services
│   ├── package.json         # Backend dependencies & scripts
│   └── README.md            # Backend setup and configuration
│
└── README.md                # Project documentation
```

The directory trees above highlight the main project directories. Refer to each application's README for its detailed source-code organization and configuration requirements.

## 📚 Related Documentation

- [Flutter Documentation](https://docs.flutter.dev/)
- [Riverpod Documentation](https://riverpod.dev/docs/introduction/getting_started)
- [NestJS Documentation](https://docs.nestjs.com/)
- [Prisma Documentation](https://www.prisma.io/docs)

## 🖥️ Screenshots

### 1. Home

![Home](./assets/screenshots/home.png)

### 2. Livestock Inventory

![Livestock Inventory](./assets/screenshots/inventaris-ternak.png)

### 3. Daily Records

![Daily Records](./assets/screenshots/catatan-harian.png)

### 4. Vaccination History

![Vaccination History](./assets/screenshots/riwayat-vaksinasi.png)
