"# EventMaster - Event Management System

<div align="center">

![EventMaster](https://img.shields.io/badge/EventMaster-v1.0.0-blueviolet?style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-v23.11.0-brightgreen?style=for-the-badge&logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-v7.0+-green?style=for-the-badge&logo=mongodb)
![Express](https://img.shields.io/badge/Express-v4.18.2-lightgrey?style=for-the-badge&logo=express)
![License](https://img.shields.io/badge/License-ISC-blue?style=for-the-badge)

**A comprehensive web application for creating, managing, and attending events with ease**

[Features](#-features) • [Tech Stack](#-tech-stack) • [Installation](#-installation) • [Usage](#-usage) • [API Documentation](#-api-documentation) • [Contributing](#-contributing)

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [API Documentation](#-api-documentation)
- [Database Schema](#-database-schema)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 Overview

**EventMaster** is a full-stack event management platform that enables users to:
- Create and manage events
- Find and join events created by others
- Invite participants to events
- Check in attendees
- Search for events by various criteria

Perfect for organizing corporate events, conferences, weddings, team gatherings, and private celebrations.

---

## ✨ Features

### 🔐 Authentication
- **User Registration**: Secure registration with email validation and strong password requirements
  - Password Requirements: Minimum 8 characters, uppercase, lowercase, number, and special character
  - Email Validation: Standard email format validation
- **User Login**: Session-based authentication
- **User Logout**: Secure session termination

### 📅 Event Management
- **Create Events**: Users can create new events with details like:
  - Event title and description
  - Date and time
  - Location
  - Event type
  - Attendees list
- **View Events**: 
  - My Events Dashboard: View all events created by the user
  - Browse All Events: Discover public events
  - Event Details: Get comprehensive information about any event
- **Event Search**: Search and filter events by keywords
- **Invite System**: Manually invite users via email to events
- **Join Events**: Users can join public events
- **Check-in**: Track event attendance during check-in

### 🎨 User Interface
- Responsive design with Bootstrap 5
- Modern and intuitive dashboard
- Real-time data updates
- Toast notifications for user feedback

---

## 🛠 Tech Stack

### Frontend
- **HTML5** - Structure
- **CSS3** - Styling with custom theme
- **JavaScript** - Vanilla JS & AngularJS
- **AngularJS** (v1.8.2) - Framework for dynamic content
- **Bootstrap 5** - Responsive UI components
- **jQuery** - DOM manipulation
- **Font Awesome & Bootstrap Icons** - Icon library

### Backend
- **Node.js** - Runtime environment
- **Express.js** (v4.18.2) - Web application framework
- **MongoDB** (v7.0+) - NoSQL database
- **Mongoose** (v7.0.3) - MongoDB object modeling
- **CORS** - Cross-Origin Resource Sharing
- **Express Session** - Session management
- **Cookie Parser** - Cookie parsing middleware

### Deployment
- **Vercel** - Frontend and backend hosting
- **Railway** - Backend API deployment (as configured in app.js)

---

## 📁 Project Structure

```
Event-Management-System/
├── frontend/                      # Client-side application
│   ├── index.html                # Landing page
│   ├── login.html                # Login page
│   ├── register.html             # Registration page
│   ├── dashboard.html            # User dashboard (My Events)
│   ├── create-event.html         # Event creation form
│   ├── event-details.html        # Event details page
│   ├── search.html               # Event search page
│   ├── invite.html               # Event invitation page
│   ├── about-us.html             # About page
│   ├── css/
│   │   ├── style.css             # Main stylesheet
│   │   ├── dashboard.css         # Dashboard styles
│   │   └── event-details.css     # Event details styles
│   ├── js/
│   │   ├── app.js                # AngularJS app and controllers
│   │   ├── main.js               # DOM manipulation and utilities
│   │   └── search.js             # Search functionality
│   └── data/
│       └── events.json           # Sample event data
│
├── backend/                       # Server-side application
│   ├── server.js                 # Express server configuration
│   ├── models/
│   │   ├── User.js               # User schema and model
│   │   └── Event.js              # Event schema and model
│   ├── routes/
│   │   ├── auth.js               # Authentication routes
│   │   └── events.js             # Event management routes
│   └── package.json              # Backend dependencies
│
├── package.json                   # Root package.json
├── package-lock.json             # Dependency lock file
├── vercel.json                   # Vercel deployment config
└── README.md                      # This file
```

---

## 🚀 Installation

### Prerequisites
- Node.js (v14 or higher)
- npm (v6 or higher)
- MongoDB account (for connection string)
- Git

### Step 1: Clone the Repository
```bash
git clone https://github.com/CHIRAG9066/Event-Management-System.git
cd Event-Management-System
```

### Step 2: Install Backend Dependencies
```bash
cd backend
npm install
cd ..
```

### Step 3: Install Frontend Dependencies (if applicable)
```bash
cd frontend
# Frontend uses CDN libraries, so npm install is optional
cd ..
```

### Step 4: Environment Setup
Create a `.env` file in the `backend` directory with the following variables:
```env
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/?appName=Cluster0
SESSION_SECRET=your-secret-key
PORT=3000
NODE_ENV=development
```

---

## ⚙️ Configuration

### MongoDB Connection
Update the connection string in `backend/server.js`:
```javascript
mongoose.connect('YOUR_MONGODB_URI', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});
```

### Session Configuration
The session secret is currently hardcoded in `server.js`:
```javascript
app.use(session({
  secret: 'Web-Project-eventManagementSystem',
  resave: false,
  saveUninitialized: true,
  cookie: { secure: false }
}));
```
**⚠️ Security Note**: Use environment variables in production.

### CORS Configuration
CORS is enabled for all origins in `server.js`. For production, restrict this to specific domains:
```javascript
app.use(cors({
  origin: 'https://yourdomain.com',
  credentials: true
}));
```

---

## 📖 Usage

### Running Locally

#### Start the Backend Server
```bash
cd backend
npm start
```
Server will run on: `http://localhost:3000`

#### Open Frontend in Browser
```bash
# Navigate to frontend folder and open index.html in your browser
# Or use a simple HTTP server
cd frontend
python -m http.server 8000
# Open http://localhost:8000 in your browser
```

### User Workflow

1. **Register**: Create a new account with valid credentials
2. **Login**: Sign in with your registered credentials
3. **Dashboard**: View all events you've created
4. **Create Event**: Click "Create Event" and fill in the details
5. **Invite Users**: Add participants via email
6. **Search Events**: Find events created by others
7. **Join Event**: Click "Join" on any public event
8. **Check-in**: Verify attendance at your events

---

## 🔌 API Documentation

### Base URL
- Local: `http://localhost:3000`
- Production: `https://eventmaster-backend.up.railway.app`

### Authentication Endpoints

#### Register User
```http
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "SecurePass123!"
}

Response:
{
  "success": true,
  "toast": {
    "message": "Registration successful!",
    "type": "success"
  }
}
```

#### Login User
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "SecurePass123!"
}

Response:
{
  "success": true,
  "user": {
    "_id": "user_id",
    "email": "john@example.com",
    "name": "John Doe"
  },
  "toast": {
    "message": "Login successful!",
    "type": "success"
  }
}
```

#### Logout User
```http
POST /api/auth/logout

Response:
{
  "success": true,
  "message": "Logged out successfully",
  "toast": {
    "message": "Logged out successfully",
    "type": "success"
  }
}
```

### Event Endpoints

#### Create Event
```http
POST /api/events/create
Content-Type: application/json

{
  "title": "Tech Conference 2024",
  "description": "Annual tech conference",
  "date": "2024-12-15",
  "location": "San Francisco, CA",
  "type": "Conference",
  "userId": "user_id",
  "attendees": [],
  "participants": []
}

Response:
{
  "success": true
}
```

#### Get User Events
```http
GET /api/events/user/:userId

Response:
[
  {
    "_id": "event_id",
    "title": "Tech Conference 2024",
    "description": "Annual tech conference",
    "date": "2024-12-15T00:00:00.000Z",
    "location": "San Francisco, CA",
    "type": "Conference",
    "userId": "user_id",
    "attendees": [],
    "participants": []
  }
]
```

#### Get All Events
```http
GET /api/events/all

Response:
[
  { /* event objects */ }
]
```

#### Get Event Details
```http
GET /api/events/:eventId

Response:
{
  "_id": "event_id",
  "title": "Tech Conference 2024",
  "description": "Annual tech conference",
  "date": "2024-12-15T00:00:00.000Z",
  "location": "San Francisco, CA",
  "type": "Conference",
  "userId": "user_id",
  "attendees": [],
  "participants": []
}
```

#### Invite User to Event
```http
POST /api/events/invite/:eventId
Content-Type: application/json

{
  "email": "invited@example.com"
}

Response:
{
  "success": true,
  "message": "Invitation added"
}
```

#### Join Event
```http
POST /api/events/join/:eventId
Content-Type: application/json

{
  "userId": "user_id"
}

Response:
{
  "success": true,
  "message": "You have joined the event"
}
```

#### Check-in to Event
```http
POST /api/events/checkin
Content-Type: application/json

{
  "eventId": "event_id",
  "email": "user@example.com"
}

Response:
{
  "success": true,
  "message": "Check-in successful"
}
```

---

## 💾 Database Schema

### User Schema
```javascript
{
  name: String,
  email: String,
  password: String
}
```

### Event Schema
```javascript
{
  title: String,
  description: String,
  date: Date (required),
  location: String,
  type: String,
  userId: ObjectId (ref: 'User'),
  attendees: [String], // emails of invited users
  participants: [ObjectId] // user IDs who joined
}
```

---

## 🌐 Deployment

### Deploy on Vercel

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Connect to Vercel**
   - Go to [vercel.com](https://vercel.com)
   - Click "Import Project"
   - Select your GitHub repository
   - Configure environment variables
   - Click "Deploy"

3. **Configure Environment Variables in Vercel**
   - Go to Settings → Environment Variables
   - Add `MONGODB_URI`, `SESSION_SECRET`, etc.

### Deploy Backend on Railway

1. **Create Railway Account**
   - Visit [railway.app](https://railway.app)

2. **Deploy from GitHub**
   - Connect your GitHub repository
   - Select the backend directory as root
   - Add environment variables
   - Deploy

3. **Update API URL**
   - Update the API URL in `frontend/js/app.js`:
   ```javascript
   const API_URL = 'https://your-railway-backend.up.railway.app';
   ```

---

## 🤝 Contributing

We welcome contributions! Here's how to contribute:

1. **Fork the Repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/Event-Management-System.git
   ```

2. **Create a Feature Branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Make Your Changes**
   - Follow the existing code style
   - Add comments where necessary
   - Test your changes

4. **Commit Your Changes**
   ```bash
   git commit -m "Add amazing feature"
   ```

5. **Push to Branch**
   ```bash
   git push origin feature/amazing-feature
   ```

6. **Open a Pull Request**
   - Describe your changes
   - Reference any related issues
   - Wait for review

---

## 📋 Roadmap

- [ ] User profile customization
- [ ] Event categories and filtering
- [ ] Email notifications
- [ ] Real-time messaging between event organizers and participants
- [ ] Payment integration for paid events
- [ ] Event ratings and reviews
- [ ] Analytics dashboard
- [ ] Mobile app (React Native)
- [ ] Advanced search with filters
- [ ] Event calendar view
- [ ] Automated email reminders

---

## 🐛 Known Issues

- Passwords are stored in plain text (use bcrypt in production)
- CORS is open to all origins (restrict in production)
- Session secret is hardcoded (use environment variables)
- No input sanitization (implement in production)

---

## 🔒 Security Considerations

### Current Implementation
- Session-based authentication
- Email and password validation
- CORS enabled

### Recommendations for Production
- ✅ Hash passwords using bcrypt
- ✅ Implement JWT tokens
- ✅ Add HTTPS
- ✅ Use environment variables for secrets
- ✅ Implement input sanitization
- ✅ Add rate limiting
- ✅ Implement CSRF protection
- ✅ Use secure cookies

---

## 📞 Support

For issues and questions:
- Create an Issue on GitHub
- Email: chiragbansal9066@gmail.com
- Check existing issues first

---

## 📝 License

This project is licensed under the **ISC License** - see the LICENSE file for details.

---

## 👥 Contributors

- **Chirag** - Project Creator
- Special thanks to all contributors and users

---

## 🙏 Acknowledgments

- [Bootstrap](https://getbootstrap.com/) - UI Framework
- [AngularJS](https://angularjs.org/) - Frontend Framework
- [Express.js](https://expressjs.com/) - Backend Framework
- [MongoDB](https://www.mongodb.com/) - Database
- [Vercel](https://vercel.com/) - Deployment Platform
- [Railway](https://railway.app/) - Backend Hosting

---

<div align="center">

**Built with ❤️ by EventMaster Team**

[⭐ Star us on GitHub](https://github.com/CHIRAG9066/Event-Management-System)

</div>" 
