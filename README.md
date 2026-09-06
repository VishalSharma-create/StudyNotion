# StudyNotion - EdTech Learning Platform

A comprehensive full-stack educational technology platform that enables instructors to create and manage courses while allowing students to learn and progress through structured course content.

## 🌟 Features

### For Students

- **User Authentication** - Secure signup, login, and email verification
- **Course Enrollment** - Browse and enroll in available courses
- **Course Dashboard** - Track enrolled courses and learning progress
- **Interactive Learning** - Watch course videos, complete sections and subsections
- **Progress Tracking** - Monitor course completion percentage and performance
- **Ratings & Reviews** - Rate and review completed courses
- **Wishlist** - Save favorite courses for later
- **Payment Integration** - Secure course purchases via Razorpay
- **Profile Management** - Update profile information and settings

### For Instructors

- **Course Creation** - Create and manage courses with multiple sections
- **Content Management** - Organize course content into sections and subsections
- **Video Upload** - Upload course videos to Cloudinary
- **Analytics** - Track student enrollment and course performance
- **Revenue Tracking** - Monitor course sales and earnings
- **Course Catalog** - Organize courses by category

### Admin Features

- **Category Management** - Create and manage course categories
- **Platform Statistics** - View platform-wide analytics
- **User Management** - Manage users and their roles

## 🛠️ Tech Stack

### Frontend

- **React.js** (v18.2.0) - UI library
- **Redux & Redux Toolkit** - State management
- **React Router DOM** (v6.9.0) - Routing
- **Tailwind CSS** - Styling
- **Axios** - HTTP client
- **React Hook Form** - Form handling
- **React Hot Toast** - Notifications
- **Chart.js** - Analytics visualizations

### Backend

- **Node.js** - Runtime environment
- **Express.js** (v4.18.2) - Web framework
- **MongoDB** (v7.0.3) - Database
- **Mongoose** - ODM for MongoDB
- **JWT** - Authentication
- **Bcrypt** - Password encryption
- **Nodemailer** - Email service
- **Cloudinary** - Image/Video storage
- **Razorpay** - Payment gateway

### DevOps & Tools

- **Nodemon** - Development auto-reload
- **dotenv** - Environment variables
- **Concurrently** - Run multiple processes

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v14 or higher)
- **npm** (v6 or higher)
- **MongoDB** (local or Atlas connection string)
- **Git**

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/studynotion-edtech-project.git
cd studynotion-edtech-project-main
```

### 2. Install Client Dependencies

```bash
npm install
```

### 3. Install Server Dependencies

```bash
cd server
npm install
cd ..
```

### 4. Configure Environment Variables

#### Backend (.env)

Create a `.env` file in the `server` directory:

```env
# Server Configuration
PORT=4000

# Database
MONGODB_URL=your_mongodb_connection_string

# JWT Secret
JWT_SECRET=your_jwt_secret_key

# Email Configuration (Nodemailer)
MAIL_HOST=smtp.gmail.com
MAIL_USER=your_email@gmail.com
MAIL_PASS=your_app_password

# Cloudinary Configuration
CLOUD_NAME=your_cloudinary_name
API_KEY=your_cloudinary_api_key
API_SECRET=your_cloudinary_api_secret

# Razorpay Configuration
RAZORPAY_KEY=your_razorpay_key_id
RAZORPAY_SECRET=your_razorpay_key_secret
```

#### Frontend (.env)

Create a `.env` file in the root directory:

```env
REACT_APP_API_BASE_URL=http://localhost:4000/api/v1
```

### 5. Setup Instructions

#### MongoDB

- Create a MongoDB Atlas account or set up a local MongoDB instance
- Get your connection string and add it to the server `.env` file

#### Cloudinary

- Sign up at [Cloudinary](https://cloudinary.com/)
- Get your cloud name, API key, and API secret
- Add them to the server `.env` file

#### Razorpay

- Create a Razorpay account at [Razorpay](https://razorpay.com/)
- Get your API key and secret from the dashboard
- Add them to the server `.env` file

#### Email Service

- Enable "Less secure app access" in your Gmail account settings, OR
- Generate an [App Password](https://support.google.com/accounts/answer/185833) for Gmail
- Add credentials to the server `.env` file

## 🏃 Running the Project

### Start Both Frontend and Backend Concurrently

```bash
npm run dev
```

### Start Backend Only

```bash
cd server
npm run dev
```

Backend will run on `http://localhost:4000`

### Start Frontend Only

```bash
npm start
```

Frontend will run on `http://localhost:3000`

## 📁 Project Structure

```
studynotion-edtech-project/
├── public/                 # Static files
├── server/                 # Backend (Node.js + Express)
│   ├── config/            # Database, Cloudinary, Razorpay config
│   ├── controllers/       # Route controllers
│   ├── models/           # MongoDB schemas
│   ├── routes/           # API routes
│   ├── middleware/       # Custom middleware
│   ├── mail/            # Email templates
│   ├── utils/           # Utility functions
│   └── index.js         # Server entry point
├── src/                   # Frontend (React)
│   ├── components/       # Reusable React components
│   ├── pages/           # Page components
│   ├── slices/          # Redux slices
│   ├── services/        # API services
│   ├── utils/           # Utility functions
│   ├── hooks/           # Custom React hooks
│   ├── data/            # Static data
│   ├── App.jsx
│   └── index.js
├── package.json         # Root dependencies
└── README.md           # Project documentation
```

## 🔌 API Endpoints

### Authentication

- `POST /api/v1/auth/signup` - User registration
- `POST /api/v1/auth/login` - User login
- `POST /api/v1/auth/sendotp` - Send OTP for verification
- `POST /api/v1/auth/changepassword` - Change password
- `POST /api/v1/auth/reset-password-token` - Request password reset

### Courses

- `GET /api/v1/course/getAllCourses` - Get all courses
- `GET /api/v1/course/getCourseDetails` - Get course details
- `POST /api/v1/course/createCourse` - Create a new course (Instructor)
- `POST /api/v1/course/addSectionToourse` - Add section to course
- `POST /api/v1/course/updateSection` - Update course section
- `DELETE /api/v1/course/deleteSection` - Delete course section

### Payments

- `POST /api/v1/payment/capturePayment` - Initiate payment
- `POST /api/v1/payment/verifySignature` - Verify payment signature
- `POST /api/v1/payment/sendPaymentSuccessEmail` - Send success email

### User Profile

- `GET /api/v1/profile/getUserDetails` - Get user profile
- `PUT /api/v1/profile/updateProfile` - Update user profile
- `PUT /api/v1/profile/updateProfilePicture` - Update profile picture

### Contact

- `POST /api/v1/reach/contact` - Submit contact form

## 📊 Database Models

### User

- Email, password (hashed)
- First name, last name
- Role (Student/Instructor/Admin)
- Profile reference
- Enrolled courses
- Created courses

### Course

- Title, description
- Category
- Instructor reference
- Sections with subsections
- Ratings and reviews
- Thumbnail image

### Section

- Title, description
- Course reference
- Subsections array

### OTP

- Email
- OTP code
- Expiration time

### CourseProgress

- User reference
- Course reference
- Completed subsections
- Progress percentage

## 🐛 Troubleshooting

### Server won't start

- Ensure MongoDB is running and connection string is correct
- Check all environment variables are set in `.env`
- Verify Node.js version is v14 or higher

### Frontend compilation errors

- Delete `node_modules` folder and `package-lock.json`
- Run `npm install` again
- Clear npm cache: `npm cache clean --force`

### Nodemon not found

- Run `npm install` in the server directory
- On Windows, try: `npx nodemon server/index.js`

### Port already in use

- Backend: Change PORT in `.env` file
- Frontend: Use: `PORT=3001 npm start`

## 🔒 Security Notes

- All passwords are hashed using bcrypt
- JWT tokens for authentication
- CORS enabled for frontend-backend communication
- Environment variables for sensitive data
- Input validation on both frontend and backend

## 📝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/AmazingFeature`
3. Commit your changes: `git commit -m 'Add some AmazingFeature'`
4. Push to the branch: `git push origin feature/AmazingFeature`
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License - see the LICENSE file for details.

## 👨‍💻 Author

**Saikat Mukherjee**

## 🤝 Support

For support, email your_email@example.com or open an issue in the repository.

## 🔗 Useful Links

- [MongoDB Documentation](https://docs.mongodb.com/)
- [Express.js Documentation](https://expressjs.com/)
- [React Documentation](https://react.dev/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Redux Documentation](https://redux.js.org/)

---

**Happy Learning! 🚀**
