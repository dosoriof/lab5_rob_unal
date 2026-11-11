# Industrial Robotics with the ABB IRB 140

**Laboratory 5 · RobotStudio · RAPID**

## Project demonstration

[![Watch the Laboratory 5 demonstration](https://img.youtube.com/vi/AeCOol4kHso/0.jpg)](https://youtu.be/AeCOol4kHso)

The video shows the RobotStudio simulation and the implementation on the real IRB 140 robot.

**Authors**

- Rafael Ricardo Galindo
- Diego Fabian Osorio Fonseca

---

## Solution

The two drawing trajectories use the same target points, and neither requires a different configuration for those points. The digital inputs therefore select the trajectory by redefining the **work object**.

This approach uses one set of targets and calls the same drawing routines for both surfaces. The work object is defined at the beginning of each sequence according to the active digital input.

### Defining the work objects

First, the reference coordinates needed to define each work object are obtained by jogging the robot, following a process similar to Laboratory 4.

For the horizontal plane, one point is measured and its Z coordinate is used as a reference.

For the inclined plane, three points are measured:

1. The work object origin.
2. A point on the work object’s X axis.
3. A point on the work object’s XY plane.

These points provide the information needed to define the work object in which the trajectory will be executed.

### Running the program

After measuring the environment, the RAPID code is exported and the module is loaded into the robot controller. With the digital inputs configured and the control panel connected, the program is executed.

- **Digital input 01** selects the horizontal-plane work object and runs the trajectory.
- **Digital input 02** selects the inclined-plane work object and runs the trajectory.

After completing each trajectory, the robot returns to its home position. The original implementation describes the robot as waiting for a new input before the next trajectory.

---

## RAPID code

The following module was used for the laboratory.

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
        ! Add your code here
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
