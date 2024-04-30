### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?

The DevBoard handles received serial messages through interrupt methods. So when a serial message arrives to the microcontroller, then an interrupt is generated which means that the microcontroller will stop executing the task it's currently executing, then start an interrupt routine to handle the new, arriving data. This is different from the naive approach in that the microcontroller keeps checking if there are any incoming bytes which wastes energy and uses more CPU versus an interrupt.

### What does `detached_callback` do? What would happen if it wasn't used?

It's a way to avoid the UI to freeze in the event that there's code that takes too long to run.

### What does `LockedSerial` do? Why is it _necessary_?

Sometimes multiple threads will try to use the same serial port at the same time which can cause unpredictable behavior. LockedSerial makes sure that multiple threads are able to share the same resources at the same time. 
