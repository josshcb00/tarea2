# **Métodos para graficar a partir de datos en archivos ".csv"**
  Al momento de iniciar a trabajar en *Rstudio*, primeramente se debe crear un *script* nuevo y después establecer el directorio en el que se desea trabajar con los archivos (*session > set working directory > to source file location*).
  
  Para establecer los datos se puede usar el siguiente comando ***inp <- read.csv("FDC.csv", na.strings="")***. Este funciona para establecer el dato, y seguidamente establecer el archivo con el que se trabaja, la parte de *na.strings* funciona para convertir espacios con datos faltantes en espacios vacios. Una vez hecho eso para comprobar que no quedan espacios sin datos, se utiliza el comando ***inp[!complete.cases(inp),]***

