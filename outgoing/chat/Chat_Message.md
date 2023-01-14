## Chat Message
	
Any chat message with a length > 100 is impossible in vanilla, however a client can bypass it and send one with a greater length and vanilla servers do not trim it.

Code preventing it from happening in vanilla

```java
public C01PacketChatMessage(String messageIn)
    {
        if (messageIn.length() > 100)
        {
            messageIn = messageIn.substring(0, 100);
        }
```
But there is no code preventing it from surpassing > 100 in the method processChatMessage.
