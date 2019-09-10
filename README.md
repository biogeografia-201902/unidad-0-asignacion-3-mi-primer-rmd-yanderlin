
<!-- Este .md fue generado a partir del .Rmd homónimo. Edítese el .Rmd -->
Mi primer RMarkdown
===================

Primero lo primero: acepta la invitación, genera tu repo en GitHub y clónalo localmente en RStudio. Si no te acuerdas de cómo hacerlo, tienes como referencia la guía [¿Cómo realizar una asignación?](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/como-hacer-una-asignacion.md)

A continuación, estudia la [Guía mínima de RMarkdown](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/guia-minima-de-rmarkdown.md). Puedes darle un vistazo general primero, y luego utilizarla como referencia mientras vas haciendo esta asignación.

Tarea 0. Toma nota de tu número asignado
----------------------------------------

Al final del bloque de código de R a continuación, verás una lista de números aleatorios asignados a cada nombre de usuario. Localiza tu usuario y toma nota del número que te tocó, porque lo usarás para cumplir con las tareas que verás en este mismo documento, más abajo. No tienes que hacer nada en la consola de R, ni ejecutar el código, sólo toma nota del número asignado a tu usuario.

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
## Warning in RNGkind(sample.kind = "Rounding"): non-uniform 'Rounding'
## sampler used
set.seed(10) #Fija una tabla de números aleatorios
df <- data.frame(
  usuario = gsub(' .*$', '', estudiantes),
  numero_aleatorio = sample(1:70, length(estudiantes))
) #Crea tabla df (estudiantes-números aleatorios)
df #Muestra la tabla df
##             usuario numero_aleatorio
## 1         AbigailCP               36
## 2  BidelkisCastillo               22
## 3       dahianagb07               30
## 4          emdilone               47
## 5        enrique193                6
## 6         Erasbel05               15
## 7            geofis               18
## 8   hoyodepelempito               64
## 9       jimenezsosa               39
## 10    Jorge-Mutonen               27
## 11     JuanJoseGH06               40
## 12        Mangoland               34
## 13        maritzafg                7
## 14   merali-rosario               59
## 15   ramosramos1886               21
## 16        sanchez26               24
## 17     victorcabsid                3
## 18        yanderlin               65
```

Tarea 1. Abre el archivo `README.Rmd`
-------------------------------------

A partir de este punto, necesitarás editar el archivo `README.Rmd` (recalco, el que termina en `.Rmd`), porque tendrás que colocar tus respuestas en dicho archivo.

-   **Si ya aceptaste la asignación, clona tu repo localmente en RStudio usando la guía [¿Cómo realizar una asignación?](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/como-hacer-una-asignacion.md)**

-   **Abre el archivo `README.Rmd` y mantenlo abierto hasta finalizar la asignación**. Se te solicitará escribir y a ejecutar código de R en la consola. El código deberás escribirlo en este archivo.

> Deberás colocar tu código dentro de los bloques creados al efecto. Un bloque de código comienza por algo tal que esto ```` ```{r} ```` y termina con esto ```` ``` ````.

Tarea 2. Abre la matriz de comunidad `mite` y despliégala
---------------------------------------------------------

-   **Entra en la guía "Introducción a R y análisis exploratorio de datos (EDA)"**, y lee la parte [El conjunto de datos mite](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/introduccion-a-r.md#el-conjunto-de-datos-mite) (ya tendrás tiempo de leer la guía completa).

> `mite` es un conjunto de datos (disponible en el paquete `vegan`), que contiene información sobre ácaros oribátidos colectados y procesados por Borcard y colaboradores, a partir de 70 núcleos de esfagnos extraídos de una turbera de 2.5x10 m en el lago Geai, Canadá (Borcard & Legendre, 1994; Borcard, Legendre, & Drapeau, 1992).

-   **Carga el paquete `vegan`** (primera línea, `library()`).

-   **Carga la matriz de comunidad en la memoria** (segunda línea con `data()`).

-   **Imprime la matriz de comunidad**. Haz que se despliegue, ya sea en la consola de R o en tu `.Rmd` (tercera línea del bloque de código, donde escribirás el nombre del objeto antes del símbolo `#`).

> El símbolo `#` **dentro los bloques de código** precede comentarios. R ignora lo escrito a partir de `#`. Verás que usaré `#` para colocar pistas sobre lo solicitado.

**Tus respuestas en este bloque de código:**

``` r
library(vegan) #Escribe el nombre del paquete al cual pertenece el conjunto de datos entre los paréntesis
## Loading required package: permute
## Loading required package: lattice
## This is vegan 2.5-5
data(mite) #Rellena el nombre del conjunto de datos entre los paréntesis
mite#Por delante del símbolo de almohadilla, escribe el nombre del objeto
##    Brachy PHTH HPAV RARD SSTR Protopl MEGR MPRO TVIE HMIN HMIN2 NPRA TVEL
## 1      17    5    5    3    2       1    4    2    2    1     4    1   17
## 2       2    7   16    0    6       0    4    2    0    0     1    3   21
## 3       4    3    1    1    2       0    3    0    0    0     6    3   20
## 4      23    7   10    2    2       0    4    0    1    2    10    0   18
## 5       5    8   13    9    0      13    0    0    0    3    14    3   32
## 6      19    7    5    9    3       2    3    0    0   20    16    2   13
## 7      17    3    8    2    3       0    3    0    0   19     3    0   22
## 8       5    4    8    2    1       2    3    0    0    1     4   10   12
## 9       3    3    2    2    1       1   12    0    0    0     3    9   20
## 10     22    4    5    3    0       0    0    0    0   11     4    5   16
## 11     36    7   35    9    0       2    5    0    0    0     6    1   42
## 12     28    2   12   13    0       0    1    0    0   11     1    2   27
## 13      3    2    4   12    0       0    2    0    0    1     1    2   11
## 14     41    5   12    0    2       0    2    0    0   24    20    3   19
## 15      6    0    6    0    0       0    1    0    0    0     5    1   21
## 16      7    2    3    2    0       0    3    0    0    1     0    6   19
## 17      9    0    1    2    0       0    2    0    0    2     1    3   24
## 18     19    3    7    0    0       0    2    0    0   10     4    0    9
## 19     12    2   10    1    0       0    4    1    0   16     5    2    5
## 20      3    1    7    1    0       0   17    0    0   13     7    7   25
## 21      5    2    8    2    0       0    3    0    0   24     0    1   11
## 22      4    0    4    0    0       0    1    0    0   25     2    1   18
## 23     19    0    8    0    0       1    4    0    0    0     3    1    5
## 24      4    0    1    4    0       0    4    1    0    4     0    0   22
## 25     12    4   15    2    0       1    0    1    0    1     2    1   38
## 26      6    0    4    1    0       0    1    0    0    0     2    1   24
## 27      4    4    4    3    0       0    2    0    1   17     0    9   20
## 28      9    0    4    0    0       0    1    0    3    0     0    1   21
## 29     42    0    6    0    0       0    1    0    0    0     0    0   21
## 30     20    1    2    0    0       0    7    1    0    0     0    1    6
## 31     12    0    5    0    0       0    0    0    1    1     0    0    9
## 32      4    0    9    0    0       0    5    0    0    5     9    2    2
## 33     38    0   17    0    0       0    2    0    0    1     0    0    8
## 34      5    0   14    0    0       0    1    0    1   11     4    2   22
## 35      3    0    0    0    0       1    1    2    0   26     0    0    2
## 36      3    1    2    0    0       1    3    0    0   20     0    0    3
## 37      3    0    5    0    0       0    2    0    0   36     0    0    0
## 38      8    0    6    0    0       0   15    0    4    0     0    0    0
## 39      0    0    0    0    0       0    0    0    0    0     0    1    5
## 40      1    0   31    0    0       0    0    0    0    3     0    1    0
## 41      2    0   10    0    0       0    0    0    0    0     0    0    0
## 42      0    0   12    0    0       0    0    0    0    0     0    1    0
## 43      5    0    2    0    0       0   16    0    0    0     0    0    0
## 44      0    0    2    0    0       0    5    0    0    0     0    0    0
## 45     11    0    8    0    0       0    0    0    1    1     0    4    1
## 46      4    0    4    0    0       0    2    0    1   12     0    2    0
## 47      0    0    8    0    0       1    0    0    0   18     0    1    0
## 48      0    0    3    0    0       0    0    0    0    1     0    0    0
## 49     10    0   14    0    0       0    2    0    0    1     0    7    0
## 50      4    0   37    0    0       0    0    0    2    0     0    1    0
## 51      2    0    5    0    0       0    0    0    3    0     0    2    0
## 52      3    0    4    0    0       0    0    0    2    0     0    0    0
## 53      3    0   17    0    0       0    0    0    2    0     0    1    0
## 54      2    0    7    0    0       0    0    0    0    0     0    1    0
## 55      1    0    3    0    0       0    0    0    0    0     0    5    0
## 56      1    0   16    0    0       0    0    0    3    0     0    2    0
## 57      0    0    0    0    0       0    0    0    0    0     0    0    0
## 58      0    0   12    0    0       0    0    1    0    2     0    0    0
## 59      1    0    0    0    0       0    0    0    2    0     0    0    0
## 60      1    0   16    0    0       0    0    0    7    0     0    0    0
## 61      6    0    9    0    0       0    0    0    0    0     0    0    0
## 62      3    0    5    0    0       0    0    0    1    0     0    0    0
## 63     19    0    3    0    0       0    0    0    2    0     0    2    0
## 64      3    0   16    0    0       0    0    0    3    0     0    3    0
## 65      4    0   10    0    0       0    0    0    4    0     0    2    0
## 66      8    0   18    0    0       0    0    0    4    0     0    6    0
## 67      4    0    3    0    0       0    0    0    0    0     0    0    0
## 68      6    0   22    0    0       0    0    0    3    0     0    4    0
## 69     20    2    4    0    0       0    0    0    0    0     0    3    3
## 70      5    0   11    0    0       0    0    0    5    0     0    0    0
##    ONOV SUCT LCIL Oribatl1 Ceratoz1 PWIL Galumna1 Stgncrs2 HRUF Trhypch1
## 1     4    9   50        3        1    1        8        0    0        0
## 2    27   12  138        6        0    1        3        9    1        1
## 3    17   10   89        3        0    2        1        8    0        3
## 4    47   17  108       10        1    0        1        2    1        2
## 5    43   27    5        1        0    5        2        1    0        1
## 6    38   39    3        5        0    1        1        8    0        4
## 7    27   37    0        4        0    0        1        3    0        0
## 8    25   26    0        6        0    3        1        3    2        0
## 9     8   19   30        7        0    0        2        1    0        0
## 10   33   29    0        8        2    1        5        2    0        0
## 11   17   15    0        2        5    6        3        4    1        1
## 12   34   59    0        3        5    1        4        1    0        0
## 13   57   63    0       10        2    1        3        1    0        0
## 14   61   20    0       17        0    5        7        2    2        1
## 15    7    7   29        8        0    1        0        0    1        0
## 16    8   30    1        3        5    0        2        0    0        0
## 17    9   31    0        0        0    1        1        0    0        0
## 18   32   16    3        1        0    1        1        2    0        0
## 19   14   18    7        3        0    2        2        0    0        0
## 20   51   12    0       14        0    7        4        2    0        0
## 21   20   31    0        1        1    0        2        0    0        2
## 22   69   38    0        0        1    1        4        0    0        0
## 23    3   20    8        0        2    0        0        0    0        0
## 24   13   19    0        3        1    0        0        1    0        0
## 25    5   32    1        0        0    2        0        0    0        0
## 26   27   35    8        1        1    3        1        0    0        0
## 27   66   18    0        3        1    3        2        0    0        1
## 28    9   30    1        2        3    0        0        0    0        1
## 29   12   24    0        0        0    2        0        0    0        0
## 30    6   10   18        1        2    2        1        0    0        1
## 31   11   20   50        1        0    0        0        0    0        1
## 32   17   18    4        0        2    0        0        0    0        0
## 33   15   10   12        0        2    2        0        1    0        0
## 34   39   56    4        2        0    0        5        0    0        2
## 35   29   21    3        0        2    1        0        0    0        0
## 36   12   23   29        1        4    2        0        0    0        0
## 37   22   24   12        0        1    0        0        0    0        0
## 38    9    2  110        0        1    8        0        0    1        4
## 39    8   12   40        0        0    1        0        0    0        3
## 40    6   10   65        0        0    1        0        0    0        0
## 41    5    2   44        0        0    1        0        0    0        0
## 42    5    7   73        0        1    0        0        0    0        0
## 43    7    4   89        0        5    0        0        0    0       14
## 44    0    0   24        0        0    0        0        0    0       28
## 45    6    6   52        0        1    0        0        0    0        2
## 46   22   28   42        0        4    0        0        0    0        0
## 47   20   24    7        0        1    0        0        0    0        0
## 48   10    1   53        0        0    0        0        0    3        4
## 49    7   17    5        0        0    0        0        0    0        0
## 50    8   11   57        0        3    0        0        0    0        0
## 51    3    8   31        0        4    0        0        0    0        0
## 52    5    3   46        0        1    0        0        0    0        4
## 53    5   10   44        0        2    0        0        0    0        2
## 54    0    1   21        0        1    0        0        0    0        0
## 55    3    5   18        0        0    0        0        0    0        0
## 56    0    5   54        0        1    0        0        0    0        3
## 57    0    0    2        0        2    0        0        0    0        1
## 58   12    9   20        0        1    0        0        0    0        0
## 59    0    1   54        0        0    0        0        0    0       29
## 60    4    9   55        0        2    1        0        0    2        0
## 61    1    1    6        0        2    0        0        0    0        0
## 62    0    1    0        0        1    0        0        0    0        0
## 63    8   13   14        2        2    2        0        0    0        1
## 64    4    4   20        0        1    0        0        0    0        4
## 65   12    8   16        0        0    0        0        0    0       23
## 66   12   25    4        1        1    0        0        0    0        3
## 67    0    0  723        0        0    0        0        0    0        7
## 68    7    9   32        0        3    1        0        0    0        1
## 69   73   14   11        0        4    3        0        0    2       22
## 70   13   12   23        0        2    1        0        0    0        7
##    PPEL NCOR SLAT FSET Lepidzts Eupelops Miniglmn LRUG PLAG2 Ceratoz3
## 1     0    0    0    0        0        0        0    0     0        0
## 2     1    2    2    2        1        0        0    0     0        0
## 3     0    2    0    8        0        0        0    0     0        0
## 4     1    3    2   12        0        0        0    0     0        0
## 5     0    0    0   12        2        0        0    0     0        0
## 6     0    1    0   10        0        0        0    0     0        0
## 7     0    0    0    9        0        1        0    0     0        0
## 8     0    0    0    6        1        0        1    0     0        0
## 9     0    0    0    0        0        0        0    0     0        0
## 10    0    0    3   10        0        1        2    0     0        0
## 11    1    0    3    7        3        3        0    1     1        0
## 12    1    0    0    5        0        3        0    0     0        0
## 13    0    0    0    1        0        0        0    0     1        0
## 14    2    0    8    8        1        2        5    0     0        0
## 15    2    0    1    0        1        1        1    1     0        0
## 16    0    0    0    1        2        2        0    0     0        0
## 17    0    0    0    3        0        1        0    0     0        0
## 18    0    0    2    2        0        1        3    0     0        0
## 19    0    0    2    1        0        1        0    8     0        2
## 20    3    0    4    3        0        1        2    0     0        0
## 21    0    0    0    3        0        0        0    0     0        0
## 22    0    0    0    3        0        0        0    1     0        0
## 23    0    1    0    0        0        0        1    3     0        0
## 24    0    0    0    3        0        0        0    0     0        0
## 25    0    0    0    1        0        1        0    1     0        1
## 26    0    0    0    2        0        0        0    0     1        0
## 27    0    1    0    7        0        4        1    1     0        1
## 28    0    4    0    0        0        1        0   11     2        6
## 29    0    0    0    0        0        1        0    2     0        0
## 30    0    1    1    1        0        1        0   12     0        0
## 31    0    1    0    0        0        0        0   12     2        3
## 32    0    0    0    2        0        1        0    7     2        0
## 33    0    1    0    0        0        1        0   23     0        1
## 34    0    1    0    2        1        0        0   11     1        1
## 35    0    1    0    1        0        4        0    4     3        1
## 36    0    1    0    3        0        0        0   20     4        0
## 37    0    2    0    1        0        2        1   21     3        2
## 38    0    2    0    0        0        0        0   18     0        0
## 39    0    0    0    0        0        3        0   18     0        2
## 40    0    2    0    0        0        0        0   26     0        6
## 41    0    1    0    0        0        1        0   13     0        1
## 42    0    6    0    0        0        1        0   31     0        3
## 43    0    1    0    0        0        0        0    3     0        0
## 44    0    0    0    0        0        0        0    1     0        0
## 45    0    6    0    0        0        1        0   52     2        1
## 46    0    3    0    1        0        2        0   19     3        0
## 47    0    1    0    0        0        1        0   34     2        1
## 48    0    1    0    0        0        0        0   29     1        6
## 49    0    3    0    0        0        0        0   25     5        7
## 50    0    0    0    0        0        2        0   14     0        9
## 51    0    1    0    0        0        0        0   26     1        3
## 52    0    3    0    0        0        0        0   31     9        1
## 53    0    6    0    0        0        0        0   25     9        9
## 54    0    0    0    0        0        0        0   15     0        0
## 55    0    0    0    0        0        0        0   15     0        2
## 56    0    0    0    0        0        0        0   17     0        1
## 57    0    0    0    0        0        1        0    2     0        0
## 58    0    1    0    0        0        0        0   57     0        2
## 59    0    0    0    0        0        0        0    2     0        0
## 60    0    0    0    0        0        0        0   28     0        0
## 61    0    0    0    0        0        0        0    9     0        3
## 62    0    0    0    0        0        0        0    2     0        0
## 63    0    2    0    0        0        0        0    5     0        1
## 64    0    1    0    0        0        0        0   16     0        2
## 65    1    1    0    0        0        0        0    4     0        2
## 66    0    3    0    0        0        0        0   21     0        1
## 67    0    0    0    0        0        0        0   11     0        0
## 68    0    3    0    0        0        0        0    0     0        3
## 69    0    7    0    0        0        0        0    6     3        0
## 70    0    3    0    0        0        0        0   16     1        7
##    Oppiminu Trimalc2
## 1         0        0
## 2         0        0
## 3         0        0
## 4         0        0
## 5         0        0
## 6         0        0
## 7         0        0
## 8         0        0
## 9         0        0
## 10        0        0
## 11        0        0
## 12        0        0
## 13        0        0
## 14        0        0
## 15        0        0
## 16        0        0
## 17        0        0
## 18        0        0
## 19        0        0
## 20        0        0
## 21        1        0
## 22        0        0
## 23        2        0
## 24        0        0
## 25        2        0
## 26        2        0
## 27        0        0
## 28        2        0
## 29        0        0
## 30        1        0
## 31        1        0
## 32        4        0
## 33        2        0
## 34        9        0
## 35        6        0
## 36        1        0
## 37        2        0
## 38        1        0
## 39        1        0
## 40        5        0
## 41        1        0
## 42        0        0
## 43        1        1
## 44        0        0
## 45        3        0
## 46        5        0
## 47        2        0
## 48        0        1
## 49        4        0
## 50        0        0
## 51        1        1
## 52        0        0
## 53        1        9
## 54        0        1
## 55        6        0
## 56        0        5
## 57        0        0
## 58        4        0
## 59        0        1
## 60        1        1
## 61        0        5
## 62        0        0
## 63        2        8
## 64        0       11
## 65        0       25
## 66        0        9
## 67        0       33
## 68        0       17
## 69        4        3
## 70        1       14
```

> Tal como explica la [Guía mínima de RMarkdown](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/guia-minima-de-rmarkdown.md), prueba tu código línea a línea. Configura la ejecución de código en la consola de R, marcando la opción `Chunk Output in Console` de la rueda dentada (barra de herramientas de archivo `.Rmd`). Así, cuando presiones *Run&gt;Run Selected Line(s)* (o `Ctrl+Enter`) para ejecutar la o las líneas seleccionadas. Tu código se ejecutará en la consola de R y en ésta verás los resultados.

Si lograste ver en pantalla un `data.frame` con varias columnas y filas, conseguiste cargar e "imprimir" correctamente la matriz de comunidad `mite`. .

Tarea 3. Filtra la matriz `mite`
--------------------------------

-   **Filtra la matriz mostrando sólo la fila que corresponde a tu número**.

> `mite` es un `data.frame` y, por lo tanto, como cualquier tabla, es susceptible de filtrado ("extraer" filas/columnas). A continuación te explico brevemente cómo funciona el filtrado de un `data.frame` en R. Denominemos `x` a un `data.frame`. Podemos filtrar a `x` mediante índices de extracción de filas `i` y columnas `j`, de la siguiente manera: `x[i,j]`. Como ves, el índice de filas corresponde a la primera parte dentro de los corchetes, y el índice de columnas a la segunda. Así, si necesitas la fila 1 de `x`, con todas sus columnas, escribes `x[1,]`; si sólo necesitas la fila 1 columna 1, ejecutas `x[1,1]`. Profundiza estudiando la sección [Una pequeña parada para explicar cómo filtrar](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/introduccion-a-r.md#una-pequeña-parada-para-explicar-cómo-filtrar).

**Tus respuestas en este bloque de código:**

``` r
mite[,] #Debes colocar tu número asignado dentro del corchete donde corresponda.
##    Brachy PHTH HPAV RARD SSTR Protopl MEGR MPRO TVIE HMIN HMIN2 NPRA TVEL
## 1      17    5    5    3    2       1    4    2    2    1     4    1   17
## 2       2    7   16    0    6       0    4    2    0    0     1    3   21
## 3       4    3    1    1    2       0    3    0    0    0     6    3   20
## 4      23    7   10    2    2       0    4    0    1    2    10    0   18
## 5       5    8   13    9    0      13    0    0    0    3    14    3   32
## 6      19    7    5    9    3       2    3    0    0   20    16    2   13
## 7      17    3    8    2    3       0    3    0    0   19     3    0   22
## 8       5    4    8    2    1       2    3    0    0    1     4   10   12
## 9       3    3    2    2    1       1   12    0    0    0     3    9   20
## 10     22    4    5    3    0       0    0    0    0   11     4    5   16
## 11     36    7   35    9    0       2    5    0    0    0     6    1   42
## 12     28    2   12   13    0       0    1    0    0   11     1    2   27
## 13      3    2    4   12    0       0    2    0    0    1     1    2   11
## 14     41    5   12    0    2       0    2    0    0   24    20    3   19
## 15      6    0    6    0    0       0    1    0    0    0     5    1   21
## 16      7    2    3    2    0       0    3    0    0    1     0    6   19
## 17      9    0    1    2    0       0    2    0    0    2     1    3   24
## 18     19    3    7    0    0       0    2    0    0   10     4    0    9
## 19     12    2   10    1    0       0    4    1    0   16     5    2    5
## 20      3    1    7    1    0       0   17    0    0   13     7    7   25
## 21      5    2    8    2    0       0    3    0    0   24     0    1   11
## 22      4    0    4    0    0       0    1    0    0   25     2    1   18
## 23     19    0    8    0    0       1    4    0    0    0     3    1    5
## 24      4    0    1    4    0       0    4    1    0    4     0    0   22
## 25     12    4   15    2    0       1    0    1    0    1     2    1   38
## 26      6    0    4    1    0       0    1    0    0    0     2    1   24
## 27      4    4    4    3    0       0    2    0    1   17     0    9   20
## 28      9    0    4    0    0       0    1    0    3    0     0    1   21
## 29     42    0    6    0    0       0    1    0    0    0     0    0   21
## 30     20    1    2    0    0       0    7    1    0    0     0    1    6
## 31     12    0    5    0    0       0    0    0    1    1     0    0    9
## 32      4    0    9    0    0       0    5    0    0    5     9    2    2
## 33     38    0   17    0    0       0    2    0    0    1     0    0    8
## 34      5    0   14    0    0       0    1    0    1   11     4    2   22
## 35      3    0    0    0    0       1    1    2    0   26     0    0    2
## 36      3    1    2    0    0       1    3    0    0   20     0    0    3
## 37      3    0    5    0    0       0    2    0    0   36     0    0    0
## 38      8    0    6    0    0       0   15    0    4    0     0    0    0
## 39      0    0    0    0    0       0    0    0    0    0     0    1    5
## 40      1    0   31    0    0       0    0    0    0    3     0    1    0
## 41      2    0   10    0    0       0    0    0    0    0     0    0    0
## 42      0    0   12    0    0       0    0    0    0    0     0    1    0
## 43      5    0    2    0    0       0   16    0    0    0     0    0    0
## 44      0    0    2    0    0       0    5    0    0    0     0    0    0
## 45     11    0    8    0    0       0    0    0    1    1     0    4    1
## 46      4    0    4    0    0       0    2    0    1   12     0    2    0
## 47      0    0    8    0    0       1    0    0    0   18     0    1    0
## 48      0    0    3    0    0       0    0    0    0    1     0    0    0
## 49     10    0   14    0    0       0    2    0    0    1     0    7    0
## 50      4    0   37    0    0       0    0    0    2    0     0    1    0
## 51      2    0    5    0    0       0    0    0    3    0     0    2    0
## 52      3    0    4    0    0       0    0    0    2    0     0    0    0
## 53      3    0   17    0    0       0    0    0    2    0     0    1    0
## 54      2    0    7    0    0       0    0    0    0    0     0    1    0
## 55      1    0    3    0    0       0    0    0    0    0     0    5    0
## 56      1    0   16    0    0       0    0    0    3    0     0    2    0
## 57      0    0    0    0    0       0    0    0    0    0     0    0    0
## 58      0    0   12    0    0       0    0    1    0    2     0    0    0
## 59      1    0    0    0    0       0    0    0    2    0     0    0    0
## 60      1    0   16    0    0       0    0    0    7    0     0    0    0
## 61      6    0    9    0    0       0    0    0    0    0     0    0    0
## 62      3    0    5    0    0       0    0    0    1    0     0    0    0
## 63     19    0    3    0    0       0    0    0    2    0     0    2    0
## 64      3    0   16    0    0       0    0    0    3    0     0    3    0
## 65      4    0   10    0    0       0    0    0    4    0     0    2    0
## 66      8    0   18    0    0       0    0    0    4    0     0    6    0
## 67      4    0    3    0    0       0    0    0    0    0     0    0    0
## 68      6    0   22    0    0       0    0    0    3    0     0    4    0
## 69     20    2    4    0    0       0    0    0    0    0     0    3    3
## 70      5    0   11    0    0       0    0    0    5    0     0    0    0
##    ONOV SUCT LCIL Oribatl1 Ceratoz1 PWIL Galumna1 Stgncrs2 HRUF Trhypch1
## 1     4    9   50        3        1    1        8        0    0        0
## 2    27   12  138        6        0    1        3        9    1        1
## 3    17   10   89        3        0    2        1        8    0        3
## 4    47   17  108       10        1    0        1        2    1        2
## 5    43   27    5        1        0    5        2        1    0        1
## 6    38   39    3        5        0    1        1        8    0        4
## 7    27   37    0        4        0    0        1        3    0        0
## 8    25   26    0        6        0    3        1        3    2        0
## 9     8   19   30        7        0    0        2        1    0        0
## 10   33   29    0        8        2    1        5        2    0        0
## 11   17   15    0        2        5    6        3        4    1        1
## 12   34   59    0        3        5    1        4        1    0        0
## 13   57   63    0       10        2    1        3        1    0        0
## 14   61   20    0       17        0    5        7        2    2        1
## 15    7    7   29        8        0    1        0        0    1        0
## 16    8   30    1        3        5    0        2        0    0        0
## 17    9   31    0        0        0    1        1        0    0        0
## 18   32   16    3        1        0    1        1        2    0        0
## 19   14   18    7        3        0    2        2        0    0        0
## 20   51   12    0       14        0    7        4        2    0        0
## 21   20   31    0        1        1    0        2        0    0        2
## 22   69   38    0        0        1    1        4        0    0        0
## 23    3   20    8        0        2    0        0        0    0        0
## 24   13   19    0        3        1    0        0        1    0        0
## 25    5   32    1        0        0    2        0        0    0        0
## 26   27   35    8        1        1    3        1        0    0        0
## 27   66   18    0        3        1    3        2        0    0        1
## 28    9   30    1        2        3    0        0        0    0        1
## 29   12   24    0        0        0    2        0        0    0        0
## 30    6   10   18        1        2    2        1        0    0        1
## 31   11   20   50        1        0    0        0        0    0        1
## 32   17   18    4        0        2    0        0        0    0        0
## 33   15   10   12        0        2    2        0        1    0        0
## 34   39   56    4        2        0    0        5        0    0        2
## 35   29   21    3        0        2    1        0        0    0        0
## 36   12   23   29        1        4    2        0        0    0        0
## 37   22   24   12        0        1    0        0        0    0        0
## 38    9    2  110        0        1    8        0        0    1        4
## 39    8   12   40        0        0    1        0        0    0        3
## 40    6   10   65        0        0    1        0        0    0        0
## 41    5    2   44        0        0    1        0        0    0        0
## 42    5    7   73        0        1    0        0        0    0        0
## 43    7    4   89        0        5    0        0        0    0       14
## 44    0    0   24        0        0    0        0        0    0       28
## 45    6    6   52        0        1    0        0        0    0        2
## 46   22   28   42        0        4    0        0        0    0        0
## 47   20   24    7        0        1    0        0        0    0        0
## 48   10    1   53        0        0    0        0        0    3        4
## 49    7   17    5        0        0    0        0        0    0        0
## 50    8   11   57        0        3    0        0        0    0        0
## 51    3    8   31        0        4    0        0        0    0        0
## 52    5    3   46        0        1    0        0        0    0        4
## 53    5   10   44        0        2    0        0        0    0        2
## 54    0    1   21        0        1    0        0        0    0        0
## 55    3    5   18        0        0    0        0        0    0        0
## 56    0    5   54        0        1    0        0        0    0        3
## 57    0    0    2        0        2    0        0        0    0        1
## 58   12    9   20        0        1    0        0        0    0        0
## 59    0    1   54        0        0    0        0        0    0       29
## 60    4    9   55        0        2    1        0        0    2        0
## 61    1    1    6        0        2    0        0        0    0        0
## 62    0    1    0        0        1    0        0        0    0        0
## 63    8   13   14        2        2    2        0        0    0        1
## 64    4    4   20        0        1    0        0        0    0        4
## 65   12    8   16        0        0    0        0        0    0       23
## 66   12   25    4        1        1    0        0        0    0        3
## 67    0    0  723        0        0    0        0        0    0        7
## 68    7    9   32        0        3    1        0        0    0        1
## 69   73   14   11        0        4    3        0        0    2       22
## 70   13   12   23        0        2    1        0        0    0        7
##    PPEL NCOR SLAT FSET Lepidzts Eupelops Miniglmn LRUG PLAG2 Ceratoz3
## 1     0    0    0    0        0        0        0    0     0        0
## 2     1    2    2    2        1        0        0    0     0        0
## 3     0    2    0    8        0        0        0    0     0        0
## 4     1    3    2   12        0        0        0    0     0        0
## 5     0    0    0   12        2        0        0    0     0        0
## 6     0    1    0   10        0        0        0    0     0        0
## 7     0    0    0    9        0        1        0    0     0        0
## 8     0    0    0    6        1        0        1    0     0        0
## 9     0    0    0    0        0        0        0    0     0        0
## 10    0    0    3   10        0        1        2    0     0        0
## 11    1    0    3    7        3        3        0    1     1        0
## 12    1    0    0    5        0        3        0    0     0        0
## 13    0    0    0    1        0        0        0    0     1        0
## 14    2    0    8    8        1        2        5    0     0        0
## 15    2    0    1    0        1        1        1    1     0        0
## 16    0    0    0    1        2        2        0    0     0        0
## 17    0    0    0    3        0        1        0    0     0        0
## 18    0    0    2    2        0        1        3    0     0        0
## 19    0    0    2    1        0        1        0    8     0        2
## 20    3    0    4    3        0        1        2    0     0        0
## 21    0    0    0    3        0        0        0    0     0        0
## 22    0    0    0    3        0        0        0    1     0        0
## 23    0    1    0    0        0        0        1    3     0        0
## 24    0    0    0    3        0        0        0    0     0        0
## 25    0    0    0    1        0        1        0    1     0        1
## 26    0    0    0    2        0        0        0    0     1        0
## 27    0    1    0    7        0        4        1    1     0        1
## 28    0    4    0    0        0        1        0   11     2        6
## 29    0    0    0    0        0        1        0    2     0        0
## 30    0    1    1    1        0        1        0   12     0        0
## 31    0    1    0    0        0        0        0   12     2        3
## 32    0    0    0    2        0        1        0    7     2        0
## 33    0    1    0    0        0        1        0   23     0        1
## 34    0    1    0    2        1        0        0   11     1        1
## 35    0    1    0    1        0        4        0    4     3        1
## 36    0    1    0    3        0        0        0   20     4        0
## 37    0    2    0    1        0        2        1   21     3        2
## 38    0    2    0    0        0        0        0   18     0        0
## 39    0    0    0    0        0        3        0   18     0        2
## 40    0    2    0    0        0        0        0   26     0        6
## 41    0    1    0    0        0        1        0   13     0        1
## 42    0    6    0    0        0        1        0   31     0        3
## 43    0    1    0    0        0        0        0    3     0        0
## 44    0    0    0    0        0        0        0    1     0        0
## 45    0    6    0    0        0        1        0   52     2        1
## 46    0    3    0    1        0        2        0   19     3        0
## 47    0    1    0    0        0        1        0   34     2        1
## 48    0    1    0    0        0        0        0   29     1        6
## 49    0    3    0    0        0        0        0   25     5        7
## 50    0    0    0    0        0        2        0   14     0        9
## 51    0    1    0    0        0        0        0   26     1        3
## 52    0    3    0    0        0        0        0   31     9        1
## 53    0    6    0    0        0        0        0   25     9        9
## 54    0    0    0    0        0        0        0   15     0        0
## 55    0    0    0    0        0        0        0   15     0        2
## 56    0    0    0    0        0        0        0   17     0        1
## 57    0    0    0    0        0        1        0    2     0        0
## 58    0    1    0    0        0        0        0   57     0        2
## 59    0    0    0    0        0        0        0    2     0        0
## 60    0    0    0    0        0        0        0   28     0        0
## 61    0    0    0    0        0        0        0    9     0        3
## 62    0    0    0    0        0        0        0    2     0        0
## 63    0    2    0    0        0        0        0    5     0        1
## 64    0    1    0    0        0        0        0   16     0        2
## 65    1    1    0    0        0        0        0    4     0        2
## 66    0    3    0    0        0        0        0   21     0        1
## 67    0    0    0    0        0        0        0   11     0        0
## 68    0    3    0    0        0        0        0    0     0        3
## 69    0    7    0    0        0        0        0    6     3        0
## 70    0    3    0    0        0        0        0   16     1        7
##    Oppiminu Trimalc2
## 1         0        0
## 2         0        0
## 3         0        0
## 4         0        0
## 5         0        0
## 6         0        0
## 7         0        0
## 8         0        0
## 9         0        0
## 10        0        0
## 11        0        0
## 12        0        0
## 13        0        0
## 14        0        0
## 15        0        0
## 16        0        0
## 17        0        0
## 18        0        0
## 19        0        0
## 20        0        0
## 21        1        0
## 22        0        0
## 23        2        0
## 24        0        0
## 25        2        0
## 26        2        0
## 27        0        0
## 28        2        0
## 29        0        0
## 30        1        0
## 31        1        0
## 32        4        0
## 33        2        0
## 34        9        0
## 35        6        0
## 36        1        0
## 37        2        0
## 38        1        0
## 39        1        0
## 40        5        0
## 41        1        0
## 42        0        0
## 43        1        1
## 44        0        0
## 45        3        0
## 46        5        0
## 47        2        0
## 48        0        1
## 49        4        0
## 50        0        0
## 51        1        1
## 52        0        0
## 53        1        9
## 54        0        1
## 55        6        0
## 56        0        5
## 57        0        0
## 58        4        0
## 59        0        1
## 60        1        1
## 61        0        5
## 62        0        0
## 63        2        8
## 64        0       11
## 65        0       25
## 66        0        9
## 67        0       33
## 68        0       17
## 69        4        3
## 70        1       14
```

-   **Usando la misma guía, ¿cuántos individuos hay de la especie de la columna número 2 en la fila (sitio) que corresponde con tú número?**

**Tus respuestas en este bloque de código:**

``` r
mite[,] #Debes colocar tu número en el índice de filas, y en el otro el de la columna. Lee la guía
##    Brachy PHTH HPAV RARD SSTR Protopl MEGR MPRO TVIE HMIN HMIN2 NPRA TVEL
## 1      17    5    5    3    2       1    4    2    2    1     4    1   17
## 2       2    7   16    0    6       0    4    2    0    0     1    3   21
## 3       4    3    1    1    2       0    3    0    0    0     6    3   20
## 4      23    7   10    2    2       0    4    0    1    2    10    0   18
## 5       5    8   13    9    0      13    0    0    0    3    14    3   32
## 6      19    7    5    9    3       2    3    0    0   20    16    2   13
## 7      17    3    8    2    3       0    3    0    0   19     3    0   22
## 8       5    4    8    2    1       2    3    0    0    1     4   10   12
## 9       3    3    2    2    1       1   12    0    0    0     3    9   20
## 10     22    4    5    3    0       0    0    0    0   11     4    5   16
## 11     36    7   35    9    0       2    5    0    0    0     6    1   42
## 12     28    2   12   13    0       0    1    0    0   11     1    2   27
## 13      3    2    4   12    0       0    2    0    0    1     1    2   11
## 14     41    5   12    0    2       0    2    0    0   24    20    3   19
## 15      6    0    6    0    0       0    1    0    0    0     5    1   21
## 16      7    2    3    2    0       0    3    0    0    1     0    6   19
## 17      9    0    1    2    0       0    2    0    0    2     1    3   24
## 18     19    3    7    0    0       0    2    0    0   10     4    0    9
## 19     12    2   10    1    0       0    4    1    0   16     5    2    5
## 20      3    1    7    1    0       0   17    0    0   13     7    7   25
## 21      5    2    8    2    0       0    3    0    0   24     0    1   11
## 22      4    0    4    0    0       0    1    0    0   25     2    1   18
## 23     19    0    8    0    0       1    4    0    0    0     3    1    5
## 24      4    0    1    4    0       0    4    1    0    4     0    0   22
## 25     12    4   15    2    0       1    0    1    0    1     2    1   38
## 26      6    0    4    1    0       0    1    0    0    0     2    1   24
## 27      4    4    4    3    0       0    2    0    1   17     0    9   20
## 28      9    0    4    0    0       0    1    0    3    0     0    1   21
## 29     42    0    6    0    0       0    1    0    0    0     0    0   21
## 30     20    1    2    0    0       0    7    1    0    0     0    1    6
## 31     12    0    5    0    0       0    0    0    1    1     0    0    9
## 32      4    0    9    0    0       0    5    0    0    5     9    2    2
## 33     38    0   17    0    0       0    2    0    0    1     0    0    8
## 34      5    0   14    0    0       0    1    0    1   11     4    2   22
## 35      3    0    0    0    0       1    1    2    0   26     0    0    2
## 36      3    1    2    0    0       1    3    0    0   20     0    0    3
## 37      3    0    5    0    0       0    2    0    0   36     0    0    0
## 38      8    0    6    0    0       0   15    0    4    0     0    0    0
## 39      0    0    0    0    0       0    0    0    0    0     0    1    5
## 40      1    0   31    0    0       0    0    0    0    3     0    1    0
## 41      2    0   10    0    0       0    0    0    0    0     0    0    0
## 42      0    0   12    0    0       0    0    0    0    0     0    1    0
## 43      5    0    2    0    0       0   16    0    0    0     0    0    0
## 44      0    0    2    0    0       0    5    0    0    0     0    0    0
## 45     11    0    8    0    0       0    0    0    1    1     0    4    1
## 46      4    0    4    0    0       0    2    0    1   12     0    2    0
## 47      0    0    8    0    0       1    0    0    0   18     0    1    0
## 48      0    0    3    0    0       0    0    0    0    1     0    0    0
## 49     10    0   14    0    0       0    2    0    0    1     0    7    0
## 50      4    0   37    0    0       0    0    0    2    0     0    1    0
## 51      2    0    5    0    0       0    0    0    3    0     0    2    0
## 52      3    0    4    0    0       0    0    0    2    0     0    0    0
## 53      3    0   17    0    0       0    0    0    2    0     0    1    0
## 54      2    0    7    0    0       0    0    0    0    0     0    1    0
## 55      1    0    3    0    0       0    0    0    0    0     0    5    0
## 56      1    0   16    0    0       0    0    0    3    0     0    2    0
## 57      0    0    0    0    0       0    0    0    0    0     0    0    0
## 58      0    0   12    0    0       0    0    1    0    2     0    0    0
## 59      1    0    0    0    0       0    0    0    2    0     0    0    0
## 60      1    0   16    0    0       0    0    0    7    0     0    0    0
## 61      6    0    9    0    0       0    0    0    0    0     0    0    0
## 62      3    0    5    0    0       0    0    0    1    0     0    0    0
## 63     19    0    3    0    0       0    0    0    2    0     0    2    0
## 64      3    0   16    0    0       0    0    0    3    0     0    3    0
## 65      4    0   10    0    0       0    0    0    4    0     0    2    0
## 66      8    0   18    0    0       0    0    0    4    0     0    6    0
## 67      4    0    3    0    0       0    0    0    0    0     0    0    0
## 68      6    0   22    0    0       0    0    0    3    0     0    4    0
## 69     20    2    4    0    0       0    0    0    0    0     0    3    3
## 70      5    0   11    0    0       0    0    0    5    0     0    0    0
##    ONOV SUCT LCIL Oribatl1 Ceratoz1 PWIL Galumna1 Stgncrs2 HRUF Trhypch1
## 1     4    9   50        3        1    1        8        0    0        0
## 2    27   12  138        6        0    1        3        9    1        1
## 3    17   10   89        3        0    2        1        8    0        3
## 4    47   17  108       10        1    0        1        2    1        2
## 5    43   27    5        1        0    5        2        1    0        1
## 6    38   39    3        5        0    1        1        8    0        4
## 7    27   37    0        4        0    0        1        3    0        0
## 8    25   26    0        6        0    3        1        3    2        0
## 9     8   19   30        7        0    0        2        1    0        0
## 10   33   29    0        8        2    1        5        2    0        0
## 11   17   15    0        2        5    6        3        4    1        1
## 12   34   59    0        3        5    1        4        1    0        0
## 13   57   63    0       10        2    1        3        1    0        0
## 14   61   20    0       17        0    5        7        2    2        1
## 15    7    7   29        8        0    1        0        0    1        0
## 16    8   30    1        3        5    0        2        0    0        0
## 17    9   31    0        0        0    1        1        0    0        0
## 18   32   16    3        1        0    1        1        2    0        0
## 19   14   18    7        3        0    2        2        0    0        0
## 20   51   12    0       14        0    7        4        2    0        0
## 21   20   31    0        1        1    0        2        0    0        2
## 22   69   38    0        0        1    1        4        0    0        0
## 23    3   20    8        0        2    0        0        0    0        0
## 24   13   19    0        3        1    0        0        1    0        0
## 25    5   32    1        0        0    2        0        0    0        0
## 26   27   35    8        1        1    3        1        0    0        0
## 27   66   18    0        3        1    3        2        0    0        1
## 28    9   30    1        2        3    0        0        0    0        1
## 29   12   24    0        0        0    2        0        0    0        0
## 30    6   10   18        1        2    2        1        0    0        1
## 31   11   20   50        1        0    0        0        0    0        1
## 32   17   18    4        0        2    0        0        0    0        0
## 33   15   10   12        0        2    2        0        1    0        0
## 34   39   56    4        2        0    0        5        0    0        2
## 35   29   21    3        0        2    1        0        0    0        0
## 36   12   23   29        1        4    2        0        0    0        0
## 37   22   24   12        0        1    0        0        0    0        0
## 38    9    2  110        0        1    8        0        0    1        4
## 39    8   12   40        0        0    1        0        0    0        3
## 40    6   10   65        0        0    1        0        0    0        0
## 41    5    2   44        0        0    1        0        0    0        0
## 42    5    7   73        0        1    0        0        0    0        0
## 43    7    4   89        0        5    0        0        0    0       14
## 44    0    0   24        0        0    0        0        0    0       28
## 45    6    6   52        0        1    0        0        0    0        2
## 46   22   28   42        0        4    0        0        0    0        0
## 47   20   24    7        0        1    0        0        0    0        0
## 48   10    1   53        0        0    0        0        0    3        4
## 49    7   17    5        0        0    0        0        0    0        0
## 50    8   11   57        0        3    0        0        0    0        0
## 51    3    8   31        0        4    0        0        0    0        0
## 52    5    3   46        0        1    0        0        0    0        4
## 53    5   10   44        0        2    0        0        0    0        2
## 54    0    1   21        0        1    0        0        0    0        0
## 55    3    5   18        0        0    0        0        0    0        0
## 56    0    5   54        0        1    0        0        0    0        3
## 57    0    0    2        0        2    0        0        0    0        1
## 58   12    9   20        0        1    0        0        0    0        0
## 59    0    1   54        0        0    0        0        0    0       29
## 60    4    9   55        0        2    1        0        0    2        0
## 61    1    1    6        0        2    0        0        0    0        0
## 62    0    1    0        0        1    0        0        0    0        0
## 63    8   13   14        2        2    2        0        0    0        1
## 64    4    4   20        0        1    0        0        0    0        4
## 65   12    8   16        0        0    0        0        0    0       23
## 66   12   25    4        1        1    0        0        0    0        3
## 67    0    0  723        0        0    0        0        0    0        7
## 68    7    9   32        0        3    1        0        0    0        1
## 69   73   14   11        0        4    3        0        0    2       22
## 70   13   12   23        0        2    1        0        0    0        7
##    PPEL NCOR SLAT FSET Lepidzts Eupelops Miniglmn LRUG PLAG2 Ceratoz3
## 1     0    0    0    0        0        0        0    0     0        0
## 2     1    2    2    2        1        0        0    0     0        0
## 3     0    2    0    8        0        0        0    0     0        0
## 4     1    3    2   12        0        0        0    0     0        0
## 5     0    0    0   12        2        0        0    0     0        0
## 6     0    1    0   10        0        0        0    0     0        0
## 7     0    0    0    9        0        1        0    0     0        0
## 8     0    0    0    6        1        0        1    0     0        0
## 9     0    0    0    0        0        0        0    0     0        0
## 10    0    0    3   10        0        1        2    0     0        0
## 11    1    0    3    7        3        3        0    1     1        0
## 12    1    0    0    5        0        3        0    0     0        0
## 13    0    0    0    1        0        0        0    0     1        0
## 14    2    0    8    8        1        2        5    0     0        0
## 15    2    0    1    0        1        1        1    1     0        0
## 16    0    0    0    1        2        2        0    0     0        0
## 17    0    0    0    3        0        1        0    0     0        0
## 18    0    0    2    2        0        1        3    0     0        0
## 19    0    0    2    1        0        1        0    8     0        2
## 20    3    0    4    3        0        1        2    0     0        0
## 21    0    0    0    3        0        0        0    0     0        0
## 22    0    0    0    3        0        0        0    1     0        0
## 23    0    1    0    0        0        0        1    3     0        0
## 24    0    0    0    3        0        0        0    0     0        0
## 25    0    0    0    1        0        1        0    1     0        1
## 26    0    0    0    2        0        0        0    0     1        0
## 27    0    1    0    7        0        4        1    1     0        1
## 28    0    4    0    0        0        1        0   11     2        6
## 29    0    0    0    0        0        1        0    2     0        0
## 30    0    1    1    1        0        1        0   12     0        0
## 31    0    1    0    0        0        0        0   12     2        3
## 32    0    0    0    2        0        1        0    7     2        0
## 33    0    1    0    0        0        1        0   23     0        1
## 34    0    1    0    2        1        0        0   11     1        1
## 35    0    1    0    1        0        4        0    4     3        1
## 36    0    1    0    3        0        0        0   20     4        0
## 37    0    2    0    1        0        2        1   21     3        2
## 38    0    2    0    0        0        0        0   18     0        0
## 39    0    0    0    0        0        3        0   18     0        2
## 40    0    2    0    0        0        0        0   26     0        6
## 41    0    1    0    0        0        1        0   13     0        1
## 42    0    6    0    0        0        1        0   31     0        3
## 43    0    1    0    0        0        0        0    3     0        0
## 44    0    0    0    0        0        0        0    1     0        0
## 45    0    6    0    0        0        1        0   52     2        1
## 46    0    3    0    1        0        2        0   19     3        0
## 47    0    1    0    0        0        1        0   34     2        1
## 48    0    1    0    0        0        0        0   29     1        6
## 49    0    3    0    0        0        0        0   25     5        7
## 50    0    0    0    0        0        2        0   14     0        9
## 51    0    1    0    0        0        0        0   26     1        3
## 52    0    3    0    0        0        0        0   31     9        1
## 53    0    6    0    0        0        0        0   25     9        9
## 54    0    0    0    0        0        0        0   15     0        0
## 55    0    0    0    0        0        0        0   15     0        2
## 56    0    0    0    0        0        0        0   17     0        1
## 57    0    0    0    0        0        1        0    2     0        0
## 58    0    1    0    0        0        0        0   57     0        2
## 59    0    0    0    0        0        0        0    2     0        0
## 60    0    0    0    0        0        0        0   28     0        0
## 61    0    0    0    0        0        0        0    9     0        3
## 62    0    0    0    0        0        0        0    2     0        0
## 63    0    2    0    0        0        0        0    5     0        1
## 64    0    1    0    0        0        0        0   16     0        2
## 65    1    1    0    0        0        0        0    4     0        2
## 66    0    3    0    0        0        0        0   21     0        1
## 67    0    0    0    0        0        0        0   11     0        0
## 68    0    3    0    0        0        0        0    0     0        3
## 69    0    7    0    0        0        0        0    6     3        0
## 70    0    3    0    0        0        0        0   16     1        7
##    Oppiminu Trimalc2
## 1         0        0
## 2         0        0
## 3         0        0
## 4         0        0
## 5         0        0
## 6         0        0
## 7         0        0
## 8         0        0
## 9         0        0
## 10        0        0
## 11        0        0
## 12        0        0
## 13        0        0
## 14        0        0
## 15        0        0
## 16        0        0
## 17        0        0
## 18        0        0
## 19        0        0
## 20        0        0
## 21        1        0
## 22        0        0
## 23        2        0
## 24        0        0
## 25        2        0
## 26        2        0
## 27        0        0
## 28        2        0
## 29        0        0
## 30        1        0
## 31        1        0
## 32        4        0
## 33        2        0
## 34        9        0
## 35        6        0
## 36        1        0
## 37        2        0
## 38        1        0
## 39        1        0
## 40        5        0
## 41        1        0
## 42        0        0
## 43        1        1
## 44        0        0
## 45        3        0
## 46        5        0
## 47        2        0
## 48        0        1
## 49        4        0
## 50        0        0
## 51        1        1
## 52        0        0
## 53        1        9
## 54        0        1
## 55        6        0
## 56        0        5
## 57        0        0
## 58        4        0
## 59        0        1
## 60        1        1
## 61        0        5
## 62        0        0
## 63        2        8
## 64        0       11
## 65        0       25
## 66        0        9
## 67        0       33
## 68        0       17
## 69        4        3
## 70        1       14
```

Tarea 4. Teje
-------------

-   **Lee la [sección "Antes de tejer"](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/guia-minima-de-rmarkdown.md#antes-de-tejer) y la [sección "Teje"](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/guia-minima-de-rmarkdown.md#teje) de la Guía Mínima de RMarkdown.**

-   **Cuando estés listo/a, teje tu `.Rmd`. Generarás un `.md` nuevo, que contendrá los cambios que hayas hecho, incluyendo los resultados que produzca tu código.**

> Como pone la Guía, "Debes estar pendiente a los errores...", porque si el código no se ejecuta correctamente, no se podrá generar el `.md`. Por ello es muy importante que, antes de tejer, hayas ejecutado tu código en la consola y comprobado que devuelve resultados sin errores.

Tarea final: *commit*&gt;*push*
-------------------------------

-   **Usa la guía [¿Cómo realizar una asignación?](https://github.com/biogeografia-201902/material-de-apoyo/blob/master/ref/como-hacer-una-asignacion.md) para sincronizar con tu repo remoto.**

Si llegaste hasta aquí sin fallos, pasaste varios mundos. Sin embargo, las probabilidades de que encuentres tropiezos son de más de un 60%. Tropiezos, errores, fallos, "da error" conllevarán aprendizajes.

Referencias
===========

Borcard, D., & Legendre, P. (1994). Environmental control and spatial structure in ecological communities: An example using oribatid mites (acari, oribatei). *Environmental and Ecological Statistics*, *1*(1), 37–61.

Borcard, D., Legendre, P., & Drapeau, P. (1992). Partialling out the spatial component of ecological variation. *Ecology*, *73*(3), 1045–1055.
