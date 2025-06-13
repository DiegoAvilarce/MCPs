# MCPs Project

Este es un proyecto de Model Context Protocol (MCP) servers con funcionalidades de consulta de tiempo, GitHub y contenido literario, además de un entorno Docker para bases de datos.

## Descripción

Este repositorio contiene implementaciones de servidores MCP para diferentes casos de uso, incluyendo:

- **Funciones de Tiempo**: Consulta de hora actual y conversión entre zonas horarias
- **Integración con GitHub**: Gestión de repositorios, issues, pull requests y más
- **Contenido Literario**: Resúmenes y análisis de obras literarias
- **Entorno Docker**: Configuración PostgreSQL + CloudBeaver para desarrollo
- **Ejemplos prácticos**: Notebook Jupyter con demostraciones de uso

## Estructura del Proyecto

```
MCPs/
├── harry_potter_resumen.md    # Resumen de Harry Potter
├── prueba.ipynb              # Notebook con ejemplos MCP
├── README.md                 # Este archivo
└── Docker Code/              # Entorno de base de datos
    ├── docker-compose.yml    # Configuración Docker
    ├── cloudbeaver-config.json # Configuración CloudBeaver
    ├── .env                  # Variables de entorno
    └── README.md             # Documentación específica Docker
```

## Características

### 🕐 Funciones de Tiempo
- Consulta de hora actual en cualquier zona horaria mundial
- Conversión de horarios entre diferentes zonas horarias
- Soporte para formato IANA timezone (ej: 'America/Sao_Paulo', 'Europe/London')

### 🐙 Integración con GitHub
- Crear y gestionar repositorios
- Manejar issues y pull requests
- Búsqueda de código y repositorios
- Gestión de archivos y commits

### 📚 Contenido Literario
- Resúmenes detallados de obras clásicas
- Análisis de personajes y temas principales
- Datos curiosos e impacto cultural

### 🐳 Entorno Docker
- PostgreSQL 15 preconfigurado
- CloudBeaver para administración web
- Variables de entorno centralizadas
- Configuración flexible con `.env`

## Inicio Rápido

### 1. Configurar entorno Docker (opcional)
```bash
cd "Docker Code"
# Configurar variables de entorno en .env
docker-compose up -d
```

### 2. Explorar ejemplos
Abre `prueba.ipynb` en Jupyter para ver ejemplos de las funciones MCP de tiempo.

### 3. Consultar contenido literario
Revisa `harry_potter_resumen.md` para ver un ejemplo de análisis literario detallado.

## Zonas Horarias Soportadas en Brasil
- **America/Sao_Paulo** - Región Sudeste y Sur (UTC-3)
- **America/Manaus** - Región Amazónica (UTC-4)
- **America/Fortaleza** - Región Nordeste (UTC-3)
- **America/Noronha** - Fernando de Noronha (UTC-2)

## Tecnologías Utilizadas

- **Model Context Protocol (MCP)**: Para funcionalidades de tiempo y GitHub
- **Docker & Docker Compose**: Containerización
- **PostgreSQL 15**: Base de datos
- **CloudBeaver**: Interfaz web para BD
- **Jupyter Notebook**: Documentación interactiva

## Contribución

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.