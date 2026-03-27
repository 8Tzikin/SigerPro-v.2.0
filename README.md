# SIGER PRO v2.0
## Sistema de Gestión de Riesgos de Seguridad Operacional — AIES-SOARG / CEPA

<div align="center">

![Version](https://img.shields.io/badge/versión-2.0-blue?style=flat-square)
![Tipo](https://img.shields.io/badge/tipo-Single%20File%20App-green?style=flat-square)
![Licencia](https://img.shields.io/badge/licencia-MIT-yellow?style=flat-square)
![Estado](https://img.shields.io/badge/estado-Producción-brightgreen?style=flat-square)
![Dependencias](https://img.shields.io/badge/dependencias-ninguna-lightgrey?style=flat-square)

**Sistema web de evaluación, registro y seguimiento de eventos de seguridad operacional aeroportuaria.**

> ⚡ Sin instalación. Sin servidor. Sin dependencias. Solo abre `index.html` en Chrome o Edge.

</div>

---

## 📋 Tabla de Contenidos

- [Descripción](#-descripción)
- [Características](#-características)
- [Requisitos](#-requisitos)
- [Instalación y uso](#-instalación-y-uso)
- [Estructura del proyecto](#-estructura-del-proyecto)
- [Roles y permisos](#-roles-y-permisos)
- [Usuarios por defecto](#-usuarios-por-defecto)
- [Funcionalidades principales](#-funcionalidades-principales)
- [Indicadores de desempeño](#-indicadores-de-desempeño)
- [Formato de importación](#-formato-de-importación)
- [Evidencias en PDF](#-evidencias-en-pdf)
- [Respaldo de datos](#-respaldo-de-datos)
- [Tecnologías](#-tecnologías)
- [Changelog](#-changelog)
- [Autor](#-autor)

---

## 📖 Descripción

SIGER PRO es una **Single-Page Application (SPA) de archivo único** sin dependencias externas, diseñada para el Aeropuerto Internacional El Salvador (AIES-SOARG) bajo la gestión de la **Comisión Ejecutiva Portuaria Autónoma (CEPA)**. Permite registrar, evaluar y dar seguimiento a eventos de seguridad operacional siguiendo los estándares **OACI/SMS** y las normativas **RAC** aplicables.

---

## ✨ Características

| Función | Descripción |
|---|---|
| 📊 **Dashboard** | Resumen ejecutivo con KPIs, gráficas y últimos reportes |
| 📋 **Registro de Reportes** | CRUD completo con scroll interno, filtros y búsqueda |
| 📈 **Indicadores** | Gauges responsivos con análisis estadístico Prom+1σ / +2σ / +3σ |
| 🔲 **Matriz de Riesgo** | Visualización OACI 5×5 con conteo por celda |
| 📚 **Base Normativa** | Consulta de regulaciones RAC y normativa interna |
| 📄 **PDF Formato RSC** | Generación de reporte con firmas y evidencias adjuntas |
| 📎 **Evidencias PDF** | Adjuntar, gestionar y descargar archivos PDF por reporte |
| 📂 **Importar Excel/CSV** | Carga masiva desde `.xlsx` o `.csv` |
| 🗄️ **Bases Guardadas** | Snapshots restaurables de la base de datos |
| 📅 **Datos Históricos** | Carga de años anteriores para análisis estadístico |
| 💾 **Respaldo en D:\** | Guardado automático en unidad local (Chrome/Edge) |
| ➕ **Tipos Dinámicos** | Agregar nuevos Tipos de Ocurrencia y Tipos de Reporte con normativa asociada |
| 👥 **Gestión de Usuarios** | Control de acceso con 3 niveles de rol |
| 🔐 **Autenticación** | Login con sesiones persistentes |

---

## 💻 Requisitos

- **Navegador:** Google Chrome 86+ o Microsoft Edge 86+
- **Para respaldo en D:\:** Chrome o Edge (requiere File System Access API)
- **No requiere:** servidor web, base de datos, Node.js ni librerías externas

---

## 🚀 Instalación y uso

### Opción 1 — Uso directo (recomendado)
```bash
git clone https://github.com/TU_USUARIO/sigerpro.git
cd sigerpro

# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

### Opción 2 — Servidor local
```bash
# Python 3
python -m http.server 8080

# Node.js
npx serve .

# Accede en: http://localhost:8080
```

---

## 📁 Estructura del proyecto

```
sigerpro/
│
├── index.html                   ← Aplicación completa (HTML + CSS + JS)
│
├── docs/
│   ├── MANUAL_USUARIO.md        ← Guía de uso paso a paso
│   ├── FORMATO_IMPORTACION.md   ← Especificación CSV/XLSX
│   └── ARQUITECTURA.md          ← Documentación técnica
│
├── .gitignore
├── CHANGELOG.md
├── LICENSE
└── README.md
```

> 💡 Toda la lógica (estilos, scripts y markup) está en **un único archivo** `index.html` para máxima portabilidad.

---

## 👥 Roles y permisos

| Rol | Ver | Crear | Editar | Eliminar | Usuarios |
|---|:---:|:---:|:---:|:---:|:---:|
| `superadmin` | ✅ | ✅ | ✅ | ✅ | ✅ Completo |
| `admin` | ✅ | ✅ | ✅ | ❌ | ✅ Solo editar |
| `auditor` | ✅ | ❌ | ❌ | ❌ | ❌ |

---

## 🔑 Usuarios por defecto

| Usuario | Contraseña | Rol |
|---|---|---|
| `noe.lopez@cepa.gob.sv` | `cepa2026` | Superadministrador |
| `maria.garcia@cepa.gob.sv` | `cepa2026` | Administrador |
| `carlos.auditor@cepa.gob.sv` | `auditor123` | Auditor |

> ⚠️ Cambia las contraseñas antes de poner el sistema en producción.

---

## 🔧 Funcionalidades principales

### Base de datos vacía al iniciar
El sistema inicia sin registros. Los datos se cargan exclusivamente mediante importación de Excel/CSV o ingreso manual de reportes.

### Nuevo Reporte
- Tipos de Ocurrencia y Tipos de Reporte **dinámicos** — se pueden agregar nuevos tipos desde el formulario
- Al seleccionar un Tipo de Ocurrencia, la Regulación y Normativa se rellenan **automáticamente**
- El Índice de Riesgo se calcula en tiempo real (Probabilidad × Severidad)

### Generar PDF (Formato RSC)
1. Clic en **PDF** en cualquier fila de la lista
2. Ingresa los nombres para firmas
3. El PDF se genera con todas las secciones incluyendo evidencias adjuntas

---

## 📈 Indicadores de desempeño

Los gauges muestran la tasa de ocurrencia de cada tipo de evento y calculan automáticamente los tres niveles de desviación estándar:

| Nivel | Cálculo | Estado |
|---|---|---|
| 🟢 **Normal** | Valor ≤ Prom + 1σ | Dentro del rango esperado |
| 🟡 **Atención** | Prom+1σ < Valor ≤ Prom+2σ | Ligero incremento |
| 🟠 **Alerta** | Prom+2σ < Valor ≤ Prom+3σ | Incremento significativo |
| 🔴 **Crítico** | Valor > Prom+3σ | Requiere acción inmediata |

Los gauges son **totalmente responsivos** — se adaptan al ancho disponible en pantalla y se redibujan al redimensionar la ventana. Los indicadores de Alto y Bajo Impacto permiten seleccionar **cualquier tipo** de la base en cualquier sección.

---

## 📊 Formato de importación

| Columna | Requerido |
|---|:---:|
| `NO.` | Sí |
| `FECHA` (YYYY-MM-DD) | Sí |
| `TIPO DE OCURRENCIA/PELIGRO` | Sí |
| `REPORTE PRESENTADO POR:` | Sí |
| `ENTIDAD DE ORIGEN DE REPORTE` | No |
| `PROBABILIDAD DE RIESGO` (1–5) | No |
| `SEVERIDAD DE RIESGO` (A–E) | No |
| `ESTADO` (CIERRE/SEGUIMIENTO) | No |

> Descarga la plantilla desde el modal Importar → **Descargar plantilla CSV**.

Consulta la especificación completa en [docs/FORMATO_IMPORTACION.md](docs/FORMATO_IMPORTACION.md).

---

## 📎 Evidencias en PDF

- Botón **📎 Evidencia** en cada fila de la lista
- Drag & Drop o selector de archivos (solo `.pdf`, máx. 10 MB)
- Almacenamiento en `localStorage` del navegador
- Las evidencias aparecen listadas en el PDF generado (Sección 5)

---

## 💾 Respaldo de datos

### Respaldo automático en D:\
```
Menú lateral → Respaldo en D:\ → Seleccionar carpeta
```
Guarda archivos `.json` automáticamente cada 5 minutos y al cerrar sesión.

### Exportar CSV
Botón **Exportar** en la topbar — compatible con Excel.

### Snapshots
**Guardar versión** para crear puntos de restauración con nombre personalizado.

---

## 🛠 Tecnologías

| Tecnología | Uso |
|---|---|
| HTML5 + CSS3 + JS ES6+ | Toda la aplicación |
| localStorage API | Persistencia de datos |
| File System Access API | Respaldo en unidad local |
| Canvas API | Gráficas y gauges (sin Chart.js) |
| DecompressionStream API | Lectura XLSX sin librerías |
| IBM Plex Sans | Tipografía (Google Fonts) |

---

## 📝 Changelog

Ver [CHANGELOG.md](CHANGELOG.md) para el historial detallado de versiones.

---

## 👤 Autor

**Noé López**  
CEPA — Aeropuerto Internacional El Salvador (AIES-SOARG)  
SIGER PRO v2.0 · 2026

---

## 📄 Licencia

MIT License — ver [LICENSE](LICENSE).

---

<div align="center">
✦ Desarrollado por Noé López · SIGER PRO v2.0 · CEPA 2026
</div>
