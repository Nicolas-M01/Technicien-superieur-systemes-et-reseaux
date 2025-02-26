# L'Observateur d'Événements Windows  
---

* ### Crée une machine virtuelle Windows Server, installe le rôle DNS, puis crée une vue personnalisée dans l'Event Viewer pour surveiller spécifiquement les événements liés au service DNS et son état.  

:hash: **Régler les paramètres machine comme ceci :**  
![Capture d'écran 2024-12-16 142642](https://github.com/user-attachments/assets/89f49b09-2e15-4d0b-8a9d-9079e2cd4a07)  

:hash: **Installer le rôle DNS :**  
![Capture d'écran 2024-12-16 142448](https://github.com/user-attachments/assets/e84ac490-85c2-4f8b-b8e6-7f131fab3865)  

:hash: **Lancement d'Event Viewer :**  
Tapez **[Windows + R]**, puis dans la fenêtre exécuter, **[eventvwr]**, puis **[enter]**.  
La fenêtre va se lancer.  

:hash: **Créer vue personnalisée :**  
![Capture d'écran 2024-12-16 143029](https://github.com/user-attachments/assets/629023b3-c732-4f35-a804-98ec57b52297)  

* ### Configuration de la vue personnalisée :  
:hash: **1. Niveaux à surveiller :**  
Critical/Error/Warning/Information : dans la fenêtre ``Event level``  
:hash: **2. Sources d'événements à inclure :**  
``DNS-Server-Service: Pour les opérations du serveur DNS``  
``DNS Client Events: Pour les événements côté client``  
Cette partie est à rentrer dans `By source`/`Event logs` comme sur la photo :  

![Capture d'écran 2024-12-16 150802](https://github.com/user-attachments/assets/6a33079e-ef7b-4e86-9892-5305fb7805ba)

:hash: **3. Événements critiques (ID principaux) :**  
Événements critiques (ID principaux)  
``2``: Démarrage du serveur DNS  
``4``: Arrêt du serveur DNS  
``409``: Erreur de résolution de nom  
``501-502``: Échec de chargement de zone  
``6001-6002``: Problèmes de réplication DNS  

Ajouter les IDs dans la colonne des IDs.  
![Capture d'écran 2024-12-16 151325](https://github.com/user-attachments/assets/4fbb529f-3bae-486a-b184-c95f1671d278)  

:hash: **Attribuer nom et descriptif :**  

![Capture d'écran 2024-12-16 151525](https://github.com/user-attachments/assets/8315b509-62ee-4453-8c87-a346f832b667)  

:hash: **Exporter au format XML :**  
Clique droit sur le filtre créé. cliquer sur `Export Custom View...`, puis le nommer.  
![Capture d'écran 2024-12-16 152952](https://github.com/user-attachments/assets/ee598dbe-4ad5-4427-81b5-c478c1aa1613)  
