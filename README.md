# Real-Time To-Do List Application

A collaborative task management application that provides real-time updates across multiple clients, built with Angular, Node.js/Express, Socket.IO, and MongoDB.

## Features

- **Real-time updates**: Changes made by one user are instantly reflected for all connected users
- **Task management**: Create, read, update, and delete tasks
- **Task completion**: Mark tasks as completed or incomplete
- **Collaborative editing**: Lock mechanism to prevent multiple users from editing the same task
- **User authentication**: Secure login with JWT
- **Responsive design**: Works on desktop and mobile devices

## Tech Stack

### Frontend
- Angular 17 (Latest LTS)
- Angular Material
- RxJS
- Socket.IO Client

### Backend
- Node.js 20 (Latest LTS)
- Express.js
- Socket.IO
- MongoDB & Mongoose
- JWT Authentication
- Winston (Logging)
- Swagger/OpenAPI (API Documentation)

### Testing & Quality
- Jest
- Angular Testing Library

### Deployment
- Docker & Docker Compose

## Prerequisites

Before you begin, ensure you have the following installed:
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

For local development, you'll also need:
- [Node.js](https://nodejs.org/) (v20 LTS)
- [Angular CLI](https://angular.io/cli) (`npm install -g @angular/cli`)
- [MongoDB](https://www.mongodb.com/try/download/community) (if not using Docker)

## Installation & Running the Application

### Using Docker (Recommended)

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/real-time-todo-app.git
   cd real-time-todo-app
   ```

2. Start the application using Docker Compose:
   ```bash
   docker-compose up
   ```

3. Access the application at http://localhost:4200

### Manual Setup (Development)

#### Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file with the following content:
   ```
   PORT=3000
   MONGODB_URI=mongodb://localhost:27017/todo-app
   JWT_SECRET=your_jwt_secret_key
   NODE_ENV=development
   ```

4. Start the backend server:
   ```bash
   npm run dev
   ```

#### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the Angular development server:
   ```bash
   ng serve
   ```

4. Access the application at http://localhost:4200

## API Documentation

The API documentation is available via Swagger UI when the backend is running:

- Swagger UI: http://localhost:3000/api-docs

## Running Tests

### Backend Tests

```bash
cd backend
npm test
```

### Frontend Tests

```bash
cd frontend
ng test
```

## Project Structure

```
.
├── frontend/                 # Angular application
│   ├── src/
│   │   ├── app/
│   │   │   ├── components/   # UI components
│   │   │   ├── services/     # Services for API communication
│   │   │   ├── models/       # Data models
│   │   │   ├── guards/       # Route guards for authentication
│   │   │   └── ...
│   │   ├── environments/     # Environment configurations
│   │   └── ...
│   └── ...
├── backend/                  # Node.js/Express application
│   ├── src/
│   │   ├── controllers/      # Route controllers
│   │   ├── models/           # Mongoose models
│   │   ├── routes/           # API routes
│   │   ├── middlewares/      # Express middlewares
│   │   ├── services/         # Business logic
│   │   ├── utils/            # Utility functions
│   │   ├── config/           # Configuration files
│   │   └── app.js            # Express app setup
│   └── ...
├── docker-compose.yml        # Docker Compose configuration
├── .gitignore                # Git ignore file
├── .dockerignore             # Docker ignore file
└── README.md                 # Project documentation
```

## Design Decisions

### Real-Time Implementation

The real-time functionality is implemented using Socket.IO, which provides bidirectional communication between clients and the server. When a user makes changes to a task, the server broadcasts these changes to all connected clients, ensuring that everyone sees the most up-to-date information.

### Task Locking Mechanism

To prevent conflicts when multiple users attempt to edit the same task simultaneously, we've implemented a locking mechanism. When a user begins editing a task, it becomes locked for other users until the edit is complete or the lock times out.

### Authentication

JWT (JSON Web Tokens) is used for authentication. When a user logs in, they receive a token that must be included in subsequent requests to authenticate them. This token contains information about the user and has an expiration time for security.

### Design Patterns

- **Frontend**:
  - Service pattern for API communication
  - Observer pattern with RxJS for reactive state management
  - Repository pattern for data access
  - Component pattern for UI elements

- **Backend**:
  - MVC architecture for route handling
  - Repository pattern for database interactions
  - Middleware pattern for request processing
  - Singleton pattern for database connection

## Contribution

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
