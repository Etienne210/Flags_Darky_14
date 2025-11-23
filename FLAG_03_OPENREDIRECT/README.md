FLAG 03 — Open Redirect

En naviguant sur le site, je remarque une page suspecte :
?page=redirect

Elle contient un paramètre :
site=

Quand je teste plusieurs valeurs :
?page=redirect&site=https://google.com

Je suis redirigé vers google.

Le paramètre site n'est pas filtré, ce qui est une vulnérabilité Open Redirect.

Sur certains challenges, les flags apparaissent quand on déclenche des comportements prévus. J'utilise donc un site bidon pour voir si le serveur réagit :
http://192.168.1.47/?page=redirect&site=https://www.lebidonfrancais.com/

Le serveur n'est pas une redirection normal.

<img width="1790" height="762" alt="image" src="https://github.com/user-attachments/assets/e82a8e76-d4df-4a4b-9b08-059b8a4b950b" />

Good Job Here is the flag : b9e775a0291fed784a2d9680fcfad7edd6b8cdf87648da647aaf4bba288bcab3
