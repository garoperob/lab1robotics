# Laboratorio 1
- ## Dessarrollo de solución
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

Los puntos se ubicaron usando las opciones Surface Selection, Snap Edge y Snap End. Se tuvo en cuenta las discontinuidades cuando terminaba de dibujar una forma para generar un alejamiento de 30 mm de distancia y luego se acercará de forma más segura al siguiente punto para empezar la próxima forma. Estos puntos se les conoce como puntos de evacuación. Finalmente, se llegó a la construcción de la trayectoria que debía recorrer a través de los puntos, la cual se generó de forma automática. Sin embargo, fue necesario cambiar tanto los comandos MoveL para algunos puntos de evacuación como la configuración del movimiento que generaba muchas singularidades.



