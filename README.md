# 🚇 Metro Navigator

A full-stack **Metro Navigation System** that models real-world metro networks and calculates optimal routes using graph algorithms. The platform provides multiple route optimization modes, an interactive metro map, user authentication, and an admin dashboard for managing metro network data.

---

## 🌟 Features

### 🗺️ Route Planning

* Search for metro stations by name.
* Find optimal routes between two stations.
* Supports multiple optimization modes:

  * **Minimum Stations** — finds the route with the fewest stops.
  * **Minimum Travel Time** — finds the fastest route.
  * **Minimum Fare** — finds the cheapest route.
* Displays:

  * Complete route
  * Number of stations
  * Estimated travel time
  * Fare
  * Route details

### 📊 Graph Algorithms

The metro network is represented as a weighted graph.

* **BFS (Breadth-First Search)**

  * Used for minimum-station routing.
  * Suitable for unweighted route optimization.

* **Dijkstra's Algorithm**

  * Used for minimum travel-time routing.
  * Used for minimum-fare routing.
  * Handles weighted metro connections.

### 🔐 Authentication

* User registration and login.
* JWT-based authentication.
* Protected API routes.
* Secure user sessions.

### 👨‍💼 Admin Dashboard

Administrators can manage the metro network through a dedicated dashboard.

* Add stations.
* Update station information.
* Delete stations.
* Manage metro connections.
* Manage route/network data.
* Monitor the metro network.

### 🎨 Interactive Metro Map

* Interactive SVG-based metro map.
* Visual representation of stations and connections.
* Route visualization.
* Responsive user interface.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │      React + Vite    │
                    │      Frontend        │
                    └──────────┬───────────┘
                               │
                               │ REST API
                               ▼
                    ┌──────────────────────┐
                    │   Node.js + Express  │
                    │      Backend         │
                    └──────────┬───────────┘
                               │
                               │ Mongoose
                               ▼
                    ┌──────────────────────┐
                    │      MongoDB         │
                    │       Database       │
                    └──────────────────────┘

                     Authentication
                           │
                           ▼
                     JWT Middleware
```

---

## 🛠️ Tech Stack

### Frontend

* React.js
* Vite
* JavaScript
* HTML5
* CSS3
* SVG

### Backend

* Node.js
* Express.js
* REST API
* JWT Authentication
* bcrypt

### Database

* MongoDB
* Mongoose

### Algorithms

* Breadth-First Search (BFS)
* Dijkstra's Algorithm
* Graph-based route optimization

### Development Tools

* Git
* GitHub
* npm

---

## 📁 Project Structure

```text
metro-navigator/
│
├── public/
│
├── src/
│   ├── main.js
│   ├── admin.js
│   ├── data.js
│   └── style.css
│
├── backend/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── server.js
│   ├── seeder.js
│   ├── package.json
│   └── .env
│
├── admin.html
├── index.html
├── package.json
├── package-lock.json
├── .gitignore
└── README.md
```

---

# 🚀 Getting Started

## Prerequisites

Make sure you have the following installed:

* Node.js
* npm
* MongoDB / MongoDB Atlas
* Git

Check your installation:

```bash
node --version
npm --version
git --version
```

---

## 📥 Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/metro-navigator.git
cd metro-navigator
```

---

## 2. Install Frontend Dependencies

From the project root:

```bash
npm install
```

---

## 3. Install Backend Dependencies

```bash
cd backend
npm install
cd ..
```

---

# ⚙️ Environment Variables

Create a `.env` file inside the `backend` directory:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
PORT=5000
```

Example:

```env
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/metro_navigator
JWT_SECRET=your_super_secret_key
PORT=5000
```

> **Important:** Never commit `.env` files or database credentials to GitHub.

Make sure `.gitignore` contains:

```text
.env
node_modules
dist
```

---

# ▶️ Running the Application

## Start the Backend

Open a terminal:

```bash
cd backend
npm start
```

The backend will run on:

```text
http://localhost:5000
```

---

## Start the Frontend

Open another terminal in the project root:

```bash
npm run dev
```

Vite will provide a local URL, usually:

```text
http://localhost:5173
```

Open the URL in your browser.

---

# 🔗 API Configuration

The frontend communicates with the backend through the REST API.

Use a Vite environment variable rather than hardcoding the backend URL.

In the frontend:

```javascript
const API_URL = import.meta.env.VITE_API_URL;
```

For local development, create:

```text
.env
```

in the project root:

```env
VITE_API_URL=http://localhost:5000/api
```

For production, set the same variable in your hosting provider:

```env
VITE_API_URL=https://your-backend-url.com/api
```

---

# 🗄️ Database Seeding

The backend includes a database seeder for initializing metro network data.

From the backend directory:

```bash
cd backend
npm run data:import
```

This will populate the database with the initial metro network data.

---

# 🧠 Route Optimization

Metro Navigator uses graph algorithms to calculate optimal routes.

### Minimum Stations

The metro network is treated as an unweighted graph.

```text
BFS
```

is used to find the route containing the minimum number of stations.

### Minimum Travel Time

Connections are assigned travel-time weights.

```text
Dijkstra's Algorithm
```

is used to calculate the shortest travel-time route.

### Minimum Fare

Connections are assigned fare weights.

Dijkstra's Algorithm is again used to calculate the minimum-cost route.

---

# 🔐 Authentication Flow

The application uses JWT-based authentication.

```text
User
 │
 ▼
Login / Register
 │
 ▼
Backend
 │
 ├── Validate credentials
 │
 ├── Hash / verify password
 │
 ▼
JWT Token
 │
 ▼
Frontend
 │
 ▼
Authenticated API Requests
```

Protected routes require a valid JWT token.

---

# 👨‍💼 Admin Dashboard

The admin interface is available at:

```text
/admin.html
```

For local development:

```text
http://localhost:5173/admin.html
```

The dashboard provides administrative functionality for managing metro stations and connections.

> For production, use a strong admin password and do not rely on default development credentials.

---

# 🌐 Deployment

A recommended production architecture is:

```text
Frontend  → Vercel
Backend   → Render / Railway
Database  → MongoDB Atlas
Repository → GitHub
```

### Frontend

Build the production frontend:

```bash
npm run build
```

The generated files will be placed in:

```text
dist/
```

For Vercel, use:

```text
Framework: Vite
Build Command: npm run build
Output Directory: dist
```

Set:

```env
VITE_API_URL=https://your-backend-url.com/api
```

### Backend

Deploy the `backend` directory as a Node.js service.

Typical commands:

```bash
npm install
```

and:

```bash
npm start
```

Configure the production environment variables:

```env
MONGO_URI=your_mongodb_atlas_uri
JWT_SECRET=your_production_secret
PORT=5000
```

---

# 🔒 Security

For production deployments:

* Never commit `.env` files.
* Use a strong `JWT_SECRET`.
* Use MongoDB Atlas authentication.
* Use HTTPS.
* Configure CORS to allow only your frontend domain.
* Use a strong administrator password.
* Never expose database credentials in frontend code.
* Validate and sanitize API inputs.

---

# 📌 Future Improvements

Potential future enhancements include:

* 🚉 Real-time metro status.
* 📍 GPS-based nearest-station detection.
* 🕐 Live train arrival information.
* 🔄 Real-time route updates.
* 🌐 Multi-city metro support.
* 📱 Progressive Web App (PWA).
* 📊 Analytics dashboard for administrators.
* 🧭 Station-to-station navigation.
* 🌙 Dark mode.
* 🗺️ Improved interactive metro visualization.
* ⚡ Route caching for faster responses.

---

# 📸 Screenshots

Add screenshots of the application here:

```text
screenshots/
├── home.png
├── route-search.png
├── metro-map.png
├── login.png
└── admin-dashboard.png
```

Example:

```markdown
![Metro Navigator](screenshots/home.png)
```

---

# 🤝 Contributing

Contributions are welcome!

### 1. Fork the repository

### 2. Create a feature branch

```bash
git checkout -b feature/new-feature
```

### 3. Commit your changes

```bash
git commit -m "Add new feature"
```

### 4. Push the branch

```bash
git push origin feature/new-feature
```

### 5. Open a Pull Request

---

# 📄 License

This project is intended for educational and development purposes.

---

## 👨‍💻 Author

**Soham Mondal**

Electrical Engineering
IIT Kharagpur

---

⭐ If you found this project useful, consider giving the repository a star!
