# Chat Application Setup Instructions

## Prerequisites
- Java 21 or higher
- Node.js 16 or higher
- MySQL 8.0 or higher
- Maven 3.6 or higher

## Backend Setup (Spring Boot)

1. **Database Setup**
   ```sql
   CREATE DATABASE chat;
   ```

2. **Update Database Configuration**
   - Edit `Back-end/src/main/resources/application.properties`
   - Update database credentials if needed:
     ```properties
     spring.datasource.username=your_username
     spring.datasource.password=your_password
     ```

3. **Run the Backend**
   ```bash
   cd Back-end
   mvn spring-boot:run
   ```
   The backend will start on `http://localhost:8080`

## Frontend Setup (React)

1. **Install Dependencies**
   ```bash
   cd Front-end
   npm install
   ```

2. **Start the Frontend**
   ```bash
   npm run dev
   ```
   The frontend will start on `http://localhost:5173`

## Features Implemented

### ✅ Security Features
- JWT Authentication
- Password encryption with BCrypt
- Spring Security configuration
- CORS support
- Input validation

### ✅ Chat Features
- User registration and login
- Real-time messaging with WebSockets
- Private messaging between users
- Public chatroom
- Message history
- File sharing (images/videos)
- User search functionality

### ✅ Technical Features
- RESTful APIs
- Database persistence with JPA/Hibernate
- Global error handling
- Responsive UI with Tailwind CSS
- Token-based authentication

## API Endpoints

### Authentication
- `POST /api/users/signup` - User registration
- `POST /api/users/login` - User login
- `GET /api/users/logout` - User logout

### User Management
- `GET /api/users/search?username={username}` - Search users

### Messaging
- `GET /api/messages/history/{user1}/{user2}` - Get chat history

### WebSocket Endpoints
- `/ws` - WebSocket connection
- `/app/message` - Send public message
- `/app/private-message` - Send private message
- `/chatroom/public` - Subscribe to public messages
- `/user/{username}/private` - Subscribe to private messages

## Security Notes

- Passwords are encrypted using BCrypt
- JWT tokens expire after 5 hours
- All API endpoints (except login/signup) require authentication
- CORS is configured to allow frontend connections

## Troubleshooting

1. **Database Connection Issues**
   - Ensure MySQL is running
   - Check database credentials in application.properties
   - Verify database exists

2. **Frontend Connection Issues**
   - Ensure backend is running on port 8080
   - Check browser console for CORS errors
   - Verify JWT token is being sent in requests

3. **WebSocket Connection Issues**
   - Check if WebSocket endpoint is accessible
   - Verify STOMP client configuration
   - Check browser network tab for WebSocket connection status
