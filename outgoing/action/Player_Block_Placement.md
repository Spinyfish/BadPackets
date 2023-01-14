## Player Block Placement

### Bad Packet A: HitVec

Each value of the hitVec can not be greater than 1 and less than 0 because like the hitvec in Interact it is based off the hitbox of the target, and in this scenario it is a block.

But this isnt the end, because sides, they exist, a side like West which is Negative X the X value will always be equal to 1, and East it will always be 0, this is also true for Z and Y in there respective scenarios.

### Bad Packet B: Facing aka placedDirection

When sent, the Facing is converted to an integer representing its direction, Down being 0, Up being 1, etc

The only valid values are 0-5 and 255, 255 being the direction when it is an item interaction.

### Bad Packet C: BlockPos

A Block Position being anything but Origin (-1, -1, -1) when the facing is 255.
