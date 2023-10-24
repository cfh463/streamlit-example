#About Device Tracker
Device Tracker is an application from Zebra Technologies that provides a way for gricery store owners to locate misplaced devices that their employees are using. The devices will be "checked out" by an employee/user and every minute it will send a status update to our database. When the device is "checked in", it is considered returned and not in use (the user field will be blank).

Inside the events.csv file you will see a snapshot of the database that describes a period of events that were captured on 10/24/2023 08:40:00 

Consider the following to be indicative of devices at risk of being misplaced:
* Last Updated is longer than 3 minutes from the current time
* Last Movement is 15 minutes or greater
* Battery Level is less than 30

Consider the following to be indicative of devices that are misplaced
* The "Is Misplaced" field is set to true
* Last Updated is longer than 30 minutes from the current time
* Last Movement is 60 minutes or greater

Consider the following to be indicative of devices that are not at risk of being misplaced
* Charging is true
* Battery Level is greater than 80 and Last Movement is less than 10 minutes

The table is has the following columns:

Device ID : this is the unique id of the device that is being used by the worker

Last Updated: this is the date and time of the last update that our server received from the device. the devices are supposed to send an update every minute. If updates are missing for more than 3 minutes than the device is considered to be "misplaced"

Zone: This is the name of the area of the building that the device was being used

Is Misplaced; this is true or false showing if a worker marked the device as being misplaced

Battery Level: this is a scale of 0-100 to indicate the current level of battery. if the battery is less than 30 percent then we consider this device being "at risk" of being misplaced.

Charging: This will be true or false indicating if the device is plugged in. if it is plugged in, then it is at zero risk of being misplaced and we know that it will be in the "back room" zone

Last Movement: This is the date and time of the last time the device was moving. If the device has not moved for 15 minutes then the device is cosidered to be "at risk" of being misplaced

Last Use: this is the date and time of the last time the device was being used by a worker. If the device is being used in the last 10 minutes then it is at "low risk' of being misplaced

User: this is the name of the worker that is using the device

Objects Seen: these are objects that have been detected by the camera on the device. It can be indicative of where the device is.