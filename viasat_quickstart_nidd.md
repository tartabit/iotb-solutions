## Overview
The `Viasat NIDD Quickstart` template provides a starting point for integrating data from the Viasat NTN RAN into the IoT Bridge.
You can easily receive and send messages via the NIDD API for quick, advanced solution development.

If you with to start with Viasat's NTN network using UDP, use the `UDP ASCII Delimited Quickstart` template.

Note, this template is developed against an early version of Viasat's NTN network, and is subject to change.

## Import Parameters
The parameters described below are available from the Viasat Portal.  After logging in, navigate to `APNs` and click the `info` bubble next to your APN.
- *APN Name*: The name of your custom APN.
- *API Key*: The API Key for your APN.
- *CB API Key*: The callback API key for your APN.

## Triggers

### Viasat - Receive message
This trigger receives messages from Viasat's NIDD API and generates `viasat-received` events.  By default it can handle text, and JSON messaging.
Edit the trigger to parse binary or CBOR data or implement any other required decoding.

### Viasat - Send downlink
This trigger serves two purposes.  First, it listens on a generic event `viasat-send-downlink` and will send any message received to the device.
Second, it registers an `Endpoint Action` to send a downlink from the endpoints Actions menu.

## Next Steps
After importing this template, you will have one endpoint defined, and you can test sending traffic.

## Additional Resources
- Getting started with ASCII delimited payloads: <https://docs.tartabit.com/en/Topics/Trigger-ASCII-Parsing>