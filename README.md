# Laboratorio 1
### Gustavo Adolfo Ropero Bastidas
### Joan Sebastián Arcila Cardozo
- ## Desarrollo de solución
El desarrollo de este laboratorio partió de escoger una marca reconocida y dibujar, mediante el robot IRB140 que se encuentra en el laboratorio de Sistemas Intelegentes y Robotizados (SIR), el logo, escribir el nombre de la marca y las iniciales del primer nombra de cada integrante. La selección fue facebook. Por consiguiente, se diseñó la herramienta y el workobject en Inventor. Tal como aparece en las siguientes figuras

![Image](https://github.com/garoperob/lab1robotics/blob/main/tool.png "Title")

![Image](https://github.com/garoperob/lab1robotics/blob/main/wobject.png  "Title")

La herramienta fue diseñada con una inclinación de 30° respecto a la horizontal de la base que conecta con el flanché del robot. El tablero se diseñó partiendo de las medidas de los tableros que se encuntran en el labSIR.

Los modelos se exportaron en formato .sat para importarlos directamente a RobotStudio; la herramienta se le añadió un cono truncado para tener en cuenta la longitud del marcador. Dentro del programa se creó una nueva herramienta y se guardó en la librería, con esto se eligió el robot a usar, siendo el IRB140 con el controlador IRB140_6_81_C_03. Después de esto se instaló la herramienta y se importó la geometría del worobject resultando de la sigueinte forma

![image](https://github.com/garoperob/lab1robotics/assets/80500171/f82e330b-2526-427d-b77b-18d5a882ccc7 "Title")

A partir de esto se cobstruyó el workobject sobre la geometría del tablero, mediante situar 3 puntos, donde el eje rojo es X y el eje verde es Y. El sentido del eje Z del workbject (WO) debía ser hacia dentro del tablero, de lo contrario el robot al intentar seguir la trayectoria giraría la herramienta hasta ponerla en el mismo sentido del marco WO. La parte encerrada en amarillo es el resultado de la ubicación del WO

![wobject-construction](https://github.com/garoperob/lab1robotics/assets/80500171/4182048d-6f26-458c-bdc7-0eca4246d41a "Title")

Esto permitió crear los puntos sobre la superficie de la geometría 

![image](https://github.com/garoperob/lab1robotics/assets/80500171/5510546b-9877-4788-bc1b-f9e368032e3c "Title")

Los puntos se ubicaron usando las opciones Surface Selection, Snap Edge y Snap End. Se tuvo en cuenta las discontinuidades cuando terminaba de dibujar una forma para generar un alejamiento de 30 mm de distancia y luego se acercará de forma más segura al siguiente punto para empezar la próxima forma. Estos puntos se les conoce como puntos de evacuación. Finalmente, se llegó a la construcción de la trayectoria que debía recorrer a través de los puntos, la cual se generó de forma automática. Sin embargo, fue necesario cambiar tanto los comandos MoveL para algunos puntos de evacuación como la configuración del movimiento que generaba muchas singularidades. Obteniendo el siguiente resultado

![image](https://github.com/garoperob/lab1robotics/assets/80500171/4eab3b7a-8a3f-4dba-a122-393fe6c6e707 "Title")

Teniendo el path establecido se crearon las entradas y salidas digitales, esto se hace entrando al menú del controlador y dando click derecho en signal, luego en New signal

![image](https://github.com/garoperob/lab1robotics/assets/80500171/31f534c5-1afd-466c-b099-5ebe49c5fc38 "Title")

En el cuadro desplegado se pone el nombre y el tipo de señal. En este caso, Digital Input para entradas y Digital Output para salidas

![image](https://github.com/garoperob/lab1robotics/assets/80500171/15455136-56b4-4ce9-9ff8-49e8f5c9c826 "Title")

Asignadas las señales, se edita el código de RAPID en el main() con el fin de activar entradas y salidas, se reinició el controlador y se sincronizó desde la estación hacia el RAPID, como se ve a continuación

![image](https://github.com/garoperob/lab1robotics/assets/80500171/af08ca5c-2b13-47f5-91b9-40dbbfd98a52 "Title")

Se instanció el valor de las salidas en 0, mediante la función SetDO, para crear un WHILE TRUE que contuviese las entradas y activara el recorrido del path, más precisamente, Path_10. La otra entrada debía ser la posición de mantenimiento. Dicha posición se construyó creando otro punto cercano a home y otra trayectoria con MoveJ con el fin de evitar singularidades, por ende, la otra condición que aparece en el código pertence a esta construcción. Por último, se sincronizó desde el RAPID hacia la estación para poder llamar la rutina.

# Diagrama de flujo de acciones del robot

![image](https://github.com/garoperob/lab1robotics/assets/80500171/799ae20d-a3c0-4341-8255-fa634e4f0f28)

# Funciones utilizadas
Se empleó SetDO para instanciar las salidas en 0, un ciclo WHILE TRUE para que la acción fuera repetitiva. Dentro del WHILE se colocaron dos condicionales IF, cada uno activa un path. La trayectoria recorrió usaron MoveL y MoveJ, donde el primero se empleó para seguir de forma lineal la trayectoria de la herramienta y el segundo para facilitar el movimiento mediante ejes de los puntos de evacuación y la trayectoria path_20.

# Diseño de la herramienta

Partiendo de las medidas del flanche encontradas en el manual del brazo robótico IRB140, por tanto, la base fue de 50 mm con tornillos M6x20 con una profundidad de 10 mm. Por otro lado, se extruyó el tubo que contenía la herramienta y se le dio una inclinación de 30°.

# Código de RAPID

Dentro del repositorio se encuentra un archivo con ambos códigos de RAPID, tanto plano inclinado como llano. Sin embargo, la diferencia entre estos es únicamente es la posición de los targets.

# Video de comprobación de funcionamiento

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/V4ZzZhOP_X8/0.jpg)](https://www.youtube.com/watch?v=V4ZzZhOP_X8)
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/qPzvd4asezQ/0.jpg)](https://www.youtube.com/watch?v=qPzvd4asezQ)
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/ywTjaPXRh5Y/0.jpg)](https://www.youtube.com/watch?v=ywTjaPXRh5Y)





