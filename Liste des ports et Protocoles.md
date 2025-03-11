# Liste-des-ports

|Numéro de port|Protocole|Description|TCP|UDP|
|:--:|:--:|:--:|:--:|:--:|
|20-21|FTP|File Transfer Protocol|X||
|22|SFTP|SSH File Transfer Protoco|X||
|22|SSH|Secure Shell niveau 7|X||
|25|SMTP|Simple Mail Transfer Protocol|X||
|53|DNS|Domain Name System|X|X|
|67(srv)/68(cli)|DHCP|Dynamic Host configuration Protocol||X|
|69|TFTP|Trivial File Transfer Protocol||X|
|80|http|Hypertext Transfer Protocol lvl7|X||
|110|POP3|Post Office Protocol v3|X||
|123|NTP|Network Time Protocol||X|
|143|IMAP|Internet Message Access Protocol|X||
|161/162|SNMP|Simple Network Management Protocol||X|
|389|LDAP|Lightweight Directory Access Protocol|X||
|443|HTTPS|HTTP via SSL/TLS|X||
|445|SMB|Server message block|X||
|465|SMTPS|SMTP via SSL/TLS|X||
|500|ISAKMP|Internet Security Association and Key Management Protocol||X|
|587|SMTP|SMTP Sécurisé (port utilisé au détriment de 465)|X||
|636|LDAPS|LDAP via SSL/TLS|X||
|993|IMAPS|IMAP via SSL/TLS|X||
|995|POP3S|POP3 via SSL/TLS|X|X|
|3389|RDP|Remote Desktop Protocol|X||
|5060|SIP|Session Initiation Protocol||X|
|5061|SIPS|SIP over TLS||X|
||RTP|Real-Time Transport Protocol||X|


ISAKMP : gère les clés de chiffrement pour le VPN IPSEC


## Processus de négociation TLS/SSL  
### Étape 1  
Chaque certificat TLS consiste en une paire de clés constituée d’une clé publique d’une part et d’une clé privée d’autre part. Ces clés sont importantes, car elles interagissent en coulisses lors des transactions sur le site web.

### Étape 2  
Chaque fois que vous visitez un site web, le serveur client et le navigateur web communiquent pour garantir une connexion TLS/SSL chiffrée.

### Étape 3  
Lorsqu’un navigateur web (ou client) entre en relation avec un site web sécurisé, le serveur partage son certificat TLS/SSL et sa clé publique avec le client pour établir une connexion chiffrée et créer une clé de session unique.

### Étape 4  
Le navigateur confirme alors qu’il reconnaît et fait confiance à l’émetteur du certificat TLS/SSL, ou l’autorité de certification, en l’occurrence DigiCert. Il vérifie également que le certificat TLS/SSL n’a ni expiré ni été révoqué, et qu’il peut donc être considéré comme fiable.

### Étape 5  
Le navigateur renvoie une clé de session symétrique que le serveur déchiffre à l’aide de sa clé privée. Le serveur renvoie alors un accusé de réception chiffré avec la clé de session pour démarrer la session chiffrée.

### Étape 6  
Le serveur et le navigateur chiffrent désormais toutes les données transmises avec la clé de session. Ils démarrent une session sécurisée qui protège la confidentialité et l’intégrité des messages, tout en assurant la sécurité du serveur.
