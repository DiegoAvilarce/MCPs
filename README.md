# MCPs Project

Este es un proyecto de Model Context Protocol (MCP) servers con funcionalidades avanzadas de consulta de tiempo, integración completa con GitHub y gestión de contenido, además de un entorno Docker optimizado para desarrollo con bases de datos.

## Descripción

Este repositorio contiene implementaciones robustas de servidores MCP para diferentes casos de uso empresariales y de desarrollo, incluyendo:

- **⏰ Funciones de Tiempo Avanzadas**: Consulta de hora actual y conversión inteligente entre zonas horarias globales
- **🔧 Integración Completa con GitHub**: Gestión automatizada de repositorios, issues, pull requests, reviews y más
- **📚 Procesamiento de Contenido**: Análisis y resúmenes de contenido literario y documentación
- **🐳 Entorno Docker Profesional**: Configuración PostgreSQL + CloudBeaver para desarrollo y producción
- **📓 Documentación Interactiva**: Notebooks Jupyter con ejemplos prácticos y casos de uso

## Estructura del Proyecto

```
MCPs/
├── README.md                 # Este archivo - Documentación principal
├── Docker Postgres/          # Entorno completo de base de datos
│   ├── docker-compose.yml    # Configuración Docker optimizada
│   ├── data-sources.json     # Configuración de fuentes de datos
│   └── README.md             # Documentación específica Docker
└── [Archivos de desarrollo]  # Notebooks y contenido adicional
```

## Características Principales

### ⏰ Sistema de Tiempo Global
- **Consulta de hora mundial**: Soporte para todas las zonas horarias IANA
- **Conversión inteligente**: Transformación automática entre zonas horarias
- **Precisión empresarial**: Manejo de horario de verano y cambios estacionales
- **Zonas horarias brasileñas**: Soporte especializado para todas las regiones de Brasil

### 🚀 GitHub Enterprise Integration
- **Gestión de repositorios**: Creación, configuración y administración completa
- **Control de issues**: Creación, asignación, etiquetado y seguimiento
- **Pull requests**: Creación, revisión, merge y gestión de conflictos
- **Búsqueda avanzada**: Código, repositorios, usuarios e issues
- **Automatización**: Workflows y acciones programáticas

### 📊 Procesamiento de Contenido
- **Análisis literario**: Resúmenes detallados y análisis temático
- **Extracción de metadatos**: Información estructurada de documentos
- **Generación de reportes**: Documentación automática y resúmenes

### 🏗️ Infraestructura Docker
- **PostgreSQL 15**: Base de datos enterprise-ready con persistencia
- **CloudBeaver**: Interfaz web moderna y profesional
- **Configuración flexible**: Variables de entorno centralizadas
- **Red segura**: Aislamiento de contenedores y comunicación segura

## Inicio Rápido

### 1. Configurar Entorno de Base de Datos
```bash
cd "Docker Postgres"
# Revisar y personalizar variables de entorno
docker-compose up -d
```

### 2. Verificar Servicios
```bash
# Verificar estado de contenedores
docker-compose ps

# Acceder a CloudBeaver
# URL: http://localhost:8978
```

### 3. Explorar Funcionalidades MCP
- Utiliza las funciones de tiempo para consultas globales
- Integra con GitHub para automatización de workflows
- Procesa contenido para análisis y documentación

## Zonas Horarias Soportadas

### Brasil (Completo)
- **America/Sao_Paulo** - Brasília, São Paulo, Rio (UTC-3)
- **America/Manaus** - Amazonas, Roraima (UTC-4)
- **America/Fortaleza** - Ceará, Nordeste (UTC-3)
- **America/Noronha** - Fernando de Noronha (UTC-2)

### Global (Ejemplos)
- **America/New_York** - Costa Este EE.UU.
- **Europe/London** - Reino Unido
- **Asia/Tokyo** - Japón
- **Australia/Sydney** - Australia Oriental

## Stack Tecnológico

- **Model Context Protocol (MCP)**: Framework para funcionalidades avanzadas
- **Docker & Docker Compose**: Containerización y orquestación
- **PostgreSQL 15**: Sistema de base de datos relacional
- **CloudBeaver**: Interfaz de administración web
- **Python**: Lenguaje principal de desarrollo
- **Jupyter**: Documentación interactiva y ejemplos

## Casos de Uso Empresariales

### Desarrollo de Software
- Automatización de releases en GitHub
- Gestión de issues y tracking de bugs
- Coordinación de equipos globales con zonas horarias

### Análisis de Contenido
- Procesamiento de documentación técnica
- Generación de resúmenes ejecutivos
- Extracción de insights de repositorios

### Operaciones
- Monitoreo de bases de datos con CloudBeaver
- Logs centralizados con timestamps precisos
- Gestión de configuraciones multi-región

## Configuración Avanzada

### Variables de Entorno Clave
```env
POSTGRES_DB=bd_davila
POSTGRES_USER=davila
POSTGRES_HOST=postgres
CB_ADMIN_NAME=davila
```

### Puertos de Desarrollo
- **PostgreSQL**: `localhost:5432`
- **CloudBeaver**: `localhost:8978`

## Contribución y Desarrollo

1. **Fork** el repositorio
2. **Crear rama** para nuevas funcionalidades
   ```bash
   git checkout -b feature/nueva-funcionalidad
   ```
3. **Desarrollar** con buenas prácticas
4. **Testing** completo de cambios
5. **Pull Request** con documentación actualizada

## Mantenimiento

### Actualización Regular
- Mantener dependencias actualizadas
- Revisar logs de contenedores Docker
- Backup regular de datos PostgreSQL

### Monitoreo
- Estado de servicios Docker
- Performance de base de datos
- Logs de aplicaciones MCP

## Licencia

Proyecto bajo **Licencia MIT** - Ver [LICENSE](LICENSE) para detalles completos.

---

**Última actualización**: Junio 2025  
**Versión**: 2.0  
**Mantenedor**: @davila