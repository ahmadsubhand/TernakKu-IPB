<p align="center">
  <img src="../assets/logo.png" alt="TernakKu Logo" width="180">
</p>

<p align="center">
  <img src="../assets/icon/typescript.svg" alt="TypeScript" height="20" />
  &nbsp;&nbsp;
  <img src="../assets/icon/nestjs.svg" alt="NestJS" height="20" />
  &nbsp;&nbsp;
  <img src="../assets/icon/mysql.svg" alt="MySQL" height="20" />
  &nbsp;&nbsp;
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="../assets/icon/prisma-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="../assets/icon/prisma.svg" />
    <img src="../assets/icon/prisma.svg" alt="Prisma" height="20" />
  </picture>
  &nbsp;&nbsp;
  <img src="../assets/icon/zod.svg" alt="Zod" height="20" />
  &nbsp;&nbsp;
  <img src="../assets/icon/dayjs.png" alt="Day.js" height="20" />
</p>

The backend of **TernakKu** is a REST API built with NestJS, TypeScript, MySQL, and Prisma ORM. It powers the Flutter mobile application with secure authentication, farm management, and livestock tracking, using Zod for data validation and Day.js for date and time handling.

## 🛠️ Prerequisites

Make sure the following tools and services are available before getting started:

- **Node.js** — a version compatible with the project.
- **npm** — for dependency management.
- **MySQL** — for the application database.
- **Git** — for cloning the repository.

## 🚀 Installation & Setup

### 1. Clone the Repository

Clone the repository and navigate to the backend directory:

```bash
git clone https://github.com/ahmadsubhand/TernakKu-IPB
cd backend
```

If you have already cloned the unified repository, navigate directly to the `backend` folder.

### 2. Install Dependencies

Install the project dependencies:

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the backend root directory, alongside `package.json`, using `.env.example` as a reference.

```bash
cp .env.example .env
```

On Windows Command Prompt, you can use:

```dos
copy .env.example .env
```

Open `.env` and configure all required variables:

```dotenv
PORT=3000
NODE_ENV=development
BASE_URL=http://localhost:3000
CLIENT_URL=http://localhost:3000
APP_NAME=TernakKu

# Database
DATABASE_URL="mysql://root:@localhost:3306/ternakku"
DATABASE_HOST=localhost
DATABASE_PORT=3306
DATABASE_USER=root
DATABASE_PASSWORD=
DATABASE_NAME=ternakku

# JWT
JWT_SECRET="your-super-secure-jwt-secret"
ACCESS_TOKEN_EXPIRATION="15m"
REFRESH_TOKEN_EXPIRATION="28d"

# Mailer
MAILER_USER="email@gmail.com"
MAILER_PASSWORD="abcd efgh ijkl mnop"

# Admin Seeder
ADMIN_USERNAME="admin"
ADMIN_EMAIL="adminternakku@gmail.com"
ADMIN_PASSWORD="1234Asd!"
```

Replace placeholder values with your actual configuration. Do not leave sensitive keys empty.

#### Environment Variables Breakdown

| Variable | Description |
|---|---|
| `PORT` | Port used by the backend server. |
| `NODE_ENV` | Application environment (`development` or `production`). |
| `BASE_URL` & `CLIENT_URL` | Base URLs for application routing and client communication. |
| `DATABASE_URL` | Prisma connection string format for MySQL. |
| `JWT_SECRET` | Secret key used for signing JWT access and refresh tokens. |
| `ACCESS_TOKEN_EXPIRATION` & `REFRESH_TOKEN_EXPIRATION` | Lifespan duration for authentication tokens. |
| `MAILER_USER` & `MAILER_PASSWORD` | SMTP credentials (e.g., Gmail account and App Password) for system emails. |
| `ADMIN_*` | Initial admin credentials automatically provisioned by the database seeder. |

Generate a strong cryptographic secret for `JWT_SECRET`. For example, using Node.js:

```bash
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

#### Database Configuration

Install and start MySQL, then create a database named `ternakku` if it does not already exist:

```sql
CREATE DATABASE ternakku;
```

Configure `DATABASE_URL` using the connection string format:

```text
mysql://username:password@host:port/database_name
```

Replace `username`, `password`, `host`, `port`, and `database_name` with your local MySQL credentials. If your password contains special characters, URL-encode them appropriately.

### 4. Set Up Prisma & Database Migrations

Prisma manages the database schema, migrations, and client generation.

First, generate the Prisma Client:

```bash
npx prisma generate
```

Apply the database migrations:

```bash
npx prisma migrate dev
```

To inspect and manage database records visually through a browser interface, run:

```bash
npx prisma studio
```

### 5. Run the Backend

Start the development server with live-reloading:

```bash
npm run start:dev
```

The API will be available at:

```text
http://localhost:3000
```

The actual port depends on the `PORT` value in `.env`.

To build the application for production:

```bash
npm run build
```

To start the compiled production server:

```bash
npm run start:prod
```

## 📁 Project Structure

```text
backend/
├── dist/                 # Compiled application output
├── docs/                 # Project specification and documentation
├── node_modules/         # Installed dependencies
├── prisma/
│   ├── migrations/       # Database migration history
│   └── schema.prisma     # Database schema and models
├── public/               # Static assets
├── src/
│   ├── common/           # Shared components and utilities
│   ├── generated/        # Generated prisma client
│   ├── modules/          # Feature modules and business logic
│   │   └── livestock/
│   │       ├── livestock.controller.ts     # API endpoints
│   │       ├── livestock.model.d.ts        # Type declarations
│   │       ├── livestock.module.ts         # Feature module
│   │       ├── livestock.service.ts        # Business logic
│   │       └── livestock.validation.ts     # Input validation
│   ├── types/            # Shared TypeScript types
│   ├── utils/            # Utility functions
│   ├── validator/        # Shared validation logic
│   ├── app.controller.ts # Root application controller
│   ├── app.module.ts     # Root application module
│   └── main.ts           # Application entry point
├── templates/            # Email templates
├── test/                 # Automated tests
├── .env                  # Local environment variables
├── .env.example          # Environment variable template
├── .gitignore            # Git ignore rules
├── .prettierrc           # Prettier configuration
├── eslint.config.mjs     # ESLint configuration
├── nest-cli.json         # NestJS CLI configuration
└── package-lock.json     # Locked npm dependency versions
├── package.json          # Project metadata and npm scripts
├── prisma.config.ts      # Prisma configuration
├── README.md             # Backend documentation
├── tsconfig.build.json   # TypeScript build configuration
└── tsconfig.json         # TypeScript compiler configuration
```

**Notes:**
- Configure environment variables in `.env` using `.env.example` as a reference.
- `dist/`,  `node_modules/`, and `src/generated/prisma/` are generated locally and should not be committed to version control.
- Database schema changes are managed through Prisma migrations.

## 🔐 Security Notes

- Never commit `.env` or expose credentials, API secrets, JWT secrets, or Gmail App Passwords.
- Keep `.env.example` populated with placeholder values only.
- Use strong, unique secrets for `JWT_SECRET`.
- Use production-specific environment variables and database credentials when deploying the application.
- Run production migrations using `npx prisma migrate deploy` rather than using development migration commands.

## 📚 Related Documentation

- [Software Design Document (SDD)](./docs/sdd.md) — Use case diagram, activity diagram, and entity relationship diagram (ERD).
- [Admin Postman Collection](./docs/Admin.postman_collection.json) — API requests for admin endpoints.
- [User Postman Collection](./docs/User.postman_collection.json) — API requests for user endpoints.
- [NestJS Documentation](https://docs.nestjs.com/)
- [Prisma Documentation](https://www.prisma.io/docs)
- [MySQL Documentation](https://dev.mysql.com/doc/)