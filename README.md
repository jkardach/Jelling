# Jelling

## Jelling application overview
This application uses some unique Bluetooth hardware called ibeacons. An ibeacon can be programed and then discovered by an application, which can then give a rough indication of how close to the ibeacon the user is, and when they have arrived.

The idea is to have Harald Bluetooth's family represented by ibeacons (different ibeacon for each family member). The iBeacons run off a coincell battery and then hidden around the museum. The application will then scan for the beacons and lead the user to the ibeacon.  Once they get close enough, the application will display arrived and the user will be able to see a picture of the ibeacon as well as get a wikipedia write-up of the king.

## Jelling iBeacon App prototype
This application uses ibeacons that have been programmed with the following:
uuid = "DCB34729-D83C-4147-BB97-E1CA9067A7E2" - unique UUID for Jelling finding harald application
major = 1 (Jelling Krongs Museum)
minor = 1 (Harald Bluetooth)
minor = 2 (Sven Forkbeard)
minor = 3 (Gorm the Old)
minor = 4 (Cnut the Great)

The application uses the CoreLocation framework to discover these beacons, and then gives an indication of how close the beacon is to the user. The application will scan for iBeacons which have the Jelling UUID and a major number of 1. It then uses the minor number to provide information no the Jelling King.

The struct "Beacon" is used to identify the beacon. It contains the uuid, major and minor numbers, the actual beacon (CLBeacon), a unique id, some boolean property to identify is the ibeacon is being identified or not, and if the beacon has been found.

It has a couple of calculated properties which provide the name of the king found, their relationship to King Harald, and a link to a wiki-page, and a url to a picture of the king.

the BeaconDetector class uses the CoreLocation frame work to detect and range the ibeacons. Sadly there seems to be bug in the framework and only discovers a single iBeacon at a time. It appears that with iOS17 release they have redone ibeacon framework to use a new MLMonitor class, however I have not figured out how to use this framework yet.

##
