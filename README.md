# SIGER PRO v2.0 — Sistema de Gestión de Riesgos

**AIES-SOARG / CEPA · 2026**

Sistema web de gestión de riesgos de seguridad operacional para el Aeropuerto Internacional El Salvador (AIES-SOARG), desarrollado para la Comisión Ejecutiva Portuaria Autónoma (CEPA).

---

## 🚀 Características principales

- **Registro de Reportes** — Captura completa de eventos de seguridad operacional con todos los campos del formato OACI/SMS.
- **Evaluación de Riesgo** — Matriz de Riesgo OACI/SMS con índices de probabilidad (1–5) y severidad (A–E).
- **Indicadores de Impacto** — Gauges de alto y bajo impacto con análisis estadístico (desviación estándar σ, UCL, LCL).
- **Datos Históricos** — Carga de datos de años anteriores para enriquecer el cálculo estadístico.
- **Exportar PDF (Formato RSC)** — Generación de reporte oficial con logo CEPA, firmas y todos los campos.
- **Base Normativa** — Tabla de regulaciones RAC y normativa AIES-SOARG con auto-relleno en nuevos reportes.
- **Autoguardado** — Persistencia local automática (localStorage) con indicador visual de estado.
- **Roles de usuario** — Superadministrador, Administrador y Auditor con permisos diferenciados.
- **Importar / Exportar** — Soporte para archivos `.xlsx` y `.csv` con el mismo formato de la base de datos.
- **Versiones / Snapshots** — Guardar y restaurar versiones nombradas de la base de datos.
- **Menú hamburguesa** — Sidebar ocultable para maximizar el espacio de trabajo.

---

## 🗂️ Estructura del proyecto

```
sigerpro/
├── index.html        # Aplicación completa (single-file app, sin dependencias externas)
├── README.md         # Documentación
├── .gitignore        # Archivos a ignorar
└── LICENSE           # Licencia del proyecto
```

> **Sin dependencias externas.** Toda la lógica (gráficas, lectura de XLSX, exportación CSV, generación de PDF) está implementada en JavaScript puro dentro del archivo `index.html`.

---

## 🖥️ Uso

### Ejecución local
Simplemente abrir `index.html` en cualquier navegador moderno (Chrome, Edge, Firefox).

```bash
# Opción 1: doble clic en el archivo
open index.html

# Opción 2: servidor local rápido con Python
python3 -m http.server 8080
# Luego visitar http://localhost:8080
```

### GitHub Pages (publicación en línea)
1. Subir el repositorio a GitHub.
2. Ir a **Settings → Pages**.
3. Seleccionar rama `main` y carpeta raíz `/`.
4. La aplicación estará disponible en `https://<usuario>.github.io/<repositorio>/`.

---

## 🔐 Credenciales por defecto

| Usuario | Email | Contraseña | Rol |
|---------|-------|------------|-----|
| Noé López | `noe.lopez@cepa.gob.sv` | `cepa2026` | Superadministrador |
| María García | `maria.garcia@cepa.gob.sv` | `cepa2026` | Administrador |
| Carlos Auditor | `carlos.auditor@cepa.gob.sv` | `auditor123` | Auditor |

> ⚠️ Se recomienda cambiar las contraseñas en producción desde la sección **Gestión de Usuarios**.

---

## 📋 Formato de importación

El sistema acepta archivos `.xlsx` o `.csv` con las siguientes columnas principales:

| Columna | Descripción |
|---------|-------------|
| `NO.` | Número de reporte |
| `FECHA` | Fecha del evento (YYYY-MM-DD o DD/MM/YYYY) |
| `TIPO DE OCURRENCIA/PELIGRO` | Tipo de evento |
| `REPORTE PRESENTADO POR:` | Nombre del reportante |
| `ENTIDAD DE ORIGEN DE REPORTE` | Entidad que reporta |
| `PROBABILIDAD DE RIESGO` | Valor 1–5 |
| `SEVERIDAD DE RIESGO` | Letra A–E |
| `ESTADO` | `CIERRE` o `SEGUIMIENTO` |

Descargar plantilla desde la sección **Importar Excel → Descargar Plantilla**.

---

## 🔧 Módulos técnicos

| Módulo | Tecnología |
|--------|-----------|
| Interfaz | HTML5 + CSS3 (Variables CSS, Grid, Flexbox) |
| Lógica | JavaScript ES6+ (vanilla, sin frameworks) |
| Gráficas | Canvas API personalizado (sin Chart.js) |
| Lectura XLSX | Parser ZIP/XML propio (sin SheetJS) |
| Exportación | CSV con BOM UTF-8 (compatible Excel) |
| PDF | `window.print()` con CSS `@media print` |
| Persistencia | `localStorage` del navegador |
| Tipografía | IBM Plex Sans + IBM Plex Mono (Google Fonts) |

---

## 📊 Matriz de Riesgo OACI/SMS

| | A Catastrófico | B Peligroso | C Mayor | D Menor | E Insignificante |
|---|---|---|---|---|---|
| **5 Frecuente** | 🔴 | 🔴 | 🔴 | 🟡 | 🟡 |
| **4 Ocasional** | 🔴 | 🔴 | 🟡 | 🟡 | 🟡 |
| **3 Remoto** | 🔴 | 🟡 | 🟡 | 🟢 | 🟢 |
| **2 Improbable** | 🟡 | 🟡 | 🟡 | 🟢 | 🟢 |
| **1 S. Improbable** | 🟡 | 🟢 | 🟢 | 🟢 | 🟢 |

🔴 Intolerable · 🟡 Tolerable · 🟢 Aceptable

---

## 👨‍💻 Desarrollado por

**Noé López** — AIES-SOARG / CEPA · 2026

---

## 📄 Licencia

Este software es de uso interno institucional. Todos los derechos reservados © CEPA 2026.
