# SIGER PRO v2.0 — Sistema de Gestión de Riesgos

**AIES-SOARG / CEPA · El Salvador · 2026**

Sistema web de gestión de riesgos de seguridad operacional para el Aeropuerto Internacional El Salvador (AIES-SOARG), desarrollado para la Comisión Ejecutiva Portuaria Autónoma (CEPA).

---

## 🚀 Características principales

- **Registro de Reportes** — Captura completa de eventos de seguridad operacional con todos los campos del formato OACI/SMS.
- **Evaluación de Riesgo** — Matriz de Riesgo OACI/SMS con índices de probabilidad (1–5) y severidad (A–E).
- **Indicadores de Impacto** — Gauges de alto y bajo impacto con análisis estadístico (σ, UCL, LCL). Las selecciones se guardan automáticamente.
- **Datos Históricos** — Carga de datos de años anteriores para enriquecer el cálculo estadístico.
- **Exportar PDF (Formato RSC)** — Generación de reporte oficial con logo CEPA, datos completos y firmas.
- **Base Normativa** — Tabla de regulaciones RAC y normativa AIES-SOARG con auto-relleno en nuevos reportes.
- **Autoguardado** — Persistencia automática en localStorage con indicador visual de estado.
- **Respaldo en D:\\** — Respaldo automático en carpeta local usando File System Access API (Chrome/Edge).
- **Roles de usuario** — Superadministrador, Administrador y Auditor con permisos diferenciados. Usuarios persistidos en localStorage.
- **Importar / Exportar** — Soporte para archivos `.xlsx` y `.csv`.
- **Versiones / Snapshots** — Guardar y restaurar versiones nombradas de la base de datos.
- **Menú hamburguesa** — Sidebar ocultable para maximizar el espacio de trabajo.

---

## 🗂️ Estructura del proyecto

```
sigerpro/
├── index.html     # Aplicación completa (single-file, sin dependencias externas)
├── README.md      # Documentación
├── .gitignore     # Archivos a ignorar
└── LICENSE        # Licencia del proyecto
```

> **Sin dependencias externas.** Gráficas, lectura de XLSX, exportación CSV, generación de PDF y respaldo local están implementados en JavaScript puro dentro de `index.html`.

---

## 🖥️ Tecnologías utilizadas

| Tecnología | Uso |
|-----------|-----|
| **HTML5** | Estructura de interfaz, formularios, modales |
| **CSS3** | Diseño visual con identidad CEPA, variables CSS, Grid, Flexbox |
| **JavaScript ES6+** | Toda la lógica de negocio, sin frameworks externos |
| **Canvas API** | Gráficas de barras, dona y gauges |
| **localStorage** | Persistencia de datos, usuarios e indicadores |
| **File System Access API** | Respaldo automático en unidad local (D:\\) |
| **IBM Plex Sans/Mono** | Tipografía institucional (Google Fonts) |

---

## 🖥️ Uso

### Ejecución local
Abrir `index.html` en Chrome o Edge:

```bash
# Doble clic en el archivo, o con servidor local:
python3 -m http.server 8080
# Visitar http://localhost:8080
```

### GitHub Pages
1. Subir el repositorio a GitHub.
2. Ir a **Settings → Pages → Branch: main → Save**.
3. Disponible en `https://<usuario>.github.io/<repositorio>/`.

---

## 🔐 Credenciales por defecto

| Email | Contraseña | Rol |
|-------|-----------|-----|
| `noe.lopez@cepa.gob.sv` | `cepa2026` | Superadministrador |
| `maria.garcia@cepa.gob.sv` | `cepa2026` | Administrador |
| `carlos.auditor@cepa.gob.sv` | `auditor123` | Auditor |

> ⚠️ Cambiar contraseñas desde **Gestión de Usuarios** al desplegar en producción.

---

## 📋 Formato de importación (Excel/CSV)

| Columna | Descripción |
|---------|-------------|
| `NO.` | Número de reporte |
| `FECHA` | Fecha del evento (YYYY-MM-DD o DD/MM/YYYY) |
| `TIPO DE OCURRENCIA/PELIGRO` | Tipo de evento |
| `REPORTE PRESENTADO POR:` | Nombre del reportante |
| `PROBABILIDAD DE RIESGO` | Valor 1–5 |
| `SEVERIDAD DE RIESGO` | Letra A–E |
| `ESTADO` | `CIERRE` o `SEGUIMIENTO` |

---

## 📊 Matriz de Riesgo OACI/SMS

| | A Catastrófico | B Peligroso | C Mayor | D Menor | E Insignificante |
|---|:---:|:---:|:---:|:---:|:---:|
| **5 Frecuente** | 🔴 | 🔴 | 🔴 | 🟡 | 🟡 |
| **4 Ocasional** | 🔴 | 🔴 | 🟡 | 🟡 | 🟡 |
| **3 Remoto** | 🔴 | 🟡 | 🟡 | 🟡 | 🟢 |
| **2 Improbable** | 🟡 | 🟡 | 🟡 | 🟢 | 🟢 |
| **1 S. Improbable** | 🟡 | 🟢 | 🟢 | 🟢 | 🟢 |

🔴 Intolerable · 🟡 Tolerable · 🟢 Aceptable

---

## 🗄️ Almacenamiento de datos

Todos los datos se guardan en el navegador mediante `localStorage`:

| Clave | Contenido |
|-------|-----------|
| `sigerpro_db_v1` | Reportes de evaluación de riesgo |
| `sigerpro_users_v1` | Usuarios del sistema |
| `sigerpro_historical_v1` | Datos históricos por año |
| `sigerpro_snapshots_idx` | Índice de versiones guardadas |
| `sigerpro_ind_prefs_v1` | Selecciones de indicadores |

---

## 👨‍💻 Desarrollado por

**Noé López** — AIES-SOARG / CEPA · 2026

---

## 📄 Licencia

Uso interno institucional. Todos los derechos reservados © CEPA 2026.
