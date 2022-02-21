# PROGETTO FEDERICO CRIPPA 712
![immagine drv8833](https://github.com/FC712/RTOS_Motore_Crippa_v10/blob/main/IMMAGINI/RULLO.PNG)
## SPIEGAZIONE HARDWARE
#### MOTORE IN CORRENTE CONTINUA
Un motore in corrente continua (CC) è un tipo di macchina elettrica che converte l’energia elettrica in energia meccanica. Assorbe energia elettrica attraverso la corrente continua e la converte in rotazione meccanica.
Nei motori CC parte che gira è detta rotore o armatura mentre la parte che genera il campo magnetico fisso (nell'esempio i due magneti colorati) detta statore. Un interruttore rotante detto commutatore o collettore a spazzole inverte due volte ad ogni giro la direzione della corrente elettrica che percorre i due avvolgimenti generando un campo magnetico che entra ed esce dalle parti arrotondate dell'armatura. Nascono forze di attrazione e repulsione con i magneti permanenti fissi (indicati con N ed S nelle figure).

![immagine drv8833](https://github.com/FC712/RTOS_Motore_Crippa_v10/blob/main/IMMAGINI/MOTORE.PNG)

La velocità di rotazione dipende da: 
- Tensione applicata. 
- Corrente assorbita dal rotore. 
- Carico applicato.
La coppia generata è proporzionale alla corrente ed il controllo più semplice agisce sulla tensione d'alimentazione, mentre nei sistemi più complessi si usa per la tensione un controllo in retroazione.

### DRIVER PILOTAGGIO MOTORE DRV8833

![immagine drv8833](https://github.com/FC712/RTOS_Motore_Crippa_v10/blob/main/IMMAGINI/DRIVER.PNG)

Dual-H-Bridge Current-Control Motor Driver 
- Can Drive Two DC Motors or One Stepper Motor
- Output Current 1.5-A RMS, 2-A Peak per H-Bridge
- Power Supply Voltage Range 2.7 to 10.8V

### SCHEMA DI MONTAGGIO DEL DRIVER MOTORE
![schema elettrico driver motore](https://github.com/FC712/RTOS_Motore_Crippa_v10/blob/main/IMMAGINI/SCHEMATIC.PNG) 

## DESCRIZIONE CODICE

### PREMESSE
L' RTOS è il sistema operativo, utilizzato per il nostro progetto, in grado di generare un impulso elettrico. Questo utilizza il TIMER per generare il segnale PWM.

#### Questo codice è necessario per il controllo della velocità del motore e quindi anche del rullo.

Il motore è collegato ad un DRIVER(*DRV8833*), i cui pin di ingresso sono collegati uno a ***GND*** e l’altro alla scheda ***stm32***(*sul pin PE11*) che attraverso un segnale PWM, generato da un ***TIMER***(*PE11 -> TIM1_CH2*), viene regolata la velocità. 

## COLLAUDO
##### La task che regola la velocità del motore deve essere sempre in funzione.
Nell' ultima versione del progetto ho fatto in modo che, quando alimentiamo il rullo, il motore non si attiva, lo attiviamo quando necessario schiacciando il pulsante di sinistra.
