
# Observación: Error en la visualización del gráfico

## Inconveniente

Se presenta un error en la visualización del gráfico, impidiendo que los datos sean representados correctamente.

## Detalle del Problema

- **Visualización:** El gráfico no presenta los datos esperados y los elementos gráficos no se renderizan correctamente.
- **Error identificado:** Al revisar la consola del navegador se evidencia el siguiente error de JavaScript:

  `jsapi_compiled_ui_module.js:214 Error: <path> attribute d: Expected number, "MNaN,NaNLNaN,NaNL…"`

- **Comportamiento:** El error evidencia que el componente gráfico está recibiendo o generando valores no numéricos (`NaN`) al momento de construir los elementos SVG, afectando directamente la representación de los datos.

## Acción Necesaria

Revisar el procesamiento de los datos y la lógica JavaScript asociada al gráfico para identificar el origen de los valores `NaN` y corregirlos, garantizando que los valores utilizados para generar los elementos gráficos sean numéricos y que el gráfico pueda visualizar correctamente la información.

![](assets/Pasted%20image%2020260910144924.png)


![](assets/Pasted%20image%2020260910144942.png)


![](assets/Pasted%20image%2020260910145218.png)

![](assets/Pasted%20image%2020260910145349.png)

![](assets/Pasted%20image%2020260910145430.png)


![](assets/Pasted%20image%2020260910145517.png)