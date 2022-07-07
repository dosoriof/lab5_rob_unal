# Laboratorio 5 - Robótica Industrial IRB140

* Rafael Ricardo Galindo
* Diego Fabian Osorio Fonseca

# Código en RAPID del módulo utilizado para el desarrollo de la práctica.  
```rapid
MODULE Module_RDS_di
    CONST robtarget home_RDS:=[[636.195461814,0,604.5],[0.5,0,0.866025404,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_1:=[[0,0,50],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_2:=[[0,0,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_3:=[[0,94,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_4:=[[25.5,94,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_5:=[[48,71.5,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_6:=[[25,49,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_7:=[[0,49,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_8:=[[34.5,43,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_9:=[[40.5,33.5,0],[0,0,1,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_10:=[[53,0,0],[0,0,1,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_11:=[[53,0,0],[0,0,1,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget D_1:=[[67.6,0,50],[0,0,1,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget D_2:=[[67.6,0,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget D_3:=[[67.6,94,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget D_4:=[[97.5,94,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget D_5:=[[130,47,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget D_6:=[[97.5,0,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget R_12:=[[53,0,50],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_1:=[[150,6,50],[0,0,1,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_2:=[[150,6,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_3:=[[169,0,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_4:=[[193,14,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_5:=[[184,40,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_6:=[[160,55,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_7:=[[152,81,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_8:=[[176,94.5,0],[0,0,1,0],[0,0,1,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_9:=[[194.5,89,0],[0,0,1,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    CONST robtarget S_10:=[[194.5,89,50],[0,0,1,0],[0,0,0,0],[9E+09,9E+09,9E+09,9E+09,9E+09,9E+09]];
    PERS tooldata TCP_Porta_marcador:=[TRUE,[[0,0,150],[1,0,0,0]],[1,[0,0,1],[1,0,0,0],0,0,0]];
    TASK PERS wobjdata Workobject_1:=[FALSE,TRUE,"",[[381,-540,134],[0.240269,0.059216,-0.231855,-0.940749]],[[0,0,0],[1,0,0,0]]];
    PERS wobjdata Workobject_3:=[FALSE,TRUE,"",[[381,-540,134],[0.240268724,0.059216044,-0.231854595,-0.940748557]],[[0,0,0],[1,0,0,0]]];

    PROC main()
        !Añada aquí su código
        MoveJ home_RDS,v200,fine,TCP_Porta_marcador\WObj:=wobj0;
        IF DI_01=1 THEN
            Workobject_1:=[FALSE,TRUE,"",[[400,400,45],[0.707106781,0,0,-0.707106781]],[[0,0,0],[1,0,0,0]]];
            R;
            D;
            S;
            MoveJ home_RDS,v200,fine,TCP_Porta_marcador\WObj:=wobj0;
        ENDIF
        
        IF DI_02=1 THEN
            Workobject_1:=[FALSE,TRUE,"",[[381,-540,134],[0.240268724,0.059216044,-0.231854595,-0.940748557]],[[0,0,0],[1,0,0,0]]];
            R;
            D;
            S;
            MoveJ home_RDS,v200,fine,TCP_Porta_marcador\WObj:=wobj0;
        ENDIF
        
    ENDPROC
    PROC R()
        MoveJ R_1,v200,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_2,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_3,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_4,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveC R_5,R_6,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_7,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_6,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveC R_8,R_9,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_10,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_11,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL R_12,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
    ENDPROC
    PROC D()
        MoveL D_1,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL D_2,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL D_3,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL D_4,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveC D_5,D_6,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL D_2,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL D_1,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
    ENDPROC
    PROC S()
        MoveL S_1,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL S_2,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL S_3,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveC S_4,S_5,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL S_6,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveC S_7,S_8,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL S_9,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
        MoveL S_10,v100,fine,TCP_Porta_marcador\WObj:=Workobject_1;
    ENDPROC
ENDMODULE
```

# Video con la simulación en RobotStudio y la implementación de la práctica con el IRB 140.  

El video con la simulación en Robotstudio y la implementación de la práctica con el robot real se encuentra en el siguiente Link:  **[Video Laboratorio 5](https://youtu.be/AeCOol4kHso)**

# Descripción de la solución planteada.  
Considerando que las trayectorias son las misma y que no se requiere de ningún tipo de configuración diferente para ninguno de los puntos, se decide realizar el proceso de forma que la entrada digital se encargue únicamente de redefinir la configuración del workobject, de esta forma no se deben definir targets para las dos trayectorias, sino únicamente para una y solo se define el workobject base de dicha trayectoria acorde a la señal de entrada activa, esto se realiza creando una secuencia que permite llamar a las mismas rutinas, con la única diferencia de que al principio se realiza la definición del workobject.  

Para realizar dicho proceso primero se deben tener la coordenadas base para definir el workobject, para esto se realiza Jogging del robot de forma similar a como se realizó en el Laboratorio 4, se utiliza un punto para el caso del plano horizontal, en este caso solo se toma el valor z del punto como referencia, y para el caso del plano inclinado se toman 3 coordenadas, la primera se considera el origen del workobject la segunda se considera que esta sobre el eje X del workobject y la tercera se considera que esta sobre el plano XY del workobject, con estos valores se tiene suficiente para hacer una definición completa del workobject en el cual se realizara la trayectoria.  

Hecho el proceso de reconocimiento del entorno se procede a exportar el código RADIP y cargar el modulo en el controlador del robot, luego se inicia la ejecución del código; dado que ya se tiene las entradas configuradas y el tablero de control correctamente conectado se procede a presionar la entrada digital 01 lo cual le dice al robot que realice la trayectoria en plano horizontal, cuando haya finalizado dicha trayectoria el robot va a la posición de home y se queda esperando nuevas entradas, en este caso se presiona la entrada digital 02 lo que hace que el robot realicé la trayectoria en el plano inclinado, luego de completarla el robot vuelve a home y espera nuevas entradas; este es el bucle que presenta el programa.  

