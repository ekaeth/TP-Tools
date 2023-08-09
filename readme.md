![TP Tools](./assets/tp-tools.png)

**Por favor, infórmenos de cualquier problema con los textos. No somos hablantes nativos del inglés** 

**Hasta mediados de agosto de 2023, las herramientas son más "alfa" que "beta". Habrá muchas actualizaciones, de las características que faltan** 

---

# TP-Tools (beta)

**GRATIS para uso comercial**

Una pequeña colección de herramientas que simplifican la puesta en marcha y la programación de robots Fanuc.

Los programas están sujetos a la licencia

*CC BY-ND 4.0 Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)*


https://creativecommons.org/licenses/by-nd/4.0/

- Se permite la distribución.
- No se permite la modificación del archivo binario.
- Se da el nombre del autor, porque el archivo binario contiene información

Aunque la licencia Creative Commons no se creó para el software, en este caso nos sirve para nuestro propósito.

NO es necesario copiar un archivo de licencia en el controlador del robot.

**De este modo, nada se opone a su uso comercial.**

---
### Controlador y versión

- R-30iA (< V7.50)
- R-30iB (< V8.10)
- R-30iBPlus (< V9.10)
- R-30iBPlus/CRX (< V9.40/42)

Si no existe la subcarpeta correspondiente, la versión (actualmente) no está disponible.

Si se puede utilizar el *Arg-Wizard* o existe un plug-in CRX se describe o explica.

## Estructura del programa
Currently the programs "TP_VIEW" and "TP_WRITE" use a "uniform" API.

- Simple commands are called or executed with a string containing the command name.
  - :CALL TP_VIEW('HELP');
- Commands of same functional group have the  group name separated by a dot from the command name.
  - :CALL TP_VIEW('FORCE.VIEW');
- Commands may have (optional) parameters/arguments.
  - :CALL TP_VIEW('FORCE.VIEW',2);

*more about this  [deepdive](/.DeepDive.md)*

---
## TP_VIEW

TP_VIEW can be used to switch the windows/screens
You can switch between
- Single / Triple / Dual
- Single_User / Single_User_Wide
- Load a user-defined screen
- Show modal Dialogs


[tp_view](/tp_view/readme.md)

![tp_view](./assets/TP_VIEW_Example1.gif)


e.g.
```
 :  CALL TP_VIEW('SCREEN.TRIPLE') ;
 :  CALL TP_VIEW('DIALOG.YES_NO',123) ;
 :  CALL TP_VIEW('LOAD_VIEW',3) ;
 :  CALL TP_VIEW('CLEAR_VIEW',1) ;
```
---
## TP_WRITE

TP_WRITE can be used to write single-line (dynamic) messages to various "screens".

[tp_write](/tp_write/readme.md)

![tp](./assets/Werbung1.gif)

Among others, the following are available for selection:

  - Console
  - UserScreen
  - TPError

The usage with the Arg-Wizard is planned.
The CRX_PlugIn is  under development.


---



## RAND2REG

 
Generates a (pseudo) random number and writes the value into the corresponding register.

Uses $FAST_CLOCK to initialize, but can also be configured.

[RAND2REG](./RAND2REG/readme.md)


![tp](./assets/Random_Simple.gif)

---
## set_invisib

Make programs temporarily invisible or hide them

 [set_invisib](./set_invisib/readme.md)


![set_invisib.gif](./assets/SET_PROGS_INVISIBLE2.gif)

 ---



## ~~TP_ARGS~~

**dated for later**


TP_ARGS can be used to check and log the ARG's which are given to a decent program. 
This allows a program to use optional ARG's

e.g.
```
CALL SET_PR(10,100,0,0)
CALL SET_PR(10,100,0,0,0,0,0)

..SET_PR
    :CALL TP_ARGS('DO.COUNT',AR[1],AR[2],AR[3],AR[4],AR[5],AR[6],AR[7]);
    :IF $[TP_ARGS]COUNT = 4;
        :PR[AR1,1]=AR[2];
        :PR[AR1,2]=AR[3];
        :PR[AR1,3]=AR[4];
        :PR[AR1,4]=0;
        :PR[AR1,5]=0;
        :PR[AR1,6]=0;
        :END;
    :ENDIF;
    :IF $[TP_ARGS]COUNT = 7;
        :PR[AR1,1]=AR[2];
        :PR[AR1,2]=AR[3];
        :PR[AR1,3]=AR[4];
        :PR[AR1,4]=AR[5];
        :PR[AR1,5]=AR[6];
        :PR[AR1,6]=AR[7];
        :END;
    :ENDIF;
    !Number of ARGS invalid;
    :ABORT;

```

---

## ~~PING~~

**dated for later**


A simple program for "pinging" network participants


---


## ~~CRC-Tools~~

**not a program, but an API**
**dated for later**


Enables the calculation of different checksums:
  
  - MODBUS
  - CCITT
  - MCRF4XX

---

## ~~MESSAGE~~


Replaces the internal command

    MESSAGE[string].


***TP_WRITE*** is the more powerful alternative :-)


---
---
## F.A.Q.

- Why xy ? --> Check  faq.md
- I need more technical information. --> Check  DeepDive.md
- Where ca I find a changelog? Use github and check info files.

---

- Fanuc is a registered trademark. 

---

Copyright (c) 2023 Backdate Software/Andreas Wissing

---


