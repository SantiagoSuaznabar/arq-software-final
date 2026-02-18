# API REST Contracts - User Management Module

## 1. Introducción
Este documento define los contratos de comunicación para el módulo de usuarios. La API sigue los principios RESTful y utiliza JSON como formato de intercambio de datos.

## 2. Endpoints Principales

### A. Obtener Perfil de Usuario
**GET** `/api/v1/users/{id}`
- **Descripción:** Recupera la información pública de un usuario específico.
- **Respuesta Exitosa (200 OK):**
```json
{
    "id": "uuid-12345",
    "username": "arquitecto_dev",
    "email": "user@example.com",
    "created_at": "2026-02-15T10:00:00Z"
}
```

### B. Registro de Nuevo Usuario
**POST** `/api/v1/users/register`
Cuerpo de la Petición:
```json
{
    "username": "string",
    "email": "string",
    "password": "hashed_string"    
}
```
**Respuesta (201 Created)**
```json
{
    "message": "User created successfully",
    "userId": "uuid"
}
```
## 3. Manejo de Errores
|Código|Descripción|
|---|---|
|400|Bad Request - Parámetros de entrada inválidos.|
|401|Unauthorized - Token de acceso ausente o expirado.|
|404|Not Found - El recurso solicitado no existe.|