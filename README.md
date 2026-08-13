# AgroPredict

Sistema de predicción de rendimiento agrícola con análisis climático, gestión de parcelas y siembras, y asistente de IA.

## Repositorios

| Carpeta | Descripción |
|---|---|
| `agropredict-be/` | API REST — Spring Boot 3, Java 17 |
| `agropredict-fe/` | Frontend — React + Vite |

## Arquitectura

```
agropredict/
├── agropredict-be/     # Backend — Puerto 8080
│   └── /api            # Context path de todos los endpoints
└── agropredict-fe/     # Frontend — Puerto 5173 (dev)
```

El frontend consume la API en `http://localhost:8080/api` en desarrollo y en la URL configurada en `VITE_API_URL` en producción.

## Arranque rápido

### Backend

```bash
cd A241S5_APS_T03_be
cp .env.example .env
./mvnw spring-boot:run
```

API disponible en `http://localhost:8080/api`

### Frontend

```bash
cd A241S5_APS_T03_fe
npm install
npm run dev
```

App disponible en `http://localhost:5173`

## Variables de entorno requeridas

Ver `A241S5_APS_T03_be/.env.example` para la lista completa.

| Variable | Descripción |
|---|---|
| `NEON_DB_URL` | URL de conexión PostgreSQL (Neon) |
| `NEON_DB_USERNAME` | Usuario de la BD |
| `NEON_DB_PASSWORD` | Contraseña de la BD |
| `GOOGLE_CLIENT_ID` | OAuth2 Google — Client ID |
| `GOOGLE_CLIENT_SECRET` | OAuth2 Google — Client Secret |
| `GROQ_API_KEY` | Clave de la API de Groq |
| `JWT_SECRET` | Secreto para firmar tokens JWT (mín. 32 chars) |
| `FRONTEND_URL` | URL del frontend en producción |

## Docker

```bash
cd A241S5_APS_T03_be
docker build -t agropredict-be .
docker run -p 8080:8080 --env-file .env agropredict-be
```

## Stack

| Capa | Tecnología |
|---|---|
| Backend | Java 17, Spring Boot 3.3, Spring Security, JPA |
| Base de datos | PostgreSQL — Neon serverless |
| Autenticación | JWT + OAuth2 Google |
| IA | Groq API |
| Frontend | React, Vite |
| Contenedor | Docker multi-stage (JDK 17 build → JRE 17 runtime) |
