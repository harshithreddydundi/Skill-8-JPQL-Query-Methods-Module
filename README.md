# Skill 8 - JPQL Query Methods Module

A Spring Boot project demonstrating JPQL Query Methods and Derived Query Methods.

## Project Overview

This module showcases:
- **Derived Query Methods**: Automatically generated queries from method names
- **JPQL Queries**: Custom queries using `@Query` annotation
- **Product Management**: REST API for managing products with various query operations

## Features

### API Endpoints

1. **Add Product**
   - `POST /products`
   - Add a new product to the database

2. **Get All Products**
   - `GET /products`
   - Retrieve all products

3. **Get by Category**
   - `GET /products/category/{category}`
   - Filter products by category

4. **Price Filter**
   - `GET /products/filter?min=X&max=Y`
   - Get products within a price range

5. **Sorted Products**
   - `GET /products/sorted`
   - Get products sorted by price (ascending)

6. **Get Expensive Products**
   - `GET /products/expensive/{price}`
   - Get products above a specific price

## Query Types

### Derived Query Methods
- `findByCategory(String category)` - Find by category
- `findByPriceBetween(Double min, Double max)` - Find by price range

### JPQL Queries
- `getProductsSortedByPrice()` - Sort by price ASC
- `getExpensiveProducts(Double price)` - Products above price
- `getProductsByCategoryJPQL(String category)` - Find by category using JPQL

## Project Structure

```
src/main/java/com/klu/
├── model/
│   └── Product.java
├── controller/
│   └── ProductController.java
├── service/
│   └── ProductService.java
└── repository/
    └── ProductRepository.java
```

## Technologies Used

- Spring Boot 3.0.0
- Spring Data JPA
- MySQL Database
- Maven
- Java 21

## Configuration

Update `application.properties` with your database configuration:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/your_database
spring.datasource.username=root
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

