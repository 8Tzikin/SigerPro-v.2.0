# SIGER PRO v2.0
## Sistema de Gestión de Riesgos — AIES-SOARG / CEPA

<div align="center">

![Version](https://img.shields.io/badge/versión-2.0-blue?style=flat-square)
![Tipo](https://img.shields.io/badge/tipo-Single%20File%20App-green?style=flat-square)
![Licencia](https://img.shields.io/badge/licencia-MIT-yellow?style=flat-square)
![Estado](https://img.shields.io/badge/estado-Producción-brightgreen?style=flat-square)
![Dependencias](https://img.shields.io/badge/dependencias-ninguna-lightgrey?style=flat-square)

**Sistema web de evaluación, registro y seguimiento de eventos de seguridad operacional aeroportuaria.**

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
- [Formato de importación](#-formato-de-importación)
- [Evidencias en PDF](#-evidencias-en-pdf)
- [Respaldo de datos](#-respaldo-de-datos)
- [Tecnologías](#-tecnologías)
- [Capturas](#-capturas)
- [Changelog](#-changelog)
- [Autor](#-autor)

---

## 📖 Descripción

SIGER PRO es una aplicación web de **una sola página (SPA)** sin dependencias externas, diseñada para el Aeropuerto Internacional El Salvador (AIES-SOARG) bajo la gestión de la **Comisión Ejecutiva Portuaria Autónoma (CEPA)**. Permite registrar, evaluar y hacer seguimiento a eventos de seguridad operacional siguiendo los estándares **OACI/SMS** y las normativas **RAC** aplicables.

> ⚡ **Sin instalación requerida.** Solo abre `index.html` en un navegador moderno.

---

## ✨ Características

| Función | Descripción |
|---|---|
| 📊 Dashboard | Resumen ejecutivo con KPIs, gráficas de distribución y últimos reportes |
| 📋 Registro de Reportes | CRUD completo con paginación, filtros y búsqueda avanzada |
| 📈 Indicadores | Gauges por tipo de ocurrencia con análisis estadístico σ (UCL/LCL) |
| 🔲 Matriz de Riesgo | Visualización OACI 5×5 con conteo de ocurrencias por celda |
| 📚 Base Normativa | Consulta de regulaciones RAC y normativa interna AIES-SOARG |
| 📄 Exportación PDF | Generación de Formato RSC con firmas y evidencias adjuntas |
| 📎 Evidencias PDF | Adjuntar, gestionar y descargar archivos PDF por reporte |
| 📂 Importar Excel/CSV | Carga masiva de reportes desde archivos `.xlsx` o `.csv` |
| 🗄️ Bases Guardadas | Snapshots restaurables de la base de datos |
| 📅 Datos Históricos | Carga de años anteriores para análisis estadístico comparativo |
| 💾 Respaldo en D:\ | Guardado automático en unidad local vía File System Access API |
| 👥 Gestión de Usuarios | Control de acceso con 3 niveles de rol |
| 🔐 Autenticación | Sistema de login con sesiones por pestaña |
| 💾 Autoguardado | Persistencia automática en localStorage cada 60 segundos |

---

## 💻 Requisitos

- **Navegador:** Google Chrome 86+ o Microsoft Edge 86+
- **Para respaldo en D:\:** Chrome o Edge (la función `showDirectoryPicker` no está disponible en Firefox)
- **No requiere:** servidor web, base de datos, Node.js, ni ninguna librería externa

---

## 🚀 Instalación y uso

### Opción 1 — Uso directo (recomendado)
```bash
# Clona el repositorio
git clone https://github.com/TU_USUARIO/sigerpro.git

# Entra al directorio
cd sigerpro

# Abre el archivo directamente en Chrome o Edge
# Windows:
start index.html

# macOS:
open index.html

# Linux:
xdg-open index.html
```

### Opción 2 — Servidor local (opcional)
```bash
# Con Python 3
python -m http.server 8080

# Con Node.js (si tienes npx)
npx serve .

# Luego abre: http://localhost:8080
```

---

## 📁 Estructura del proyecto

```
sigerpro/
│
├── index.html          # Aplicación completa (HTML + CSS + JS embebidos)
│
├── docs/
│   ├── MANUAL_USUARIO.md    # Guía de uso detallada
│   ├── FORMATO_IMPORTACION.md  # Especificación del formato CSV/XLSX
│   └── ARQUITECTURA.md      # Notas técnicas de la aplicación
│
├── .gitignore
├── CHANGELOG.md
├── LICENSE
└── README.md
```

> 💡 Toda la lógica de la aplicación (estilos, scripts y markup) está contenida en **un único archivo** `index.html` para máxima portabilidad y facilidad de distribución.

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

> ⚠️ **Importante:** Cambia las contraseñas por defecto antes de poner el sistema en producción.

---

## 🔧 Funcionalidades principales

### Nuevo Reporte
1. Ve a **Nuevo Reporte** en el menú lateral
2. Completa los campos obligatorios: Fecha, Reportado Por, Tipo de Ocurrencia, Descripción
3. La **Regulación** y **Normativa** se rellenan automáticamente al seleccionar el tipo
4. El **Índice de Riesgo** se calcula automáticamente (Probabilidad × Severidad)
5. Guarda el reporte → regresa automáticamente a la lista

### Generar PDF (Formato RSC)
1. En la lista de reportes, haz clic en el botón **PDF** de cualquier fila
2. Ingresa los nombres para las firmas (Elaborado por, Revisado por, Autorizado por)
3. Clic en **Generar PDF** → se abre una ventana con el documento listo para imprimir/guardar

### Importar desde Excel
1. En el menú lateral, haz clic en **Importar Excel**
2. Arrastra o selecciona un archivo `.xlsx` o `.csv`
3. Verifica la vista previa de los datos
4. Confirma la importación

---

## 📊 Formato de importación

El archivo debe contener las siguientes columnas (ver `docs/FORMATO_IMPORTACION.md`):

| Columna | Requerido | Formato |
|---|:---:|---|
| `NO.` | Sí | Número entero |
| `FECHA` | Sí | YYYY-MM-DD o DD/MM/YYYY |
| `TIPO DE OCURRENCIA/PELIGRO` | Sí | Texto |
| `REPORTE PRESENTADO POR:` | Sí | Texto |
| `ENTIDAD DE ORIGEN DE REPORTE` | No | Texto |
| `PROBABILIDAD DE RIESGO` | No | 1–5 |
| `SEVERIDAD DE RIESGO` | No | A–E |
| `ESTADO` | No | `CIERRE` o `SEGUIMIENTO` |

> 📥 Descarga la plantilla desde el modal de importación → **Descargar plantilla CSV**.

---

## 📎 Evidencias en PDF

Cada reporte puede tener **archivos PDF de evidencia** adjuntos:

- **Adjuntar:** botón 📎 Evidencia en la fila del reporte o desde el detalle
- **Drag & Drop:** arrastra PDFs directo al modal
- **Límite:** 10 MB por archivo
- **Almacenamiento:** `localStorage` del navegador
- **Descarga:** botón ⬇ en la lista de evidencias
- **En el PDF RSC:** se genera automáticamente una sección "5. Evidencias Adjuntas"

---

## 💾 Respaldo de datos

### Respaldo automático en D:\
1. Menú lateral → **Respaldo en D:\**
2. Haz clic en **Seleccionar carpeta en D:\** y elige una carpeta
3. El sistema guardará archivos `.json` automáticamente cada **5 minutos** y al cerrar sesión
4. Para restaurar: haz clic en **Restaurar desde archivo de respaldo (.json)**

> ⚠️ Esta función requiere **Chrome** o **Edge** 86+.

### Exportar a CSV
- Usa el botón **Exportar** en la barra superior para descargar todos los reportes en formato `.csv` compatible con Excel.

### Bases guardadas (snapshots)
- Menú lateral → **Guardar versión** para crear un punto de restauración con nombre personalizado
- Menú lateral → **Bases guardadas** para cargar o eliminar versiones

---

## 🛠 Tecnologías

| Tecnología | Uso |
|---|---|
| **HTML5** | Estructura de la aplicación |
| **CSS3** | Estilos, variables CSS, animaciones |
| **JavaScript ES6+** | Toda la lógica de negocio |
| **localStorage API** | Persistencia de datos en el navegador |
| **File System Access API** | Respaldo en unidad local (D:\) |
| **Canvas API** | Gráficas y medidores (sin Chart.js) |
| **DecompressionStream API** | Lectura de archivos XLSX sin librerías |
| **IBM Plex Sans** | Tipografía (Google Fonts) |

> 🔒 **Sin dependencias externas de npm/CDN** para la lógica principal. La tipografía se carga desde Google Fonts (requiere conexión a internet para la fuente).

---

## 📸 Capturas

> Las capturas de pantalla se pueden encontrar en la carpeta `docs/` (si aplica).

---

## 📝 Changelog

Ver [CHANGELOG.md](CHANGELOG.md) para el historial de cambios.

---

## 👤 Autor

**Noé López**
- Institución: CEPA — Aeropuerto Internacional El Salvador (AIES-SOARG)
- Sistema: SIGER PRO v2.0
- Año: 2026

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver [LICENSE](LICENSE) para más detalles.

---

<div align="center">
✦ Desarrollado por Noé López · SIGER PRO v2.0 · CEPA 2026
</div>
