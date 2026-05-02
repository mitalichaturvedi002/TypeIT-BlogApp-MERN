TypeIT Blog App – Fullstack Documentation
How to run
Frontend

Open terminal in frontend folder and run this command 👉🏼 npm install
Backend

Open terminal in backend folder and run this command 👉🏼 node server seed
NOTE :- ONLY 1 TIME --> to store admin data in backend
for the next time if you want to run backend then use this command 👉🏼 npm start
Table of Contents
Overview
Frontend
Frontend Project Structure
Frontend Technology Stack
Frontend Installation & Setup
Frontend Architecture
Frontend Components
Frontend Pages
Frontend Configuration
Frontend Development
Frontend Build & Deployment
Backend
Backend Project Structure
Backend Technology Stack
Backend Installation & Setup
Backend Architecture
Database Models
Controllers
Routes
Middlewares
Utilities
Backend Configuration
API Endpoints
Backend Development
Backend Security
Contributing
License
Overview
TypeIT Blog App is a fullstack blogging platform built with a modern React frontend, powered by Vite and styled with Tailwind CSS, and a Node.js backend with Express.js and MongoDB. The application provides users with seamless blog reading and interaction, while maintainers benefit from a comprehensive admin dashboard, powerful content management features, and robust security, scalability, and image handling.

Key Features
Modern React 19+ frontend with Vite HMR
Node.js REST API backend with Express.js
MongoDB database with Mongoose ODM
JWT-based authentication with HTTP-only cookies
Role-based access control (Admin/User)
Image upload and management via ImageKit
Rich text editing with Quill editor
Comment moderation system
Blog CRUD operations with publish/draft status
Responsive design using Tailwind CSS
Category-based blog filtering
Newsletter subscription
Social media integration
Frontend
Frontend Project Structure
frontend/
├── public/
│   ├── favicon.svg
│   └── vite.svg
├── src/
│   ├── assets/
│   │   ├── *.svg (icons)
│   │   ├── *.png (images)
│   │   ├── assets.js
│   │   └── rich-text-css.txt
│   ├── components/
│   │   ├── admin/
│   │   │   ├── CommentTableItem.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Sidebar.jsx
│   │   │   └── TableItem.jsx
│   │   ├── BlogCard.jsx
│   │   ├── BlogList.jsx
│   │   ├── Footer.jsx
│   │   ├── Header.jsx
│   │   ├── Loader.jsx
│   │   ├── Navbar.jsx
│   │   └── NewsLetter.jsx
│   ├── pages/
│   │   ├── admin/
│   │   │   ├── AddBlog.jsx
│   │   │   ├── BlogLists.jsx
│   │   │   ├── Comments.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   └── Layout.jsx
│   │   ├── Blog.jsx
│   │   └── Home.jsx
│   ├── App.jsx
│   ├── index.css
│   └── main.jsx
├── .gitignore
├── README.md
├── bun.lock
├── eslint.config.js
├── index.html
├── package-lock.json
├── package.json
└── vite.config.js
Frontend Technology Stack
Core Technologies
React 19+ - Frontend library with latest features
Vite 7+ - Build tool and development server
React Router DOM 7+ - Client-side routing
Tailwind CSS 4+ - Utility-first CSS framework
Key Dependencies
Quill 2.0 - Rich text editor for blog content
Motion 12+ - Animation library
Moment.js 2.30 - Date/time manipulation
@tailwindcss/vite - Tailwind integration for Vite
Development Tools
ESLint 9+ - Code linting and formatting
@vitejs/plugin-react - React support for Vite
TypeScript types - Type definitions for React
Frontend Installation & Setup
Prerequisites
Node.js 18+ or Bun runtime
npm, yarn, or bun package manager
Installation Steps
Clone the repository

git clone https://github.com/Wolfgang281/TypeIT-BlogApp.git
cd TypeIT-BlogApp/frontend
Install dependencies

npm install
# or
bun install
Start development server

npm run dev
# or
bun run dev
Build for production

npm run build
# or
bun run build
Available Scripts
Script	Description
npm run dev	Start development server with HMR
npm run build	Build production bundle
npm run lint	Run ESLint code analysis
npm run preview	Preview production build locally
Frontend Architecture
Application Entry Points
main.jsx - The main entry point that renders the React application:

import { createRoot } from "react-dom/client";
import "./index.css";
import App from "./App.jsx";
import { BrowserRouter } from "react-router-dom";

createRoot(document.getElementById("root")).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
App.jsx - Central routing configuration connecting all pages:

import React from "react";
import { Routes, Route } from "react-router-dom";
// Import statements for all components and pages
// Route definitions for public and admin sections
Routing Structure
Public Routes:

/ - Home page with blog listings
/blog/:id - Individual blog post view
Admin Routes:

/admin - Dashboard overview
/admin/addBlog - Create new blog posts
/admin/blogLists - Manage existing blogs
/admin/comments - Comment moderation
/admin/login - Admin authentication
Frontend Components
Public Components
Navbar

Location: src/components/Navbar.jsx
Features: Logo display, home navigation
Dependencies: React Router navigation
BlogCard

Location: src/components/BlogCard.jsx
Features: Blog thumbnail, title, category, excerpt
Props: blog object with blog data
Navigation: Links to full blog post
BlogList

Location: src/components/BlogList.jsx
Features: Category filtering, blog grid layout
Dependencies: Motion for animations
State: Menu selection for categories
Header

Location: src/components/Header.jsx
Features: Hero text, search bar, gradient background
Form: Search input for blog discovery
Footer

Location: src/components/Footer.jsx
Features: Dynamic footer sections, social links
Data Source: footer_data from assets
NewsLetter

Location: src/components/NewsLetter.jsx
Features: Email input, subscription form
Styling: Responsive form layout
Loader

Location: src/components/Loader.jsx
Features: Simple loading animation
Usage: Displayed during data fetching
Admin Components
Login

Location: src/components/admin/Login.jsx
Features: Email/password form, credential validation
State: Email and password management
Styling: Centered form layout
Sidebar

Location: src/components/admin/Sidebar.jsx
Features: Navigation menu, active state highlighting
Navigation: Links to all admin sections
Icons: SVG icons for each menu item
TableItem

Location: src/components/admin/TableItem.jsx
Props: blog, fetchBlogs, index
Features: Blog info display, status indicator, delete action
Status: Published/Draft indication
CommentTableItem

Location: src/components/admin/CommentTableItem.jsx
Props: comment, fetchComments
Features: Comment details, approval actions, delete option
Actions: Approve/delete comment functionality
Frontend Pages
Public Pages
Home

Location: src/pages/Home.jsx
Components: Navbar, Header, BlogList, NewsLetter, Footer
Layout: Vertical stack of main sections
Blog

Location: src/pages/Blog.jsx
Features:
Full blog content display
Comment section with form
Social sharing buttons
Related blog suggestions
State Management: Blog data, comments, form inputs
Dependencies: Moment.js for date formatting
Admin Pages
Layout

Location: src/pages/admin/Layout.jsx
Features:
Header with logo and logout
Sidebar integration
Content area with React Router Outlet
Navigation: Home navigation and logout functionality
Dashboard

Location: src/pages/admin/Dashboard.jsx
Features:
Blog, comment, and draft counters
Recent blogs table
Dashboard statistics cards
State: Dashboard data from assets
Components: TableItem for blog rows
AddBlog

Location: src/pages/admin/AddBlog.jsx
Features:
Image upload with preview
Title and subtitle inputs
Rich text editor (Quill)
Category selection
Publish toggle
Editor: Quill integration with snow theme
State: Form fields and image handling
BlogLists

Location: src/pages/admin/BlogLists.jsx
Features:
All blogs table display
Blog management actions
Status filtering
Components: TableItem for each blog row
Data: Blog data from assets
Comments

Location: src/pages/admin/Comments.jsx
Features:
Comment filtering (Approved/Not Approved)
Comment approval actions
Comment deletion
State: Comments list and filter selection
Components: CommentTableItem for each comment
Frontend Configuration
Vite Configuration
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";
import tailwindcss from "@tailwindcss/vite";

export default defineConfig({
  plugins: [react(), tailwindcss()],
});
ESLint Configuration
Modern ESLint configuration with React-specific rules:

React hooks linting
React refresh integration
Browser globals
Unused variables handling
Tailwind CSS Setup
Integration: Via Vite plugin
Theme: Custom primary color (#5044e5)
Fonts: Outfit font family from Google Fonts
Customizations: Scrollbar hiding, rich text styles
Rich Text Styling
Comprehensive CSS rules for Quill editor output:

Heading hierarchy (h1-h6)
Paragraph spacing
List styling (ordered/unordered)
Link styling
Strong text emphasis
Frontend Development
Code Organization
Components: Functional components with hooks
State Management: React hooks (useState, useEffect)
Routing: React Router DOM with nested routes
Styling: Tailwind utility classes with custom CSS variables
Assets: Centralized asset management via assets.js
Best Practices
ESLint configuration enforces code quality
Responsive design patterns
Component reusability
Separation of concerns (components vs pages)
Proper prop validation and handling
Development Workflow
Component development in isolation
Integration with routing
Styling with Tailwind utilities
Testing with development server
Linting before commits
Frontend Build & Deployment
Production Build
npm run build
Generates optimized bundle in dist/ directory with:

Minified JavaScript and CSS
Asset optimization
Code splitting
Tree shaking for unused code elimination
Preview Production Build
npm run preview
Serves the production build locally for verification.

Environment Considerations
Development: Hot module replacement, source maps
Production: Optimized bundles, asset hashing
Browser Support: Modern browsers with ES6+ support
Backend
Backend Project Structure
backend/
├── src/
│   ├── config/
│   │   ├── database.js
│   │   └── imageKit.config.js
│   ├── controllers/
│   │   ├── admin.controller.js
│   │   ├── blog.controller.js
│   │   └── comment.controller.js
│   ├── middlewares/
│   │   ├── auth.middleware.js
│   │   ├── error.middleware.js
│   │   └── multer.middleware.js
│   ├── models/
│   │   ├── blog.model.js
│   │   ├── comment.model.js
│   │   └── user.model.js
│   ├── routes/
│   │   ├── auth.route.js
│   │   ├── blog.routes.js
│   │   └── comment.routes.js
│   ├── seed/
│   │   └── admin.seed.js
│   └── utils/
│       ├── Error.util.js
│       ├── imageKit.util.js
│       └── jwt.util.js
├── .gitignore
├── bun.lock
├── package-lock.json
├── package.json
└── server.js
Backend Technology Stack
Core Technologies
Node.js - Runtime environment
Express.js 5+ - Web application framework
MongoDB - NoSQL database
Mongoose 8+ - MongoDB object modeling
Key Dependencies
Production Dependencies

@imagekit/nodejs - ImageKit SDK for image management
bcryptjs - Password hashing and comparison
cookie-parser - Cookie parsing middleware
cors - Cross-Origin Resource Sharing
dotenv - Environment variable management
express-async-handler - Async error handling wrapper
joi - Schema validation
jsonwebtoken - JWT token generation and verification
multer - Multipart/form-data file upload handling
Development Dependencies

@esbuild-kit/esm-loader - ESM module loader for development
nodemon - Auto-restart development server
Backend Installation & Setup
Prerequisites
Node.js 16+ or Bun runtime
MongoDB database (local or cloud)
ImageKit account with API credentials
Environment Variables
Create a .env file in the backend root directory:

# Server Configuration
PORT=9000
NODE_ENV=development

# Database
MONGO_URL=mongodb://localhost:27017/typeit-blog

# JWT Secret
JWT_SECRET=your_jwt_secret_key_here

# Admin Credentials (for seeding)
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=securePassword123

# ImageKit Configuration
IMAGEKIT_PUBLIC_KEY=your_imagekit_public_key
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
IMAGEKIT_URL_ENDPOINT=https://ik.imagekit.io/your_id
Installation Steps
Clone the repository

git clone https://github.com/Wolfgang281/TypeIT-BlogApp.git
cd TypeIT-BlogApp/backend
Install dependencies

npm install
# or
bun install
Seed admin user

npm start seed
# or
bun run start seed
Start development server

npm start
# or
bun start
Available Scripts
Script	Description
npm start	Start server with nodemon and ESM loader
npm start seed	Seed admin user into database
npm test	Run tests (not configured)
Backend Architecture
Application Entry Point (server.js)
The main server file initializes the Express application with the following setup:

import dotenv from "dotenv";
dotenv.config();
import express from "express";
import cors from "cors";
import cookieParser from "cookie-parser";

// Database connection
connectDB();

// Admin seeding (if 'seed' argument passed)
if (process.argv[2] === "seed") {
  seedAdmin();
}

// Middleware setup
app.use(cors({ credentials: true, origin: "http://localhost:5173" }));
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(cookieParser());

// Routes
app.use("/api/admin", authRoutes);
app.use("/api/blogs", authenticate, authorize, blogRoutes);

// Error handling
app.use(errorMiddleware);
Database Configuration
Location: src/config/database.js

Establishes MongoDB connection using Mongoose:

export const connectDB = expressAsyncHandler(async () => {
  let client = await mongoose.connect(process.env.MONGO_URL);
  console.log(`Database connected to: ${client.connection.host}`);
});
ImageKit Configuration
Location: src/config/imageKit.config.js

Configures ImageKit SDK for image upload and management:

export const imagekit = new ImageKit({
  publicKey: process.env.IMAGEKIT_PUBLIC_KEY,
  privateKey: process.env.IMAGEKIT_PRIVATE_KEY,
  urlEndpoint: process.env.IMAGEKIT_URL_ENDPOINT,
});
Database Models
Blog Model
Location: src/models/blog.model.js

Schema Definition:

{
  title: String (required),
  subTitle: String (required),
  description: String (required),
  image: String (required),
  category: String (required),
  isPublished: Boolean (default: false),
  timestamps: true
}
Features:

Automatic timestamp generation (createdAt, updatedAt)
Published/draft status management
Category-based organization
Image URL storage
Comment Model
Location: src/models/comment.model.js

Schema Definition:

{
  blogId: ObjectId (ref: "Blog", required),
  name: String (required),
  content: String (required),
  isApproved: Boolean (default: false),
  timestamps: true
}
Features:

Blog reference via ObjectId
Comment moderation with approval status
Automatic timestamp tracking
Mongoose automatically maps "Comment" model to "comments" collection
User Model
Location: src/models/user.model.js

Schema Definition:

{
  email: String (required, unique),
  password: String (required),
  isAdmin: Boolean (default: false),
  timestamps: true
}
Pre-save Hook:

Automatically hashes password before saving using bcrypt
Only hashes if password is modified
Methods:

matchPassword(enteredPassword) - Compares entered password with hashed password
Controllers
Admin Controller
Location: src/controllers/admin.controller.js

Handles administrative operations and authentication.

Functions:

login

Validates user credentials
Generates JWT token
Sets HTTP-only cookie with 90-day expiration
Returns success response
logout

Clears authentication cookie
Returns logout confirmation
getAllBlogs

Fetches all blogs (published and drafts) sorted by creation date
Returns blog list for admin management
getAllComments

Retrieves all comments with blog population
Sorted by creation date (newest first)
Returns comments for moderation
getDashboard

Aggregates dashboard statistics:
Total blogs count
Total comments count
Draft blogs count
Recent 5 blogs
Returns comprehensive dashboard data
deleteComment

Deletes comment by ID
Returns success confirmation
approveComment

Updates comment approval status
Returns success confirmation
Blog Controller
Location: src/controllers/blog.controller.js

Manages blog CRUD operations and publication status.

Functions:

addBlog

Handles multipart form data with image upload
Converts image buffer to base64
Uploads image to ImageKit
Creates blog entry with image URL
Returns created blog object
getBlogs

Fetches all published blogs
Returns array of published blogs
getBlog

Retrieves single published blog by ID
Returns blog details or 404 error
deleteBlog

Deletes blog by ID
Cascades deletion to all associated comments
Returns success confirmation
TODO: Delete image from ImageKit
updateBlog

Updates blog fields by ID
Returns updated blog object
togglePublish

Toggles isPublished status
Saves and returns updated blog
Comment Controller
Location: src/controllers/comment.controller.js

Handles comment creation and retrieval.

Functions:

addComment

Creates new comment with blog reference
Sets default approval status to false
Returns created comment
getBlogComments

Fetches approved comments for specific blog
Sorted by creation date (newest first)
Returns filtered comment list
Routes
Authentication Routes
Location: src/routes/auth.route.js

Method	Endpoint	Middleware	Controller	Description
POST	/api/admin/login	-	login	Admin login
POST	/api/admin/logout	authenticate	logout	Admin logout
Blog Routes
Location: src/routes/blog.routes.js

All routes protected with authenticate and authorize middleware.

Method	Endpoint	Middleware	Controller	Description
POST	/api/blogs/add	upload.single("image")	addBlog	Create new blog
GET	/api/blogs/all	-	getBlogs	Get all published blogs
GET	/api/blogs/:id	-	getBlog	Get single blog
PATCH	/api/blogs/:id	-	updateBlog	Update blog
DELETE	/api/blogs/:id	-	deleteBlog	Delete blog
PATCH	/api/blogs/update-publish/:id	-	togglePublish	Toggle publish status
Comment Routes
Location: src/routes/comment.routes.js

Method	Endpoint	Controller	Description
POST	/api/comments/add	addComment	Add new comment
GET	/api/comments/comments/:id	getBlogComments	Get blog comments
Middlewares
Authentication Middleware
Location: src/middlewares/auth.middleware.js

authenticate

Extracts JWT token from cookies or Authorization header
Verifies token using JWT_SECRET
Fetches user from database
Attaches user object to request
Returns 401 if token invalid or missing
authorize

Checks if authenticated user has admin privileges
Returns 403 if user is not admin
Allows request to proceed if admin
Error Middleware
Location: src/middlewares/error.middleware.js

Comprehensive error handling for various error types:

Handled Error Types:

MulterError - File upload errors (size limit, unexpected field)
ImageKit Errors - Image upload/transformation failures
MongoParseError - Invalid MongoDB configuration
ValidationError - Mongoose validation failures
CastError - Invalid MongoDB ObjectId
Default Errors - Generic server errors
Error Response Structure:

{
  success: false,
  message: "Error message",
  errObj: { /* original error object */ },
  errStack: "stack trace (development only)"
}
Multer Middleware
Location: src/middlewares/multer.middleware.js

Configures file upload handling:

Uses memory storage (files stored in buffer)
No disk storage for security
Files processed and uploaded to ImageKit immediately
const storage = multer.memoryStorage();
const upload = multer({ storage });
Utilities
Custom Error Utility
Location: src/utils/Error.util.js

Custom error class extending native Error:

class CustomError extends Error {
  constructor(message, statusCode) {
    super(message);
    this.statusCode = statusCode;
  }
}
Usage: Throw errors with specific HTTP status codes

ImageKit Utility
Location: src/utils/imageKit.util.js

Handles image upload to ImageKit:

export const uploadImage = expressAsyncHandler(async (file) => {
  const response = await imagekit.upload({
    file, // base64 data string
    fileName: `blog-${Date.now()}.webp`,
    folder: "/blogs",
  });
  return response.url;
});
Features:

Accepts base64 encoded image data
Generates unique filename with timestamp
Uploads to /blogs folder in ImageKit
Returns uploaded image URL
JWT Utility
Location: src/utils/jwt.util.js

JWT token generation:

export const generateToken = (id) => {
  return jwt.sign({ id }, process.env.JWT_SECRET, { expiresIn: "30d" });
};
Features:

Signs token with user ID payload
30-day expiration
Uses environment variable for secret
Backend Configuration
Admin Seeding
Location: src/seed/admin.seed.js

Seeds initial admin user:

export const seedAdmin = expressAsyncHandler(async (req, res, next) => {
  const email = process.env.ADMIN_EMAIL;
  const password = process.env.ADMIN_PASSWORD;

  const existingUser = await userModel.findOne({ email });

  if (!existingUser) {
    await userModel.create({
      email,
      password,
      isAdmin: true,
    });
    console.log(`Admin Data added Successfully!!!`);
  } else {
    console.log(`Admin already present, skipping seeding!!!!`);
  }
});
Usage:

npm start seed
API Endpoints
Complete API Reference
Authentication Endpoints
Login

POST /api/admin/login
Content-Type: application/json

Body:
{
  "email": "admin@example.com",
  "password": "password123"
}

Response:
{
  "success": true,
  "message": "Login successful"
}
Logout

POST /api/admin/logout
Cookie: token=<jwt_token>

Response:
{
  "success": true,
  "message": "Logout successful"
}
Blog Endpoints
Create Blog

POST /api/blogs/add
Authorization: Bearer <token>
Content-Type: multipart/form-data

Body:
- title: string
- subTitle: string
- description: string (HTML content)
- category: string
- isPublished: boolean
- image: file

Response:
{
  "success": true,
  "message": "Blog added successfully",
  "blog": { /* blog object */ }
}
Get All Published Blogs

GET /api/blogs/all

Response:
{
  "success": true,
  "message": "Blogs fetched successfully",
  "blogs": [ /* array of blogs */ ]
}
Get Single Blog

GET /api/blogs/:id

Response:
{
  "success": true,
  "message": "Blog fetched successfully",
  "blog": { /* blog object */ }
}
Update Blog

PATCH /api/blogs/:id
Authorization: Bearer <token>
Content-Type: application/json

Body:
{
  "title": "Updated title",
  "subTitle": "Updated subtitle",
  // any other fields to update
}

Response:
{
  "success": true,
  "message": "Blog updated successfully",
  "blog": { /* updated blog */ }
}
Delete Blog

DELETE /api/blogs/:id
Authorization: Bearer <token>

Response:
{
  "success": true,
  "message": "Blog deleted successfully"
}
Toggle Publish Status

PATCH /api/blogs/update-publish/:id
Authorization: Bearer <token>

Response:
{
  "success": true,
  "message": "Blog updated successfully",
  "blog": { /* updated blog */ }
}
Comment Endpoints
Add Comment

POST /api/comments/add
Content-Type: application/json

Body:
{
  "blogId": "blog_object_id",
  "name": "Commenter Name",
  "content": "Comment content"
}

Response:
{
  "success": true,
  "message": "Comment added for review",
  "comment": { /* comment object */ }
}
Get Blog Comments

GET /api/comments/comments/:id

Response:
{
  "success": true,
  "message": "Comments fetched successfully",
  "comments": [ /* array of approved comments */ ]
}
Admin Dashboard Endpoints
Get Dashboard Data

GET /api/admin/dashboard
Authorization: Bearer <token>

Response:
{
  "success": true,
  "message": "Dashboard fetched successfully",
  "recentBlogs": [ /* recent 5 blogs */ ],
  "blogs": 42,
  "comments": 156,
  "drafts": 8
}
Get All Comments (Admin)

GET /api/admin/comments
Authorization: Bearer <token>

Response:
{
  "success": true,
  "message": "Comments fetched successfully",
  "comments": [ /* all comments with blog data */ ]
}
Approve Comment

PATCH /api/admin/approve-comment
Authorization: Bearer <token>
Content-Type: application/json

Body:
{
  "id": "comment_object_id"
}

Response:
{
  "success": true,
  "message": "Comment approved successfully"
}
Delete Comment

DELETE /api/admin/delete-comment
Authorization: Bearer <token>
Content-Type: application/json

Body:
{
  "id": "comment_object_id"
}

Response:
{
  "success": true,
  "message": "Comment deleted successfully"
}
Backend Development
Code Organization
MVC Pattern - Models, Controllers, Routes separation
Middleware Chain - Authentication → Authorization → Controller
Error Handling - Centralized error middleware
Async Handling - express-async-handler for clean async/await
Modular Structure - Separation of concerns
Best Practices Implemented
Password Security - Bcrypt hashing with salt rounds
JWT Authentication - HTTP-only cookies for token storage
Role-Based Access - Admin authorization middleware
Input Validation - Mongoose schema validation
Error Handling - Custom error classes with status codes
File Upload Security - Memory storage with immediate processing
Database Relationships - Proper ObjectId references
Cascade Deletion - Delete related comments when blog deleted
Development Workflow
Define data models with Mongoose schemas
Create controller functions with business logic
Set up routes with appropriate middleware
Test endpoints using Postman or similar tools
Handle errors appropriately
Document API changes
ESM Module Support
The project uses ES6 module syntax with:

"type": "module" in package.json
@esbuild-kit/esm-loader for development
Import/export syntax throughout codebase
Backend Security
Authentication & Authorization
JWT Tokens - Secure token generation with 30-day expiration
HTTP-Only Cookies - Prevents XSS attacks on token storage
Password Hashing - Bcrypt with automatic salt generation
Role-Based Access - Admin-only routes protected with middleware
CORS Configuration
app.use(
  cors({
    credentials: true,
    origin: "http://localhost:5173",
  })
);
Credentials enabled for cookie transmission
Origin restricted to frontend URL
Environment Variables
Sensitive credentials stored in .env file
.gitignore configured to exclude environment files
No hardcoded secrets in codebase
Input Validation
Mongoose schema validation on all models
Required field enforcement
Type checking at schema level
Joi available for additional validation
File Upload Security
Memory storage prevents disk-based attacks
Files processed immediately and uploaded to external service
No direct file system access
Multer error handling for malicious uploads
Contributing
When contributing to TypeIT Blog App:

Frontend Contributions
Follow the established component structure
Use Tailwind CSS for styling
Ensure ESLint passes before committing
Test components in both development and production builds
Maintain responsive design principles
Backend Contributions
Follow the established MVC pattern
Use express-async-handler for all async route handlers
Implement proper error handling with CustomError
Add authentication/authorization where needed
Update this documentation for new endpoints
Test all API endpoints before committing
Follow RESTful conventions for route naming
General Guidelines
Write clean, maintainable code
Add comments for complex logic
Update documentation for new features
Test thoroughly before submitting pull requests
Follow existing code style and conventions
Ensure security best practices are maintained
License
This project is part of the TypeIT Blog App repository. Please refer to the main repository for licensing information.