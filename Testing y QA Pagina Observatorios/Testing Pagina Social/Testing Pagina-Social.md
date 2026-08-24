 # Reporte de Incidencias – Observatorio Social


**Fecha:** 24 de agosto de 2026  
**Estado:** Pendiente de revisión  
**Prioridad:** Alta  
**Responsable:** David Fernando Monroy Buitrago


## 1. Error de contraste y superposición en el slider

**Inconveniente**  
Se presenta un fallo de maquetación y contraste visual en los controles y etiquetas del banner principal (slider).

**Detalle del Problema**  
- **Superposición y Legibilidad:** Las flechas de navegación del slider quedan superpuestas sobre el círculo azul de la izquierda y el texto de la derecha sin el contraste suficiente. La etiqueta inferior (<span style="color:#b22222;">"Observatori Social"</span>) tapona parcialmente la información de las líneas temáticas e incluye un carácter/icono cortado en la palabra.  
- **Comprobación:** Aunque no afecta la funcionalidad del carrusel, compromete la estética, dificulta la lectura de los datos presentados y restringe la visibilidad del contenido inferior.

**Acción Necesaria**  
Ajustar la posición (`position`, `bottom`) y el tamaño del botón/etiqueta flotante en la maquetación CSS, corregir la errata en el texto (<span style="color:#2e8b57;">"Observatorio Social"</span>) y modificar el color o fondo de las flechas de navegación para asegurar el contraste.

![](../../assets/Pasted%20image%2020260824083152.png)


## 2. Inconsistencia en la cantidad total de indicadores – Dimensión Social

**Inconveniente**  
Existe una discrepancia en el número total de indicadores reportados en la interfaz, lo que genera confusión e incertidumbre en la experiencia de usuario.

**Detalle del Problema**  
- **Incoherencia en los Datos:** El texto o encabezado de la sección indica la presencia de <span style="color:#b22222;">69 indicadores</span>; sin embargo, al validar el listado y conteo real en el detalle inferior, existen <span style="color:#2e8b57;">317 indicadores</span>.  
- **Comprobación:** La diferencia de 248 registros crea una falsa expectativa de contenido y afecta la precisión de la información presentada al usuario que consulta el observatorio.

**Acción Necesaria**  
Actualizar el valor estático o ajustar la consulta dinámica del contador principal para que refleje exactamente la cantidad real de indicadores disponibles (<span style="color:#2e8b57;">317</span>).

## 3. Error en los enlaces a archivos de información

**Inconveniente**

En el apartado de **Hoja de Vida de la Dimensión Social**, algunos enlaces de las fuentes de información presentan errores al intentar acceder a ellos.

**Detalle del Problema**

- **Enlace inaccesible:** Al hacer clic en el enlace o abrirlo en una nueva ventana, se muestra un error **404 Not Found**, indicando que el recurso no fue encontrado.
- **Posible causa:** El archivo puede no encontrarse disponible en el hosting o la ruta del enlace puede estar desactualizada.

**Acción Necesaria**

Verificar la existencia del archivo en el hosting y, de ser necesario, actualizar o corregir la ruta del enlace para garantizar su correcto acceso.
*(Por lo general las hojas de vida que cuentan con este error son los que cuentan con toda su información disponible)*

![](../../assets/Pasted%20image%2020260824085019.png)


## 4. Error de Renderizado en los Gráficos de Algunos Indicadores

**Inconveniente**  
Los cuadros de las gráficas aparecen en la página pero se quedan totalmente en blanco, por lo que no es posible visualizar la información del indicador.

**Detalle del Problema**  
- **Carga Correcta de Datos:** La información del archivo subido (Excel/CSV) sí llega completa al sistema y cuenta con más de dos registros cargados correctamente en cada caso.
- **Comportamiento Inconsistente:** Se identificó que mientras algunos indicadores sí logran desplegar mensajes de error o advertencias en pantalla, este grupo en específico no muestra ningún aviso al usuario.
- **Componentes de Pantalla Desalineados:** El sistema intentaba dibujar las gráficas usando comandos antiguos que ya no existen o que están incompletos en el código del sistema.
- **Bloqueo Silencioso:** Al no encontrar la instrucción exacta para dibujar cada cuadro, el proceso se detiene a mitad de camino y deja los contenedores completamente vacíos.

**Indicadores Afectados**  
![](../../assets/Pasted%20image%2020260824090818.png)
*(Nota: Todos los indicadores listados poseen más de 2 datos cargados en el sistema).*

**Acción Necesaria**  
Verificar y estandarizar la generación de las gráficas utilizando las mismas funciones y el mismo constructor implementado en los apartados donde funcionan correctamente, con el fin de mantener un comportamiento uniforme y evitar inconsistencias.
