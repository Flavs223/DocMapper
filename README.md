# SystemDoc & InfraMapper

Aplicación de escritorio en Java para **centralizar y generar automáticamente la documentación
técnica de infraestructura TI**: manuales de instalación por solución, reportes de atención
en sitio y diagramas de flujo de datos de red.

> Proyecto personal en desarrollo. Nombre provisional.

---

## ¿Qué problema resuelve?

En soporte de impresión (PaperCut, NDD Print, Lexmark LCPM) la documentación termina dispersa
en archivos Word, correos y notas sueltas. Este proyecto busca unificar tres tareas que hoy
se hacen a mano:

1. **Estandarizar manuales de instalación** por plataforma, con requisitos, pasos, puertos y troubleshooting.
2. **Generar reportes de visita en sitio** con formato limpio y exportable (Markdown / TXT / HTML).
3. **Documentar la infraestructura del cliente** (nodos, IPs, flujos) y exportarla como diagrama
   visual en sintaxis **Mermaid.js**, sin dibujar a mano.

---

## Módulos previstos

| Módulo | Descripción |
|--------|-------------|
| **A. Manuales** | Plantillas estandarizadas, clasificación por plataforma, búsqueda por palabra clave. |
| **B. Reportes de visita** | Captura de cliente, fecha, falla, causa raíz y solución; exportación a formatos limpios. |
| **C. Infraestructura** | Registro de nodos (servidores, switches, MFP, nubes) y flujos IP/puerto; exportación a Mermaid. |
| **D. Persistencia** | Almacenamiento local en JSON con operaciones CRUD. |

---

## ¿Qué NO incluye (v1)?

- Conexión directa por SNMP a impresoras o switches reales (el mapeo será documental/manual).
- Interfaz gráfica pesada. Se prioriza la lógica de negocio y una CLI o interfaz web ligera.

---

## Flujo de uso

```
[ Inicio de la App ]
       │
       ├──> 1. Crear / Consultar Manual Técnico (PaperCut, NDD, Lexmark)
       │       └──> Genera guía paso a paso en formato formateado.
       │
       ├──> 2. Generar Reporte de Visita en Sitio
       │       └──> Solicita datos del cliente y exporta reporte final.
       │
       ├──> 3. Documentar Infraestructura de Cliente
       │       └──> Captura IPs/Nodos y exporta código de Diagrama de Red.
       │
       └──> [ Guardado en JSON Local ] (Persistencia automática)
```

---

## Estado del proyecto

- [x] Definición del alcance
- [ ] Estructura base del proyecto (Maven + carpetas)
- [ ] Módulo D — Persistencia JSON
- [ ] Módulo A — Manuales
- [ ] Módulo B — Reportes de visita
- [ ] Módulo C — Diagramas Mermaid
- [ ] Interfaz web ligera (futuro)

---

## Requisitos técnicos

- JDK 17+
- Maven 3.9+

---

## Estructura del repositorio (prevista)

```
systemdoc-inframapper/
├── pom.xml
├── src/
│   ├── main/java/com/systemdoc/
│   │   ├── model/       → POJOs (Manual, Reporte, Nodo, Flujo…)
│   │   ├── repository/  → CRUD sobre JSON
│   │   ├── service/     → lógica de negocio
│   │   ├── exporter/    → Markdown, HTML, Mermaid
│   │   └── cli/         → menú de consola
│   └── test/java/...
└── data/                → archivos JSON locales (no versionados)
```

---

