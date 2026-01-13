# ATTENDANCE-BASED MEAL SYSTEM

The integration of the Free Meal Monitoring System and Security Attendance System enables a unified platform where employee attendance data is securely validated and directly used to determine free meal eligibility. By leveraging RFID-based attendance verification, the system ensures that only authorized and present employees can claim meals, preventing misuse and improving operational efficiency.

This integrated approach provides real-time monitoring, enhanced security, accurate attendance tracking, and automated meal distribution, supported by administrative controls and comprehensive reporting.

<!-- ## 🚀 Features

### 🏠 Employee Interface
- **RFID Tag Reading**: Instant free meal logging via RFID card scanning
- **Real-time Clock**: Live time display with smooth animations
- **Employee Information Display**: Shows employee details, photo, and free meal status
- **Visual Feedback**: Smooth animations and audio feedback for successful/failed scans
- **Status Indicators**: Clear visual indicators for claimed/claimed already status

### 👨‍💼 Admin Dashboard
- **Comprehensive Dashboard**: Overview statistics including total employees, free meal logs, and department metrics
- **Employee Management**: Full CRUD operations for employee records
- **Free Meal Logs**: Detailed free meal tracking with filtering and export capabilities
- **Department Management**: Organize employees by departments and positions
- **Account Management**: Admin user account creation and role management
- **Data Export**: Export attendance data to CSV format
- **Real-time Statistics**: Live dashboard with attendance insights

### 🔐 Security & Authentication
- **NextAuth.js Integration**: Secure authentication system
- **Role-based Access Control**: Different access levels (superadmin, admin, hr)
- **Protected Routes**: Secure admin areas with proper authorization
- **Session Management**: Persistent login sessions with proper security

### 🎨 User Experience
- **Modern UI/UX**: Built with Tailwind CSS and Radix UI components
- **Responsive Design**: Works perfectly on desktop, tablet, and mobile devices
- **Dark/Light Theme Support**: Adaptive theming capabilities
- **Smooth Animations**: Framer Motion animations for enhanced user experience
- **Audio Feedback**: Sound notifications for attendance actions

## 🛠️ Technology Stack

### Frontend
- **Next.js 15.3.1** - React framework with App Router
- **React 19** - Modern React with latest features
- **Tailwind CSS** - Utility-first CSS framework
- **Radix UI** - Headless UI components
- **Framer Motion** - Animation library
- **Lucide React** - Beautiful icons
- **React Hook Form** - Form state management
- **Zod** - Schema validation

### Backend
- **Next.js API Routes** - Serverless API endpoints
- **MySQL 2** - Database connection and queries
- **NextAuth.js** - Authentication and session management
- **bcryptjs** - Password hashing
- **JSON2CSV** - Data export functionality

### Development Tools
- **ESLint** - Code linting
- **PostCSS** - CSS processing
- **Turbopack** - Fast development builds

## 🚀 Getting Started

### Prerequisites
- Node.js 18.0 or higher
- MySQL database server
- RFID reader (compatible with HID keyboard emulation)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/jericocarlos/attendance-based-meal-system.git
   cd attendance-based-meal-system
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Setup**
   Create a `.env.local` file in the root directory:
   ```env
   # Database Configuration
   DB_HOST=localhost
   DB_USER=your_db_username
   DB_PASSWORD=your_db_password
   DB_NAME=db_freemeal

   # NextAuth Configuration
   NEXTAUTH_SECRET=your_nextauth_secret
   NEXTAUTH_URL=http://localhost:3000

   # Application Settings
   NODE_ENV=development
   ```

4. **Database Setup**
   ```bash
   # Create the database
   mysql -u root -p -e "CREATE DATABASE db_freemeal;"
   
   # Import the database schema
   mysql -u root -p db_freemeal < databases/db_freemeal.sql
   
   # Run additional setup if needed
   mysql -u root -p db_freemeal < databases/db_setup.sql
   ```

5. **Create Admin User**
   ```bash
   node scripts/create-user.js
   ```

6. **Start Development Server**
   ```bash
   npm run dev
   ```

7. **Access the Application**
   - Main attendance interface: [http://localhost:3000](http://localhost:3000)
   - Admin dashboard: [http://localhost:3000/admin](http://localhost:3000/admin)

## 📖 Usage

### For Employees
1. Simply tap your RFID card on the reader
2. The system will automatically detect your card and log your free meal claimed
3. Visual and audio feedback will confirm the action
4. Claimed/Claimed Already status is automatically determined based on your last log

### For Administrators
1. Login to the admin dashboard at `/admin/login`
2. Use the dashboard to:
   - View real-time free meal statistics
   - Manage employee records
   - Monitor free meal logs
   - Export free meal data
   - Manage departments and positions
   - Create additional admin accounts

## 🏗️ Project Structure

```
freemeal-monitoring-system/
├── app/                          # Next.js App Router
│   ├── admin/                    # Admin dashboard pages
│   │   ├── (root)/              # Protected admin routes
│   │   └── login/               # Admin login page
│   ├── api/                     # API routes
│   │   ├── admin/               # Admin API endpoints
│   │   ├── attendance/          # Attendance API endpoints
│   │   └── auth/                # Authentication endpoints
│   └── page.js                  # Main attendance interface
├── components/                   # Reusable UI components
│   ├── auth/                    # Authentication components
│   ├── layout/                  # Layout components
│   ├── profile/                 # Profile-related components
│   └── ui/                      # Base UI components
├── constants/                    # Application constants
├── databases/                    # Database schemas and setup
├── hooks/                       # Custom React hooks
├── lib/                         # Utility libraries
├── providers/                   # React context providers
├── scripts/                     # Setup and utility scripts
├── services/                    # External service integrations
└── utils/                       # Helper utilities
```

## 🔧 Configuration

### RFID Reader Setup
The system is designed to work with RFID readers that emulate keyboard input (HID mode). Most USB RFID readers support this functionality out of the box.

### Audio Configuration
Audio feedback files are located in `public/sounds/`. You can customize the audio files:
- `success.mp3` - Successful attendance log
- `error.mp3` - Failed attendance attempt
- `aray-ko.mp3` - Custom audio feedback
- `ml-voice.mp3` - Voice feedback

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `DB_HOST` | MySQL database host | Yes |
| `DB_USER` | MySQL username | Yes |
| `DB_PASSWORD` | MySQL password | Yes |
| `DB_NAME` | Database name | Yes |
| `NEXTAUTH_SECRET` | NextAuth.js secret key | Yes |
| `NEXTAUTH_URL` | Application URL | Yes |

### SMTP (Email) Configuration

To enable sending CSV reports via email, set the following environment variables (use Mailtrap for testing):

- `SMTP_HOST`
- `SMTP_PORT`
- `SMTP_USER`
- `SMTP_PASS`
- `FROM_EMAIL` (sender address used in outgoing messages)

**Usage:** On the Admin → Free Meal Logs page click the **Send Email** button, enter the recipient email address, and an email with the CSV attachment will be sent using the configured SMTP provider (Mailtrap recommended for development/testing).


## 🚀 Deployment

### Production Build
```bash
npm run build
npm start
```

### Environment Setup for Production
1. Set up MySQL database on your production server
2. Configure environment variables for production
3. Ensure RFID reader drivers are installed on the client machines
4. Set up proper SSL certificates for HTTPS (recommended)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

For support and questions:
- Create an issue in the GitHub repository
- Check the documentation in the `/docs` folder (if available)
- Review the API documentation in the codebase

## 🙏 Acknowledgments

- Built with [Next.js](https://nextjs.org/)
- UI components from [Radix UI](https://www.radix-ui.com/)
- Icons from [Lucide](https://lucide.dev/)
- Styling with [Tailwind CSS](https://tailwindcss.com/)
- Animations powered by [Framer Motion](https://www.framer.com/motion/) -->
