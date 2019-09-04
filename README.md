
<!-- Este .md fue generado a partir del .Rmd homónimo. Edítese el .Rmd -->
Mi primer RMarkdown
===================

Primero lo primero: acepta la invitación, genera tu repo en GitHub y clónalo localmente en RStudio. Tienes como referencia la guía [¿Cómo realizar una asignación?](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/como-hacer-una-asignacion.md)

Estudia la [Guía mínima de RMarkdown](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/guia-minima-de-rmarkdown.md). Puedes estudiarla mientras vas haciendo esta asignación.

Tarea 0. Toma nota de tu número asignado
----------------------------------------

Si estás leyendo este documento en GitHub, podrás ver esta lista renderizada en HTML. Si estás leyendo el archivo `.Rmd` estarás viendo líneas de código de R; ejecútalas en la consola de R. Esta lista contiene números aleatorios para cada persona. Utiliza dicho número cuando se te solicite:

``` r
estfuente <- paste0(
  'https://raw.githubusercontent.com/biogeografia-201902/',
  'miembros-y-colaboradores/master/suscripciones_github.txt'
)
estudiantes <- readLines(estfuente)
rver <- as.numeric(paste(version$major, gsub('\\.','', version$minor), sep = '.'))
if(rver>=3.6){
  RNGkind(sample.kind = "Rounding") #Utiliza redondeo (compatibilidad entre versiones de R)
}
set.seed(10) #Fija una tabla de números aleatorios
df <- data.frame(
  nombre = gsub(' .*$', '', estudiantes),
  numero = sample(1:70, length(estudiantes))
) #Crea tabla df (estudiantes-números aleatorios)
df #Muestra la tabla df
##              nombre numero
## 1         AbigailCP     36
## 2  BidelkisCastillo     22
## 3       dahianagb07     30
## 4          emdilone     47
## 5        enrique193      6
## 6         Erasbel05     15
## 7            geofis     18
## 8   hoyodepelempito     64
## 9       jimenezsosa     39
## 10    Jorge-Mutonen     27
## 11     JuanJoseGH06     40
## 12        Mangoland     34
## 13        maritzafg      7
## 14   merali-rosario     59
## 15   ramosramos1886     21
## 16        sanchez26     24
## 17     victorcabsid      3
## 18        yanderlin     65
```

Tarea 1. Abre la matriz de comunidad `mite` y despliégala
---------------------------------------------------------

A partir de este punto necesitarás editar este archivo `.Rmd`, para colocar tus respuestas donde te indico. Si ya aceptaste la asignación, clona tu repo localmente usando la guía [¿Cómo realizar una asignación?](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/como-hacer-una-asignacion.md).

1.  Entra en la guía "Introducción a R y análisis exploratorio de datos (EDA)", pero **sólo** lee la parte [El conjunto de datos mite](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/introduccion-a-r.md#el-conjunto-de-datos-mite). `mite` es un conjunto de datos sobre ácaros oribátidos colectados y procesados por Borcard y colaboradores, a partir de 70 núcleos de suelo en una parcela de 2.5x10 m \[@borcard1992partialling, @borcard1994environmental\]. Tendrás una asignación para desarrollar íntegramente dicha guía, y aprender más sobre este conjunto de datos. Por lo pronto, añado que dicho conjunto pertenece al paquete `vegan`. Con lo que leíste en la sección indicada, carga la matriz de comunidad `mite` y haz que se despligue en tu `.Rmd`

2.  Carga la matriz de comunidad.

3.  Imprímela.

-   Tus respuestas en este bloque de código:

``` r
library() #Escribe el nombre del paquete al cual pertenece el conjunto de datos
data() #Rellena el nombre del conjunto de datos
 #Aquí escribe el nombre del objeto
```

Nota: Tal como explica la [Guía mínima de RMarkdown](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/guia-minima-de-rmarkdown.md), prueba tu código en la medida que lo escribes (línea a línea es mejor). No olvides configurar la ejecución de código en la consola de R, marcando la opción `Chunk Output in Console` de la rueda dentada (barra de herramientas de archivo `.Rmd`). Así, cuando presiones *Run* (o las alternativas de teclado) tu código se ejecutará en la consola de R y allí mismo verás los resultados.

Si lograste imprimir en pantalla un `data.frame` con varias columnas y filas, conseguiste cargar correctamente la matriz de comunidad `mite`.

Tarea 2. Teje tu `.Rmd`.
------------------------

Teje para que generes tu `.md` usando la [sección "Teje" de la Guía mínima de RMarkdown](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/guia-minima-de-rmarkdown.md#teje). Podrás ver una previsualización de tu resultado desde RStudio.

Tarea 3. Filtra la matriz `mite`
--------------------------------

1.  Estudia la sección [Una pequeña parada para explicar cómo filtrar](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/introduccion-a-r.md#una-pequeña-parada-para-explicar-cómo-filtrar), y filtra la matriz mostrando sólo la fila que corresponde a tu número.

-   Tu respuesta en este bloque de código:

``` r
mite[,] #Debes colocar tu número dentro del corchete. Lee la guía
```

1.  Usando la misma guía, ¿cuántos individuos hay de la especie de la columna número 2 en la fila (sitio) que corresponde con tú número?

-   Tus respuestas en este bloque de código:

``` r
mite[,] #Debes colocar tu número y el de la columna dentro del corchete. Lee la guía
```

Tarea final: *commit*&gt;*push*
-------------------------------

Usa la guía [¿Cómo realizar una asignación?](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/como-hacer-una-asignacion.md) para sincronizar con tu repo remoto.
