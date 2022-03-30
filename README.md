# Intra Satellite Software

This repository contains the **mother board (MB)** software and example code for the **daughter boards (DB)**.

> Each 3U satellites contains a number (maximum 30) circuits, each 10x10x1 cm stacked to form a 10x10x30 cm (3U) CubeSat. Each of these circuits are reffered to as daughter boards or DB. They all comunicate downlink data and get power from one mother board or MB.

## Power
Each DB can spend up to 250mA (peek). A resetable fuse will break the power should it exceed the allowed allocation.
Both 5v and 3.3v will be supplied.
Further specification TBD with bluShift.

For redundancy there are two power busses running on each side of the DB, and each power bus is physically connected twice to the DB, i.e. each DB is wired 4 times to the DB, that is 4x 3.3v and 4x 5v!

# Communication
The DB will communicate with the MB via a CAN-bus. See more below. 

For redundancy there are two CAN-busses running on each side of the DB, and each CAN-bus is physically connected twice to the DB, i.e. each DB is wired 4 times to the DB.

The `db.ino` is the example code for communicating to the MB. The `mb.ino` is the current version of the MB code, and will be continousely updated.

## ISO Model
The communication follows this ISO Model
|Layer|Layer Name|Standard|Library|Notes|
|:-:|--|--|--|--|
|7| Application |	
|6|	Presentation|	MessagePack|ArduinoJSON|https://msgpack.org|
|5|	Session     |
|4|	Transport   |	ISO-TP|iso-tp|ISO 15765-2|
|3|	Network     |
|2|	Data        | CAN bus| CAN2.0|
|1|	Physical    |
