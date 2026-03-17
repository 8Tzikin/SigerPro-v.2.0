# Changelog — SIGER PRO

Todos los cambios notables de este proyecto están documentados aquí.

El formato sigue [Keep a Changelog](https://keepachangelog.com/es-ES/1.0.0/).

---

## [2.0.0] — 2026-03-17

### Agregado
- **Módulo de Evidencias PDF:** adjuntar archivos PDF por reporte, con gestión (subir, descargar, eliminar), drag & drop, validación de tamaño (10 MB max) y visualización en el modal de detalle.
- **Evidencias en Formato RSC:** el PDF generado incluye automáticamente la sección "5. Evidencias Adjuntas" con nombre, tamaño y fecha de cada archivo.
- **Badge de evidencias:** indicador visual en la tabla de reportes que muestra el número de evidencias adjuntas por reporte.
- **Botón "Adjuntar Evidencia"** en el pie del modal de detalle para acceso rápido.
- **Panel de evidencias** dentro del modal de detalle con descarga directa.
- **Respaldo en Unidad D:\:** guardado automático de la base completa en formato `.json` cada 5 minutos usando File System Access API (requiere Chrome/Edge 86+).
- **Datos Históricos:** carga de registros de años anteriores para calcular desviación estándar (σ), UCL y LCL en indicadores.
- **Análisis estadístico σ:** cada gauge de indicador muestra Media, Desviación Estándar, UCL (μ+2σ) y LCL (μ-2σ) con estado de control.
- **Selector dinámico de indicadores:** los gauges ya no se muestran todos a la vez; el usuario elige cuántos y cuáles ver en indicadores de alto y bajo impacto.
- **Persistencia de selecciones de indicadores:** las preferencias de gauges se guardan en localStorage y se restauran al recargar.
- **Botón hamburger:** colapsa/expande el sidebar lateral con animación suave.
- **Auto-rellenado de normativa:** al seleccionar el Tipo de Ocurrencia, los campos de Regulación y Normativa AIES-SOARG se rellenan automáticamente.
- **Gestión de Usuarios completa:** agregar, editar y eliminar usuarios con control por rol.
- **Lector XLSX nativo:** importación de archivos `.xlsx` y `.csv` sin dependencias externas (DecompressionStream API).
- **Autodetección de hoja correcta:** al importar XLSX, detecta automáticamente la hoja con datos aunque el archivo tenga múltiples hojas.
- **Snapshots (Bases guardadas):** guardar y restaurar versiones nombradas de la base de datos.
- **Autosave:** guardado automático en localStorage cada 60 segundos y al cerrar pestaña.
- **Indicador de autoguardado:** en la topbar muestra el estado y hora del último guardado.
- **Vaciar base de datos** con confirmación.
- **Exportar histórico a CSV** por año.
- **Revisor AAC** en campos del reporte y en el PDF RSC.

### Cambiado
- **Gráficas internas:** reemplazo completo de Chart.js por motor Canvas propio, eliminando la dependencia externa.
- **Exportación:** reemplazo de SheetJS/XLSX.js por exportación CSV con BOM UTF-8 (compatible con Excel).
- **UI:** rediseño completo con paleta institucional CEPA (Navy #00205B, Gold #C9A227, Teal).
- **Tabla de lista:** columnas adicionales (Entidad, Prob., Sev.), paginación de 25 por página.
- **Modal de detalle:** se agregó panel de evidencias adjuntas integrado en la vista.
- **PDF RSC:** encabezado con logo CEPA, secciones numeradas, colores de riesgo y sección de evidencias condicional.

### Corregido
- Autodetección de fila de encabezado en archivos XLSX con filas de título superiores.
- Reconocimiento de múltiples variantes de nombres de columna en importación.
- Manejo de fechas en formato serial Excel, ISO y DD/MM/YYYY.
- Sincronización de badges de conteo tras importación.

---

## [1.0.0] — 2025-01-01

### Agregado
- Primera versión del sistema.
- Registro básico de eventos de seguridad operacional.
- Matriz de riesgo OACI 5×5.
- Generación de PDF Formato RSC.
- Importación desde Excel.
- Dashboard con gráficas (Chart.js).
- Login con roles de usuario.
