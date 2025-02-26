# Bases-cryptographie
1) Définition :
Permet de transformer un message clair en un message chiffré grâce à un algorythme de chiffrement.

2) Permet de fournir 4 éléments :
Confidentialité : S'assurer que le message est lu uniquement par la personne autorisée.
Intégrité : S'assurer que le message n'a pas été modifié par une personne non autorisée.
Authenticité : S'assurer que le message a bien été envoyé par son auteur.
Non répudiation : L'auteur du message ne peut pas refuser qu'il a envoyé un message (sauf si la clé a été compromise).
3) Chiffrement symétrique :
Différents algo :

AES : Advanced Encryption Standard
DES : Data Encryption
4) Chiffrement asymétrique :
2 clés sont utilisées, une clé publique et une clé privée. Les 2 clées sonr liées.
Différents algo :

RSA : Rivest Shamir Adleman
ECC : Elyptic Curve Cryptography
DSA : Digital Signature Algorythm
DIFFIE-HELLEMAN :
5) Fonction de hashage :
Utilisée pour vérifier intégrité d'un fichier ou pour la signature numérique. L'algorythme de hashage prend le message en clair et génère en sortie une empreinte numérique (donnée unique)
Empreinte numérique = Hash.
Un hashage est irréversible.
Une bonne fonction de hashage ne doit pas générer de collision.

Différents algo :

MD5 (plus utilisé car vulnérable)
SHA-1 (plus utilisé car vulnérable)
SHA-256
SHA-3
SHA-512
Vérifier Hash en lignes de commande sous Windows
certutil -hashfile logiciel.exe sha512 : Cette commande avec ce paramètre suivi du nom du logiciel, puis l'algorythme de hashage va nous donner le hash du logiciel. Il suffira de comparer avec le hash fourni par l'éditeur sur le site officiel pour vérifier l'intégrité de ce qui a été téléchargé.
