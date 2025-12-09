# Habit Tracker AI

An advanced AI-powered task and habit tracking application with analytics dashboard. Built with React, Node.js/Python, and MongoDB for comprehensive habit management and intelligent insights.

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [AI Features](#ai-features)
- [Database Schema](#database-schema)
- [Contributing](#contributing)
- [License](#license)

## Features

### Core Features
- **User Authentication**: JWT-based authentication with secure password hashing
- **Task Management**: Create, read, update, delete tasks with categories and priorities
- **Habit Tracking**: Track daily habits with streak counting and completion status
- **Analytics Dashboard**: Visual analytics with charts and progress metrics
- **AI Predictions**: Machine learning-powered habit success predictions
- **Insights Engine**: AI-generated personalized insights and recommendations
- **Progress Visualization**: Real-time progress tracking with multiple chart types

### Advanced Features
- Mobile-responsive design with Tailwind CSS
- Dark mode support
- Real-time notifications
- Social sharing capabilities
- Goal setting and tracking
- Habit recommendations based on user patterns
- Data export functionality
- User statistics and milestones

## Architecture

```
┌─────────────────────┐
│   React Frontend    │
│  (UI Components)    │
└──────────┬──────────┘
           │
     ┌─────┴──────┐
     │             │
┌────▼─────┐  ┌───▼──────┐
│ Node.js   │  │  Python  │
│ Backend   │  │   AI     │
│ (Express) │  │ Service  │
└────┬─────┘  └───┬──────┘
     │             │
     └─────┬───────┘
           │
      ┌────▼──────┐
      │ MongoDB   │
      │ Database  │
      └───────────┘
```

## Tech Stack

### Frontend
- **React 18**: Latest React with hooks
- **Redux**: State management
- **React Router**: Client-side routing
- **Tailwind CSS**: Utility-first CSS framework
- **Chart.js**: Data visualization
- **Axios**: HTTP client
- **Date-fns**: Date utilities
- **Lucide React**: Icon library

### Backend (Node.js)
- **Express.js**: Web framework
- **MongoDB**: NoSQL database
- **Mongoose**: ODM for MongoDB
- **JWT**: Authentication tokens
- **BCrypt**: Password hashing
- **Cors**: Cross-origin resource sharing
- **Dotenv**: Environment variables

### AI Service (Python)
- **Flask**: Web framework
- **Scikit-learn**: Machine learning library
- **Pandas**: Data analysis
- **NumPy**: Numerical computing
- **Joblib**: Model serialization

### DevOps
- **Docker**: Containerization
- **Docker Compose**: Multi-container orchestration
- **Nginx**: Reverse proxy

## Project Structure

```
habit-tracker-ai/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Layout.jsx
│   │   │   ├── Navbar.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   ├── PrivateRoute.jsx
│   │   │   ├── TaskCard.jsx
│   │   │   ├── HabitCard.jsx
│   │   │   └── Charts.jsx
│   │   ├── pages/
│   │   │   ├── Dashboard.jsx
│   │   │   ├── Tasks.jsx
│   │   │   ├── Habits.jsx
│   │   │   ├── Analytics.jsx
│   │   │   ├── Login.jsx
│   │   │   └── Signup.jsx
│   │   ├── store/
│   │   │   ├── authSlice.js
│   │   │   ├── tasksSlice.js
│   │   │   ├── habitsSlice.js
│   │   │   └── index.js
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   ├── authService.js
│   │   │   ├── taskService.js
│   │   │   └── habitService.js
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   ├── Task.js
│   │   ├── Habit.js
│   │   └── Analytics.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── tasks.js
│   │   ├── habits.js
│   │   └── analytics.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── taskController.js
│   │   ├── habitController.js
│   │   └── analyticsController.js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── errorHandler.js
│   ├── utils/
│   │   ├── validators.js
│   │   └── helpers.js
│   ├── server.js
│   ├── package.json
│   └── .env.example
├── ai-service/
│   ├── models/
│   │   ├── habit_predictor.py
│   │   └── insight_generator.py
│   ├── routes/
│   │   ├── predict.py
│   │   └── insights.py
│   ├── utils/
│   │   ├── data_processor.py
│   │   └── ml_utils.py
│   ├── app.py
│   ├── requirements.txt
│   └── .env.example
├── docker-compose.yml
├── .gitignore
├── README.md
├── LICENSE
└── CONTRIBUTING.md
```

## Getting Started

### Prerequisites
- Node.js (v16+)
- Python (v3.8+)
- MongoDB (local or Atlas)
- Git

### Installation

#### 1. Clone the repository
```bash
git clone https://github.com/SnakeEye-sudo/habit-tracker-ai.git
cd habit-tracker-ai
```

#### 2. Backend Setup (Node.js)
```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your MongoDB URI and JWT secret
npm start
```

#### 3. AI Service Setup (Python)
```bash
cd ai-service
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

#### 4. Frontend Setup (React)
```bash
cd frontend
npm install
npm run dev
```

### Using Docker
```bash
docker-compose up --build
```

## Usage

### Web Interface
1. Open http://localhost:5173 (frontend)
2. Sign up or log in
3. Create tasks and habits
4. Track daily progress
5. View analytics and AI insights

### API Endpoints

**Authentication**
- POST `/api/auth/signup` - User registration
- POST `/api/auth/login` - User login
- POST `/api/auth/logout` - User logout

**Tasks**
- GET `/api/tasks` - Get all tasks
- POST `/api/tasks` - Create task
- PUT `/api/tasks/:id` - Update task
- DELETE `/api/tasks/:id` - Delete task

**Habits**
- GET `/api/habits` - Get all habits
- POST `/api/habits` - Create habit
- PUT `/api/habits/:id` - Update habit
- DELETE `/api/habits/:id` - Delete habit
- POST `/api/habits/:id/complete` - Mark habit complete

**Analytics**
- GET `/api/analytics/dashboard` - Dashboard metrics
- GET `/api/analytics/habits/:id` - Habit analytics
- GET `/api/analytics/trends` - Trend analysis

**AI Service**
- POST `/predict/habit-success` - Predict success probability
- POST `/insights/generate` - Generate personalized insights

## AI Features

### Habit Success Predictor
- Analyzes completion patterns
- Predicts success probability
- Identifies optimal timing
- Suggests improvements

### Insight Generator
- Analyzes user behavior patterns
- Generates personalized recommendations
- Identifies habit correlations
- Provides motivational insights

## Database Schema

### User Model
```javascript
{
  _id: ObjectId,
  email: String,
  password: String (hashed),
  name: String,
  createdAt: Date,
  updatedAt: Date
}
```

### Habit Model
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  name: String,
  description: String,
  frequency: String (daily/weekly),
  category: String,
  createdAt: Date,
  completions: [{
    date: Date,
    completed: Boolean
  }],
  streak: Number,
  bestStreak: Number
}
```

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open Pull Request

## License

MIT License - see LICENSE file for details

---

**Built with ❤️ for developers who want to build better habits**
