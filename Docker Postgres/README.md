# Docker PostgreSQL + CloudBeaver Setup

Este directorio configura un entorno de desarrollo profesional y completo con PostgreSQL 15 y CloudBeaver usando Docker Compose, optimizado para desarrollo de aplicaciones MCP con variables de entorno centralizadas para máxima flexibilidad y seguridad.

## 🚀 Servicios Incluidos

- **PostgreSQL 15**: Base de datos principal enterprise-ready con persistencia automática
- **CloudBeaver**: Interfaz web moderna y profesional para administración de bases de datos
- **Red dedicada**: Comunicación segura y aislada entre contenedores
- **Configuración preestablecida**: Data sources y conexiones automáticas

## 📋 Variables de Entorno Centralizadas

El archivo `.env` contiene todas las configuraciones necesarias para un despliegue flexible:

```env
# Configuración de PostgreSQL
POSTGRES_DB=bd_davila          # Nombre de la base de datos principal
POSTGRES_USER=davila           # Usuario administrador de PostgreSQL
POSTGRES_PASSWORD=cramer*69    # Contraseña segura de PostgreSQL
POSTGRES_HOST=postgres         # Host del servidor PostgreSQL (para contenedores)

# Configuración de CloudBeaver
CB_ADMIN_NAME=davila           # Usuario administrador de CloudBeaver
CB_ADMIN_PASSWORD=Davila_admin*69  # Contraseña del administrador web
```

## 🛠️ Prerrequisitos y Configuración

### 1. Verificar Docker
```bash
docker --version
docker-compose --version
```

### 2. Personalizar Configuración
Edita el archivo `.env` con tus credenciales específicas:
- ⚠️ **Importante**: Cambia las contraseñas por defecto en entornos de producción
- ✅ Mantén credenciales consistentes entre servicios
- 🔒 Nunca versiones el archivo `.env` con credenciales reales

## 🚀 Gestión del Entorno

### Inicialización Completa
```bash
# Construir e iniciar todos los servicios
docker-compose up -d

# Verificar que todo está funcionando
docker-compose ps
```

### Monitoreo y Logs
```bash
# Ver estado de todos los servicios
docker-compose ps

# Logs en tiempo real (todos los servicios)
docker-compose logs -f

# Logs específicos por servicio
docker-compose logs postgres
docker-compose logs cloudbeaver

# Ver últimas 50 líneas de logs
docker-compose logs --tail=50
```

### Gestión de Servicios
```bash
# Reiniciar servicios específicos
docker-compose restart postgres
docker-compose restart cloudbeaver

# Detener servicios manteniendo datos
docker-compose stop

# Iniciar servicios previamente detenidos
docker-compose start

# Parada completa
docker-compose down
```

### Limpieza y Mantenimiento
```bash
# Eliminar contenedores (mantiene volúmenes)
docker-compose down

# ⚠️ PELIGRO: Eliminar TODO incluyendo datos
docker-compose down -v

# Reconstruir imágenes si hay cambios
docker-compose up -d --build
```

## 🌐 Acceso a Servicios

### CloudBeaver Web Interface
- **URL**: http://localhost:8978
- **Usuario**: Valor de `CB_ADMIN_NAME` en `.env`
- **Contraseña**: Valor de `CB_ADMIN_PASSWORD` en `.env`
- **Conexión automática**: La conexión a PostgreSQL se configura automáticamente

### PostgreSQL Direct Access
- **Host**: localhost
- **Puerto**: 5432
- **Base de datos**: Valor de `POSTGRES_DB` en `.env`
- **Usuario**: Valor de `POSTGRES_USER` en `.env`
- **Contraseña**: Valor de `POSTGRES_PASSWORD` en `.env`

## 📊 Arquitectura y Puertos

| Servicio | Puerto Host | Puerto Contenedor | Descripción | Acceso |
|----------|-------------|-------------------|-------------|---------|
| PostgreSQL | 5432 | 5432 | Base de datos principal | Directo/Apps |
| CloudBeaver | 8978 | 8978 | Interfaz web admin | Browser |

## 💾 Persistencia de Datos

### Volúmenes Docker
- **postgres_data**: 
  - Almacena toda la información de la base de datos
  - Persiste entre reinicios de contenedores
  - Ubicación: Docker volume management
  
- **cloudbeaver_data**: 
  - Configuraciones de CloudBeaver
  - Workspace y preferencias del usuario
  - Conexiones guardadas

### Backup y Restauración
```bash
# Backup de la base de datos
docker-compose exec postgres pg_dump -U davila bd_davila > backup_$(date +%Y%m%d).sql

# Restaurar desde backup
docker-compose exec -T postgres psql -U davila bd_davila < backup_file.sql
```

## ⚙️ Configuración Avanzada

### Personalizar Puertos
Modifica `docker-compose.yml` para cambiar puertos:
```yaml
services:
  postgres:
    ports:
      - "5433:5432"  # Cambiar puerto PostgreSQL
  cloudbeaver:
    ports:
      - "8080:8978"  # Cambiar puerto CloudBeaver
```

### Variables de Entorno Adicionales
```env
# Configuraciones adicionales PostgreSQL
POSTGRES_INITDB_ARGS=--encoding=UTF-8 --lc-collate=C --lc-ctype=C

# Configuraciones CloudBeaver
CB_WORKSPACE=/opt/cloudbeaver/workspace
```

### Data Sources Preconfigurados
El archivo `data-sources.json` incluye:
- Conexión automática a PostgreSQL
- Configuración de drivers
- Parámetros de conexión optimizados

## 🔐 Seguridad y Mejores Prácticas

### Configuración de Seguridad
- ✅ Archivo `.env` excluido del control de versiones
- ✅ Red Docker aislada (`db_network`)
- ✅ Acceso por credenciales únicamente
- ✅ Variables de entorno para configuración sensible

### Recomendaciones de Producción
```env
# Usar contraseñas complejas
POSTGRES_PASSWORD=Tu_Password_Complejo_123!
CB_ADMIN_PASSWORD=Admin_Password_Seguro_456!

# Considerar certificados SSL
# Configurar firewalls apropiados
# Implementar backup automático
```

## 🔧 Solución de Problemas

### Problemas Comunes

#### CloudBeaver no se conecta a PostgreSQL
```bash
# 1. Verificar que ambos contenedores estén running
docker-compose ps

# 2. Revisar logs de conexión
docker-compose logs cloudbeaver

# 3. Verificar variables de entorno
cat .env

# 4. Reiniciar servicios
docker-compose restart
```

#### Puerto ya en uso
```bash
# Verificar qué proceso usa el puerto
netstat -tulpn | grep :5432
netstat -tulpn | grep :8978

# Cambiar puertos en docker-compose.yml si es necesario
```

#### Problemas de permisos
```bash
# Recrear volúmenes con permisos correctos
docker-compose down -v
docker volume prune
docker-compose up -d
```

#### Base de datos corrupta
```bash
# Backup de emergencia
docker-compose exec postgres pg_dumpall -U davila > emergency_backup.sql

# Recrear contenedor
docker-compose down
docker volume rm postgres_data
docker-compose up -d
```

## 📈 Desarrollo y Integración

### Conectar Aplicaciones Externas
```python
# Ejemplo Python con psycopg2
import psycopg2

conn = psycopg2.connect(
    host="localhost",
    port=5432,
    database="bd_davila",
    user="davila",
    password="cramer*69"
)
```

### Integración con MCP Servers
- Base de datos lista para aplicaciones MCP
- Variables de entorno compatibles
- Red Docker para microservicios

### Próximos Pasos
1. **Crear esquemas** específicos para tus aplicaciones
2. **Configurar usuarios** adicionales con permisos específicos
3. **Implementar backup** automático programado
4. **Monitorear performance** con CloudBeaver
5. **Escalar horizontalmente** si es necesario

## 📚 Recursos Adicionales

### Documentación
- [PostgreSQL 15 Documentation](https://www.postgresql.org/docs/15/)
- [CloudBeaver Documentation](https://cloudbeaver.io/docs/)
- [Docker Compose Reference](https://docs.docker.com/compose/)

### Comandos Útiles PostgreSQL
```sql
-- Ver todas las bases de datos
\l

-- Conectar a una base específica
\c bd_davila

-- Ver todas las tablas
\dt

-- Describir una tabla
\d nombre_tabla
```

---

**Entorno optimizado para**: Desarrollo MCP, Análisis de datos, Aplicaciones web  
**Última actualización**: Junio 2025  
**Versión**: 2.1  
**Compatibilidad**: Docker 20+, Docker Compose 2+