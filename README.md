

# 🏠 Real Estate Management System  

A full-stack web application for managing property listings, bookings, and client interactions. Built with **Node.js**, **Express**, and **SQL server**, with a responsive frontend using **HTML/CSS/JavaScript**.  

### ✨ **Key Features**  
- **Property Listings**: Add, edit, and browse properties with filters (price, location, type).  
- **User Authentication**: Secure signup/login for agents and clients.  
- **Booking System**: Schedule property visits and manage appointments.  
- **Admin Dashboard**: Manage users, listings, and transactions.  
- **Responsive UI**: Mobile-friendly design with modern CSS.  

### 🛠 **Tech Stack**  
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)  
- **Backend**: Node.js, Express  
- **Database**: MySQL/PostgreSQL (via `db.js`)  
- **Auth**: JWT/Bcrypt  
- **Environment**: Configured with `text.env`  

### 📂 **Project Structure**  
```bash
├── public/          # Static assets (CSS, JS, images)
├── routes/          # Express API routes  
├── views/           # Frontend HTML templates  
├── db.js            # Database connection  
├── server.js        # Backend entry point  
├── package.json     # Dependencies  
└── text.env         # Environment variables  
```

### 🚀 **Setup**  
1. Clone the repo:  
   ```bash
   git clone [your-repo-link]
   ```
2. Install dependencies:  
   ```bash
   npm install
   ```
3. Configure `.env` (rename `text.env`):  
   ```env
   DB_HOST=your_db_host
   DB_USER=your_db_user
   DB_PASS=your_db_password
   JWT_SECRET=your_jwt_secret
   ```
4. Start the server:  
   ```bash
   node server.js
   ```

### 🌟 **Use Cases**  
- Real estate agencies  
- Property rental platforms  
- Personal portfolio project  

Here’s an expanded **Troubleshooting** section to add to your README.md, covering common issues and solutions if the project fails to execute:

---

## 🚨 **Troubleshooting Guide**  

If the project doesn’t run as expected, follow these steps:  

### 1️⃣ **Dependency Issues**  
**Error**: `Module not found` or `npm install fails`  
✅ **Solution**:  
- Delete `node_modules/` and `package-lock.json`, then reinstall:  
  ```bash
  rm -rf node_modules package-lock.json
  npm install
  ```
- Ensure you’re using **Node.js v16+**:  
  ```bash
  node --version
  ```

### 2️⃣ **Database Connection Errors**  
**Error**: `DB Connection Failed` or `Access denied`  
✅ **Solution**:  
- Verify credentials in `text.env` (rename it to `.env`):  
  ```env
  DB_HOST=localhost  # Or your DB host (e.g., 127.0.0.1)
  DB_USER=root       # Default SQL server username
  DB_PASS=          # Leave empty if no password
  ```
- Start your SQL server:  
  ```bash
  sudo service sql server start  # Linux/Mac
  ```
- Create the database manually if migrations fail:  
  ```sql
  CREATE DATABASE real_estate_db;
  ```

### 3️⃣ **Environment File Issues**  
**Error**: `JWT_SECRET not found` or `undefined environment variable`  
✅ **Solution**:  
- Rename `text.env` to `.env` (critical for `dotenv` to work).  
- Restart the server after changes:  
  ```bash
  node server.js
  ```

### 4️⃣ **Port Already in Use**  
**Error**: `EADDRINUSE :::3000`  
✅ **Solution**:  
- Kill the process:  
  ```bash
  sudo lsof -i :3000    # Find PID
  kill -9 PID           # Replace PID with the process ID
  ```
- Or change the port in `server.js`:  
  ```javascript
  app.listen(5000);  // Switch to port 5000
  ```

### 5️⃣ **Frontend Not Loading**  
**Error**: Blank page or `404` for CSS/JS files  
✅ **Solution**:  
- Ensure files in `public/` are linked correctly in HTML:  
  ```html
  <link rel="stylesheet" href="/css/style.css">  <!-- Path starts with "/" -->
  ```
- Check Express static files setup in `server.js`:  
  ```javascript
  app.use(express.static('public'));  // Correct path
  ```

### 6️⃣ **Authentication Failures**  
**Error**: `Invalid token` or `Login redirect loop`  
✅ **Solution**:  
- Clear browser cookies/localStorage for the app URL.  
- Regenerate a new `JWT_SECRET` in `.env` and restart the server.  

### 🆘 **Still Stuck?**  
1. **Check Logs**:  
   ```bash
   node server.js  # Look for errors in terminal
   ```
2. **Open an Issue**:  
   Provide:  
   - OS (Windows/Linux/Mac)  
   - Node.js version (`node --version`)  
   - Exact error message + screenshot  

---

### 🛠 **Pro Tips**  
- **Debugging**: Use `console.log()` in `server.js` to trace API flow.  
- **Database Backup**: Run `mysqldump` if data corruption occurs.  
- **Reset Everything**:  
  ```bash
  npm install
  mysql -u root -p < SQLQuery.sql  # Import DB schema
  ```


