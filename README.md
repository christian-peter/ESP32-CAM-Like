# ESP32-CAM-Like
ESP32-CAM with more IO

Ce projet est né du manque d'E/S (GPIO) de la carte ESP32-CAM.

La carte est construite autour d'un ESP32 WROVER. Elle est alimentée sous 5V.
Elle comporte des sorties numériques, des entrées analogiques, une carte microSD et bien sur une caméra (CAMERA_MODEL_AI_THINKER est le seul modèle testé à ce jour).  
Vu le nombre d'E/S nécessaires, tous les périphériques ne sont pas accessibles simultanément.  
Les sorties numériques et les entrées analogiques sont contrôlées par un bus I2C.


Les sorties numériques (PWM/MLI) sont gérées par un PCA9685, alimenté en permanence sous 5V ou 3,3V (pont de soudure 'OUTPUTS').  
le pont de soudure '/OE' doit être à 0 pour que les sorties soient actives.  
Deux sorties de ce circuit ('POWER' et 'POWER_SD') sont utilisées pour sélectionner les périphériques.  
<b>Seule une de ces deux sorties doit être activée.</b>  
Si 'POWER_SD' est au niveau haut, il est possible d'utiliser la carte microSD.  
Si 'POWER' est au niveau haut, il est possible d'utiliser les autres périphériques.  
Ce circuit pilote également deux LEDs (rouge et verte).

Les entrées analogiques sont contrôlées par un MCP3428 (4 canaux).  
Le canal 1 est relié au connecteur 'MAX9814' qui peut recevoir un ampli audio du même nom.  
Le canal 2 est connecté à un LDR polarisée par une résistance R22.  
Le canal 3 permet de mesurer la tension d'alimentation.  
Ces trois premiers canaux sont référencés par rapport à la masse (0V).  
Le 4ème canal est relié au connecteur 'CAN' qui permet une entrée différentielle.  

Les schémas et PCB ont été dessinés avec Eagle.  
Le logiciel est développé avec l'IDE arduino.


![ESP32-CAM-Like](./pictures/ESP32-CAM-Like.jpg)
