Flag 5 – Web crawling sur /.hidden

En visitant http://192.168.1.47/robots.txt, on voit :

User-agent: *
Disallow: /whatever
Disallow: /.hidden

On recupère le contenu :
wget -r --no-parent --execute robots=off http://192.168.1.47/.hidden/

On rentre :
cd 192.168.1.47/.hidden


Tous les sous dossiers contiennent des fichiers README avec du texte en clair.
On les parcourt tous et on filtre sur le mot "flag" :
find . -type f -iname "README*" -exec cat {} + | grep -i flag

<img width="651" height="58" alt="image" src="https://github.com/user-attachments/assets/6d233e77-40aa-4c73-a599-443754f1b8fe" />


Hey, here is your flag : d5eec3ec36cf80dce44a896f961c1831a05526ec215693c8f2c39543497d4466
