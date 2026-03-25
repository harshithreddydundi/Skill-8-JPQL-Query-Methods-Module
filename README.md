# Skill 8 - JPQL Query Methods Module

A comprehensive Spring Boot project demonstrating JPQL (Java Persistence Query Language) Query Methods and Derived Query Methods with REST API endpoints.

## 📋 Project Overview

This module showcases:
- **Derived Query Methods**: Automatically generated queries from method names
- **JPQL Queries**: Custom queries using `@Query` annotation
- **REST API**: Complete REST endpoints for product management
- **Database Integration**: MySQL database with Spring Data JPA
- **API Documentation**: Integrated Swagger UI for easy API testing

## ✨ Features

### 1. **Get All Products**
   - Endpoint: `GET /products`
   - Retrieve all products from the database

### 2. **Add Product** 
   - Endpoint: `POST /products`
   - Request body: `{ "name": "...", "category": "...", "price": ... }`
   - Add a new product

### 3. **Get by Category**
   - Endpoint: `GET /products/category/{category}`
   - Example: `/products/category/Electronics`
   - Filter products by category

### 4. **Price Range Filter**
   - Endpoint: `GET /products/filter?min=100&max=500`
   - Get products within a price range

### 5. **Get Sorted Products**
   - Endpoint: `GET /products/sorted`
   - Retrieve all products sorted by price (ascending)

### 6. **Get Expensive Products**
   - Endpoint: `GET /products/expensive/{price}`
   - Example: `/products/expensive/1000`
   - Get all products above a specific price

## 🏗️ Project Architecture

### Model (Entity)
- **Product.java** - JPA Entity with Hibernate annotations
  - Fields: id, name, category, price
  - Table: product_skill8

### Controller
- **ProductController.java** - REST endpoints
  - Maps HTTP requests to service layer
  - Handles all CRUD operations

### Service
- **ProductService.java** - Business logic
  - Orchestrates data operations
  - Separates controller from repository layer

### Repository
- **ProductRepository.java** - Data access layer
  - Extends JpaRepository
  - Contains both derived and JPQL queries

## 🗄️ Query Types Implemented

### Derived Query Methods (Auto-generated)
```java
List<Product> findByCategory(String category);
List<Product> findByPriceBetween(Double min, Double max);
```

### JPQL Query Methods
```java
@Query("SELECT p FROM Product p ORDER BY p.price ASC")
List<Product> getProductsSortedByPrice();

@Query("SELECT p FROM Product p WHERE p.price > :price")
List<Product> getExpensiveProducts(Double price);

@Query("SELECT p FROM Product p WHERE p.category = :category")
List<Product> getProductsByCategoryJPQL(String category);
```

## 🛠️ Technologies Used

- **Spring Boot** 3.0.0
- **Spring Data JPA** - ORM framework
- **Hibernate** - JPA implementation
- **MySQL** - Database
- **Maven** - Build tool
- **Java** 21
- **Springdoc OpenAPI** - Swagger UI documentation
- **Lombok** - Boilerplate reduction

## 📁 Project Structure

```
src/main/
├── java/com/klu/
│   ├── Skill8JpqlApplication.java
│   ├── model/
│   │   └── Product.java
│   ├── controller/
│   │   └── ProductController.java
│   ├── service/
│   │   └── ProductService.java
│   └── repository/
│       └── ProductRepository.java
└── resources/
    └── application.properties

pom.xml
README.md
.gitignore
```

## ⚙️ Configuration

### Database Setup
Update `application.properties` with your MySQL configuration:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/skill8_db
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
```

### Server Port
Default port: **2026**

## 🚀 Getting Started

### Prerequisites
- Java 21 or higher
- MySQL Server running
- Maven 3.8+

### Installation
1. Clone the repository
2. Update database credentials in `application.properties`
3. Create MySQL database: `CREATE DATABASE skill8_db;`
4. Run the application:
   ```bash
   mvn spring-boot:run
   ```

### API Documentation
Once running, access Swagger UI at: `http://localhost:2026/swagger-ui.html`

## 📝 Testing the API

### Using cURL Examples:

**Get all products:**
```bash
curl -X GET http://localhost:2026/products
```

**Add a product:**
```bash
curl -X POST http://localhost:2026/products \
  -H "Content-Type: application/json" \
  -d '{"name":"Laptop","category":"Electronics","price":50000}'
```

**Get by category:**
```bash
curl -X GET http://localhost:2026/products/category/Electronics
```

**Price filter:**
```bash
curl -X GET "http://localhost:2026/products/filter?min=10000&max=50000"
```

**Sorted products:**
```bash
curl -X GET http://localhost:2026/products/sorted
```

**Expensive products:**
```bash
curl -X GET http://localhost:2026/products/expensive/50000
```

## 📌 Key Concepts Demonstrated

1. **JPA Entities** - Object-Relational Mapping
2. **Spring Data Repositories** - Data access abstraction
3. **JPQL Queries** - Java Persistence Query Language
4. **Derived Query Methods** - Method naming conventions
5. **REST Controllers** - RESTful API design
6. **Service Layer** - Business logic separation
7. **Entity Relationships** - Database modeling

## 👨‍💻 Author

KLU - Skill 8 JPQL Query Methods Module

## 📄 License

This project is for educational purposes.

