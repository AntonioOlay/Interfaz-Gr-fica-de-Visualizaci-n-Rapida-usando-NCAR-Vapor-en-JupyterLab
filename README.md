<h1 align="center"> Interfaz Gráfica de Visualización Rapida usando NCAR Vapor en un entorno Conda dentro de JupyterLab </h1>

![PortadaGitHub](https://github.com/AntonioOlay/Interfaz-Gr-fica-de-Visualizaci-n-Rapida-usando-NCAR-Vapor-en-JupyterLab/assets/138058637/516e59ad-6704-4a67-8f8a-b647aec67bbe)


![Badge en Desarollo](https://img.shields.io/badge/Estado-EN%20DESARROLLO-green) 
![Badge](https://img.shields.io/badge/JupyterLab-3.6.2-orange)
![Badge](https://img.shields.io/badge/NCAR%20Vapor-3.8.2-light_green?labelColor=violet&color=blue)
![Badge](https://img.shields.io/badge/ipywidgets-4.0.1-orange?logoColor=orange&labelColor=orange&color=orange)
![Badge](https://img.shields.io/badge/mambaforge-22.11.1-bluish_green)

## Descripción del Proyecto
Notebook de JupyterLab desarrollado en lenguaje Python que por medio de Widgets, genera una interfaz gráfica que permite una interacción más intuitiva y amigable entre NCAR Vapor API y los usuarios. Sí requiere de una personalización más profunda deberá remitirse a la documentación de Vapor (https://ncar.github.io/VaporDocumentationWebsite/pythonAPIReference/classReference.html) con la cual podrá generar un renderizado más especifico y adecuado de acuerdo con sus requerimentos.

## Demostración de funciones y aplicaciones
*Función 1: La pantalla principal muestra un botón llamado "ACTUALIZAR" que permite aplicar los cambios realizados en el menú, se muestra el menú de cambios realizado con ipywidgets, se muestra la escena principal con 2 cuadros de anotaciones correspondientes a los renderizados "IsoSurface", dentro de la escena se especifica el "TIMESTEP" actual y los valores mínimo y máximo de las variables indicadas por el usuario para los "IsoSurface".

![Funcion1](https://github.com/AntonioOlay/Interfaz-Gr-fica-de-Visualizaci-n-Rapida-usando-NCAR-Vapor-en-JupyterLab/assets/138058637/c71dfbe0-ebb7-4e59-9023-c92b883e0886)

*Función 2: El NoteBook realiza una busqueda e incorporación de archivos ".nc", ".tms" y ".tiff", dentro del directorio en el que se encuentra alojado. La pestaña "ARCHIVOS" permite al usuario seleccionar uno de estos archivos para trabajar. Tambien se puede indicar un "TIMESTEP" especifico, y las 2 variables de tipo 3D para generar los 2 "IsoSurface".

![Funcion1](https://github.com/AntonioOlay/Interfaz-Gr-fica-de-Visualizaci-n-Rapida-usando-NCAR-Vapor-en-JupyterLab/assets/138058637/01d6d04c-8765-48c9-8739-6cd892aad295)


*Función 3: La pestaña "RENDERIZADOS" permite mostrar u ocultar cada uno de los 5 renderizados, los cuales se detallan a continuación.

-- Renderizado 1: "ImageRenderer" muestra un mapa geogrfico y georeferenciado correspondiente a las coordenadas del archivo netCDF seleccionado. El relieve es incorporado con una variable de altura llamada "HGT". La skin del mapa puede cambiarse seleccionando un archivo ".tiff" o ".tms" desde la pestaña "ARCHIVOS".

-- Renderizado 2: "IsoSurface" número 1. Incorpora a la escena una variable 3D cuyos datos se muestran en el cuadro de anotaciones SUPERIOR.  

-- Renderizado 3: "IsoSurface" número 2. Incorpora a la escena una variable 3D cuyos datos se muestran en el cuadro de anotaciones INFERIOR.  

-- Renderizado 4: "Barbs" representa el flujo de viento usando flechas cuyas coordenadas son especificadas por las variables "U10" y "V10" en un plano dado por "X" y "Y", respectivamente, la altura al igual que con "ImageRenderer" es dada por "HGT", respetando así el relieve del mapa, y el color se muestra de acuerdo con la variable de temperatura "T2".

-- Renderizado 5: "Flow" muestra Líneas de Corriente en el espacio 3D usando "U", "V" y "W" para sus coordenadas, y una variable de color "T". 

*Función 4: La pestaña "COLOR" permite elegir y cambiar la paleta de colores de cada uno de los 4 renderizados, exceptuando "ImageRenderer". Tambien se puede cambiar el color del fondo de la escena entre BLANCO y NEGRO. 
De acuerdo con las variable seleccionadas para los "IsoSurface" se puede situar la capa de cada uno de estos, en un dato especifico de las variables seleccionadas.



*Función 5: La pestaña "OPACIDAD" cuenta con 4 widgets para controlar el nivel de los puntos de opacidad de ambos "IsoSurface" (8 widgets en total), estos puntos estan distribuidos uniformemente a lo largo de los datos de las variables seleccionadas. Cuando acercamos el nivel de opacidad de un punto al valor 1, el renderizado en esa parte de los datos se hará más visible, contrario a acercar el nivel al valor 0, donde se hará menos visible. 



*Función 6: La pestaña "TRANSFORMACIÓN" permite ajustar la escala de la altura de todos los renderizados. Donde una escala cercana a cero no afecta la altura original, pero si se ingresa un numero cualquiera, la altura será multiplicada por la escala, pudiendo mostrar un relieve más agresivo. 
El Zoom de la camará controla el acercamiento con respecto al renderizado, puede aumentarse (número positivo) o disminuirse (número negativo). 
Existen 3 angulos de la camara que nos ayuda a observar de forma rapida el renderizado desde 3 puntos distintos, desde arriba, inclinado o muy inclinado (Aún en desarrollo, debido a que, los distintos archivos .nc y la longitud de sus coordenadas no permiten un control estandarizado de la cámara, forzando a utilizar coordenadas especificas para la camara por cada archivo con coordenadas distintas, como ejemplo, tenemos 2 archivos, uno perteneciente a la CDMX y el otro a la Republica Mexicana, las coordendas de la cámara diseñadas para el archivo de la CDMX no funcionan adecuadamente para el archivo de la Republica Mexicana, por lo que, en este ultimo no se incorpora la camara correctamente para mostrar los angulos deseados)



*Función 7: Pestaña "ANIMACION" ayuda a generar archivos multimedia de la escena actual. Pueden ser imagenes ".png" o videos ".MP4" ambos con la escena fija, que en el caso de las imagenes, se genera una por cada "TIMESTEP" y en el caso del video, se genera uno con duración de 30 segundos. Tambien hay una opción para ambos formatos donde la camara rota centrando siempre al renderizado. 
Para usar esta pestaña primero se debe seleccionar el "Formato del archivo multimedia", dar click en el botón "ACTUALIZAR", el widget a la derecha actualizará sus opciones y ahí deberemos seleccionar el tipo de escena (rotando o estatica), y actualizar una ultima vez, generando el archivo de video o una sucesión de imagenes. 



# EJEMPLO DE ANIMACIÓN ESTATICA EN FORMATO DE VIDEO MP4
https://github.com/AntonioOlay/Interfaz-Gr-fica-de-Visualizaci-n-Rapida-usando-NCAR-Vapor-en-JupyterLab/assets/138058637/b5b687ee-ecc4-4a03-85d8-17bf22227a5b




## Acceso al Proyecto 
Se requiere de un entorno Conda donde ya se haya instalado previamente NCAR Vapor (http://www.vapor.ucar.edu/pages/vaporPythonDownloads.html), así como todos los paquetes necesarios (adjunto un PDF indicando los pasos a seguir para crear este entorno desde la INSTALACIÓN DE MAMBAFORGE).

Para usar este NoteBook es necesario descargarlo de este repositorio y guardarlo en un directorio de JupyterLab donde esten almacenados los archivo netCDF y ".tms" o ".tiff". Una vez guardado, abrimos este archivo ".ipynb", seleccionamos el Kernel correspondiente al entorno con NCAR Vapor, lo ejecutamos y automaticamente se mostrará la PANTALLA PRINCIPAL.

## Tecnologías utilizadas
°Mambaforge
°Python 
°JupyterLab
°IpyWidgets
°NCAR Vapor
°netCDF


## Personas Contribuyentes
Lic. en Informatica Pedro Cruz

Doc. Augustín Garcia

## Personas Desarrolladoras del Proyecto
Miguel Olaya
![octocat-1692736817031](https://github.com/AntonioOlay/Interfaz-Gr-fica-de-Visualizaci-n-Rapida-usando-NCAR-Vapor-en-JupyterLab/assets/138058637/4cac354d-dabc-465a-8c1f-71efd650bf24)

