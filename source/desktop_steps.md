# Edición en Oficina

<div class="warning">
<p class="admonition-title">WARNING</p>
<p>Los pasos descritos a continuación son una guía pero es necesario que el proceso sea realizado por una persona con conocimientos en sistemas de información geográfica en caso de requerirsen modificaciones a la información capturada en campo.</p>
</div>

<a class="" data-lightbox="Plugin" href="_static/plugin.gif" title="Plugin" data-title="Plugin"><img src="_static/plugin.gif" class="align-center" width="1024px" alt="Plugin">
</a>

1. Eliminar duplicados por Geometría y Attributos.

Funcionalidad del nucleo de QGIS que permite realizar la limpieza de los datos en primera instancia. 

2. Remover terrenos con área despreciable.

Una de las situaciones que se puede evidenciar en los datos capturados en campo, es que los terrenos estén conformados por múltiples partes, en los cuales se generan polígonos adicionales con áreas muy pequeñas. Este algoritmo requiere que el usuario defina: la capa de Terreno a analizar (aunque por defecto se referencia la capa CCA_Terreno) y el valor del área de validación (en metros cuadrados). Una vez se confirmen estos valores, el algoritmo retornará un listado de los polígonos que tienen un área igual o menor al umbral definido en la capa definida, permitiendo al usuario seleccionar que polígonos desea eliminar y cuales mantener en una nueva capa, la cual se denomina (Etapa 1) Terrenos ajustados.

3. Calcular coordenadas automáticamente.

Este algoritmo considera los siguientes parámetros: capa de puntos (CCA_Punto), capa de terrenos (por defecto se considera la capa generada en la etapa anterior del complemento -Terrenos ajustados-), tabla de predios (CCA_Predio), tabla de relación puntos con predios (por defecto, CCA_Predio_Punto), la distancia del área de influencia (tamaño de la zona de influencia) y el número de segmentos del área de influencia (un número mayor da como resultado una zona de influencia más suave con más nodos).

4. Ajustar polígonos a puntos.

El algoritmo recibe como entrada las capas de puntos y terrenos ajustados, así como un umbral de distancia (en metros). A continuación, establece una correspondencia entre vértices y puntos ajustados y actualiza las coordenadas de los vértices en consecuencia.

5. Validar áreas.

Este algoritmo ha sido desarrollado para realizar una comparación de áreas entre los polígonos correspondientes a los terrenos en su estado inicial (CCA_Terreno) y los obtenidos tras el proceso de ajuste (Etapa 3 del complemento). El objetivo principal es cuantificar la variación porcentual en el área de cada terreno, permitiendo así identificar de manera rápida y precisa aquellos casos en los que se ha producido un cambio significativo.

6. Construir linderos.

Este algoritmo tiene como objetivo generar la capa geográfica 'CCA_Lindero' y sus atributos, la cual representa las líneas divisorias entre los bienes inmuebles. Esta capa se construirá a partir de las geometrías de la capas: (Etapa 2) Puntos ajustados y (Etapa 3) Terrenos ajustados. 

7. Migrar información.

La última etapa del complemento consiste en generar una copia exacta del GeoPackage de origen para posteriormente realizar una serie de ajustes específicos. Este nuevo GeoPackage servirá como base para la migración final.

En primer lugar, se procede a eliminar las capas correspondientes a terrenos, puntos y linderos del nuevo GeoPackage. A continuación, se incorporan las versiones ajustadas de estas capas, que fueron generadas en etapas anteriores del proceso (Puntos ajustados, Terrenos ajustados y Linderos). Finalmente, se establecen las relaciones espaciales entre los elementos geográficos, creando vínculos entre los puntos y los linderos (relación cca_punto_lindero) y entre los puntos y los predios (relación cca_predio_punto).