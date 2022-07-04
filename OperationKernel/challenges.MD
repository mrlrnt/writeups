## Sommaire
[**Forensic**](#forensic)  
   [Research paper](#research-paper)  
[**Web**](#web)  
   [Research paper blog](#research-paper-blog)  
[**Crypto**](#crypto)  
   [Scytale](#scytale)  
[**Steganography**](#steganography)  
   [Audiospectre](#audiospectre)  
    [Takazume](#takazume)  
[**Reverse**](#reverse)  
   [Cryptolocker](#cryptolocker)


## Challenges
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

### Steganography 
#### Audiospectre
Le fichier lié est un .wav indéchiffrable à l'oreille humaine. Le nom du fichier AudioSpectre.wav donne déjà un indice sur la nature de la résolution de la problématique, ainsi il est possible d'utiliser [un outil de création de spectrogramme à partir d'un fichier audio](https://convert.ing-now.com/audio-spectrogram-creator/). À partir de la, il convient de charger le fichier "AudioSpectre.wav" préalablement téléchargé, configuré l'image de sortie si souhaité, l'image est alors générée et le flag à récupérer : 

![2022-07-03 19_57_30-Audio Spectrogram Creator - Download _ convert ing-now com](https://user-images.githubusercontent.com/93680908/177051726-db3f6479-af7e-41ba-9ad5-a681dd781d18.png)

#### Takazume 
Il suffit de zoomer sur une zone de l'image HD téléchargée pour découvrir le flag ... ou une liste d'ingrédients pour faire des crêpes selon. 

![2022-07-03 20_20_12-Takazume png ‎- Photos](https://user-images.githubusercontent.com/93680908/177052413-6592fdc1-bc03-430b-a173-25b02f14ffaa.png)

### Reverse
#### Cryptolocker 
Le fichier source est au [format ELF - Executable and Linkable Format](https://fr.wikipedia.org/wiki/Executable_and_Linkable_Format). En le lancant via terminal, on obtient : 

![2022-07-04 21_38_54-Kali-Linux-2021 3-vbox-amd64  En fonction  - Oracle VM VirtualBox](https://user-images.githubusercontent.com/93680908/177209862-9a6aadf5-aaed-4d75-a924-afc48c4b5ad7.png)

Le format ressemble à un codage en Base 64. L'outil [Cyberchef](https://gchq.github.io/CyberChef/) permet de le décoder (et de détecter aussi le format avec l'option "Magic"), cela nous donne une URL.

![2022-07-04 22_21_33-Window](https://user-images.githubusercontent.com/93680908/177213149-faf09841-a459-4e06-b542-80e0205aae7a.png)

L'URL mène vers une page de login avec username & password. 

![2022-07-04 21_30_05-Window](https://user-images.githubusercontent.com/93680908/177210714-0cf4dd2c-807f-4621-8dc4-d8549a58b757.png)

Rien de plus sur la page. Afin d'obtenir plus de données, tentative avec la commande **strings** permettant d'extraire les chaines de caractères imprimables sur le fichier Crypolocker initial. On voit ici un élément notable au niveau de "Enter the key to ecrypt files". Même procédure que précédemment, en passant à [Cyberchef](https://gchq.github.io/CyberChef/) l'élément on obtient l'username recherché et le mot de passe.

![2022-07-04 21_26_55-Window](https://user-images.githubusercontent.com/93680908/177215280-82585e97-d4c5-438a-a225-53a83c1ebeb6.png)

Après le login, le flag est à retrouver dans le partie "About" du site : 

![2022-07-04 21_52_59-Window](https://user-images.githubusercontent.com/93680908/177210849-2656ce9f-1d09-44be-9010-e457b822a9c3.png)


