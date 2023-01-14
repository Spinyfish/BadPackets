##Player Action

Player Action has 6 states.

```java
public static enum Action
    {
        START_DESTROY_BLOCK,
        ABORT_DESTROY_BLOCK,
        STOP_DESTROY_BLOCK,
        DROP_ALL_ITEMS,
        DROP_ITEM,
        RELEASE_USE_ITEM;
    }
```

Bad Packet A: Any scenario in which the facing is incorrect.

Bad Packet B: When the drop item facing is anything but DOWN and the BlockPos is anything but ORIGIN

Bad Packet C: Any scenario in which the player has already aborted mining and sends an Abort.

Bad Packet D: Continuing to destroy block after it has broken, however this can false very easily.
