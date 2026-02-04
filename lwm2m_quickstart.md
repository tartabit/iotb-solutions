## Overview
The `LWM2M Quickstart` template is the foundation for integrating 
LWM2M devices to the IoT Bridge.  This template provides the basic building blocks to interact with LWM2M devices.

## Import Parameters
- *LWM2M Lifetime*: If the device bootstraps to the server, it will be configured with this lifetime.

## LWM2M Service
Defines a LWM2M Service instance to enable devices to connect.

## Triggers

### LWM2M - On Registration
This trigger fires when a device registers to the server.  It will read all available instances from the device, and 
attempt to observe any of the common IPSO objects for changes.  This is useful for initial trials, but you will want
to customize this trigger to suit your needs.

### LWM2M - On Update
This trigger reads a subset of data when an update occurs, this trigger can be modified depending on what information
you may wish to refresh when the device sends an update.

### LWM2M - Flatten device data
The registration and update triggers will cause the device to start emitting `lwm2m-data` events when data is received
from the device.  The standard data format is an object that has multiple levels of depth.  If you start this trigger
if will emit a generic `lwm2m-simple-data` event that flattens the data tree into a single level with "_" between each level.

## Next Steps
After importing this template, you will need to onboard your first endpoints.  You can do this from the LWM2M device 
onboarding solution templates, or by defining an endpoint manually.

## Additional Resources
LWM2M Service Documentation: <https://docs.tartabit.com/en/Topics/LWM2M>