# System Architecture

## Overview

Habit Tracker AI is a distributed full-stack application with three main services:
- **Frontend**: React-based SPA
- **Backend**: Node.js/Express REST API
- **AI Service**: Python Flask microservice

## System Components

### 1. Frontend (React)
- **Technology**: React 18, Redux, Tailwind CSS
- **Port**: 5173 (dev), 80 (prod)
- **Key Features**:
  - Single Page Application with client-side routing
  - Redux for state management
  - Real-time UI updates
  - Responsive design with Tailwind CSS
  - Chart visualization with Chart.js

### 2. Backend (Node.js/Express)
- **Technology**: Express.js, MongoDB, Mongoose
- **Port**: 5000
- **Responsibilities**:
  - User authentication and authorization
  - Task and Habit CRUD operations
  - Analytics data aggregation
  - API gateway for AI service

### 3. AI Service (Python/Flask)
- **Technology**: Flask, scikit-learn, pandas
- **Port**: 5001
- **Capabilities**:
  - Habit success prediction
  - Pattern analysis
  - Personalized insights generation
  - Data processing and ML model inference

### 4. Database (MongoDB)
- **Port**: 27017
- **Collections**:
  - Users
  - Tasks
  - Habits
  - Analytics
  - Sessions

## Data Flow

### Authentication Flow
1. User submits credentials via frontend
2. Backend validates and generates JWT
3. JWT stored in localStorage (frontend)
4. Subsequent requests include JWT in headers
5. Backend validates JWT and processes request

### Task/Habit Management Flow
1. User creates/updates habit via frontend
2. Frontend sends request to backend API
3. Backend validates and stores in MongoDB
4. Backend returns updated data
5. Frontend updates Redux state and UI

### AI Prediction Flow
1. User views habit analytics
2. Frontend triggers prediction request
3. Backend collects historical data
4. Backend sends to AI service
5. AI service processes and returns predictions
6. Backend aggregates results
7. Frontend displays predictions and insights

## API Communication

### Frontend ↔ Backend
- **Protocol**: REST with JSON
- **Authentication**: JWT in Authorization header
- **Base URL**: http://localhost:5000/api

### Backend ↔ AI Service
- **Protocol**: REST with JSON
- **Base URL**: http://ai-service:5000
- **Endpoints**:
  - `/predict/habit-success`
  - `/insights/generate`

## Deployment Architecture

### Development
- Docker Compose with all services
- MongoDB local instance
- Hot reload for backend and frontend
- Console logging

### Production
- Containerized services on Kubernetes/Docker Swarm
- MongoDB Atlas for database
- Environment-specific configurations
- Load balancing with Nginx
- SSL/TLS encryption

## Scalability Considerations

### Horizontal Scaling
- Backend instances load balanced
- AI service instances for prediction scaling
- Database replication and sharding
- Redis caching for frequent queries

### Vertical Scaling
- Increase container resource limits
- Database optimization and indexing
- AI model caching

## Security

### Authentication
- JWT-based authentication
- Secure password hashing with bcrypt
- Token refresh mechanism
- CORS configuration

### Data Protection
- MongoDB authentication
- Environment-based secrets management
- API rate limiting
- Input validation and sanitization

## Performance Optimization

### Frontend
- Code splitting and lazy loading
- Image optimization
- Minification and compression
- Caching strategies

### Backend
- Database indexing
- Query optimization
- Caching with Redis
- Connection pooling

### AI Service
- Model preloading
- Batch processing
- Feature caching
- Efficient data structures

## Monitoring and Logging

- Application logs to stdout
- Error tracking
- Performance metrics
- User analytics
- API usage monitoring

## Technology Stack Rationale

### React
- Modern component-based architecture
- Large ecosystem and community
- Excellent performance

### Express.js
- Lightweight and flexible
- Rich middleware ecosystem
- Perfect for RESTful APIs

### MongoDB
- Document-based flexibility
- Scalable NoSQL solution
- Developer-friendly schema

### Python/Flask
- Rapid ML development
- Rich data science libraries
- Easy to deploy and scale
