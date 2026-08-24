 # Reporte de Incidencias – Observatorio Económico

**Fecha:** 21 de agosto de 2026  
**Estado:** Pendiente de revisión  
**Prioridad:** Alta  
**Responsable:** David Fernando Monroy Buitrago

---

## 1. Error de contraste y superposición en el slider

**Inconveniente**  
Se presenta un fallo de maquetación y contraste visual en los controles y etiquetas del banner principal (slider).

**Detalle del Problema**  
- **Superposición y Legibilidad:** Las flechas de navegación del slider quedan superpuestas sobre el círculo azul de la izquierda y el texto de la derecha sin el contraste suficiente. La etiqueta inferior (<span style="color:#b22222;">"Observatori Económico"</span>) tapona parcialmente la información de las líneas temáticas e incluye un carácter/icono cortado en la palabra.  
- **Comprobación:** Aunque no afecta la funcionalidad del carrusel, compromete la estética, dificulta la lectura de los datos presentados y restringe la visibilidad del contenido inferior.

**Acción Necesaria**  
Ajustar la posición (`position`, `bottom`) y el tamaño del botón/etiqueta flotante en la maquetación CSS, corregir la errata en el texto (<span style="color:#2e8b57;">"Observatorio Económico"</span>) y modificar el color o fondo de las flechas de navegación para asegurar el contraste.
![](../../assets/Pasted%20image%2020260821085143.png)

## 2. Inconsistencia en la cantidad total de indicadores – Dimensión Económica

**Inconveniente**  
Existe una discrepancia en el número total de indicadores reportados en la interfaz, lo que genera confusión e incertidumbre en la experiencia de usuario.

**Detalle del Problema**  
- **Incoherencia en los Datos:** El texto o encabezado de la sección indica la presencia de <span style="color:#b22222;">127 indicadores</span>; sin embargo, al validar el listado y conteo real en el detalle inferior, únicamente existen <span style="color:#2e8b57;">88 indicadores</span>.  
- **Comprobación:** La diferencia de 39 registros crea una falsa expectativa de contenido y afecta la precisión de la información presentada al usuario que consulta el observatorio.

**Acción Necesaria**  
Actualizar el valor estático o ajustar la consulta dinámica del contador principal para que refleje exactamente la cantidad real de indicadores disponibles (<span style="color:#2e8b57;">88</span>).

---

## 3. Superposición visual del menú de navegación – Dimensión Económica

**Inconveniente**  
Existe un problema de maquetación y estilos CSS en el menú de pestañas (*Tablero, Hoja de Vida, Categorías, DATALAKE*), el cual se solapa físicamente con los contenedores adyacentes.

**Detalle del Problema**  
- **Superposición de Capas:** El menú flotante/transitorio choca con la tarjeta superior (el banner de encabezado) y con las tarjetas del contenedor inferior, rompiendo la separación visual e interrumpiendo el diseño de la interfaz.  
- **Comprobación:** Aunque el fallo no interrumpe la navegabilidad ni la funcionalidad del sistema, compromete la estética del sitio web y afecta la legibilidad general de los componentes.

**Acción Necesaria**  
Ajustar el margen (`margin`), el relleno (`padding`) o la propiedad `z-index` en la hoja de estilos CSS para garantizar un espaciado adecuado entre el contenedor del menú y las secciones adyacentes.

![](../../assets/Pasted%20image%2020260821090108.png)

---

## 4. Redeclaración de variable `const` – Módulo Hoja de Vida

**Inconveniente**  
No es posible consultar la ficha técnica básica de un indicador en la opción *Hoja de vida* debido a una excepción en el código JavaScript.

**Detalle del Problema**  
- **Redeclaración de Variable (`const`):** Existe un error de sintaxis en el archivo JavaScript al intentar redeclarar una variable con la instrucción `const` dentro del mismo bloque de código.  
- **Comprobación:** Al ser `const` una variable inmutable en su referencia dentro del mismo ámbito, el motor de JS detiene la ejecución arrojando un `Uncaught SyntaxError`, lo que bloquea la interfaz e impide cargar la ficha técnica al seleccionar el indicador.

**Acción Necesaria**  
Modificar la declaración en el archivo JavaScript cambiando `const` por `let` (si se requiere reasignar su valor), renombrar la variable duplicada o ajustar su ámbito (*scope*).

![](../../assets/Pasted%20image%2020260821091805.png)

---

## 5. Inconsistencia en el Mapeo de Códigos – Módulo Hoja de Vida

**Inconveniente**  
No es posible consultar la ficha técnica de un indicador debido a un error en la distribución y asignación de los códigos según la dimensión seleccionada.

**Detalle del Problema**  
- **Inconsistencia en Mapeo de Datos:** Los códigos de los indicadores están desalineados respecto a su dimensión correspondiente. Al realizar la consulta con esta parametrización incorrecta, la búsqueda no devuelve la información esperada.  
- **Comprobación:** Se verificó que al ajustar o cambiar manualmente el código para que coincida con la dimensión correcta, la ficha técnica se despliega de manera adecuada.

**Acción Necesaria**  
Revisar y reestructurar la matriz, diccionario o tabla de equivalencias que relaciona cada código de indicador con su respectiva dimensión.

![](../../assets/Pasted%20image%2020260821093017.png)

## 6. Error de Renderizado en los Gráficos de Algunos Indicadores

**Inconveniente**  
Los cuadros de las gráficas aparecen en la página pero se quedan totalmente en blanco, por lo que no es posible visualizar la información del indicador.

**Detalle del Problema**  
- **Carga Correcta de Datos:** La información del archivo subido (Excel/CSV) sí llega completa al sistema y cuenta con más de dos registros cargados correctamente en cada caso.
- **Comportamiento Inconsistente:** Se identificó que mientras algunos indicadores sí logran desplegar mensajes de error o advertencias en pantalla, este grupo en específico no muestra ningún aviso al usuario.
- **Componentes de Pantalla Desalineados:** El sistema intentaba dibujar las gráficas usando comandos antiguos que ya no existen o que están incompletos en el código del sistema.
- **Bloqueo Silencioso:** Al no encontrar la instrucción exacta para dibujar cada cuadro, el proceso se detiene a mitad de camino y deja los contenedores completamente vacíos.

**Indicadores Afectados**  
- 1001  
- 1002  
- 1003  
- 1004  
- 1014  
- 1902  

*(Nota: Todos los indicadores listados poseen más de 2 datos cargados en el sistema).*

**Acción Necesaria**  
Reemplazar las instrucciones antiguas por un código de dibujo directo que tome la información cargada y genere las gráficas de manera inmediata.

```text
[ Datos del Excel / CSV ]
           │
           ▼ (Más de 2 datos cargados)
 [ Datos recibidos correctamente ]
           │
           ▼
 [ Instrucciones antiguas de dibujo ]
           │
           ├──► Faltan piezas en el código
           └──► Se interrumpe la lectura (sin mostrar error al usuario)
           │
           ▼
 [ Resultado ]: Cuadros visibles pero totalmente vacíos
```

![](../../assets/Pasted%20image%2020260821120427.png)
 
