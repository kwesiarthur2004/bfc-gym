# Body Fitness Center - Gym Membership Management System

Private administrative system for authorized personnel only. Not accessible to gym members or clients.

## Project Overview

Full-stack web application for gym staff to manage members, track attendance, generate reports, and monitor membership status.

## System Features

- **Authentication**: Secure admin login with session-based authentication
- **Member Management**: Add, view, update, delete members with status tracking
- **Check-In System**: Quick member check-in with real-time validation
- **Dashboard**: Key metrics overview (members, attendance, expirations)
- **Attendance Tracking**: Complete history with filtering and pagination
- **Reports**: Generate attendance, membership, and financial reports

## Technologies Used

**Frontend**: HTML5, CSS3, JavaScript (ES6+), Fetch API

**Backend**: Node.js, Express.js, MySQL, mysql2, bcrypt, express-session, CORS

## System Architecture

- **Frontend**: Static HTML pages with external CSS/JS, responsive design
- **Backend**: RESTful API with MVC pattern, session-based auth, connection pooling
- **Database**: MySQL with tables for admins, members, and checkins

## Installation & Setup

### Prerequisites
- Node.js (v14+)
- MySQL Server (v5.7+)
- npm

### Backend Setup

1. `cd Backend && npm install`
2. Create `.env` file:
```env
DB_HOST=localhost
DB_USER=your_username
DB_PASSWORD=your_password
DB_NAME=bfc_gym_db
DB_PORT=3306
PORT=3000
SESSION_SECRET=your-secret-key
FRONTEND_URL=http://localhost:5500
```
3. Setup database:
   - Option 1 (Recommended): Run the setup script:
     ```bash
     mysql -u your_username -p < setup.sql
     ```
   - Option 2: Manually create database and tables (see setup.sql for SQL commands)
4. Start server: `npm start` (or `npm run dev` for development)

## Login Instructions

**Default Admin Credentials:**
- Username: `admin`
- Password: `admin123`

**To Log In:**
1. Start the backend server (port 3000)
2. Open the frontend login page: `http://localhost:5500/login.html`
3. Enter the admin username and password
4. Click "Login" to access the dashboard

**To Create Additional Admin Accounts:**
```sql
INSERT INTO admins (username, password, name, role) 
VALUES ('your_username', 'your_password', 'Your Name', 'administrator');
```

**Note:** For production, use bcrypt to hash passwords:
```javascript
const bcrypt = require('bcrypt');
const hashedPassword = await bcrypt.hash('your_password', 10);
// Then use hashedPassword in the INSERT statement
```

### Frontend Setup

1. `cd frontend`
2. Serve files: `python -m http.server 5500` or `npx http-server -p 5500`
3. Open: `http://localhost:5500/login.html`

## API Endpoints

**Authentication**: `/api/auth/login`, `/api/auth/logout`, `/api/auth/me`

**Members**: `/api/members` (GET, POST), `/api/members/:id` (GET, PUT, DELETE), `/api/members/:id/status`

**Check-In**: `/api/checkin` (POST), `/api/checkin/recent`, `/api/checkin/history`

**Dashboard**: `/api/dashboard/stats`

**Attendance**: `/api/attendance/history`

**Reports**: `/api/reports/summary`, `/api/reports/history`, `/api/reports/generate`

## Screenshots

- Login Page
- Dashboard Overview
- Member Check-In Interface
- Attendance History
- Reports Page

## Limitations

- Session-based authentication (not JWT)
- No email notifications
- No payment processing
- Limited report export options
- No real-time notifications
- Single admin account support

## Future Improvements

- JWT Authentication
- Email notifications
- Payment integration
- Advanced reporting (PDF/Excel export, charts)
- Mobile app
- Barcode/QR code scanning
- Multi-branch support
- Role-based access control
- Analytics dashboard
- Automated backups
- API documentation (Swagger/OpenAPI)

## Author

**Ebenezer Kwesi Arthur**

---

## License

Proprietary software developed for Body Fitness Center.
