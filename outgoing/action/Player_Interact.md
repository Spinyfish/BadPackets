## Player Interact

Player Interact has three interaction states, two of the three types have restrictions.

```java
public static enum Action
    {
        INTERACT,
        ATTACK,
        INTERACT_AT;
    }
```

Bad Packet A: It is impossible to send an interaction with the action ATTACK whilst in spectator.

```java
if (this.currentGameType != WorldSettings.GameType.SPECTATOR)
        {
            playerIn.attackTargetEntityWithCurrentItem(targetEntity);
        }
```

Bad Packet B: It is impossible to send INTERACT_AT whilst not looking over an entity.

Bad Packet C: INTERACT_AT sends a Vec3 equivalent to the look over of the hitbox. For example if you are looking at the bottom right corner of a regular bipedal entity the Vec3 will look something like this
```java
x = 0.4
y = -0.1
z = -0.4
```
Or if it were the top left of it
```java
x = -0.4
y = 2.05
z = 0.4
```
Each hitVec coord is limited at min and max of the entities hitbox. So for example if x was equal to 5 on a zombie or a villager, that would be impossible in vanilla. However it can be achieved in a modified client.

