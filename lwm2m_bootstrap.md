## Overview
The `LWM2M Bootstrap Examples` template provides several triggers demonstrating how to perform dynamic bootstrapping
of LWM2M devices via the IoT Bridge.  Three examples are provided to show a wide range of use cases.

Important note, only one of these triggers should be started at any time, the first trigger that processes a `lwm2m-bootstrap` 
event to complete will configure the device, others will be ignored.

## Triggers

### LWM2M Bootstrap to IOTB
This trigger is started by default, and will bootstrap any device that connects to your account to this IoT Bridge
with DTLS.

### LWM2M Bootstrap to Leshan with DTLS
This trigger is stopped by default.  It will bootstrap the device to the demo Leshan server using DTLS, 
you will have to configure the identity and pre-shared key to match what you have configured in Leshan.  The purpose
of this example is to show that you can bootstrap to IoT Bridge, but register to a foreign server.

### LWM2M Bootstrap to IOTB & Leshan
This trigger is stopped by default.  It will bootstrap the device to both the IoT Bridge and Leshan, this shows the 
power of multi-server bootstrapping that can be easily configured using the IoT Bridge.

## Additional Resources
LWM2M Service Documentation: <https://docs.tartabit.com/en/Topics/LWM2M>