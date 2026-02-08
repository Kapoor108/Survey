# 🎨 SurveyX Frontend (Client)

## 📁 This is the FRONTEND folder

This folder contains the **React web application** that provides:
- User interface for all roles (Admin, CEO, User)
- Login and authentication UI
- Dashboards and analytics visualization
- Survey creation and completion forms
- Responsive design with Tailwind CSS

---

## 🏗️ Technology Stack

- **Framework**: React 18
- **Styling**: Tailwind CSS
- **Routing**: React Router v6
- **HTTP Client**: Axios
- **State Management**: React Context API
- **Build Tool**: Create React App (Webpack)

---

## 📂 Folder Structure

```
client/
├── public/              # Static files
│   └── index.html       # HTML template
├── src/
│   ├── components/      # Reusable React components
│   │   ├── AdminLayout.js
│   │   ├── CEOLayout.js
│   │   ├── UserLayout.js
│   │   ├── Layout.js
│   │   ├── Footer.js
│   │   ├── CXOLogo.js
│   │   ├── AIChatbot.js
│   │   └── SimplePage.js
│   ├── context/         # React Context providers
│   │   └── AuthContext.js
│   ├── pages/           # Page components
│   │   ├── admin/       # Admin pages
│   │   │   ├── Dashboard.js
│   │   │   ├── Organizations.js
│   │   │   ├── OrgDetails.js
│   │   │   ├── UserDetails.js
│   │   │   ├── Reports.js
│   │   │   ├── SupportTickets.js
│   │   │   ├── SurveyReport.js
│   │   │   └── Templates.js
│   │   ├── ceo/         # CEO pages
│   │   │   ├── Dashboard.js
│   │   │   ├── Departments.js
│   │   │   ├── Employees.js
│   │   │   ├── Surveys.js
│   │   │   └── SurveyAnalytics.js
│   │   ├── user/        # User pages
│   │   │   ├── Dashboard.js
│   │   │   └── Survey.js
│   │   ├── LandingPage.js
│   │   ├── Login.js
│   │   ├── Signup.js
│   │   ├── About.js
│   │   ├── Features.js
│   │   ├── Pricing.js
│   │   ├── Contact.js
│   │   ├── Blog.js
│   │   ├── Careers.js
│   │   ├── Help.js
│   │   ├── API.js
│   │   ├── Integrations.js
│   │   ├── PrivacyPolicy.js
│   │   ├── TermsOfService.js
│   │   ├── CookiePolicy.js
│   │   ├── GDPR.js
│   │   ├── AuthCallback.js
│   │   └── ForgotPassword.js
│   ├── utils/           # Utility functions
│   │   └── api.js       # Axios configuration
│   ├── App.js           # Main app component
│   ├── index.js         # Entry point
│   └── index.css        # Global styles
├── .env.example         # Environment variables template
├── package.json         # Dependencies and scripts
├── postcss.config.js    # PostCSS configuration
├── tailwind.config.js   # Tailwind CSS configuration
├── vercel.json          # Vercel deployment config
└── README.md            # This file
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ installed
- Backend server running (see `../server/README.md`)

### Installation

```bash
# Navigate to client folder
cd client

# Install dependencies
npm install

# Start development server
npm start
```

The app will open at **http://localhost:3000**

---

## 🔐 Environment Variables (Optional)

The app defaults to `http://localhost:5000/api` for the backend.

To use a different backend, create `.env.local`:

```env
REACT_APP_API_URL=http://localhost:5000/api
```

For production backend:
```env
REACT_APP_API_URL=https://your-backend.onrender.com/api
```

**Note**: Environment variables must start with `REACT_APP_`

---

## 🎨 Available Pages

### Public Pages
- `/` - Landing page
- `/login` - Login page (OTP-based)
- `/signup` - Signup page
- `/about` - About page
- `/features` - Features page
- `/pricing` - Pricing page
- `/contact` - Contact page
- `/blog` - Blog page
- `/careers` - Careers page
- `/help` - Help center
- `/api` - API documentation
- `/integrations` - Integrations page
- `/privacy-policy` - Privacy policy
- `/terms-of-service` - Terms of service
- `/cookie-policy` - Cookie policy
- `/gdpr` - GDPR compliance

### Admin Pages (Role: admin)
- `/admin` - Admin dashboard
- `/admin/organizations` - Manage organizations
- `/admin/organizations/:id` - Organization details
- `/admin/users/:id` - User details
- `/admin/reports` - View reports
- `/admin/support-tickets` - Support tickets
- `/admin/survey-report/:id` - Survey report
- `/admin/templates` - Survey templates

### CEO Pages (Role: ceo)
- `/ceo` - CEO dashboard
- `/ceo/departments` - Manage departments
- `/ceo/employees` - Manage employees
- `/ceo/surveys` - Manage surveys
- `/ceo/surveys/:id/analytics` - Survey analytics

### User Pages (Role: user)
- `/dashboard` - User dashboard
- `/surveys/:id` - Take survey

---

## 🎨 Styling

### Tailwind CSS
The app uses Tailwind CSS for styling. Configuration in `tailwind.config.js`.

### Custom Styles
Global styles in `src/index.css`.

### Color Scheme
- Primary: Indigo/Purple gradient
- Secondary: Gray tones
- Accent: Blue, Green, Red for status indicators

---

## 🔒 Authentication Flow

1. User enters email on login page
2. Backend sends OTP to email
3. User enters OTP
4. Backend verifies OTP and returns JWT token
5. Token stored in localStorage
6. Token sent with every API request
7. Auto-redirect based on user role:
   - Admin → `/admin`
   - CEO → `/ceo`
   - User → `/dashboard`

### Protected Routes
All dashboard routes require authentication. Unauthorized users are redirected to `/login`.

---

## 🧩 Key Components

### AuthContext
Manages authentication state globally:
- `user` - Current user object
- `token` - JWT token
- `login()` - Login function
- `logout()` - Logout function
- `isAuthenticated` - Auth status

### Layouts
- `AdminLayout` - Layout for admin pages
- `CEOLayout` - Layout for CEO pages
- `UserLayout` - Layout for user pages
- `Layout` - Layout for public pages

### API Client
`src/utils/api.js` - Axios instance with:
- Base URL configuration
- JWT token interceptor
- Error handling
- Auto-redirect on 401

---

## 📱 Responsive Design

The app is fully responsive:
- **Mobile**: < 768px
- **Tablet**: 768px - 1024px
- **Desktop**: > 1024px

Uses Tailwind's responsive utilities (`sm:`, `md:`, `lg:`, `xl:`)

---

## 🚀 Deployment

### Build for Production

```bash
npm run build
```

Creates optimized build in `build/` folder.

### Deploy to Vercel

1. Push code to GitHub
2. Import project on Vercel
3. Set Root Directory: `client`
4. Add environment variable:
   - `REACT_APP_API_URL` = `https://your-backend.onrender.com/api`
5. Deploy!

See `../DEPLOY_NOW.md` for detailed instructions.

---

## 📝 Scripts

```bash
npm start        # Start development server (port 3000)
npm run build    # Build for production
npm test         # Run tests
npm run eject    # Eject from Create React App (irreversible!)
```

---

## 🎯 Features

### Admin Features
- View all organizations and users
- Create and manage organizations
- Invite users (Admin, CEO, User)
- View system-wide reports
- Manage support tickets
- View survey templates

### CEO Features
- Organization dashboard with metrics
- Create and manage departments
- Invite and manage employees
- Create surveys and assign to departments
- View survey analytics and responses
- Export survey data

### User Features
- Personal dashboard
- View assigned surveys
- Complete surveys
- View survey history
- Track completion status

### Common Features
- OTP-based authentication
- Google OAuth login
- Responsive design
- AI chatbot assistance
- Real-time notifications
- Dark mode support (coming soon)

---

## 🔧 Configuration Files

### `tailwind.config.js`
Tailwind CSS configuration - colors, fonts, breakpoints

### `postcss.config.js`
PostCSS configuration for Tailwind

### `vercel.json`
Vercel deployment configuration - routing rules

### `package.json`
Dependencies, scripts, and project metadata

---

## 🐛 Common Issues

### Port 3000 Already in Use
```bash
# Windows
netstat -ano | findstr :3000
taskkill /PID <PID> /F

# Mac/Linux
lsof -ti:3000 | xargs kill
```

### API Calls Failing
- Check if backend is running on port 5000
- Verify `REACT_APP_API_URL` is correct
- Check browser console for CORS errors

### Build Fails
- Delete `node_modules` and `package-lock.json`
- Run `npm install` again
- Clear npm cache: `npm cache clean --force`

### Blank Page After Deployment
- Check browser console for errors
- Verify environment variables in Vercel
- Check if backend URL is correct

---

## 📚 Dependencies

**Production:**
- react - UI library
- react-dom - React DOM renderer
- react-router-dom - Routing
- axios - HTTP client
- tailwindcss - CSS framework
- recharts - Charts and graphs (for analytics)

**Development:**
- react-scripts - Build tooling
- autoprefixer - CSS vendor prefixes
- postcss - CSS processing

---

## 🎨 Design System

### Typography
- Headings: Font weight 700 (bold)
- Body: Font weight 400 (normal)
- Font family: System fonts (sans-serif)

### Spacing
- Consistent padding/margin using Tailwind scale
- Container max-width: 1280px

### Components
- Buttons: Rounded corners, hover effects
- Cards: Shadow, rounded corners
- Forms: Consistent input styling
- Tables: Striped rows, hover effects

---

## 🧪 Testing

### Manual Testing Checklist
- [ ] Login flow works
- [ ] All roles can access their dashboards
- [ ] Forms submit correctly
- [ ] Navigation works
- [ ] Responsive on mobile
- [ ] No console errors

### Automated Testing (Coming Soon)
```bash
npm test
```

---

## 📞 Support

For issues or questions:
1. Check browser console for errors
2. Verify backend is running
3. Check environment variables
4. See `../DEPLOY_NOW.md` for deployment help

---

## 🔗 Related Files

- Backend: `../server/README.md`
- Deployment: `../DEPLOY_NOW.md`
- Quick Deploy: `../QUICK_DEPLOY_STEPS.md`
- Environment Guide: `../FRONTEND_ENV_GUIDE.md`

---

**This is the FRONTEND - handles all user interface and client-side logic.**

For the backend (API server), see `../server/README.md`
