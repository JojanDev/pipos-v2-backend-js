![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-5.x-000000?style=flat-square&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-Autenticación-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)

🇬🇧 English version available here: [README.md](./README.md)

# API de Gestión Veterinaria

API REST diseñada para la gestión de clínicas veterinarias.  
Este proyecto fue desarrollado como proyecto final académico en el SENA y funciona como una base estructurada de backend que puede evolucionar hacia un entorno productivo con mejoras adicionales.

El sistema gestiona historias clínicas, tratamientos, inventario, servicios y ventas mediante control de acceso basado en roles.

---

## 📌 Descripción General

Esta API proporciona funcionalidades principales para administrar:

- Usuarios y autenticación
- Roles y permisos
- Mascotas e historial médico
- Tratamientos y medicamentos
- Inventario (productos y medicamentos)
- Servicios veterinarios
- Sistema de ventas con detalles relacionales

La arquitectura es modular y estructurada, pensada para facilitar escalabilidad y futuras mejoras.

---

## 🛠 Stack Tecnológico

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

## 🏗 Arquitectura

El proyecto sigue una arquitectura por capas:
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


### Enfoque de Diseño

- Controllers → Manejo de lógica HTTP  
- Services → Lógica de negocio  
- Models → Interacción directa con la base de datos  
- Middlewares → Autenticación y autorización  
- Clase base `Modelo` → Implementación reutilizable de operaciones CRUD  

La estructura es simple pero organizada, permitiendo refactorización y expansión futura.

---

## 🔐 Autenticación y Autorización

La API implementa:

- Tokens de acceso (corta duración)
- Tokens de refresco
- Control de acceso basado en roles (RBAC)
- Permisos asignados a roles
- Roles asignados a usuarios
- Hashing de contraseñas con bcrypt

Variables de entorno relacionadas:
```
ACCESS_TOKEN_SECRET=
REFRESH_TOKEN_SECRET=
TOKEN_EXPIRATION=
REFRESH_EXPIRATION=
REFRESH_TOKEN_THRESHOLD=
```

> Nota: El sistema de autenticación es funcional, pero requeriría endurecimiento adicional para entornos de producción.

---

## 📦 Módulos Principales

### Gestión Clínica
- Antecedentes
- Tratamientos
- Medicamentos
- Medicamentos por tratamiento

### Gestión de Mascotas
- Mascotas
- Razas
- Especies

### Inventario
- Productos
- Tipos de productos
- Información de medicamentos

### Sistema de Ventas
- Ventas
- Productos en venta
- Medicamentos en venta
- Servicios en venta

### Control de Acceso
- Usuarios
- Credenciales
- Roles
- Permisos
- roles_usuarios
- permisos_roles

---

## 🗄 Base de Datos

El sistema utiliza una base de datos relacional MySQL con:

- Llaves foráneas correctamente definidas
- Relaciones muchos a muchos mediante tablas intermedias
- Separación entre usuarios y credenciales

Tablas pivote principales:

- permisos_roles
- roles_usuarios
- medicamentos_tratamientos
- medicamentos_ventas
- productos_ventas
- servicios_ventas

El script completo de creación se encuentra en el directorio:
```
/sql
```


---

## ⚙ Variables de Entorno

Crea un archivo `.env` basado en `.env.example`:
```
PORT=3000

DB_HOST=localhost
DB_USER=tu_usuario
DB_PASSWORD=tu_contraseña
DB_NAME=veterinaria_pipos

ACCESS_TOKEN_SECRET=tuAccessSecret
REFRESH_TOKEN_SECRET=tuRefreshSecret
TOKEN_EXPIRATION=15m
REFRESH_EXPIRATION=1d
REFRESH_TOKEN_THRESHOLD=18000
```


---

## 🚀 Instalación

1. Clonar el repositorio  
2. Instalar dependencias:
```
npm install
```

3. Configurar el archivo `.env`  
4. Ejecutar el script SQL para crear la base de datos  
5. Iniciar el servidor  

Modo desarrollo:
```
npm run dev
```

Modo producción:
```
npm start
```


---

## 📈 Estado del Proyecto

Proyecto académico finalizado que puede servir como base sólida para un sistema real de gestión veterinaria.

Para uso en producción se recomienda:

- Implementar validación robusta de datos
- Incorporar carga de archivos clínicos
- Estandarizar manejo de errores
- Añadir pruebas automatizadas
- Implementar sistema de logging
- Mejorar sanitización de consultas
- Documentación con Swagger

---

## 🔮 Mejoras Futuras

Posibles extensiones:

- Adjuntar documentos médicos en antecedentes
- Paginación y filtros
- Sistema centralizado de validación
- Estrategia avanzada de rotación de tokens
- Dockerización
- Integración CI/CD

---

## 🎓 Contexto Académico

Desarrollado como proyecto final académico en el SENA.  
El proyecto demuestra diseño de arquitectura backend, modelado relacional de bases de datos, implementación de autenticación y desarrollo modular de APIs REST.








