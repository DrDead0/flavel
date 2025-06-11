# Blog Application - Frontend

A modern React frontend for the blog application built with Vite, featuring a clean interface for reading blogs and an admin dashboard for content management.

## 🚀 Features

### Public Interface

- 📖 Browse and read blog posts
- 🏠 Responsive home page with featured content
- 📱 Mobile-friendly design
- 📧 Newsletter subscription
- 🔍 Blog categories and filtering
- ⚡ Fast loading with optimized images

### Admin Dashboard

- 🔐 Secure admin login
- ➕ Add new blog posts with rich text editor
- 📝 Manage existing blog content
- 🗑️ Delete and edit posts
- 📊 Dashboard analytics
- 💬 Comments management
- 🔄 Publish/unpublish posts

## 🛠️ Tech Stack

- **React 18** - Modern React with hooks
- **Vite** - Fast build tool and dev server
- **CSS3** - Custom styling with responsive design
- **React Router** - Client-side routing
- **ESLint** - Code linting and formatting

## 📋 Prerequisites

- Node.js (v14 or higher)
- npm or yarn package manager

## ⚙️ Installation

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## 🚀 Development

The development server will start on `http://localhost:5173` with hot module replacement (HMR) enabled.

### Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally
- `npm run lint` - Run ESLint

## 📁 Project Structure

```
src/
├── components/          # Reusable UI components
│   ├── BlogCard.jsx    # Individual blog post card
│   ├── BlogList.jsx    # List of blog posts
│   ├── Footer.jsx      # Site footer
│   ├── Header.jsx      # Site header
│   ├── Navbar.jsx      # Navigation bar
│   ├── Newsletter.jsx  # Newsletter subscription
│   └── admin/          # Admin-specific components
│       ├── BlogTableItem.jsx
│       ├── CommentTableItem.jsx
│       ├── Login.jsx
│       └── Sidebar.jsx
├── pages/              # Page components
│   ├── Home.jsx        # Homepage
│   ├── Blog.jsx        # Individual blog page
│   └── admin/          # Admin pages
│       ├── Dashboard.jsx
│       ├── AddBlog.jsx
│       ├── ListBlog.jsx
│       ├── Comments.jsx
│       └── Layout.jsx
├── assets/             # Static assets (images, icons)
├── App.jsx             # Main app component
└── main.jsx            # App entry point
```

## 🎨 Styling

The application uses custom CSS with:

- Responsive design principles
- Modern CSS Grid and Flexbox layouts
- Custom color schemes and typography
- Mobile-first approach

## 🔗 API Integration

The frontend communicates with the backend API running on `http://localhost:3000`:

- **Public endpoints**: Blog listing, individual blog posts
- **Protected endpoints**: Admin authentication, blog management
- **Image uploads**: Handled through multipart form data

## 📱 Responsive Design

The application is fully responsive and optimized for:

- Desktop (1200px+)
- Tablet (768px - 1199px)
- Mobile (320px - 767px)

## 🛡️ Admin Features

Access the admin dashboard at `/admin` with proper authentication:

- Secure login system
- Rich text editor for blog content
- Image upload functionality
- Content management tools

## 🚀 Build & Deployment

```bash
# Build for production
npm run build

# The built files will be in the 'dist' directory
# Deploy the contents to your hosting service
```

## 🔧 Configuration

### Vite Configuration

The project uses Vite with React plugin for fast development and optimized builds.

### ESLint Configuration

ESLint is configured with React-specific rules for code quality and consistency.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is part of the Blog Application suite. See the main project README for license information.
