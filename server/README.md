# Blog Application - Backend Server

A robust Node.js backend server for the blog application, featuring JWT authentication, MongoDB integration, image upload with ImageKit, and comprehensive blog management APIs.

## 🚀 Features

### Core Functionality
- 🔐 JWT-based authentication system
- 📝 Complete blog CRUD operations
- 📸 Image upload and optimization with ImageKit
- 🗄️ MongoDB database integration with Mongoose
- 🛡️ Protected admin routes and middleware
- 📊 RESTful API architecture

### Security Features
- 🔒 JWT token authentication
- 🛡️ Input validation and sanitization
- 🔐 Environment variable configuration
- 🚫 Protected endpoint access control
- 🔑 Admin credential management

## 🛠️ Tech Stack

- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling
- **JWT** - JSON Web Token authentication
- **Multer** - File upload middleware
- **ImageKit** - Image storage and optimization service
- **dotenv** - Environment variable management

## 📋 Prerequisites

Before running the server, ensure you have:

- Node.js (v14 or higher)
- MongoDB database (local or MongoDB Atlas)
- ImageKit account with API credentials
- npm or yarn package manager

## ⚙️ Installation

```bash
# Navigate to server directory
cd server

# Install dependencies
npm install

# Create environment file
cp .env.example .env  # Or create manually
```

## 🔧 Environment Configuration

Create a `.env` file in the server root directory:

```env
# JWT Configuration
JWT_SECRET="your-secure-jwt-secret-key"

# Database Configuration
MONGODB_URI="mongodb://localhost:27017/blogapp"
# or for MongoDB Atlas:
# MONGODB_URI="mongodb+srv://username:password@cluster.mongodb.net/blogapp"

# Admin Credentials
ADMIN_EMAIL="admin@example.com"
ADMIN_PASSWORD="your-secure-admin-password"

# ImageKit Configuration
IMAGEKIT_PUBLIC_KEY="your-imagekit-public-key"
IMAGEKIT_PRIVATE_KEY="your-imagekit-private-key"
IMAGEKIT_URL_ENDPOINT="https://ik.imagekit.io/your-imagekit-id"
```

## 🚀 Running the Server

### Development Mode
```bash
npm run dev
```

### Production Mode
```bash
npm start
```

The server will start on `http://localhost:3000`

## 📊 API Endpoints

### Authentication Routes (`/api/admin`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/login` | Admin login | ❌ |

**Login Request:**
```json
{
  "email": "admin@example.com",
  "password": "your-password"
}
```

**Login Response:**
```json
{
  "success": true,
  "token": "jwt-token-here"
}
```

### Blog Management Routes (`/api/blog`)

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/add` | Create new blog post | ✅ |
| GET | `/list` | Get all published blogs | ❌ |
| GET | `/:id` | Get blog by ID | ❌ |
| DELETE | `/delete` | Delete blog post | ✅ |
| PUT | `/toggle` | Toggle publish status | ✅ |

### Blog Creation (`POST /api/blog/add`)

**Request Format:** `multipart/form-data`

```bash
# Form fields:
image: [file] # Image file
blog: [string] # JSON string with blog data
```

**Blog JSON Structure:**
```json
{
  "title": "Blog Title",
  "subTitle": "Blog Subtitle",
  "description": "Blog content description",
  "category": "startup|technology|health|lifestyle",
  "isPublished": true
}
```

## 📁 Project Structure

```
server/
├── configs/
│   ├── db.js              # MongoDB connection
│   └── imageKit.js        # ImageKit configuration
├── controllers/
│   ├── adminController.js # Admin authentication logic
│   └── blogController.js  # Blog CRUD operations
├── middleware/
│   ├── auth.js           # JWT authentication middleware
│   └── multer.js         # File upload configuration
├── models/
│   └── Blog.js           # Blog database schema
├── routes/
│   ├── adminRoutes.js    # Admin route definitions
│   └── blogRoutes.js     # Blog route definitions
├── .env                  # Environment variables
├── .gitignore           # Git ignore rules
├── package.json         # Dependencies and scripts
├── README.md            # This file
└── server.js            # Main server entry point
```

## 🗄️ Database Schema

### Blog Model
```javascript
{
  title: {
    type: String,
    required: true
  },
  subTitle: {
    type: String,
    required: false
  },
  description: {
    type: String,
    required: true
  },
  category: {
    type: String,
    required: true,
    enum: ['startup', 'technology', 'health', 'lifestyle']
  },
  image: {
    type: String,
    required: true
  },
  isPublished: {
    type: Boolean,
    default: false
  },
  createdAt: {
    type: Date,
    default: Date.now
  },
  updatedAt: {
    type: Date,
    default: Date.now
  }
}
```

## 🔐 Authentication Flow

1. **Admin Login**: POST credentials to `/api/admin/login`
2. **Receive JWT Token**: Server validates and returns token
3. **Protected Requests**: Include token in `Authorization` header
4. **Token Validation**: Middleware verifies token for protected routes

### Example Protected Request:
```bash
curl -X POST http://localhost:3000/api/blog/add \
  -H "Authorization: your-jwt-token" \
  -F "image=@image.jpg" \
  -F 'blog={"title":"Test","description":"Content","category":"startup","isPublished":true}'
```

## 📸 Image Upload Process

1. **Multer Middleware**: Handles multipart file upload
2. **File Validation**: Checks file type and size
3. **ImageKit Upload**: Stores image with optimization
4. **URL Generation**: Creates optimized image URLs
5. **Database Storage**: Saves optimized URL to MongoDB

### Image Optimization Features:
- Automatic WebP conversion
- Quality optimization
- Responsive image sizing
- CDN delivery

## 🛡️ Security Measures

### Input Validation
- Required field validation
- Data type checking
- File upload restrictions

### Authentication Security
- JWT token expiration
- Secure secret key usage
- Protected route middleware

### Database Security
- Mongoose schema validation
- Input sanitization
- Connection string security

## 📚 Available Scripts

```json
{
  "start": "node server.js",
  "dev": "nodemon server.js"
}
```

- `npm start` - Production server start
- `npm run dev` - Development with auto-restart

## 🧪 Testing the API

### Using cURL

**Login:**
```bash
curl -X POST http://localhost:3000/api/admin/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@example.com","password":"your-password"}'
```

**Get All Blogs:**
```bash
curl -X GET http://localhost:3000/api/blog/list
```

**Add Blog Post:**
```bash
curl -X POST http://localhost:3000/api/blog/add \
  -H "Authorization: your-jwt-token" \
  -F "image=@test-image.jpg" \
  -F 'blog={"title":"Test Blog","description":"Test content","category":"startup","isPublished":true}'
```

### Using Postman

1. **Set up environment variables**
2. **Create login request** to get token
3. **Use token in Authorization header** for protected routes
4. **Test file uploads** with form-data

## 🐛 Common Issues & Troubleshooting

### Database Connection Issues
- Verify MongoDB URI in `.env`
- Check database permissions
- Ensure MongoDB service is running

### ImageKit Upload Issues
- Verify API credentials
- Check folder permissions
- Validate image file formats

### Authentication Problems
- Verify JWT secret configuration
- Check token format in requests
- Validate admin credentials

## 📈 Performance Optimization

- **Image Optimization**: Automatic WebP conversion and compression
- **Database Indexing**: Optimized queries with proper indexes
- **Caching**: ImageKit CDN for fast image delivery
- **Connection Pooling**: MongoDB connection optimization

## 🚀 Deployment

### Environment Setup
1. Set production environment variables
2. Configure MongoDB Atlas or production database
3. Set up ImageKit production settings
4. Configure CORS for frontend domain

### Deployment Platforms
- **Heroku**: Easy deployment with git integration
- **Railway**: Modern deployment platform
- **DigitalOcean**: VPS deployment
- **AWS EC2**: Scalable cloud deployment

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is part of the Blog Application suite. See the main project README for license information.

---

**Backend Server by FLAVEL** 🚀