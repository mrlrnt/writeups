### Forensic
#### Research paper 
Pour retrouver le nom du scientifique à partir du .pdf à disposition : dans les propriétés du PDF, on obtient au niveau d'"Application" une URL : 

  ![2022-06-27 23_19_40-Propriétés du document](https://user-images.githubusercontent.com/93680908/176037482-06916b9d-d070-48ff-b19b-dadc3a2dc503.png)
  
  En accédant à l'URL depuis son navigateur, on obtient le nom et prénom du scientifique à renseigner.
  
### Web 
#### Research paper blog 
À partir du site retrouvé dans le challenge ["Research paper"](#research-paper), on cherche un fichier caché sur le site pour localiser l'auteur. Première idée : les liens de réseaux sociaux, ceux-ci ne sont pas actifs. Ensuite on observe que les articles sont dans /papers & /maths, la aussi en ouvrant ces répertoires à la raçine rien à voir. 
Tentative alors avec [Dirb](https://www.kali.org/tools/dirb/) de scanner l’arborescence, la encore RAS. 

La solution viendra via les outils de développement du navigateur, onglet Réseau. En naviguant sur un papier, on remarque que chaque fichier est accessible via un ID suivant son répertoire, par exemple " Hierarchical Databases Considered Harmful" est accessible via /maths/12. 

![2022-06-27 23_40_00-PaperBlog](https://user-images.githubusercontent.com/93680908/176040214-3836fdcd-7b5c-4beb-98e2-911219b5250c.png)

En testant une ID proche des IDs des articles, on parvient au flag demandé. 

### Crypto 
#### Scytale
Le message suivant est à déchiffrer "Bj.lsC1_T!iolatKsSA.eueg.{_PA.né..HT14}..efeAhSR..". Le titre du challenge facilite l'identification du type de chiffrement. Il est ensuite possible d'utiliser par exemple https://www.dcode.fr/chiffre-scytale pour obtenir le flag. 
