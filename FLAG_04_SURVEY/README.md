FLAG 04 – Survey (Injection)

Sur la page Survey, chaque ligne contient un formulaire permettant de donner une note.

En inspectant le code HTML avec le navigateur, on voit des choses intéressantes :
<form action="#" method="post">
    <input type="hidden" name="sujet" value="1">
    <select name="valeur" onChange="javascript:this.form.submit();">

Cela signifie que le formulaire utilise le POST.

Il envoie deux champs :
- sujet (l'ID)
- valeur (la note envoyée)
Le formulaire se soumet automatiquement au changement du SELECT.

Nous pouvons donc faire notre propre requête POST, en envoyant n'importe quelle valeur.

On utilise curl pour reproduire la requête attendu :
curl -s -X POST "http://192.168.1.47/index.php?page=survey" \
  -d "sujet=1&valeur=9999"

<img width="1596" height="577" alt="image" src="https://github.com/user-attachments/assets/32975380-2b6a-4a8b-84f3-b6020f0dc85e" />




The flag is : 03a944b434d5baff05f46c4bede5792551a2595574bcafc9a6e25f67c382ccaa
