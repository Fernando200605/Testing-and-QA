## 1. Inconsistencia en la Codificación de Caracteres en Archivos Descargables (.CSV)

**Inconveniente**  
Al descargar y abrir los archivos en formato `.csv` desde el Observatorio Económico, se presentan problemas de lectura en los textos que contienen caracteres especiales.

**Detalle del Problema**  
- **Error de Codificación (Encoding):** Los caracteres propios del idioma español (como la letra **ñ**, vocales con tilde **á, é, í, ó, ú**, o símbolos especiales) no se visualizan correctamente, mostrándose reemplazados por símbolos extraños o signos de interrogación (ej. *BoyacÃ¡*, *AÃ±o*, *NÂ°*).
- **Causa Técnica:** El archivo se genera o exporta desde el servidor sin una codificación estándar en **UTF-8 con BOM (Byte Order Mark)**, lo que provoca que programas como Microsoft Excel interpreten el archivo usando codificaciones por defecto (ANSI/Windows-1252), corruptiendo la lectura del texto.

**Archivos Afectados**  
- Reportes y datasets descargables en formato `.csv` a lo largo del módulo del Observatorio Económico.

**Acción Necesaria**  
Ajustar la exportación de archivos `.csv` en el backend (PHP) para forzar la cabecera e inclusión del BOM UTF-8 (`\xEF\xBB\xBF`), garantizando que cualquier hoja de cálculo o editor de texto interprete correctamente las tildes y la letra **ñ**.

```text
[ Servidor genera reporte .CSV ]
               │
               ▼ (Falta codificación UTF-8 con BOM)
 [ Usuario descarga el archivo ]
               │
               ▼
 [ Apertura en Excel / Software ]
               │
               ├──► "Año"  ──────►  AÃ±o
               └──► "Boyacá" ────►  BoyacÃ¡
               │
               ▼
 [ Resultado ]: Caracteres especiales corruptos o ilegibles
 ```