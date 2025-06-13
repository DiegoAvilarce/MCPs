# Docker PostgreSQL + CloudBeaver Setup

Este directorio configura un entorno de desarrollo completo con PostgreSQL y CloudBeaver usando Docker Compose, con variables de entorno centralizadas para máxima flexibilidad.

## 🚀 Servicios Incluidos

- **PostgreSQL 15**: Base de datos principal con persistencia de datos
- **CloudBeaver**: Interfaz web moderna para administrar la base de datos
- **Red dedicada**: Comunicación segura entre contenedores

## 📋 Variables de Entorno

El archivo `.env` contiene todas las configuraciones necesarias:

```env
# Configuración de PostgreSQL
POSTGRES_DB=bd_davila          # Nombre de la base de datos
POSTGRES_USER=davila           # Usuario de PostgreSQL
POSTGRES_PASSWORD=cramer*69    # Contraseña de PostgreSQL
POSTGRES_HOST=postgres         # Host del servidor PostgreSQL

# Configuración de CloudBeaver
CB_ADMIN_NAME=davila           # Usuario administrador de CloudBeaver
CB_ADMIN_PASSWORD=Davila_admin*69  # Contraseña del administrador
```

## 🛠️ Configuración Inicial

1. **Verifica que tienes Docker instalado**:
   ```bash
   docker --version
   docker-compose --version
   ```

2. **Personaliza las variables de entorno**:
   Edita el archivo `.env` con tus credenciales preferidas (especialmente las contraseñas)

## 🔧 Uso

### Iniciar el entorno completo
```bash
docker-compose up -d
```

### Verificar que los servicios están ejecutándose
```bash
docker-compose ps
```

### Ver logs de los servicios
```bash
# Todos los servicios
docker-compose logs

# Solo PostgreSQL
docker-compose logs postgres

# Solo CloudBeaver
docker-compose logs cloudbeaver
```

### Acceder a CloudBeaver
- **URL**: http://localhost:8978
- **Usuario**: El definido en `CB_ADMIN_NAME`
- **Contraseña**: La definida en `CB_ADMIN_PASSWORD`

### Conexión preconfigurada a PostgreSQL
CloudBeaver viene con una conexión preconfigurada llamada "PostgreSQL Database" que usa todas las variables de entorno automáticamente.

### Detener los servicios
```bash
docker-compose down
```

### Reiniciar los servicios
```bash
docker-compose restart
```

### Eliminar volúmenes (⚠️ **¡CUIDADO! Esto borra todos los datos permanentemente!**)
```bash
docker-compose down -v
```

## 🌐 Puertos Expuestos

| Servicio | Puerto Host | Puerto Contenedor | Descripción |
|----------|-------------|-------------------|-------------|
| PostgreSQL | 5432 | 5432 | Acceso directo a la BD |
| CloudBeaver | 8978 | 8978 | Interfaz web de administración |

## 📁 Volúmenes Persistentes

- **postgres_data**: Almacena los datos de PostgreSQL
- **cloudbeaver_data**: Configuraciones y workspace de CloudBeaver

## 🔧 Configuración Avanzada

### Personalizar el puerto de CloudBeaver
Cambia el puerto en `docker-compose.yml`:
```yaml
ports:
  - "8080:8978"  # Cambia 8978 por el puerto que prefieras
```

### Acceso externo a PostgreSQL
La base está disponible en `localhost:5432` con las credenciales del `.env`

### Configuración personalizada de CloudBeaver
El archivo `cloudbeaver-config.json` contiene la configuración inicial y conexiones preconfiguradas.

## 🔒 Seguridad

- ✅ El archivo `.env` debe estar excluido del control de versiones
- ✅ Usa contraseñas seguras para entornos de producción
- ✅ Las variables `POSTGRES_HOST` permiten flexibilidad en el despliegue
- ✅ La red `db_network` aísla los contenedores

## 🐛 Solución de Problemas

### CloudBeaver no se conecta a PostgreSQL
1. Verifica que ambos contenedores estén ejecutándose: `docker-compose ps`
2. Revisa los logs: `docker-compose logs`
3. Confirma que las variables de entorno están correctas en `.env`

### Error de permisos en PostgreSQL
```bash
# Recrear volúmenes con permisos correctos
docker-compose down -v
docker-compose up -d
```

### Puerto ocupado
Si el puerto 8978 o 5432 están ocupados, cámbialos en `docker-compose.yml`

## 📈 Próximos Pasos

Una vez que tengas el entorno funcionando:
1. Crea tus primeras tablas en PostgreSQL
2. Explora las funcionalidades de CloudBeaver
3. Conecta aplicaciones externas usando las credenciales del `.env`
4. Considera configurar backups automáticos para producción