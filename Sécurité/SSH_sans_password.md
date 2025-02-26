# SSH_sans_password

## UBUNTU -> UBUNTU

ON EXÉCUTE LE TERMINAL SUR LES DEUX MACHINES

- On vérifie qu'on a OpenSSH serveur sur le client :  
  `sshd -V` (*Pour vérifier si installé, sinon installer avec :*)  
  `sudo apt install openssh-server`  
  `sshd -V` (*Pour vérifier*)  
  `systemctl status ssh` (*Si pas activé :*)  
  `systemctl enable ssh` (*Active le service au démarrage*)  
  `systemctl status ssh`  
  `systemctl status sshd` (*Si tout est bon, tout est vert et "enabled"*)  

- On met les machines sur le même réseau (VM en pont) et on redémarre le service :  
  `sudo systemctl restart Networking` (ou `NetworkManager`)  
  `ip a` (*Pour récupérer l'IP*)  
  `ping (adresse ip)` (*On vérifie si la communication est ok*)  

- On se connecte depuis le client pour vérifier que tout fonctionne :  
  `ssh serveur@ip` (*On confirme et on entre le mot de passe*)  
  `exit`  

- On crée une clé SSH :  
  `ssh-keygen -t ecdsa`  
  `yes`  
  `passphrase non obligatoire`  
  `ls -a` (*Pour vérifier le fichier .ssh => lieu de stockage de la clé SSH*)  

- On déploie la clé SSH publique depuis le client vers le serveur :  
  `ssh-copy-id -i /home/user/.ssh/id_ecdsa.pub client@ip`  
  `On entre le mot de passe` (*Si tout est ok, on se connecte*)  

- On vérifie que la clé correspond sur les deux machines :  
  `cat /home/wcs/.ssh/id_ecdsa.pub` (*Sur le client*)  
  `cat .ssh/authorized_keys` (*Sur le serveur*)  

- On se connecte sans mot de passe :  
  `ssh serveur@ip` (*Si tout est ok, aucun mot de passe demandé*)  

---

## WINDOWS -> WINDOWS

ON EXÉCUTE POWERSHELL EN ADMIN SUR LES DEUX MACHINES = toujours un mot de passe sur le client pour SSH sur Windows

- On vérifie les services du client :  
  `get-service ssh-agent`  
-Si installé mais pas activé :
Start-Service -Name ssh-agent  

- On active la fonctionnalité client-SSH sur les machines :  
  => Système => Fonctionnalités facultatives = vérifier la présence du client SSH
- On vérifie la fonctionnalité serveur-SSH sur le serveur :  
  => Système... => Ajouter une fonctionnalité = serveur OpenSSH  
Ou en PowerShell, pour savoir si le serveur et le client sont présents :  
``Get-WindowsCapability -Online -Name *ssh*``  
Nous aurons les noms exacts ( ligne "Name") de ce qu'il faut installer dans le cas où ils ne seraient pas présents.

Pour installer serveur en PowerShell si pas présent :  
``Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0``  

- On vérifie le service sur le serveur avec :  
  `get-service sshd` (*Si pas activé :*)  
  `get-service sshd | Set-Service -StartupType automatic` (*Puis on démarre :*)  
  `Restart-Service sshd`  
  `get-service sshd` (*Si tout est ok, le service est en "running"*)  

- On met les machines sur le même réseau IP (VM en pont) :  
  `ipconfig` (*On récupère l'IP du serveur*)  

- On teste la connexion SSH depuis le client :  
  `ssh client@ip powershell` (*Si tout est bon, on entre le mot de passe => on précise PowerShell*)  
  `exit`  

- Sur le client, on crée la clé SSH :  
  `ssh-keygen -t ecdsa`  
  (*On va vérifier où est la clé et si tout est ok :*)  
  `Set-Location c:\Users\client\.ssh\`  
  `get ChildItem` (*On vérifie la clé*)  

- On déploie la clé SSH publique depuis le client vers le serveur :  
  `get-content -path .\.ssh\id_ecdsa.pub` (*On copie la clé*)  
  `ssh server@ip` (*On se connecte en SSH au serveur*)  
  `add-content -path .ssh\authorized_keys -value "la clé"` (*On vérifie dans le fichier du serveur*)  

- On va dans le répertoire Program Data sur le serveur :  
  `C:\ProgramData\ssh\sshd_config` (*élément masqué dans affichage classique*)  
  `On commente la ligne MATCH group administrator` (*On sauvegarde et on redémarre le service :*)  
  `Restart-Service sshd`  

- On se connecte en SSH et normalement pas de mot de passe demandé :  
  `ssh client@ip`  

---

## UBUNTU -> WINDOWS

ON EXÉCUTE LE TERMINAL ET POWERSHELL EN ADMIN SUR LES MACHINES RESPECTIVES  
=> Même vérification pour OpenSSH que précédemment

- On vérifie si on peut se connecter en SSH :  
  `ssh server@ip powershell` (*Si tout est ok, on quitte*)  
  `exit`  

- On déploie la clé SSH depuis Ubuntu vers Windows :  
  `cat .ssh/id_ecdsa.pub` (*On copie la clé*)  
  `ssh server@ip` (*On se connecte en SSH au client*)  
  `add-content -path .ssh\authorized_keys -value "la clé"` (*On colle la clé*)  

- On va dans Program Data sur le client :  
  `C:\ProgramData\ssh\sshd_config` (*Élément masqué dans affichage classique*)  
  `On commente la ligne MATCH group administrator` (*On sauvegarde et on redémarre le service :*)  
  `Restart-Service sshd`  

- On se connecte en SSH et normalement pas de mot de passe demandé :  
  `ssh server@ip`  

---

## WINDOWS -> UBUNTU

ON EXÉCUTE LE TERMINAL ET POWERSHELL EN ADMIN SUR LES MACHINES RESPECTIVES  
=> Même vérification pour OpenSSH que précédemment

- On vérifie si on peut se connecter en SSH :  
  `ssh server@ip` (*Si tout est ok, on quitte*)  
  `exit`  

- On déploie la clé SSH depuis Windows vers Ubuntu :  
  `get-content -path .\.ssh\id_ecdsa.pub` (*On copie la clé*)  
  `ssh server@ip` (*On se connecte en SSH au serveur*)  
  `nano .ssh/authorized_keys` (*On colle la clé*)  

- On se connecte en SSH et normalement pas de mot de passe demandé :  
  `ssh server@ip`
