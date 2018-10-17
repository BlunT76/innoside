### [POC Reseau P2P Mesh]

## [Sujet]
Innoside souhaite dans le cadre du déploiement de son application hybride de réalité augmentée (iOS & Android) avec interface full web et backend en symphony effectuer une veille suivi d'un POC sur les plugin-apache-cordova compatibles avec la création de réseau BLE (Bluetooth Low Energy) et Wifi pour créer des réseaux Peer-2-Peer Mesh.

## [Possibilités et Avantages]
L'application google nearby connection permet d'effectuer un appareillage entre deux ou plusieurs smartphones, il est théoriquement possible d'appareiller 65 000 appareils entre eux via Bluetooth, BLE ou Wifi direct.
![Source]()

L'intêret de cette technologie et ce que nous avons exploré : 
- Transfer de fichiers en mode Hors-Ligne, il est possible de partager des photos, vidéos, ou tout autres types de données, rapidement et sans connection à un réseau GSM ou WiFi privé. 

Nearby Connections offre la possibilité d'emettre, de trouver des apareils et de les connecter entre eux grâce à un réseau peer-to-peer entièrement hors-ligne, le choix du réseau se fait automatiquement au lancement de l'application, quand l'utilisateur quite l'application les paramètres initiaux sont rétablis.

L'avantage de cette solution offre un échange entre les appareils en utilisant une grande bande passante, une latence faible, un taux de réponse immédiat entre plusieurs appareils (Les tests lors du POC nous on permis de confirmer cela pour trois appareils), mais aussi une encryption totale des données afin d'effectuer des échanges sécurisés. 

L'envoi de payloads, il existe 3 types de payloads, les connections fonctionnent en Full-dupex, ce qui veut dire que si un appareil est connecté à un autre, les deux peuvent communiquer simultanement :

- BYTES (Byte arrays de 32k)
- FILE (Pas de restriction au niveau du poids)
- STREAM (Audio)

![Les Types de payloads](https://developers.google.com/nearby/connections/android/exchange-data#types_of_payloads)

Schéma de fonctionnement de la solution :


## [Problèmatiques]
L'api de messagerie - Google Nearby Messages - permet d'échanger des messages en temps réel entre deux apareils. Cependant, il est important de prendre en compte que la solution n'offre pas d'encryptage, donc le transit de données sensibles est a éviter.

Après avoir testé l'application et ses limitations, nous avons donc écarté cette option pour le moment, un plugin Cordova est disponible mais peu de chances qu'il soit maintenu par celui qui l'a réalisé, nous sommes donc tournés vers Google Nearby Connections qui répond parfaitement à la demande.

Il n'existe pas à ce jour de plugin Cordova libre d'utilisation disposant de la technologie Google Nearby Connections, suite aux recherches sur un éventuel plugin nous nous sommes donc orientés vers React Native qui dispose d'un plugin fonctionnel sous cette technologie.


### [Limitations de Nearby Connections] 
Distances de détéction des appareils :
- 100m-80m environ pour le WiFi.
- 30m environ pour le Bluetooth, BLE.
- 1.5m environ pour les Ultrasons.

Pour plus d'informations, voir ressources.

## [Ressources about Nearby Connections]
- ![Google Nearby Github](https://github.com/googlesamples/android-nearby/tree/master/connections)
- ![Developers nearby](https://developers.google.com/nearby/connections/overview)
- ![Cordova pluggin](https://github.com/hahahannes/cordova-plugin-google-nearby)
- ![Nearby Connections APIを使ってみる - Qiita](https://qiita.com/niusounds/items/ecc759c51da8e1f1e8a0#mpayloadcallback)
- ![Exploring Nearby Connections 2.0 – Caren Chang – Medium](https://medium.com/@calren24/exploring-nearby-connections-2-0-bd0681ac8e64)
- ![Google Play Services: Using the Nearby Connections API](https://code.tutsplus.com/tutorials/google-play-services-using-the-nearby-connections-api--cms-24534)
- ![Connect Android Things to a Smartphone With Nearby Connections 2.0](https://code.tutsplus.com/tutorials/connect-android-things-to-a-smartphone-with-nearby-connections-20--cms-28269)
- ![Google Nearby Connections](https://zhuanlan.zhihu.com/p/28548310)

## [BLE - Bluetooth low energy]
- ![Communicating with Bluetooth Low Energy Devices in Cordova — SitePoint](https://www.sitepoint.com/communicating-with-bluetooth-low-energy-devices-in-cordova/)
- ![roborags/BLE_Mesh_Network](https://github.com/roborags/BLE_Mesh_Network)
- ![Bluetooth’s third trick – Mesh networking for IoT](http://iotdesign.embedded-computing.com/articles/bluetooths-third-trick-mesh-networking-for-iot/)
- ![Bluetooth Smart,Bluetooth Low Energy tutorial,BLE tutorial](https://www.rfwireless-world.com/Tutorials/Bluetooth-Smart-Bluetooth-Low-Energy-BLE-tutorial.html)
- ![Peer-to-peer network via Bluetooth on Android](http://profandroid.com/network/bluetooth/peer-to-peer-network.html)
- ![EvoThings Cordova plugin](https://github.com/evothings/cordova-ble)
- ![PDF about Wireless BLEmesh Network](http://eeca2.sogang.ac.kr/publications/international/BLEmesh_A%20Wireless%20Mesh%20Network%20Protocol%20for%20Bluetooth%20Low%20Energy%20Devices.pdf)

## [Offline first]
- ![Link ressources about offline apps](https://github.com/pazguille/offline-first)
