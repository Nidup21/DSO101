# To-Do List Web Application

A full-stack to-do list application with React frontend, Node.js/Express backend, and PostgreSQL database.

## Project Structure

```
todo-app/
├── backend/          # Express.js server with REST API
│   ├── server.js     # Main server file
│   ├── db.js         # Database connection and initialization
│   ├── routes.js     # API endpoints
│   ├── package.json  # Backend dependencies
│   └── .env.example  # Environment variables template
│
└── frontend/         # React.js client application
    ├── src/
    │   ├── App.js            # Main app component
    │   ├── TaskForm.js        # Task input form component
    │   ├── TaskList.js        # Task list display component
    │   ├── TaskItem.js        # Individual task item component
    │   ├── api.js             # API service utilities
    │   ├── index.js           # React entry point
    │   └── *.css              # Component styles
    ├── public/
    │   └── index.html         # HTML template
    ├── package.json           # Frontend dependencies
    └── .env                   # Environment variables
```

## Features

### Frontend
- ✅ Add new tasks
- ✅ Mark tasks as completed
- ✅ Edit task titles
- ✅ Delete tasks
- ✅ View completion progress
- ✅ Clean, minimal UI with responsive design

### Backend
- ✅ RESTful API endpoints for CRUD operations
- ✅ PostgreSQL database integration
- ✅ Environment variable configuration
- ✅ Error handling and validation
- ✅ CORS enabled for frontend communication

### Database
- ✅ PostgreSQL with automatic schema initialization
- ✅ Task table with: id, title, completed, created_at

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- PostgreSQL (v12 or higher)

## Setup Instructions

### 1. Database Setup

First, create a PostgreSQL database:

```bash
# Connect to PostgreSQL
psql -U postgres

# Create a new database
CREATE DATABASE todo_db;

# Exit psql
\q
```

### 2. Backend Setup

```bash
cd backend

# Copy environment variables
cp .env.example .env

# Edit .env with your database credentials
nano .env
# Update:
# DB_HOST=localhost
# DB_USER=postgres
# DB_PASSWORD=your_password
# DB_NAME=todo_db
# PORT=5000

# Install dependencies
npm install

# Start the server
npm start
# Or use development mode with auto-reload
npm run dev
```

The backend will be available at `http://localhost:5000`

### 3. Frontend Setup

In a new terminal:

```bash
cd frontend

# Install dependencies
npm install

# Start the development server
npm start
```

The frontend will automatically open at `http://localhost:3000`

## API Endpoints

### GET /tasks
Fetch all tasks

**Response:**
```json
[
  {
    "id": 1,
    "title": "Task title",
    "completed": false,
    "created_at": "2024-01-15T10:30:00.000Z"
  }
]
```

### POST /tasks
Create a new task

**Request:**
```json
{
  "title": "New task"
}
```

**Response:**
```json
{
  "id": 2,
  "title": "New task",
  "completed": false,
  "created_at": "2024-01-15T11:00:00.000Z"
}
```

### PUT /tasks/:id
Update a task

**Request:**
```json
{
  "title": "Updated title",
  "completed": true
}
```

**Response:**
```json
{
  "id": 1,
  "title": "Updated title",
  "completed": true,
  "created_at": "2024-01-15T10:30:00.000Z"
}
```

### DELETE /tasks/:id
Delete a task

**Response:**
```json
{
  "message": "Task deleted successfully",
  "task": {
    "id": 1,
    "title": "Task title",
    "completed": false,
    "created_at": "2024-01-15T10:30:00.000Z"
  }
}
```

## Environment Variables

### Backend (.env)
```
DB_HOST=localhost
DB_USER=postgres
DB_PASSWORD=your_password
DB_NAME=todo_db
PORT=5000
```

### Frontend (.env)
```
REACT_APP_API_URL=http://localhost:5000
```

## Running the Application

Make sure both the backend and frontend are running:

1. Backend terminal: `npm start` (in /backend directory)
2. Frontend terminal: `npm start` (in /frontend directory)

Visit `http://localhost:3000` in your browser.

## Building for Production

### Backend
```bash
cd backend
npm install
# The backend is ready to deploy
# Use environment variables in production
```

### Frontend
```bash
cd frontend
npm install
npm run build
# This creates an optimized production build in the 'build' folder
```

## Technologies Used

### Frontend
- React 18
- CSS3 (responsive design)
- Fetch API for HTTP requests

### Backend
- Node.js
- Express.js
- PostgreSQL
- pg (PostgreSQL client)
- CORS middleware

### Database
- PostgreSQL 12+
- SQL for schema management

## Notes

- The database schema is automatically created on first backend startup
- The frontend expects the backend to be running on `http://localhost:5000`
- Update `REACT_APP_API_URL` in frontend/.env if deploying to different servers
- Ensure PostgreSQL is running before starting the backend

## License

MIT
