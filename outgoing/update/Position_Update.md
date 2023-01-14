## Player Position

The method onUpdateWalkingPlayer has two checks to decide which of the 4 Position Update packets it will send.

```java
boolean positionFlag = deltaX * deltaX + deltaY * deltaY + deltaZ * deltaZ > 9.0E-4D || this.positionUpdateTicks >= 20;
            boolean rotationFlag = deltaYaw != 0.0D || deltaPitch != 0.0D;
```
If positionFlag is true it will updatePosition
If rotationFlag is true it will update Rotation

Bad Packet A: Updating position when positionFlag is false, which to the server is when you have not moved but update position

Bad Packet B: Updating Rotation when rotationFlag is false, which to the server is when you have not moved your head but update rotation.

Many new devs may come across the issue where their client is doing both of these, and this is because they improperly hook their EventPositionUpdate.

Many forget to change the lastReported<positionDataType> = this.<positionDataType> to lastReported<positionDataType>= event.get<positionDataType>
