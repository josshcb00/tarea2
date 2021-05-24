# **Métodos para graficar a partir de datos en archivos ".csv"**
  Al momento de iniciar a trabajar en *Rstudio*, primeramente se debe crear un *script* nuevo y después establecer el directorio en el que se desea trabajar con los archivos (*session > set working directory > to source file location*). Es importante que el archivo (*.csv*) esté bien configurado con los datos, es decir que estén separados por comas.
  
  Para establecer los datos se puede usar el siguiente comando ***inp <- read.csv("FDC.csv", na.strings="")***. Este funciona para establecer el dato, y seguidamente establecer el archivo con el que se trabaja, la parte de *na.strings* funciona para convertir espacios con datos faltantes en espacios vacios. Una vez hecho eso para comprobar que no quedan espacios sin datos, se utiliza el comando ***inp[!complete.cases(inp),]***. Esto hace que las variables de *Banano* y *Estrella* sean en el inp 2 y 3 resppectivamente.
  
  Para verificar un resumen de los datos de las variables, se puede usar el siguiente comando:
  >*summary(inp[,2:3])*

Esto generará en la consola estos datos de las variables respectivas:

![Summary](https://user-images.githubusercontent.com/83330908/119290174-44353f80-bc09-11eb-98d8-def2d617167f.PNG)


## Gráfico de líneas

Para expresar los datos obtenidos en un gráfico linear, se debe utilizar este comando:
 
>*plot(inp[,2], type = "l", col="blue",xlab = "Días", ylab = "Caudal (mL/día)", main= "Tasa de nivel de caudal de los Ríos Banano y Estrella")
lines(inp[,3], col="cyan")
legend(
  x = "topright",
  legend = c("Río Estrella", "Río Banano"),
  fill = topo.colors(6),
  inset = -0.04,
  horiz = FALSE
  )*

Este comando creará este gráfico:

![Rplot01](https://user-images.githubusercontent.com/83330908/119286951-b5252900-bc02-11eb-8762-c4e33b0bff5b.png)

## Histogramas

Los datos obtenidos con el comando de *summary* se pueden realizar histogramas con el siguiente comando, ya sea para graficar los datos del río Estrella o Banano.

>*hist(inp[,2], col="blue",xlab = "Rango absoluto", ylab = "Frecuencia", main= "Histograma de los datos recolectados del río Estrella")*

![Histograma rio estrella](https://user-images.githubusercontent.com/83330908/119290278-76df3800-bc09-11eb-9c30-fee72f41644d.png)


  
