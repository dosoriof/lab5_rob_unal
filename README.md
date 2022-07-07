# Laboratorio 5 - Robótica Industrial IRB140

* Rafael Ricardo Galindo
* Diego Fabian Osorio Fonseca


# Descripción de la solución planteada.  
Considerando que las trayectorias son las misma y que no se requiere de ningún tipo de configuración diferente para ninguno de los puntos, se decide realizar el proceso de forma que la entrada digital se encargue únicamente de redefinir la configuración del workobject, de esta forma no se deben definir targets para las dos trayectorias, sino únicamente para una y solo se define el workobject base de dicha trayectoria acorde a la señal de entrada activa, esto se realiza creando una secuencia que permite llamar a las mismas rutinas, con la única diferencia de que al principio se realiza la definición del workobject.  
Para realizar dicho proceso primero se deben tener la coordenadas base para definir el workobject, para esto se realiza Jogging del robot de forma similar a como se realizó en el Laboratorio 4, se utiliza un punto para el caso del plano horizontal, en este caso solo se toma el valor z del punto como referencia, y para el caso del plano inclinado se toman 3 coordenadas, la primera se considera el origen del workobject la segunda se considera que esta sobre el eje X del workobject y la tercera se considera que esta sobre el plano XY del workobject, con estos valores se tiene suficiente para hacer una definición completa del workobject en el cual se realizara la trayectoria.  
Hecho el proceso de reconocimiento del entorno se procede a exportar el código RADIP y cargar el modulo en el controlador del robot, luego se inicia la ejecución del código; dado que ya se tiene las entradas configuradas y el tablero de control correctamente conectado se procede a presionar la entrada digital 01 lo cual le dice al robot que realice la trayectoria en plano horizontal, cuando haya finalizado dicha trayectoria el robot va a la posición de home y se queda esperando nuevas entradas, en este caso se presiona la entrada digital 02 lo que hace que el robot realicé la trayectoria en el plano inclinado, luego de completarla el robot vuelve a home y espera nuevas entradas; este es el bucle que presenta el programa.  

