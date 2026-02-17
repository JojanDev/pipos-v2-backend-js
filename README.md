![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-5.x-000000?style=flat-square&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-Auth-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)

🇪🇸 Versión en español disponible aquí: [README.es.md](./README.es.md)

# Veterinary Management API

A RESTful API designed for veterinary clinic management.
This project was developed as a final academic project at SENA, and serves as a structured backend foundation that can be scaled into a production-ready system.

The system manages clinical records, treatments, inventory, services, and sales with role-based access control.

---

## Overview

This API provides core functionality for managing:

- Users and authentication
- Roles and permissions
- Pets and medical history
- Treatments and medications
- Inventory (products and medicines)
- Veterinary services
- Sales system with detailed line items

The architecture is structured and modular, designed to support scalability and future improvements.

---

## Tech Stack

- Node.js
- Express 5
- MySQL
- mysql2
- JWT (Access & Refresh Tokens)
- bcrypt
- dotenv
- cookie-parser
- cors

---

## Architecture

The project follows a layered architecture:

```
src/
 ├── controllers/
 ├── services/
 ├── models/
 ├── routes/
 ├── middlewares/
 ├── providers/
 ├── utils/
 ├── sql/
```

--- 

### Design Approach

- Controllers handle HTTP logic
- Services contain business logic
- Models interact directly with the database
- Middlewares manage authentication and permissions
- A reusable base Modelo class handles generic CRUD operations

The architecture is intentionally simple but structured to allow scaling and refactoring.

---

## Authentication & Authorization

The API implements:

- Access Tokens (short-lived)
- Refresh Tokens
- Role-based access control (RBAC)
- Permissions assigned to roles
- Roles assigned to users
- bcrypt password hashing

Environment variables related to authentication:

```
ACCESS_TOKEN_SECRET=
REFRESH_TOKEN_SECRET=
TOKEN_EXPIRATION=
REFRESH_EXPIRATION=
REFRESH_TOKEN_THRESHOLD=
```

> Note: The authentication system is implemented and functional, but further hardening and testing would be required for production environments.

---

### Main Modules
**Clinical Management**

- Antecedentes (Medical history)
- Tratamientos
- Medicamentos
- Medicamentos por tratamiento

**Pet Management**

- Mascotas
- Razas
- Especies

**Inventory**

- Productos
- Tipos de productos
- Medicamentos
- Información de medicamentos

**Sales System**

- Ventas
- Productos en venta
- Medicamentos en venta
- Servicios en venta

**Access Control**

- Usuarios
- Credenciales
- Roles
- Permisos
- Roles_Usuarios
- Permisos_Roles

---

### Database

The system uses a relational MySQL database with properly defined foreign keys and many-to-many relationships through pivot tables:

- permisos_roles
- roles_usuarios
- medicamentos_tratamientos
- medicamentos_ventas
- productos_ventas
- servicios_ventas

The full database creation script is available in the sql/ directory.

---

### Environment Variables

Create a `.env` file based on `.env.example`:

```
PORT=3000

DB_HOST=localhost
DB_USER=your_user
DB_PASSWORD=your_password
DB_NAME=veterinaria_pipos

ACCESS_TOKEN_SECRET=yourAccessSecret
REFRESH_TOKEN_SECRET=yourRefreshSecret
TOKEN_EXPIRATION=15m
REFRESH_EXPIRATION=1d
REFRESH_TOKEN_THRESHOLD=18000
```

---

### Installation

1. Clone the repository
2. Install dependencies:
```
  npm install
```
3. Configure your .env file
4. Set up the MySQL database using the SQL script
5. Start the server:

Development mode:
```
npm run dev
```
Production mode:
```
npm start
```

---

### Project Status

This is a completed academic project that can serve as a solid backend foundation for a real-world veterinary management system.

However, improvements would be needed for production use, including:

- Stronger validation layer
- File/document upload for medical records
- Improved error handling standardization
- Automated testing
- Logging system
- Query sanitization improvements
- API documentation (Swagger)

--- 
 
### Future Improvements

Potential enhancements:

- Medical document attachments for antecedentes
- Pagination and filtering
- Centralized validation system
- Better token rotation strategy
- Dockerization
- CI/CD integration

---

### Academic Context

Developed as a final academic project at SENA.
The project demonstrates backend architecture design, relational database modeling, authentication systems, and modular REST API development.


