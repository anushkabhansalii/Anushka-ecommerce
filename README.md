# Ecommerce Backend Application

A robust backend for an e-commerce platform built with Spring Boot and MongoDB. This application manages products, shopping carts, orders, and payments.

## 🚀 Technologies

- **Java**: 25
- **Spring Boot**: 4.0.1
- **Database**: MongoDB
- **Build Tool**: Maven

## 📋 Prerequisites

Ensure you have the following installed before running the application:

- [Java JDK 25](https://jdk.java.net/)
- [Apache Maven](https://maven.apache.org/)
- [MongoDB](https://www.mongodb.com/try/download/community) (running on `localhost:27017`)

## 🛠️ Installation & Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ecommerce
   ```

2. **Configure MongoDB**
   Ensure your MongoDB instance is running. The application defaults to:
   - **URI**: `mongodb://localhost:27017/ecommerce_db`
   
   To change this, update `src/main/resources/application.yaml`.

3. **Build the project**
   ```bash
   ./mvnw clean install
   ```

4. **Run the application**
   ```bash
   ./mvnw spring-boot:run
   ```

The application will start on port `8080`.

## 🔌 API Endpoints

### 📦 Products
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/products` | Create a new product. |
| `GET` | `/api/products` | Retrieve a list of all products. |

### 🛒 Cart
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/cart/add` | Add an item to the user's cart. |
| `GET` | `/api/cart/{userId}` | Get the shopping cart for a specific user. |
| `DELETE` | `/api/cart/{userId}/clear` | Clear the shopping cart for a user. |

### 📜 Orders
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/orders` | Create a new order (from current cart). |
| `GET` | `/api/orders/{orderId}` | Get details of a specific order. |

> **Note**: The Order service uses an **Adapter Pattern** to process creation requests.

### 💳 Payments
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/payments/create` | Process a payment for an order. |

## ⚙️ Configuration

Application configuration can be found in `src/main/resources/application.yaml`.

```yaml
server:
  port: 8080

spring:
  data:
    mongodb:
      uri: mongodb://localhost:27017/ecommerce_db
      auto-index-creation: true
```
