# BlackView A5 Rooting Guide
1. Introduzione
2. Specifiche del device
3. Strumenti utilizzati
4. Installazione 
5. Rooting
6. Operazioni 
7. Conclusioni


## 1. Introduzione
Questa (mini) guida descrive come eseguire il "rooting" del device BlackView A5, 
e in generale e' applicabile a tutti gli smartphone con chipset Mediatek uguale o simile.

Per eseguire i seguenti passaggi e' necessario disporre di una macchina con il sistema operativo Windows.



## 2. Specifiche del device



| Nome:         | Valore: 
|---------------|--------------------                                                                                                                                                                                                         
| Device Type   | Android Smartphone
| Brand         | Blackview
| Model         | A5
| CPU           |   Quad-Core 1.3 GHz ARM Cortex A-7 
| Chipset       | MediaTek MT6580 32-bit Processor
| Camera        | 5 Megapixel With LED Flash | 2 Megapixel Front camera
| Memory        | 1GB | ROM 8GB External Memory Storage up to 32GB
| Display       | screen size 4.5 inches
| Battery       | Non-Removable Lithium-Ion 2,000 mAh battery
| Altro         | Dual SIM with Micro SIM Compatibility
| Network type  | support 2G/3G 
| OS            | Android 6.0 Marshmallow

Ulteriori dettagli si trovano sul [sito del produttore](http://www.blackview.hk/blackview-140/)


## 3. Strumenti utilizzati
Per eseguire il rooting ci servono i seguenti componenti software:


<dl>
  <dt>SuperSu - <a href="http://www.supersu.com/download">http://www.supersu.com/download</a></dt>
  <dd>
    E' il componente che esegue il rooting vero e proprio del device. Questo componente
    viene caricato dal recovery (bootloader ?) TWRP.
  </dd>

  <dt>SP Flash Tool - <a href="https://spflashtool.com/">https://spflashtool.com/</a></dt>
  <dd>
    SmartPhone Flash Tool e' un software fatto per funzionare con i smartphone basati sui chipset MediaTek (in A5 e' MT6580).
    Nel nostro caso ci serve per caricare "scatter file" del chipset per poi caricare l'immagine recovery sul nostro device.
    <br />
    Per utilizzare il programma e' necessario installare il seguente driver sulla propria macchina.
    <br />
    <a href="https://spflashtool.com/download/MediaTek_USB_VCOM_drivers.zip">Driver 1</a>
    <br />
    <a href="https://spflashtool.com/download/Driver_Auto_Installer_v1.1236.00.zip">Driver 2</a>
  </dd>
  
  <dt>Scatter File</dt>
  <dd>
    esempio: MT6580_Android_scatter.txt <br />
    Si tratta di un file di testo che rappresena l'indice di partizioni del device. Serve al programma SP Flash Tool per capire in che parte della memoria dello smartphone caricare un'immagine.
  </dd>
  
  <dt>Recovery Image <a href="https://www.needrom.com/download/blackview-a5/">https://www.needrom.com/download/blackview-a5/</a></dt>
  <dd>
  <em>File: TWRP_3.0.3_Materialised1.img</em>
  <br />
  Team Win Recovery Project - ROM
  <br />
  E' un'immagine di recovery che permette di installare software custom sul device, come rooting.
    
  </dd>

</dl>




## 4. Installazione
L'unico software che deve essere installato sul nostro sistema e' il driver Mediatek, che ci permettera' di comunicare con il device quando questo e' spento.
(nota personale: verificare se su 8.1 deve essere disabilitata driver security)


## 5. Rooting

### 5.0 Abilitare modalita' sviluppatore (e sbloccare OEM bootloader)
Aprire: Impostazioni -> Info sul telefono (in fondo)
<br />
Nella schermata cercare la voce: "Numero build" e fare tap ~7 volte, finche' non appare la scritta "sei uno sviluppatore".
<br />
Tornare nella schermata precedente ed entrare nella nuova voce "Opzioni sviluppatore", dove spuntare l'opzione "Debug USB" per abilitare la comunicazione con lo smartphone tramite ADB.

### 5.1 Disabilitare la protezione del bootloader (comporta la perdita dei dati utente)
Su alcuni modelli puo' essere necessario lo sblocco OEM, che si trova nelle "Opzioni sviluppatore" del passo precedente, dove basta spuntare la voce Sblocco OEM (consenti lo sblocco del bootloader).
<br />
<br />
Adesso occorre collegare il dispositivo al PC e riavviare in modalita' bootloader dando il seguente comando:
```
adb reboot bootloader
```

Questo riavvia lo smartphone nella speciale modalita' bootloader dalla quale possiamo sbloccare il bootloader stesso.
Usiamo fastboot (un tool che viene distribuito insieme ad adb)
```
fastboot oem unlock
```
Qui il dispositivo chiedera' conferma sul proprio schermo.
Premere il tasto specificato per confermare l'operazione.
<br />
<em>Questa operazione comporta la perdita dei dati utente</em>
<br />
Ora riavviare il device
```
fastboot reboot
```

### 5.3 caricare SuperSu nella cartella / (root) del device
File: SuperSU-v2.82-201705271822.zip
<br />
Copiare il file <em>zip</em> nella cartella principale del dispositivo. 

### 5.4 Spegnere il device ed estrarre la batteria
Spegnere il device ed estrarre la batteria. Le operazioni successive avvengono quando il dispositivo e' completamente spento.

### 5.5 Aprire SP Tool con i diritti di amministratore
  Aprire SP tool con i diritti di amministratore e caricare "scatter file" cliccando a nel campo di testo accanto a "Scatter-Loading File" - quindi navigare e aprire il file <em>MT6580_Android_scatter.txt</em>
  <br />
### 5.6 Assicurarsi che lo smartphone sia scollegato dal pc e che sia spento
Il device viene riconosciuto dal programma solo quando e' spento (si puo' anche estrarre la batteria). E' necessario anche che prima di avviare il processo di scrittura dell'immagine, il device sia scollegato dal PC.

### 5.7 Cliccare "Download"
Il processo si avvia e a questo punto possiamo collegare lo smartphone al PC, che verra' riconosciuto, e in pochi istanti l'immagine "recovery" verra' copiata sul device.
Terminata la copia cliccare "Stop" e scollegare il device.

### 5.8












## 8 Recovery of a bricked phone:

dal sito del produttore: 
http://bbs.blackview.hk/viewtopic.php?t=25829

1) Check the software verison number in the device, if the version date is before May 3rd, then download the following one :
https://mega.nz/#!3t9RQRyZ!PJb3YPreGL6f3Xyg8NujlwusIM1CNKEtt4AfwbH5Vlg

2) Otherwise, this one below will be suitable for yours:
https://mega.nz/#!v8sVAQLY!TnRgieY3rYSl2ENrSjSbW0N8y2WQly0P_Hc0xnW2HNY

