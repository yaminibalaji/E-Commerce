# 🛒 E-Commerce Backend API

Powering modern online shopping with a secure, scalable, and production-ready RESTful API — built with **Java** and **Spring Boot**.  
From **user authentication** to **payment processing**, this project showcases a robust e-commerce backend system ready for real-world usage.

Easily **browse products**, **manage carts**, and **place orders** — all through a seamless, reliable API experience.

---

## 🚀 Project Overview

This project is a **full-fledged e-commerce backend API** managing essential store functionalities:

- Secure user registration/login.
- Product browsing, filtering, and management.
- Cart operations and order placements.
- Payment integration via **Stripe** (test environment).

🔹 **Built With**: Modern Java practices, Spring Boot standards, and a scalable MySQL database.

---

## ✨ Key Features

| Feature | Details |
| :--- | :--- |
| 🔒 **Authentication & Authorization** | Secure login/register with **JWT** and **role-based access** (USER, ADMIN). |
| 📦 **Product Management** | Add, update, delete, search, and filter products (e.g., by category, price). |
| 🛒 **Shopping Cart** | Manage cart items, persist cart data into database. |
| 💳 **Payments & Orders** | Order placement and payment integration with **Stripe** (sandbox/test mode). |
| ✅ **Robust Validation** | Proper request validation and custom error handling. |
| 📚 **Interactive API Docs** | Swagger UI to explore and test all APIs. |
| ⚡ **Optimized Database Access** | Efficient queries using **Spring Data JPA** and **MySQL**. |

---

## 🛠️ Tech Stack

| Category | Tools |
| :--- | :--- |
| Backend | Java 17, Spring Boot 3.2.5, Spring Security, Spring Data JPA |
| Database | MySQL 8.0 |
| Frontend  | React.js |
| Build Tool | Maven |
| Version Control | Git |
| API Documentation | Swagger/OpenAPI |
| API Testing | Postman |

---

## 📋 Getting Started

### Prerequisites

- Java 17
- Maven 3.8+
- MySQL 8.0+
- Postman (for API testing)
- Git
- React.js frontend to consume APIs

---

## Installation Steps

1. **Clone the Repository:**

- bash
- git clone "https://github.com/yaminibalaji/E-Commerce.git"
- cd ecommerce

2. Set up MySQL Database:
   CREATE DATABASE ecommerce_db;
3.  Install Project Dependencies:
   mvn clean install
4. Configuration
  Update your configuration file at src/main/resources/application.yaml:

```**application.yaml**

server:
  port: 8080

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/ecommerce_db?useSSL=false&serverTimezone=UTC
    username: [your-mysql-username]
    password: [your-mysql-password]
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true

jwt:
  secret: [your-jwt-secret-key]
  expiration: 86400000 # 24 hours

stripe:
  api:
    key: [your-stripe-test-api-key]


```
## 📁 Project Structure
```
ecommerce-backend/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── yourpackage/
│   │   │           ├── config/
│   │   │           ├── controller/
│   │   │           ├── dto/
│   │   │           ├── entity/
│   │   │           ├── exception/
│   │   │           ├── repository/
│   │   │           ├── security/
│   │   │           ├── service/
│   │   │           ├── util/
│   │   │           └── EcommerceApplication.java
│   │   └── resources/
│   │       ├── application.yaml
│   │       └── static/
│   └── test/
│       └── java/
│           └── com/
│               └── yourpackage/
│                   ├── service/
│                   └── controller/
├── postman/
│   └── EcommerceAPI.postman_collection.json
├── .gitignore
├── README.md
├── pom.xml
└── LICENSE
```

## 🗺️ ER Diagram (Mermaid)
```
erDiagram
    USER ||--o{ ORDER : places
    USER ||--o{ CART : has
    PRODUCT ||--o{ CART : in
    PRODUCT ||--o{ ORDER_ITEM : included_in
    ORDER ||--o{ ORDER_ITEM : contains
    CART ||--o{ PRODUCT : contains

    USER {
        int id PK
        string name
        string email
        string password
        string role
    }

    PRODUCT {
        int id PK
        string name
        string description
        double price
        string category
        int stock_quantity
    }

    CART {
        int id PK
        int user_id FK
    }

    ORDER {
        int id PK
        int user_id FK
        double total_amount
        string payment_status
        datetime created_at
    }

    ORDER_ITEM {
        int id PK
        int order_id FK
        int product_id FK
        int quantity
        double price_at_purchase
    }



```
📂 Explore the API Documentation : http://localhost:8080/swagger-ui.html

**Frontend Setup (React.js)**

- React frontend is optional, but recommended for full-stack testing.
- Connect your React app to the backend APIs running at http://localhost:8080.
- Ensure CORS settings allow frontend requests (already configured in the backend if needed).

## 🌟 API Highlights

| Method | Endpoint | Description | Access |
| :--- | :--- | :--- | :--- |
| POST | /api/auth/register | Register a new user | Public |
| POST | /api/auth/login | Obtain JWT token | Public |
| GET | /api/products | List all products | Public |
| GET | /api/products?category=books | Filter products by category | Public |
| POST | /api/products | Add a new product | Admin Only |
| GET | /api/cart | View current user's cart | User |
| POST | /api/cart | Add item to cart | User |
| POST | /api/orders | Place an order | User |

🧪 Testing

- Unit Tests (for service and controller layers):
   mvn test
- Covers service and controller layers.
- API Testing:
    * Use Postman Collection: 📂 postman/EcommerceAPI.postman_collection.json
    * Swagger UI.
- Manual Testing:
   Use React Frontend (optional) for live interaction.

🤝 Contribution
Contributions are welcome and appreciated! 🌟

1. Fork the repository.

2. Create a feature branch:
    git checkout -b feature/your-feature

3. Commit your changes:
    git commit -m "Add your feature"

4. Push to your branch:
    git push origin feature/your-feature

5. Open a pull request.

📬 Contact
 Hi, I’m Muttum Venkata Yamini, a passionate Java Backend Developer!

   - 📧 Email: venkatayaminimuttum.com

   - 🐙 GitHub: github.com/MuttumVenkataYamini

   - 🌐 Portfolio: 

⭐ If you like this project, don't forget to star the repo and share your feedback!





