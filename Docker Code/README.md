# Docker PostgreSQL + CloudBeaver Setup

Este proyecto configura un entorno de desarrollo con PostgreSQL y CloudBeaver usando Docker Compose.

## Servicios incluidos

- **PostgreSQL 15**: Base de datos principal
- **CloudBeaver**: Interfaz web para administrar la base de datos

## Configuración inicial

1. Copia el archivo de ejemplo de variables de entorno:
   ```bash
   copy .env.example .env
   ```

2. Edita el archivo `.env` con tus credenciales reales:
   - `POSTGRES_DB`: Nombre de tu base de datos
   - `POSTGRES_USER`: Usuario de PostgreSQL
   - `POSTGRES_PASSWORD`: Contraseña de PostgreSQL
   - `CB_ADMIN_NAME`: Usuario administrador de CloudBeaver
   - `CB_ADMIN_PASSWORD`: Contraseña del administrador

## Uso

### Iniciar los servicios
```bash
docker-compose up -d
```

### Acceder a CloudBeaver
- URL: http://localhost:8080
- Usuario: El definido en `CB_ADMIN_NAME`
- Contraseña: La definida en `CB_ADMIN_PASSWORD`

### Conectar a PostgreSQL desde CloudBeaver
La conexión ya está preconfigurada como "PostgreSQL Local".

### Detener los servicios
```bash
docker-compose down
```

### Eliminar volúmenes (¡cuidado, esto borra todos los datos!)
```bash
docker-compose down -v
```

## Puertos

- PostgreSQL: 5432
- CloudBeaver: 8080

## Seguridad

- El archivo `.env` está excluido del control de versiones
- Nunca subas credenciales reales a repositorios públicos
- Usa contraseñas seguras para producción