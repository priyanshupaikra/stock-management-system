# 📦 Stock Management System

A full-stack **Stock Management System** built with **FastAPI** (Backend), **React** (Frontend), and **SQL** (Database). This application helps businesses efficiently manage their inventory, track stock levels, and streamline product management operations.

---

## 🚀 Tech Stack

| Layer      | Technology       |
|------------|-----------------|
| **Backend**   | FastAPI (Python)  |
| **Frontend**  | React.js          |
| **Database**  | SQL (MySQL / PostgreSQL / SQLite) |
| **ORM**       | SQLAlchemy        |

---

## ✨ Features

- 🔐 **User Authentication** – Secure login and registration with JWT tokens
- 📦 **Product Management** – Add, update, delete, and view products
- 📊 **Stock Tracking** – Monitor stock levels in real-time
- 🔍 **Search & Filter** – Quickly find products by name, category, or SKU
- 📈 **Dashboard** – Visual overview of inventory statistics
- ⚠️ **Low Stock Alerts** – Get notified when stock falls below threshold
- 📋 **Stock History** – Track all stock movements and changes
- 📄 **Pagination & Sorting** – Efficiently browse large inventories

---

## 📁 Project Structure

```
stock-management-system/
├── backend/                    # FastAPI Backend
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py             # FastAPI application entry point
│   │   ├── config.py           # Configuration settings
│   │   ├── database.py         # Database connection & session
│   │   ├── models/             # SQLAlchemy models
│   │   │   ├── __init__.py
│   │   │   ├── product.py
│   │   │   ├── user.py
│   │   │   └── stock.py
│   │   ├── schemas/            # Pydantic schemas
│   │   │   ├── __init__.py
│   │   │   ├── product.py
│   │   │   ├── user.py
│   │   │   └── stock.py
│   │   ├── routers/            # API route handlers
│   │   │   ├── __init__.py
│   │   │   ├── product.py
│   │   │   ├── user.py
│   │   │   └── stock.py
│   │   ├── crud/               # CRUD operations
│   │   │   ├── __init__.py
│   │   │   ├── product.py
│   │   │   ├── user.py
│   │   │   └── stock.py
│   │   └── auth/               # Authentication utilities
│   │       ├── __init__.py
│   │       └── jwt_handler.py
│   ├── requirements.txt        # Python dependencies
│   └── .env                    # Environment variables
│
├── frontend/                   # React Frontend
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/         # Reusable UI components
│   │   │   ├── Navbar.jsx
│   │   │   ├── ProductCard.jsx
│   │   │   ├── StockTable.jsx
│   │   │   └── Dashboard.jsx
│   │   ├── pages/              # Page components
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Products.jsx
│   │   │   ├── AddProduct.jsx
│   │   │   └── StockHistory.jsx
│   │   ├── services/           # API service calls
│   │   │   └── api.js
│   │   ├── App.jsx
│   │   ├── App.css
│   │   └── index.js
│   ├── package.json
│   └── .env
│
├── database/                   # SQL Scripts
│   ├── schema.sql              # Database schema
│   └── seed.sql                # Sample seed data
│
├── .gitignore
└── README.md
```

---

## ⚙️ Prerequisites

Make sure you have the following installed on your system:

- **Python** 3.9+
- **Node.js** 16+
- **npm** or **yarn**
- **MySQL / PostgreSQL / SQLite**

---

## 🛠️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/priyanshupaikra/stock-management-system.git
cd stock-management-system
```

### 2. Backend Setup (FastAPI)

```bash
# Navigate to backend directory
cd backend

# Create a virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your database credentials

# Run the FastAPI server
uvicorn app.main:app --reload --port 8000
```

### 3. Frontend Setup (React)

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your API base URL

# Start the React development server
npm start
```

### 4. Database Setup (SQL)

```bash
# Connect to your SQL database and run the schema
mysql -u root -p < database/schema.sql

# (Optional) Load sample seed data
mysql -u root -p < database/seed.sql
```

---

## 🔧 Environment Variables

### Backend (`backend/.env`)

```env
DATABASE_URL=mysql+pymysql://username:password@localhost:3306/stock_management
SECRET_KEY=your-secret-key-here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

### Frontend (`frontend/.env`)

```env
REACT_APP_API_URL=http://localhost:8000/api
```

---

## 📡 API Endpoints

### Authentication

| Method | Endpoint           | Description         |
|--------|-------------------|---------------------|
| POST   | `/api/auth/register` | Register a new user |
| POST   | `/api/auth/login`    | Login user          |

### Products

| Method | Endpoint              | Description            |
|--------|----------------------|------------------------|
| GET    | `/api/products`       | Get all products       |
| GET    | `/api/products/{id}`  | Get product by ID      |
| POST   | `/api/products`       | Create a new product   |
| PUT    | `/api/products/{id}`  | Update a product       |
| DELETE | `/api/products/{id}`  | Delete a product       |

### Stock

| Method | Endpoint                  | Description              |
|--------|--------------------------|--------------------------|
| GET    | `/api/stock`              | Get all stock entries    |
| POST   | `/api/stock/add`          | Add stock                |
| POST   | `/api/stock/remove`       | Remove stock             |
| GET    | `/api/stock/history`      | Get stock movement history |
| GET    | `/api/stock/low-alerts`   | Get low stock alerts     |

### Dashboard

| Method | Endpoint              | Description                |
|--------|----------------------|----------------------------|
| GET    | `/api/dashboard/stats` | Get inventory statistics  |

---

## 📸 Screenshots

> _Screenshots will be added as the project progresses._

<!-- 
![Dashboard](screenshots/dashboard.png)
![Products Page](screenshots/products.png)
![Stock Management](screenshots/stock.png)
-->

---

## 🗄️ Database Schema

```sql
-- Users Table
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Products Table
CREATE TABLE products (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    sku VARCHAR(50) UNIQUE NOT NULL,
    category VARCHAR(50),
    description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    quantity INT DEFAULT 0,
    min_stock_level INT DEFAULT 10,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

-- Stock Movements Table
CREATE TABLE stock_movements (
    id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT NOT NULL,
    movement_type ENUM('IN', 'OUT') NOT NULL,
    quantity INT NOT NULL,
    remarks VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

---

## 🧪 Running Tests

### Backend Tests

```bash
cd backend
pytest tests/ -v
```

### Frontend Tests

```bash
cd frontend
npm test
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👤 Author

**Priyanshu Paikra**

- GitHub: [@priyanshupaikra](https://github.com/priyanshupaikra)

---

## ⭐ Show Your Support

Give a ⭐ if this project helped you!

---

> Built with ❤️ using FastAPI, React & SQL