---
layout: default
title: "Sprint 1: Instal·lació, Configuració Inicial i Programari de Base"
---

![Captura d'autenticació com a root](image.png)

Pas 1: fem login com a root amb `sudo` per poder modificar la configuració del sistema.

![Definició del target personalitzat](image-1.png)

Pas 2: creem el target `manu.target` i li indiquem que s'ha d'executar després de `graphical.target`.

![Script d'inicialització](image-2.png)

Pas 3: preparem l'script `/usr/local/bin/manuscript.sh` perquè assigni la IP i executi la tasca del servei.

![Prova manual del script](image-3.png)

Pas 4: provem l'script manualment per verificar que funciona correctament abans d'activarlo com a servei.

![Configuració del servei](image-5.png)

Pas 5: definim el fitxer `manuscript.service` amb el nom del servei, l'usuari i la ruta de l'script.

![Servei creat i arxiu de configuració](image-4.png)

Pas 6: creem el servei a `/etc/systemd/system/manuscript.service` i el deixem preparat per gestionar-lo amb `systemctl`.

![Habilitació del servei](image-6.png)

Pas 7: recarreguem el daemon de systemd i habilitem el servei perquè s'iniciï automàticament.

![Target per defecte](image-7.png)

Pas 8: establim `manu.target` com a target per defecte perquè el servei es carregui en arrencar.

![Comprovació de l'estat del servei](image-8.png)

Pas 9: comprovem amb `systemctl status` que `manuscript.service` està actiu i en execució.