# Insurance Claim Submission System

A complete full-stack insurance claim management system with user and admin roles, built with Spring Boot and MySQL.

## 🚀 Features

### User Features
- **User Registration & Login** - Secure authentication with role-based access
- **View Insurance Policies** - Browse available insurance policies
- **Submit Claims** - Submit insurance claims with file upload support
- **Track Claim Status** - View real-time status of submitted claims (Pending, Approved, Rejected)
- **Document Management** - Upload and view proof documents (PDF, Images, Docs)

### Admin Features
- **Admin Dashboard** - Comprehensive overview with statistics
- **User Management** - View all registered users
- **Claim Management** - Review, approve, or reject claims
- **Document Access** - View uploaded proof documents
- **Status Updates** - Update claim status in real-time

## 🛠️ Technology Stack

### Backend
- **Java 17**
- **Spring Boot 3.2.0**
- **Spring Data JPA**
- **MySQL 8.0**
- **Maven**

### Frontend
- **HTML5**
- **CSS3** (Modern responsive design)
- **JavaScript** (ES6+)
- **Fetch API** for backend communication

## 📋 Prerequisites

Before running this application, ensure you have the following installed:

1. **Java Development Kit (JDK) 17** or later
2. **Apache Maven 3.6+**
3. **MySQL Server 8.0+**
4. **Modern web browser** (Chrome, Firefox, Safari, Edge)

## 🗂️ Project Structure

```
insurance-claim-system/
├── src/
│   ├── main/
│   │   ├── java/com/insurance/claimsystem/
│   │   │   ├── config/                 # Configuration classes
│   │   │   ├── controller/              # REST API controllers
│   │   │   ├── model/                  # Entity classes
│   │   │   ├── repository/             # JPA repositories
│   │   │   ├── service/                # Business logic services
│   │   │   └── InsuranceClaimSystemApplication.java
│   │   └── resources/
│   │       ├── static/                 # Frontend files
│   │       │   ├── css/                # Stylesheets
│   │       │   ├── js/                 # JavaScript files
│   │       │   ├── admin-dashboard.html
│   │       │   ├── admin-login.html
│   │       │   ├── dashboard.html
│   │       │   ├── login.html
│   │       │   ├── manage-claims.html
│   │       │   ├── my-claims.html
│   │       │   ├── register.html
│   │       │   └── submit-claim.html
│   │       └── application.properties  # Spring Boot configuration
├── uploads/                            # File upload directory (auto-created)
├── pom.xml                            # Maven configuration
└── README.md                          # This file
```

## 🚀 Setup Instructions

### 1. Database Setup

1. **Install MySQL** if not already installed
2. **Start MySQL service**
3. **Create database**:
   ```sql
   CREATE DATABASE insurance_claim_system;
   ```
4. **Create user** (optional, recommended for production):
   ```sql
   CREATE USER 'insurance_user'@'localhost' IDENTIFIED BY 'your_password';
   GRANT ALL PRIVILEGES ON insurance_claim_system.* TO 'insurance_user'@'localhost';
   FLUSH PRIVILEGES;
   ```

### 2. Application Configuration

1. **Navigate to the project directory**:
   ```bash
   cd insurance-claim-system
   ```

2. **Configure database connection** in `src/main/resources/application.properties`:
   ```properties
   # Update these values according to your MySQL setup
   spring.datasource.url=jdbc:mysql://localhost:3306/insurance_claim_system?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true
   spring.datasource.username=root
   spring.datasource.password=your_mysql_password
   ```

### 3. Build and Run the Application

#### Option 1: Using Maven (Recommended)

1. **Build the project**:
   ```bash
   mvn clean install
   ```

2. **Run the application**:
   ```bash
   mvn spring-boot:run
   ```

#### Option 2: Using IDE

1. **Import the project** as a Maven project in your IDE (IntelliJ, Eclipse, etc.)
2. **Run the main class**: `InsuranceClaimSystemApplication.java`

### 4. Access the Application

Once the application starts successfully, you can access:

- **User Registration**: http://localhost:8080/register.html
- **User Login**: http://localhost:8080/login.html
- **Admin Login**: http://localhost:8080/admin-login.html

## 👤 Default Accounts

### Admin Account
- **Email**: admin@insurance.com
- **Password**: admin123

### Test User Account
You can create a test user through the registration page or use the following steps:

1. Go to http://localhost:8080/register.html
2. Fill in the registration form
3. Login with the new credentials at http://localhost:8080/login.html

## 📱 Application Usage

### For Users

1. **Register** a new account or **login** with existing credentials
2. **View available policies** on the dashboard
3. **Submit a claim** by selecting a policy and providing details
4. **Upload supporting documents** (PDF, JPG, PNG, DOC files)
5. **Track claim status** in the "My Claims" section

### For Admins

1. **Login** with admin credentials
2. **View dashboard statistics** (total users, claims, pending approvals)
3. **Manage users** - view all registered users
4. **Review claims** - view claim details and supporting documents
5. **Approve/Reject claims** - update claim status
6. **Filter claims** by status (Pending, Approved, Rejected)

## 🔧 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User/Admin login

### Policies
- `GET /api/policies` - Get all policies
- `GET /api/policies/{id}` - Get policy by ID
- `POST /api/policies` - Create new policy (Admin only)

### Claims
- `POST /api/claims/submit` - Submit new claim
- `GET /api/claims/user/{userId}` - Get claims by user
- `GET /api/claims` - Get all claims (Admin only)
- `PUT /api/claims/{claimId}/status` - Update claim status (Admin only)
- `GET /api/claims/download/{fileName}` - Download claim document

### Admin
- `GET /api/admin/users` - Get all users (Admin only)
- `GET /api/admin/users/{id}` - Get user by ID (Admin only)

## 📁 File Upload

- **Supported formats**: PDF, JPG, JPEG, PNG, DOC, DOCX
- **Maximum file size**: 10MB
- **Storage location**: `uploads/` directory (auto-created)
- **File naming**: UUID-based to prevent conflicts

## 🎨 UI Features

- **Responsive Design** - Works on desktop, tablet, and mobile
- **Modern UI** - Clean, professional interface with smooth animations
- **Real-time Updates** - Dynamic content loading without page refresh
- **User-friendly Forms** - Validation and error handling
- **Interactive Dashboard** - Statistics and quick actions
- **Modal Windows** - Detailed claim views and confirmations

## 🐛 Troubleshooting

### Common Issues

1. **Database Connection Error**:
   - Ensure MySQL is running
   - Check database credentials in `application.properties`
   - Verify database exists

2. **Port Already in Use**:
   - Change port in `application.properties`: `server.port=8081`
   - Or stop the process using port 8080

3. **File Upload Issues**:
   - Ensure `uploads/` directory has write permissions
   - Check file size limits (max 10MB)

4. **Build Errors**:
   - Run `mvn clean install` to resolve dependencies
   - Check Java version (requires JDK 17+)

### Logs

Check the console output for detailed error messages. The application logs show:
- Database connection status
- API request/response details
- Error stack traces

## 🔒 Security Notes

- **Password Storage**: Currently stored as plain text (for demo purposes)
- **Session Management**: Uses localStorage for session persistence
- **CORS**: Enabled for development (restrict in production)
- **File Upload**: Basic validation implemented

## 🚀 Production Deployment

For production deployment, consider:

1. **Database Security**:
   - Use environment variables for credentials
   - Enable SSL for database connections

2. **Application Security**:
   - Implement JWT authentication
   - Add password encryption (BCrypt)
   - Configure proper CORS settings

3. **File Storage**:
   - Use cloud storage (AWS S3, Azure Blob)
   - Implement file virus scanning

4. **Performance**:
   - Add database connection pooling
   - Implement caching
   - Use reverse proxy (Nginx)

## 📞 Support

If you encounter any issues or have questions:

1. Check the troubleshooting section above
2. Review the application logs for detailed error messages
3. Ensure all prerequisites are properly installed and configured

## 📄 License

This project is for educational purposes. Feel free to modify and use it for learning.

---

**Happy Coding! 🎉**
