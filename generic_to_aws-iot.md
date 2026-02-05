## Overview
The `Publish to AWS IoT Core` template imports an instance of the AWS IoT Core service and sample triggers that listen for a generic event to send to AWS IoT Core.

You must run `Setup AWS IoT Core` before importing this template.  Without it your devices will not be able to connect.

## Triggers

### AWS IoT Core - Publish MQTT
This trigger listens on a generic event specified during import and sends the event details to AWS IoT Core on a topic of uplink/<thingName>.

### AWS IoT Core - Publish Device Shadow
This trigger listens on a generic event specified during import and sends the event details to AWS IoT Core as a device shadow update for a named shadow called "data".

### AWS IoT Core - Receive publish
This trigger receives MQTT publishes on downlink/<thingName> and generates a generic event for further processing.

### AWS IoT Core - Handle Job
This trigger receives AWS IoT Core jobs, it will update the job, and after 1 second it will complete the job.

## Additional Resources
- AWS IoT Core Service Documentation: <https://docs.tartabit.com/en/Topics/AWS-IoT-Core>