# File Explorer Project

This project consists of a frontend application (Vue 3) and a backend service (Elysia js) for file exploration. The system uses PostgreSQL for database storage and MinIO for object storage.

## Prerequisites

Before you begin, ensure you have the following installed:
- Docker and Docker Compose
- Node.js (recommended version 16 or higher)
- bun package manager

## Project Structure

```
.
├── fe-file-explorer/     # Frontend Vue 3 application (Git submodule)
├── svc-file-explorer/    # Backend Elysia js service (Git submodule)
└── docker-compose.yml    # Docker composition file
```

## Getting Started

### Clone with Submodules

To clone the repository with all submodules:

```bash
# Clone the main repository with submodules
git clone --recursive <repository-url>
cd file-explorer-test

# If you've already cloned without submodules, run:
git submodule update --init --recursive
```

### Update Submodules

To update all submodules to their latest commits:

```bash
git submodule update --remote
```

## Environment Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd file-explorer-test
```

2. Create `.env` file in the root directory with the following variables:
```env
# Database Configuration
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=file_explorer
DATABASE_URL=postgresql://postgres:postgres@db:5432/file_explorer?schema=public

# Backend Configuration
NODE_ENV=production

# Ports
FRONTEND_PORT=8080
BACKEND_PORT=3000
DB_PORT=5432

# MinIO Configuration
MINIO_ENDPOINT=play.min.io
MINIO_PORT=443
MINIO_USE_SSL=true
MINIO_ACCESS_KEY=Q3AM3UQ867SPQQA43P2F
MINIO_SECRET_KEY=zuf+tfteSlswRu7BJ86wekitnifILbZam1KYY3TG
MINIO_BUCKET_NAME=file-explorer-bucket

# MinIO Server Configuration
MINIO_ROOT_USER=minioadmin
MINIO_ROOT_PASSWORD=minioadmin 
```

## Installation & Running

### Using Docker (Recommended)

1. Build and start all services:
```bash
docker-compose up --build
```

This will start:
- Frontend at http://localhost:4200
- Backend API at http://localhost:3000
- MinIO Console at http://localhost:9001
- PostgreSQL at localhost:5433

### Manual Setup (Development)

#### Frontend Setup
1. Navigate to frontend directory:
```bash
cd fe-file-explorer
```

2. Install dependencies:
```bash
bun install
```

3. Run development server:
```bash
bun run dev
```

#### Backend Setup
1. Navigate to backend directory:
```bash
cd svc-file-explorer
```

2. Install dependencies:
```bash
bun install
```

3. Run development server:
```bash
bun run src/infrastructure/server/ElysiaServer.ts
```

## Services

- **Frontend (fe-file-explorer)**
  - Vue 3 application
  - Runs on port 4200
  - Provides user interface for file exploler

- **Backend (svc-file-explorer)**
  - ElysiaJS service
  - Runs on port 3000
  - Handles file operations and business logic

- **PostgreSQL Database**
  - Runs on port 5433
  - Stores file metadata and user information

- **MinIO Object Storage**
  - API runs on port 9000
  - Console runs on port 9001
  - Stores actual file data

## Development Notes

- The frontend and backend can be developed independently using their respective development servers
- Docker Compose is configured for production-like environment
- MinIO console credentials: minioadmin/minioadmin (default)

## Troubleshooting

1. If services fail to start, ensure no other applications are using the specified ports
2. For database connection issues, verify PostgreSQL is running and credentials are correct
3. For MinIO issues, ensure the bucket exists and credentials are properly configured

## Additional Resources

- [Vue 3 Documentation](https://vuejs.org/)
- [Bun Documentation](https://bun.sh/)
- [MinIO Documentation](https://min.io/docs/minio/container/index.html)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/) 