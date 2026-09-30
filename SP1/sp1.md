---
layout: default
title: "TASCA: .target personalitzat"
---

## Introducció

L’activitat consisteix en els següents punts:

- Crear un *target* de systemd personalitzat amb el nostre nom i fer-lo dependre d’un *target* existent.
- Configurar aquest nou *target* com a *target* per defecte del sistema.
- Associar-hi un servei (`.service`) que executi un *script* amb permisos de superusuari (*root*).
- Garantir que aquest servei s’iniciï correctament durant l’arrencada del sistema operatiu.

Pas 1: fem login com a root amb `sudo` per poder modificar la configuració del sistema.

![Captura d'autenticació com a root](image.png)

Pas 2: creem el target `manu.target` i li indiquem que s'ha d'executar després de `graphical.target`.

![Definició del target personalitzat](image-1.png)

Pas 3: preparem l'script `/usr/local/bin/manuscript.sh` perquè assigni la IP i executi la tasca del servei.

![Script d'inicialització](image-2.png)

Pas 4: provem l'script manualment per verificar que funciona correctament abans d'activarlo com a servei.

![Prova manual del script](image-3.png)

Pas 5: definim el fitxer `manuscript.service` amb el nom del servei, l'usuari i la ruta de l'script.

![Configuració del servei](image-5.png)

Pas 6: creem el servei a `/etc/systemd/system/manuscript.service` i el deixem preparat per gestionar-lo amb `systemctl`.

![Servei creat i arxiu de configuració](image-4.png)

Pas 7: recarreguem el daemon de systemd i habilitem el servei perquè s'iniciï automàticament.

![Habilitació del servei](image-6.png)

Pas 8: establim `manu.target` com a target per defecte perquè el servei es carregui en arrencar.

![Target per defecte](image-7.png)

Pas 9: comprovem que les dependències del `.target` estan correctament configurades i que el servei queda encadenat dins del target.

![Comprovació de les dependències del target](image-9.png)

Pas 10: comprovem amb `systemctl status` que `manuscript.service` està actiu i en execució.

![Comprovació de l'estat del servei](image-8.png)