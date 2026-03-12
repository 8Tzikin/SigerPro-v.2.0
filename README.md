# SIGER PRO v1.0
### Sistema de Gestión de Riesgos — AIES-SOARG / CEPA · El Salvador

Aplicación web de gestión y evaluación de riesgos aeroportuarios desarrollada para la Comisión Ejecutiva Portuaria Autónoma (CEPA), basada en el modelo AIES-SOARG.

---

## 📁 Estructura del proyecto

```
sigerpro/
├── index.html          # Página principal (HTML de la aplicación)
├── css/
│   └── styles.css      # Estilos (tema institucional CEPA, colores, componentes)
├── js/
│   ├── data.js         # Datos iniciales (INITIAL_DATA — reportes de ejemplo)
│   └── app.js          # Lógica principal de la aplicación
└── README.md
```

---

## 🚀 Uso

### Opción A — Abrir directamente (local)
Simplemente abre `index.html` en tu navegador. No requiere servidor ni instalación.

### Opción B — Servidor local (recomendado para desarrollo)
```bash
# Python 3
python -m http.server 8080

# Node.js (npx)
npx serve .
```
Luego visita `http://localhost:8080`

---

## 🔑 Credenciales de acceso

| Usuario | Contraseña | Rol |
|---|---|---|
| `admin` | `cepa2026` | Superadministrador |
| `maria.garcia` | `cepa2026` | Administrador |
| `auditor` | `auditor123` | Auditor |

> **Nota de seguridad:** Cambia las contraseñas antes de desplegar en producción. Las credenciales se definen en `js/app.js` en el arreglo `USERS`.

---

## ✨ Funcionalidades

- **Dashboard** con KPIs y gráficas en tiempo real (Chart.js)
- **Indicadores** de riesgo con medidores visuales (gauge charts)
- **Registro de Reportes** con búsqueda, filtros y paginación
- **Nuevo Reporte** con formulario completo (probabilidad × severidad → índice de riesgo)
- **Matriz de Riesgo** AIES-SOARG interactiva
- **Normativa** de referencia (RAC 139, normas CEPA)
- **Importar/Exportar Excel** (.xlsx) usando SheetJS (xlsx.js)
- **Historial por Año**
- **Gestión de Usuarios** (roles: superadmin, admin, auditor)

---

## 🛠 Tecnologías

| Librería | Versión | Uso |
|---|---|---|
| [Chart.js](https://www.chartjs.org/) | 4.4.0 | Gráficas y dashboards |
| [SheetJS (xlsx)](https://sheetjs.com/) | 0.18.5 | Importar/exportar Excel |
| IBM Plex Sans / Mono | — | Tipografía institucional |

No requiere frameworks ni build tools. Todo corre en el navegador.

---

## 📋 Formato de importación Excel

El archivo debe contener las siguientes columnas (primera fila = encabezado):

| Columna | Descripción |
|---|---|
| `NO` | Número de reporte * |
| `FECHA` | Fecha del evento (YYYY-MM-DD) |
| `TIPO DE OCURRENCIA` | Categoría del evento * |
| `REPORTE PRESENTADO POR` | Nombre del reportante |
| `PROBABILIDAD DE RIESGO` | Número 1–5 |
| `SEVERIDAD DE RIESGO` | Letra A–E |
| `ESTADO` | CIERRE / SEGUIMIENTO |
| `REPORTE/TEXTO` | Descripción del evento |

Compatible con el formato **MATRIZ de CEPA**.

---

## 👤 Desarrollador

**Noé López** — AIES-SOARG · CEPA · El Salvador  
SIGER PRO v2.0 · 2026
