# Bot RPA - Impuesto Registro de Compras

## Descripción

Bot RPA que automatiza el proceso de registro de compras ante SUNAT. Descarga reportes desde Dynamics 365, procesa la información mediante plantillas Excel y realiza carga masiva de archivos TXT en el portal de SUNAT, consolidando los resultados en un reporte final automatizado.

## Funcionalidades Principales

### Descarga Automatizada desde Dynamics 365
- Autenticación automática en el sistema
- Descarga semanal programada de reportes PDF
- Filtrado por rango de fechas configurable (por defecto 7 días)
- Manejo de errores con reintentos automáticos

### Procesamiento de Datos
- Extracción de información desde archivos PDF
- Transformación mediante plantillas Excel con fórmulas
- Filtrado de registros por criterios específicos
- División automática de montos por IGV

### Generación de Archivos SUNAT
- Creación de archivos TXT en formato UTF-8
- Segmentación en lotes de máximo 100 registros
- Cumplimiento de especificaciones técnicas SUNAT
- Nomenclatura automática de archivos

### Carga Masiva en Portal SUNAT
- Autenticación automática en portal gubernamental
- Carga masiva de archivos TXT
- Descarga automática de respuestas
- Manejo inteligente de errores

### Consolidación y Reporte Final
- Procesamiento de respuestas SUNAT (Habido/No habido/Sin registro)
- Consolidación en Excel final
- Envío automático por correo electrónico
- Incluye rango de fechas procesado

## Arquitectura del Sistema

```
Dynamics 365 → Procesamiento Excel → Generación TXT → 
Portal SUNAT → Consolidación → Reporte Final
```

### Interfaz Dynamics 365
*Descarga de reportes con filtros de fecha*

### Portal SUNAT - Carga Masiva
*Interfaz de carga masiva de archivos TXT*

## Programación de Ejecución

- **Frecuencia**: Todos los miércoles
- **Hora**: 9:00 AM
- **Rango de fechas**: Últimos 7 días (configurable)
- **Procesamiento**: Automático sin intervención manual

## Estructura de Archivos

### Entrada
- Reportes PDF desde Dynamics 365
- Plantilla Excel "ReporteFinal.xlsx"

### Procesamiento
```
Registros filtrados: ≠ que inicien con "3" o "s"
Formato TXT: UTF-8
Lotes: Máximo 100 registros por archivo
```

### Salida
- Archivos TXT para carga SUNAT
- Excel consolidado con resultados
- Reporte enviado por email

## Manejo Inteligente de Errores

### Errores por Palabras No Reconocidas
- Detección automática del registro problemático
- Eliminación del registro con error
- Reintento de carga sin el registro problemático

### Errores Internos de SUNAT
- Detección de pop-ups de error del sistema
- Reintentos automáticos hasta obtener respuesta válida
- Notificación de errores persistentes

### Fallos de Autenticación
- Hasta 2 reintentos automáticos
- Notificación por email al equipo de soporte
- Log detallado de errores

## Tecnologías Utilizadas

- **RPA**: Power Automate Desktop
- **Integración**: Dynamics 365
- **Procesamiento**: Excel con macros y fórmulas
- **Formato**: Archivos TXT UTF-8
- **Portal**: SUNAT - Carga Masiva
- **Notificaciones**: Email automatizado

## Configuración del Sistema

### Credenciales Requeridas
- Acceso a Dynamics 365
- Credenciales portal SUNAT
- Configuración de correo electrónico

### Plantillas y Archivos
- ReporteFinal.xlsx con fórmulas configuradas
- Plantillas de formato TXT SUNAT
- Configuración de rangos de fecha

## Resultados y Métricas

### Estados de Procesamiento
- **Habido**: Registro encontrado y válido
- **No habido**: Registro no encontrado
- **Sin registro**: Sin información disponible

### Volumen de Procesamiento
- **Capacidad**: Hasta 100 registros por lote
- **Frecuencia**: Semanal automatizada
- **Tiempo**: Proceso completamente automatizado

## Flujo de Notificaciones

### Email Final Incluye
- Reporte Excel consolidado adjunto
- Rango de fechas procesado
- Resumen de resultados obtenidos
- Estado del procesamiento

## Beneficios

- **Automatización completa**: Sin intervención manual
- **Cumplimiento normativo**: Formato SUNAT estándar
- **Manejo de errores**: Detección y corrección automática
- **Trazabilidad**: Logs detallados de procesamiento
- **Escalabilidad**: Procesamiento por lotes eficiente

## Mantenimiento

- Verificación semanal de logs de ejecución
- Actualización de credenciales según políticas
- Monitoreo de cambios en interfaces web
- Backup de plantillas y configuraciones

## Instalación y Configuración

1. Configurar credenciales de Dynamics 365 y SUNAT
2. Establecer plantilla Excel con fórmulas
3. Programar ejecución semanal automática
4. Configurar notificaciones por email
5. Realizar pruebas de conectividad

## Estado del Proyecto

- **Versión**: 3.0
- **Estado**: En producción
- **Última actualización**: 30/07/2025
- **Desarrollo**: Power Automate Desktop
