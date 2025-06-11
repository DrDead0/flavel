# Flavel - MERN-stack Blog Application

A full-stack MERN blog application built with React.js frontend and Node.js backend, featuring user authentication, image uploads, and admin dashboard functionality.

## 🚀 Features

### Frontend (React + Vite)

- 📝 Clean and modern blog interface
- 📱 Responsive design
- 🏠 Home page with featured blogs
- 📖 Individual blog post pages
- 👥 Newsletter subscription
- ⚡ Fast development with Vite

### Backend (Node.js + Express + MongoDB)

- 🔐 JWT-based authentication
- 📸 Image upload with ImageKit integration
- 🗄️ MongoDB database integration
- 🛡️ Protected admin routes
- 📝 Blog CRUD operations

### Admin Dashboard

- 👨‍💼 Admin login system
- ➕ Add new blog posts
- 📋 Manage existing blogs
- 🗑️ Delete blogs
- 📊 Dashboard analytics
- 💬 Comments management
- 🔄 Toggle publish status

## 🛠️ Tech Stack

### Frontend

- **React 18** - UI library
- **Vite** - Build tool
- **Tailwind CSS** - Styling
- **React Router** - Navigation

### Backend

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **Multer** - File upload middleware
- **ImageKit** - Image storage and optimization

## 📋 Prerequisites

Before running this application, make sure you have:

- Node.js (v14 or higher)
- MongoDB database
- ImageKit account for image storage

## ⚙️ Installation & Setup

### 1. Clone the repository

```bash
git clone <repository-url>
cd blogapp
```

### 2. Backend Setup

```bash
cd server
npm install
```

Create a `.env` file in the server directory:

```env
JWT_SECRET="your-jwt-secret"
MONGODB_URI="your-mongodb-connection-string"
ADMIN_EMAIL="admin@example.com"
ADMIN_PASSWORD="your-admin-password"
IMAGEKIT_PUBLIC_KEY="your-imagekit-public-key"
IMAGEKIT_PRIVATE_KEY="your-imagekit-private-key"
IMAGEKIT_URL_ENDPOINT="https://ik.imagekit.io/your-imagekit-id"
```

### 3. Frontend Setup

```bash
cd ../client
npm install
```

## 🚀 Running the Application

### Start Backend Server

```bash
cd server
npm start
```

The server will run on `http://localhost:3000`

### Start Frontend Development Server

```bash
cd client
npm run dev
```

The frontend will run on `http://localhost:5173`

## 📊 API Endpoints

### Authentication

- `POST /api/admin/login` - Admin login

### Blog Management

- `POST /api/blog/add` - Add new blog (Protected)
- `GET /api/blog/list` - Get all published blogs
- `GET /api/blog/:id` - Get blog by ID
- `DELETE /api/blog/delete` - Delete blog (Protected)
- `PUT /api/blog/toggle` - Toggle publish status (Protected)

## 📁 Project Structure

```
blogapp/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── pages/         # Page components
│   │   ├── assets/        # Static assets
│   │   └── ...
│   └── package.json
├── server/                # Node.js backend
│   ├── controllers/       # Route controllers
│   ├── middleware/        # Custom middleware
│   ├── models/           # Database models
│   ├── routes/           # API routes
│   ├── configs/          # Configuration files
│   └── package.json
└── README.md
```

## 🔐 Environment Variables

### Server (.env)

```env
JWT_SECRET=your-jwt-secret-key
MONGODB_URI=mongodb-connection-string
ADMIN_EMAIL=admin-email-address
ADMIN_PASSWORD=admin-password
IMAGEKIT_PUBLIC_KEY=imagekit-public-key
IMAGEKIT_PRIVATE_KEY=imagekit-private-key
IMAGEKIT_URL_ENDPOINT=imagekit-url-endpoint
```

## 🖼️ Image Upload

This application uses ImageKit for image storage and optimization:

- Images are automatically optimized (WebP format, quality auto)
- Responsive image transformations
- CDN delivery for fast loading

## 🔒 Authentication

- JWT-based authentication for admin routes
- Protected endpoints require Authorization header
- Admin credentials stored in environment variables

## 📝 Blog Schema

```javascript
{
  title: String (required),
  subTitle: String,
  description: String (required),
  category: String (required),
  image: String (required),
  isPublished: Boolean (default: false),
  createdAt: Date (auto-generated),
  updatedAt: Date (auto-generated)
}
```

## 🚦 Testing the API

### Login to get JWT token:

```bash
curl -X POST http://localhost:3000/api/admin/login \
  -H "Content-Type: application/json" \
  -d '{"email":"admin@example.com","password":"your-password"}'
```

### Add a blog post:

```bash
curl -X POST http://localhost:3000/api/blog/add \
  -H "Authorization: your-jwt-token" \
  -F "image=@path/to/image.jpg" \
  -F 'blog={"title":"Test Blog","subTitle":"Test Subtitle","description":"Test description","category":"startup","isPublished":true}'
```

## 🛡️ Security Features

- Input validation and sanitization
- JWT token authentication
- Protected admin routes
- Environment variables for sensitive data
- CORS configuration

## 📚 Available Scripts

### Backend

- `npm start` - Start the server
- `npm run dev` - Start with nodemon for development

### Frontend

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🐛 Known Issues

- Ensure ImageKit folder permissions are correctly configured
- MongoDB connection string must include database name
- CORS might need adjustment for production deployment

## 📞 Support

For support, please open an issue in the repository or contact me.

---

Made with ❤️ by [Aashish]
