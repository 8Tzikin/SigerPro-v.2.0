# Changelog — SIGER PRO

Formato basado en [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/).

---

## [2.0.0] — 2026-03-27

### Agregado
- **Base vacía al iniciar:** el sistema arranca sin registros de ejemplo; los datos se cargan exclusivamente por importación o ingreso manual.
- **Tipos de Ocurrencia dinámicos:** botón `+ Nuevo` para agregar tipos personalizados con Regulación AAC y Normativa CEPA asociadas (auto-relleno automático). Los tipos persisten en localStorage y están disponibles en todos los formularios.
- **Tipos de Reporte dinámicos:** mismo mecanismo para agregar nuevos tipos de reporte.
- **Gauges responsivos:** los medidores se adaptan automáticamente al ancho de la tarjeta; CSS Grid reemplaza el flex-wrap anterior. Se redibujan al redimensionar la ventana.
- **Análisis estadístico con tres niveles σ:** Prom+1DVSTD (Atención), Prom+2DVSTD (Alerta), Prom+3DVSTD (Crítico). Se eliminaron UCL/LCL en favor de esta escala de tres niveles.
- **Indicadores sin restricción de categoría:** los dropdowns de Alto y Bajo Impacto muestran todos los tipos de la base en lista plana (sin separadores de grupo), permitiendo elegir cualquier indicador en cualquier sección.
- **Scroll interno en Registro de Reportes:** la tabla tiene scroll lateral derecho propio; la barra de filtros y paginación quedan fijas fuera del área de scroll. Header de columnas sticky.
- **Módulo de Evidencias PDF:** adjuntar archivos PDF por reporte, con gestión (subir, descargar, eliminar), drag & drop, validación de tamaño (10 MB max) y badge de conteo en la lista.
- **Evidencias en Formato RSC:** la Sección 5 del PDF generado lista automáticamente los archivos adjuntos.
- **Respaldo en Unidad D:\:** guardado automático `.json` cada 5 minutos (File System Access API, Chrome/Edge 86+).
- **Datos Históricos:** carga de registros de años anteriores para análisis estadístico comparativo.
- **Snapshots (Bases guardadas):** puntos de restauración con nombre personalizado.
- **Autoguardado** en localStorage cada 60 segundos y al cerrar pestaña.
- **Botón hamburger** para colapsar/expandir sidebar.
- **Auto-rellenado de normativa** al seleccionar Tipo de Ocurrencia.
- **Gestión de Usuarios completa** con roles superadmin/admin/auditor.
- **Lector XLSX nativo** sin dependencias externas (DecompressionStream API).

### Cambiado
- **Severidad C:** renombrada de "Mayor" a **"Grave"** en toda la interfaz (dropdowns, PDF, tabla normativa, matriz de riesgo).
- **Columnas eliminadas en Base Normativa:** se quitaron "Artículo AAC" y "Artículo CEPA" de la vista de tabla (los datos internos se conservan para auto-relleno).
- **Gráficas:** motor Canvas propio reemplaza Chart.js (cero dependencias externas).
- **Exportación:** CSV con BOM UTF-8 reemplaza SheetJS.
- **Clave de base de datos** actualizada a `sigerpro_db_v2` para garantizar inicio limpio.
- **PDF RSC:** encabezado con logo CEPA, secciones numeradas, colores de riesgo.

### Corregido
- Autodetección de hoja correcta en archivos XLSX con múltiples hojas.
- Manejo de fechas en formato serial Excel, ISO y DD/MM/YYYY.
- Restauración de preferencias de indicadores al recargar.

---

## [1.0.0] — 2025-01-01

### Agregado
- Primera versión del sistema.
- Registro de eventos de seguridad operacional.
- Matriz de riesgo OACI 5×5.
- Generación de PDF Formato RSC.
- Importación desde Excel.
- Dashboard con gráficas (Chart.js).
- Login con roles de usuario.
