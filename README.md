# SocialSphere 🌐

A full-stack social media web application with React frontend and Spring Boot backend, organized using git submodules.

## Project Structure

This repository contains two main components as git submodules:

```
SocialSphere/
├── frontend/          # React + TypeScript + Vite frontend
├── backend/           # Spring Boot backend
├── README.md          # This file
└── .gitmodules        # Git submodule configuration
```

## Submodules

- **Frontend**: [SocialSphere-frontend](https://github.com/CodeBrosLab/SocialSphere-frontend.git) - React + TypeScript + Vite application
- **Backend**: [SocialSphere-backend](https://github.com/CodeBrosLab/SocialSphere-backend.git) - Spring Boot application with PostgreSQL

## Quick Start

### Clone the Repository with Submodules

```bash
# Clone the main repository and all submodules
git clone --recursive https://github.com/CodeBrosLab/SocialSphere.git

# Or if you already cloned without --recursive:
git clone https://github.com/CodeBrosLab/SocialSphere.git
cd SocialSphere
git submodule update --init --recursive
```

### Development Setup

#### Option 1: Using Docker Compose (Recommended)

The easiest way to run the entire application is using Docker Compose:

```bash
# Start all services (database, backend, frontend)
docker-compose up -d

# View logs for all services
docker-compose logs -f

# View logs for specific service
docker-compose logs -f backend
docker-compose logs -f frontend
docker-compose logs -f db

# Stop all services
docker-compose down

# Stop and remove volumes (clears database data)
docker-compose down -v
```

**Service URLs:**
- Frontend: http://localhost:5173
- Backend API: http://localhost:8080
- Database: localhost:5432

#### Option 2: Manual Setup

##### Backend Setup
```bash
cd backend
# Follow the backend README for setup instructions
# Typically:
mvn clean package -DskipTests
docker-compose up -d
```

##### Frontend Setup
```bash
cd frontend
# Follow the frontend README for setup instructions
# Typically:
npm install
npm run dev
```

### Working with Submodules

#### Updating Submodules
```bash
# Update all submodules to latest commits
git submodule update --remote

# Update specific submodule
git submodule update --remote frontend
git submodule update --remote backend
```

#### Making Changes to Submodules
```bash
# Navigate to the submodule directory
cd frontend  # or backend

# Make your changes and commit as normal
git add .
git commit -m "Your commit message"
git push origin main

# Return to main repository and commit the submodule reference update
cd ..
git add frontend  # or backend
git commit -m "Update frontend submodule"
git push origin main
```

#### Pulling Latest Changes
```bash
# Pull changes in main repository
git pull origin main

# Update submodules to match the committed references
git submodule update --recursive
```

## Technology Stack

### Frontend
- **Framework**: React 18
- **Language**: TypeScript
- **Build Tool**: Vite
- **Styling**: CSS/SCSS
- **Deployment**: Vercel

### Backend
- **Framework**: Spring Boot
- **Language**: Java 17+
- **Database**: PostgreSQL
- **Security**: Spring Security with JWT
- **Build Tool**: Maven
- **Containerization**: Docker
- **Deployment**: Fly.io

### Development & Deployment
- **Orchestration**: Docker Compose
- **Database**: PostgreSQL 16 with persistent volumes
- **Networking**: Custom Docker network for service communication
- **Health Checks**: Automated service health monitoring

## Features

### Authentication & Security
- JWT Authentication with secure signup and login
- Password encryption using Spring Security
- Role-based access control (User, Admin)

### Social Features
- User profile creation and management
- Create, edit, and delete posts
- Comment on posts
- Follow and unfollow users

### Technical Features
- Responsive web design
- RESTful API architecture
- Container-based deployment
- Database persistence with JPA

## Development Workflow

1. **Starting Development**: Clone with `--recursive` flag to get all submodules
2. **Running the App**: Use `docker-compose up -d` for full-stack development
3. **Making Changes**: Work in individual submodule directories (hot reload enabled)
4. **Committing**: Commit changes in submodule first, then update main repository
5. **Collaboration**: Use `git submodule update --remote` to get latest changes

## Docker Compose Features

- **Multi-service orchestration**: Database, backend, and frontend services
- **Health checks**: Automatic service dependency management
- **Hot reload**: Frontend and backend support live code changes
- **Persistent data**: PostgreSQL data persists between container restarts
- **Network isolation**: Services communicate through dedicated Docker network
- **Environment configuration**: Production-ready environment variable setup

## Troubleshooting

### Common Docker Issues

**Port conflicts:**
```bash
# If ports are already in use, stop conflicting services or modify docker-compose.yml
docker-compose down
lsof -ti:5173,8080,5432 | xargs kill -9  # Kill processes on these ports
```

**Database connection issues:**
```bash
# Reset database and volumes
docker-compose down -v
docker-compose up -d
```

**Submodule updates not reflecting:**
```bash
# Rebuild containers after submodule updates
docker-compose down
docker-compose build --no-cache
docker-compose up -d
```

## Contributors

- [Dimitris Sparagis](https://github.com/dimsparagis0210)
- [Thanos Moschou](https://github.com/thanosmoschou)
- [Andreas Hadjiantonis](https://github.com/andreas-hadjiantonis)

## License

This project is licensed under the MIT License - see the individual component repositories for details.

## Links

- [Frontend Repository](https://github.com/CodeBrosLab/SocialSphere-frontend)
- [Backend Repository](https://github.com/CodeBrosLab/SocialSphere-backend)
- [Organization](https://github.com/CodeBrosLab)