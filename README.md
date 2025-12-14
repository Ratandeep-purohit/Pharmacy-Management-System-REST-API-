# Pharmacy Management System (REST API)

## 📌 Overview

The **Pharmacy Management System** is a **RESTful backend API** built using Flask. It is designed to manage core pharmacy operations such as products, companies, distributors, formulas, customers, orders, and stock. The system follows a clean, modular architecture with proper separation of concerns (API layer, business logic, models, and schemas).

This project is backend-focused and intended to be consumed by any frontend (React, Angular, mobile apps) or API clients such as Postman.

---

## ✨ Key Features

* RESTful API architecture
* JWT-based authentication
* Role-based access control (Admin / User)
* Product, company, distributor & formula management
* Order and stock management
* Data validation using Marshmallow
* Database migrations using Flask-Migrate
* Clean business logic layer (BLC)

---

## 🛠️ Technologies Used

* **Python 3.8+**
* **Flask** – Web framework
* **Flask-SQLAlchemy** – ORM
* **Flask-Migrate** – Database migrations
* **Flask-JWT-Extended** – Authentication
* **Marshmallow** – Serialization & validation
* **MySQL** – Database
* **PyMySQL** – MySQL driver

---

## 📂 Project Structure

```text
Pharmacy-app/
│── project/
│   ├── api.py                # App factory
│   ├── config.py             # Configuration
│   ├── app/
│   │   ├── db.py              # Database instance
│   │   ├── models/            # SQLAlchemy models
│   │   ├── schemas/           # Marshmallow schemas
│   │   ├── bl/                # Business logic layer
│   │   └── decorators.py      # Custom decorators
│   ├── blueprints/            # API routes
│── migrations/                # DB migrations
│── runDebug.py                # Application entry point
│── requirements.txt
│── README.md
```

---

## ⚙️ Installation

### Prerequisites

* Python 3.8 or higher
* MySQL Server

### Steps

1. Clone the repository:

```bash
git clone https://github.com/aziz-ullah/Pharmacy-app.git
cd Pharmacy-app
```

2. Create a virtual environment:

```bash
python -m venv venv
```

3. Activate the virtual environment:

* **Windows**

```bash
venv\Scripts\activate
```

* **Linux / macOS**

```bash
source venv/bin/activate
```

4. Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 🔐 Configuration

Update `project/config.py` with your database credentials:

```python
DB_NAME = 'pharmacy'
DB_URL = 'localhost'
DB_USER = 'root'
DB_PWD = 'your_password'
DB_PORT = 3306
JWT_SECRET_KEY = 'your_jwt_secret_key'
```

---

## 🗄️ Database Setup

Initialize migrations:

```bash
flask --app runDebug.py db init
```

Generate migration files:

```bash
flask --app runDebug.py db migrate -m "initial migration"
```

Apply migrations:

```bash
flask --app runDebug.py db upgrade
```

---

## ▶️ Running the Application

Start the Flask development server:

```bash
python runDebug.py
```

The API will be available at:

```
http://127.0.0.1:5000
```

---

## 🔗 API Endpoints (Sample)

### Product

* **GET** `/api/product` – Get all products
* **GET** `/api/product?product_name=Paracetamol` – Search product
* **POST** `/api/product` – Add new product

### Authentication

* **POST** `/api/login` – User login
* **POST** `/api/register` – User registration

> 📌 All protected routes require a valid JWT token in the `Authorization` header.

---

## 🧪 Testing

You can test APIs using:

* Postman
* curl

Example:

```bash
curl http://127.0.0.1:5000/api/product
```

---

## 🚀 Future Improvements

* Swagger / OpenAPI documentation
* Pagination & advanced filtering
* Frontend integration (React)
* Deployment (Docker, AWS, Render)

---

## 🤝 Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

---

## 📄 License

This project is licensed under the **MIT License**.

---

## 👨‍💻 Author

## 👨‍💻 Author

**Ratandeep purohit**  
Software Engineer

📌 Project: Pharmacy Management System (REST API)  
🛠 Tech Stack: Python, Flask, MySQL, SQLAlchemy, JWT, REST APIs  

🔗 GitHub: https://github.com/ratandeep-purohit
🔗 LinkedIn: https://linkedin.com/in/ratandeep-purohit-ab0309304/  
📧 Email: rajatpurohit183@gmail.com

📘 Postman API Testing Guide (Step-by-Step)

⬇️ Is section ko README me
## 🧪 Testing ke baad aur
## 🚀 Future Improvements se pehle paste kar do.

📘 Postman API Testing Guide (Step-by-Step)

This section explains exactly how the APIs were tested using Postman, step by step.

1️⃣ Start the Backend Server

Activate virtual environment:

venv\Scripts\activate


Run the application:

python runDebug.py


Expected output:

Running on http://127.0.0.1:5000

2️⃣ Open Postman

Open Postman

Create a New HTTP Request

Base URL:

http://127.0.0.1:5000

3️⃣ GET All Products (Initial Test)

Method: GET
URL:

/api/product


Postman setup:

Params: ❌ Empty

Headers: ❌ None

Body: ❌ None

Expected response:

[]


📌 Empty response means API + DB connection is working.

4️⃣ Add Product (POST Request)

Method: POST
URL:

/api/product


Headers

Content-Type: application/json


Body → raw → JSON

{
  "product_name": "Paracetamol",
  "formula_id": 1,
  "company_id": 1,
  "distribution_id": 1,
  "per_pack": 10,
  "average_quantity": 500,
  "description": "Pain relief tablet"
}


⚠️ formula_id, company_id, and distribution_id must already exist in the database.

Expected response:

{
  "message": "Product added successfully"
}


Status: 201 CREATED

5️⃣ GET Products After Insert

Method: GET
URL:

/api/product


Expected response:

[
  {
    "id": 1,
    "product_name": "Paracetamol",
    "per_pack": 10,
    "average_quantity": 500,
    "company_id": 1
  }
]

6️⃣ Search Product Using Query Parameters

Method: GET
URL:

/api/product


Postman → Params tab

Key	Value
product_name	Paracetamol

Generated URL:

/api/product?product_name=Paracetamol


Expected response:

[
  {
    "id": 1,
    "product_name": "Paracetamol"
  }
]

7️⃣ Common Errors & Fixes

❌ Missing data for required field
Cause: Required JSON fields missing
Fix: Send complete POST body

❌ Foreign key constraint failed
Cause: Related IDs do not exist
Fix: Insert master data first

❌ Empty array []
Cause: No data in table
Fix: Add data using POST request

8️⃣ Important Rules

GET → Query Params

POST → JSON Body

GET request should never have body

Postman description field is optional