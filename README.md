# **Métodos para graficar a partir de datos en archivos ".csv"**
  Al momento de iniciar a trabajar en *Rstudio*, primeramente se debe crear un *script* nuevo y después establecer el directorio en el que se desea trabajar con los archivos (*session > set working directory > to source file location*). Es importante que el archivo (*.csv*) esté bien configurado con los datos, es decir que estén separados por comas.
  
  Para establecer los datos se puede usar el siguiente comando ***inp <- read.csv("FDC.csv", na.strings="")***. Este funciona para establecer el dato, y seguidamente establecer el archivo con el que se trabaja, la parte de *na.strings* funciona para convertir espacios con datos faltantes en espacios vacios. Una vez hecho eso para comprobar que no quedan espacios sin datos, se utiliza el comando ***inp[!complete.cases(inp),]***. Esto hace que las variables de *Banano* y *Estrella* sean en el inp 2 y 3 resppectivamente.
  
  Para verificar un resumen de los datos de las variables, se puede usar el siguiente comando:
  >*summary(inp[,2:3])*

Esto generará en la consola estos datos de las variables respectivas:

![Summary](https://user-images.githubusercontent.com/83330908/119290174-44353f80-bc09-11eb-98d8-def2d617167f.PNG)


### Gráfico de líneas

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

### Histogramas

Los datos obtenidos con el comando de *summary* se pueden realizar histogramas con el siguiente comando, ya sea para graficar los datos del río Estrella o Banano.

>*hist(inp[,2], col="blue",xlab = "Rango absoluto", ylab = "Frecuencia", main= "Histograma de los datos recolectados del río Estrella")*

![Histograma rio estrella](https://user-images.githubusercontent.com/83330908/119290278-76df3800-bc09-11eb-9c30-fee72f41644d.png)

>*hist(inp[,3],col="cyan",xlab = "Rango absoluto", ylab = "Frecuencia", main= "Histograma de los datos recolectados del río Banano")*

![Histograma rio banano](https://user-images.githubusercontent.com/83330908/119290435-ba39a680-bc09-11eb-948c-9d55f397b5f1.png)
 
### Gráficos plot

Este es otro tipo de gráfico que se puede realizar con el siguiente comando:

>*plot(Estrella, col="blue",xlab = "Frecuencia", ylab = "Rango absoluto", main= "Datos recolectados del río Estrella")*

![plotestrella](https://user-images.githubusercontent.com/83330908/119291602-f79f3380-bc0b-11eb-9acb-75ff61ac7da9.png)

>*plot(Banano,col="cyan",xlab = "Frecuencia", ylab = "Rango absoluto", main= "Datos recolectados del río Banano")*

![plotbanano](https://user-images.githubusercontent.com/83330908/119291612-ff5ed800-bc0b-11eb-8e0f-0fd9876b1a77.png)

## **Graficar cantidades máximas de mediciones**

Primeramente se debe establecer las variables (*MAQ y MMQ*) y el *Tempdate* con los siguientes comandos:

#### Tempdate

>*Tempdate <- strptime(inp[,1], format= "%d/%m/%Y")*

#### *MAQ (Maximum Annual Quantity)*

>*MAQ_Estrella <- tapply(inp[,2], format(Tempdate, format="%Y"),FUN=sum)*

>*MAQ_Banano <- tapply(inp[,3], format(Tempdate, format="%Y"),FUN=sum)*

#### *MMQ (Maximum Monthly Quantity)*

>*MMQ_Estrella <- tapply(inp[,2], format(Tempdate, format="%m"),FUN=sum)*

>*MMQ_Banano <- tapply(inp[,3], format(Tempdate, format="%m"),FUN=sum)*

### Cantidad Máxima Anual (*MAQ*)



  
