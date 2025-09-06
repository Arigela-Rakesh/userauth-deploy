# User Authentication System - MERN Stack (Deployment Ready)

A complete authentication system built with MongoDB, Express.js, React.js, and Node.js featuring user registration, login, logout, and protected routes.

## Features

- User Registration with Gmail validation (@gmail.com required)
- Secure login with JWT tokens and HTTP-only cookies
- Enhanced password validation (8+ chars, uppercase, lowercase, number, special char)
- Protected dashboard route
- Session persistence (24 hours)
- Duplicate email prevention
- Modern UI with gradient backgrounds and glass morphism effects

## Tech Stack

- **Frontend:** React.js, React Router, Axios
- **Backend:** Node.js, Express.js
- **Database:** MongoDB with Mongoose
- **Authentication:** JWT tokens, bcrypt for password hashing
- **Session Management:** HTTP-only cookies

## Deployment

### Backend Deployment (Render/Heroku)

#### Option 1: Render
1. Create account on [Render](https://render.com)
2. Connect your GitHub repository
3. Create new Web Service
4. Configure environment variables:
   - `MONGODB_URI`: Your MongoDB Atlas connection string
   - `JWT_SECRET`: Strong secret key for JWT
   - `NODE_ENV`: production
5. Deploy automatically from GitHub

#### Option 2: Heroku
1. Install Heroku CLI
2. Login: `heroku login`
3. Create app: `heroku create your-app-name`
4. Set environment variables:
   ```bash
   heroku config:set MONGODB_URI=your_mongodb_uri
   heroku config:set JWT_SECRET=your_jwt_secret
   heroku config:set NODE_ENV=production
   ```
5. Deploy: `git push heroku main`

### Frontend Deployment (Vercel/Netlify)

#### Option 1: Vercel
1. Install Vercel CLI: `npm i -g vercel`
2. Login: `vercel login`
3. Deploy: `vercel --prod`
4. Set environment variable:
   - `REACT_APP_API_URL`: Your backend URL

#### Option 2: Netlify
1. Create account on [Netlify](https://netlify.com)
2. Connect GitHub repository
3. Set build settings:
   - Build command: `npm run build`
   - Publish directory: `build`
4. Set environment variable:
   - `REACT_APP_API_URL`: Your backend URL

## Local Development

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local installation or MongoDB Atlas)

### Backend Setup
```bash
cd backend
npm install
# Update .env with your MongoDB URI and JWT secret
npm start
```

### Frontend Setup
```bash
cd frontend
npm install
npm start
```

## Environment Variables

### Backend (.env)
```
MONGODB_URI=mongodb://localhost:27017/userauth
JWT_SECRET=your_jwt_secret_key_here
PORT=5000
NODE_ENV=development
```

### Frontend (.env.production)
```
REACT_APP_API_URL=https://your-backend-url.onrender.com/api
```

## API Endpoints

- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `GET /api/auth/me` - Get current user info

## Security Features

- Gmail-only email validation
- Strong password requirements (8+ chars, mixed case, numbers, special chars)
- Passwords hashed using bcrypt
- JWT tokens stored in HTTP-only cookies
- CORS configured for production
- Input validation and error handling
- Protected routes requiring authentication
- Session expiration (24 hours)

## Database Schema

### User Model
```javascript
{
  email: String (required, unique, lowercase, @gmail.com only)
  password: String (required, 8+ chars, hashed)
  timestamps: true
}
```

## Deployment Checklist

### Before Deployment:
1. ✅ Set up MongoDB Atlas database
2. ✅ Update CORS origins in backend
3. ✅ Set production environment variables
4. ✅ Test all authentication flows
5. ✅ Verify password validation rules
6. ✅ Check email validation (@gmail.com)

### After Deployment:
1. Update frontend API URL to point to deployed backend
2. Test registration with valid Gmail address
3. Test login/logout functionality
4. Verify protected routes work
5. Check session persistence
6. Test password requirements

## Troubleshooting

### Common Issues:
- **CORS errors**: Update backend CORS origins
- **API connection**: Check REACT_APP_API_URL
- **Database connection**: Verify MongoDB URI
- **Authentication fails**: Check JWT_SECRET consistency

## Project Structure
```
UserAuth-Deploy/
├── backend/
│   ├── models/User.js
│   ├── routes/auth.js
│   ├── server.js
│   ├── .env.production
│   └── render.yaml
├── frontend/
│   ├── src/
│   ├── .env.production
│   ├── vercel.json
│   └── netlify.toml
└── README.md
```