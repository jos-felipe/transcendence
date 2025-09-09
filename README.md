# ft_transcendence

A comprehensive web application for the 42 School ft_transcendence project, featuring a Pong tournament system with real-time gameplay, user management, and tournament organization.

## 🏗️ Project Structure

```
transcendence/
├── server/code/backend-fastify/     # Fastify backend with SQLite database
│   ├── src/
│   │   ├── database/               # Database layer
│   │   │   ├── config.js          # Database configuration
│   │   │   ├── connection.js      # SQLite connection management
│   │   │   ├── schema.sql         # Database schema definition
│   │   │   ├── migrations.js      # Database migration script
│   │   │   ├── queries.js         # Database query methods
│   │   │   └── test-connection.js # Database connectivity tests
│   │   ├── plugins/
│   │   │   └── database.js        # Fastify database plugin
│   │   └── utils/
│   │       └── auth.js            # Authentication utilities
│   ├── server.js                  # Main server entry point
│   └── package.json               # Backend dependencies
├── srcs/front-end/                # Frontend application
├── database/                      # Database Docker configuration
├── infrastructure/               # Docker compose and infrastructure
└── documentation/                # Project documentation
```

## 🚀 Getting Started

### Prerequisites

- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **SQLite3** (automatically installed with dependencies)

### Backend Setup

1. **Navigate to the backend directory:**
   ```bash
   cd server/code/backend-fastify
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up the database:**
   ```bash
   npm run db:migrate
   ```

4. **Test database connection:**
   ```bash
   npm run test:db
   ```

5. **Start the backend server:**
   ```bash
   npm start
   ```

   The server will be available at `http://localhost:3000`

### Frontend Setup

1. **Navigate to the frontend directory:**
   ```bash
   cd srcs/front-end
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm run dev
   ```

## 🗄️ Database

The application uses **SQLite** for data persistence with a comprehensive schema supporting:

### Database Schema

- **users**: User accounts with secure password hashing
- **tournaments**: Tournament management and organization  
- **tournament_participants**: Tournament participation tracking
- **games**: Individual game sessions and results
- **match_history**: Player match history and statistics

### Database Commands

```bash
# Run database migrations
npm run db:migrate

# Test database connection
npm run test:db

# Run all tests
npm test

# Run linting
npm run lint
```

## 🔌 API Endpoints

### Core Endpoints
- `GET /` - Health check: `{"hello":"world","database":"connected"}`
- `GET /health` - Server health check with runtime info
- `GET /api/health/db` - Database health check with user count

### User Management
- `POST /api/users/register` - Register a new user
  ```json
  {
    "username": "player1",
    "email": "player1@example.com", 
    "password": "securepassword"
  }
  ```

### Tournament Management
- `POST /api/tournaments` - Create a new tournament
  ```json
  {
    "name": "Championship 2025",
    "maxParticipants": 8
  }
  ```
- `GET /api/tournaments` - List all tournaments

## 🧪 Testing the Backend

### Basic Health Check
```bash
curl http://localhost:3000
```

Expected response:
```json
{"hello":"world","database":"connected"}
```

### Database Health Check
```bash
curl http://localhost:3000/api/health/db
```

### User Registration Test
```bash
curl -X POST http://localhost:3000/api/users/register \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","email":"test@example.com","password":"password123"}'
```

### Tournament Creation Test
```bash
curl -X POST http://localhost:3000/api/tournaments \
  -H "Content-Type: application/json" \
  -d '{"name":"Test Tournament","maxParticipants":8}'
```

## 🔐 Security Features

- **Password Security**: Bcrypt hashing with 12 salt rounds
- **Input Validation**: Username, email, and password validation
- **SQL Injection Prevention**: Parameterized queries for all database operations
- **XSS Protection**: Input sanitization and validation

## 🛠️ Development

### Backend Development
The backend follows Fastify plugin architecture with:

- **Database Plugin**: Decorates Fastify instance with database connection and queries
- **Modular Structure**: Organized codebase with separation of concerns
- **Error Handling**: Comprehensive error handling for database operations
- **Resource Management**: Proper SQLite statement lifecycle management

### Available Scripts (Backend)

```bash
npm start          # Start the production server
npm run dev        # Start the development server
npm test           # Run database connection tests
npm run db:migrate # Run database migrations
npm run test:db    # Test database connectivity
npm run lint       # Run linting checks
```

### Frontend Development
Navigate to `srcs/front-end/` and refer to the frontend README for specific setup instructions.

## 🐳 Docker Support

The project includes Docker configuration for containerized deployment:

- **Backend**: Configured in `server/Dockerfile`
- **Database**: Configured in `database/Dockerfile`
- **Infrastructure**: Docker Compose setup in `infrastructure/docker-compose.yml`

## 📁 Key Files

- **`server/code/backend-fastify/server.js`** - Main Fastify server with API routes
- **`server/code/backend-fastify/src/database/schema.sql`** - Complete database schema
- **`server/code/backend-fastify/src/plugins/database.js`** - Database plugin for Fastify
- **`server/code/backend-fastify/src/utils/auth.js`** - Authentication and validation utilities

## 🎮 Features

- **User Registration & Authentication**: Secure user account management
- **Tournament System**: Create and manage Pong tournaments
- **Game Tracking**: Record game results and maintain match history
- **Real-time Gameplay**: Interactive Pong game implementation
- **Responsive Design**: Modern frontend with mobile support
- **Database Persistence**: Reliable SQLite data storage

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Run tests (`npm test`)
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

## 📝 License

This project is part of the 42 School curriculum for the ft_transcendence project.

---

**Quick Start for Newcomers:**
```bash
# Clone the repository
git clone <repository-url>
cd transcendence

# Set up backend
cd server/code/backend-fastify
npm install
npm run db:migrate
npm start

# In another terminal, set up frontend
cd srcs/front-end
npm install
npm run dev
```

The backend will be running on `http://localhost:3000` and the frontend on the port specified by the frontend development server.
