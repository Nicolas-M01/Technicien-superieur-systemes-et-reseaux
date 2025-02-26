# Cisco-Switch-Config  

`?` : Liste les commandes dans le mode actuel.  
`show` :  Liste les consultations possibles du mode actuel.  
`enable` : Monter en privilege. Petites commandes accessibles.  
`(#) configure` : Niveau de privilège > "enable".   
=> `configure terminal` : Mode configuration du terminal.  
`exit` : redescendre d'un niveau en privilèges.  
`end` : sort complètement des niveaux de privilèges.  
**`(#) show running-config` : Montre la Config en cours (ne marche pas en mode configuration).**  
`(#) show interfaces` : Peu pratique comme affichage.  
`(#) show interfaces | include Fas` : affiche les interfaces commençant par "Fas".  
**`(#) show ip interfaces brief` : toutes les interfaces physiques de la machine.**  

vlan1 configuré par défaut et contient tous les ports dessus.  

`(config #) hostname saiph` : renomme le switch en "saiph".  
`copy running-config startup-config` : Enregistre la config actuelle sur la config startup.  
`(config)# ip domain-name stars.local` : crée un nom de domaine.  
`(config)# interface fastethernet 0/1` : Paramètre l'interface fastethernet 0/1.  
`(config)# interface range fastethernet 0/1-24` : Paramètre les interfaces de fastethernet 0/1 à 0/24.  
`(config-if-range)# switchport mode access` : Envoi les ports en switchport mode access. Permet de ne pas être accessible de l'extérieur.  
`(config-if-range)#no switchport mode access` : Désactive le switchport mode access. Permet donc le mode trunk.  
`(config)# vlan 399` : crée le vlan 399.  
`(config-if-range)#switchport access vlan 399`: envoie toutes les interfaces sur le vlan 399.  
`(config-vlan)#name ADMIN` : nomme la vlan en "ADMIN".  
`(config)#no interface vlan 100` : Supprime le vlan 100.  
`(config)#int vlan 99` : Rentrer dans l'interface de vlan 99.  
`(config-if)#ip address 192.168.99.220 255.255.255.0` : Dans l'interface, permet de configurer son adresse.   
`(config-if)#ip default-gateway 192.168.99.254` : Permet d'attribuer une gateway.  

`(config)#interface fastEthernet 0/2` paramètrage de l'interface 0/2.  
`(config-if)#switchport access vlan 10`  Envoie l'interface dans le vlan10  
`(config-if)#switchport mode trunk` : Active le trunk  
