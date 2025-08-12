# OpenTelemetry Observability Stack

Este repositorio contiene una solución completa de observabilidad basada en **OpenTelemetry** para aplicaciones Java (Quarkus/Vert.x), integrando métricas, trazas y logs en un entorno de desarrollo local usando **Docker Compose**.

## Características principales

- Instrumentación automática y manual de aplicaciones Java con OpenTelemetry.
- Recolección y exportación de métricas a Prometheus.
- Recolección y visualización de trazas distribuidas con Tempo y Grafana.
- Centralización y consulta de logs con Loki y Grafana.
- Dashboards preconfigurados en Grafana para monitoreo y análisis.
- Configuración lista para desarrollo local usando Docker Compose.

## Componentes incluidos

- **Quarkus/Vert.x App:** Aplicación de ejemplo instrumentada con OpenTelemetry.
- **OpenTelemetry Collector:** Recibe, procesa y exporta métricas, trazas y logs.
- **Prometheus:** Recolecta métricas expuestas por el Collector.
- **Tempo:** Almacena y consulta trazas distribuidas.
- **Loki:** Almacena y consulta logs centralizados.
- **Grafana:** Visualiza métricas, logs y trazas en dashboards integrados.

## Estructura del repositorio

```
.
├── docker/
│   ├── docker-compose.yaml
│   └── volume/
│       ├── grafana/
│       ├── loki/
│       ├── prometheus/
│       └── otel-collector/
├── quarkus/
│   └── vertx-opentelemetry/
└── README.md
```

## Deploy

1. **Crear red de Docker**
   ```sh
   docker network create observability
   ```

2. **Desplegar los servicios**
   ```sh
   cd docker
   docker-compose up -d
   ```

## Cómo usar

1. Accede a Grafana en [http://localhost:3000](http://localhost:3000)  
   Usuario/contraseña por defecto: `admin` / `admin` (o según configuración).

2. Explora métricas, logs y trazas usando los dashboards preconfigurados.

## Personalización

- Modifica la configuración de los servicios en `docker/volume/*/config/` según tus necesidades.
- Instrumenta tus aplicaciones siguiendo las [guías de OpenTelemetry](https://opentelemetry.io/docs/instrumentation/java/).

## Requisitos

- Docker y Docker Compose
- Java 17+ (para la aplicación de ejemplo)

## Recursos útiles

- [OpenTelemetry](https://opentelemetry.io/)
- [Quarkus](https://quarkus.io/)
- [Grafana](https://grafana.com/)
- [Prometheus](https://prometheus.io/)
- [Loki](https://grafana.com/oss/loki/)
- [Tempo](https://grafana.com/oss/tempo/)

## Extensión futura: Instrumentación en Go y Node.js

Este stack de observabilidad está diseñado para ser **multilenguaje**.  
En el futuro, se planea agregar ejemplos y guías de instrumentación para aplicaciones desarrolladas en **Go** y **Node.js**, aprovechando la compatibilidad de OpenTelemetry con múltiples ecosistemas.

- **Go:** Se podrá instrumentar aplicaciones Go usando el SDK oficial de OpenTelemetry-Go, enviando métricas, trazas y logs al mismo collector.
- **Node.js:** Se podrá instrumentar aplicaciones Node.js usando el SDK oficial de OpenTelemetry-JS, integrando la observabilidad de servicios JavaScript en el mismo stack.

Esto permitirá monitorear, trazar y centralizar logs de aplicaciones heterogéneas en una sola plataforma, facilitando la observabilidad integral de arquitecturas modernas.