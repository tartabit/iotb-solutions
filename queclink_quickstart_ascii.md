## Overview
The `Queclink ASCII Quickstart` template provides a starting point for connecting Queclink devices that use the comma separated
ASCII protocol.  For newer devices that use the binary protocol, see the `Queclink Binary Quickstart` (coming soon).

This template uses one of the available shared UDP ports that enables rapid testing.  You may also request a dedicated UDP port.

Supported Queclink devices:
- GL33CG
- GL50MG
- GL51MG
- GL501
- GL502MG
- GL521MG
- GV53MG
- GV57MG
- GV57ARMG
- GV75
- GV500MAP

## Important Note
Queclink devices commonly break/change the formats in the protocol for each device model and each firmware version.  When connecting a device you may
get an error about a missing version, if so, it must be added to the `Queclink - ASCII - Core - Receiver` trigger.  We are constantly adding new devices
and versions, please inform support if you encounter an error.

## Import Parameters
- **UDP Port**: By default, port 9132 is used for Queclink devices, but you can use any port that is assigned to your account.

## UDP Service
The UDP service must be defined with a custom formatter that uses the `queclink` type, this allows the UDP server to extract
the device identifiers from the payloads.

## Triggers
### Queclink - ASCII - Core - ***
- The core triggers manage the basics of decoding the payloads and generating `queclink-data` events when they are received.
- It is recommended to configure your devices to require an SACK from the server, if you do not wish to use SACKs, then you may
stop the `Queclink - ASCII - Core - Send Ack` trigger to prevent sending ACKs back to the device.

### Queclink - ASCII - Command Handler - ***
- These triggers handle sending commands to Queclink devices.
- These triggers use custom forms in the example, this allows you to execute Actions on the endpoints from the expanision menu on the Endpoints list.
- Commands are sent using UDP when the command is issued, and will be stored and re-sent when the device next communicates.
- Commands can be sent via SMS if you implement sending the SMS in `Queclink - ASCII - Optional - SMS Handler`.
- Example how to send a command:
  - Requesting the ICCID: `exec.now('queclink-rto-command', {command:'cid'})`

### Queclink - ASCII - DM - ***
- These triggers handle device management tasks such as firmware and configuration updates, querying ICCID, and monitoring the battery.
- 
### Queclink - ASCII - Optional - ***
- These triggers enable optional features.
- `Queclink - ASCII - Optional - SMS Handler`: Implement sending an SMS in this trigger to send commands via SMS.
- `Queclink - ASCII - Optional - Message Sampler`: Start this trigger to collect sample messages for each firmware/command.
Useful when developing new devices and needing samples of each command for enhancing the decoders.
- `Queclink - ASCII - Optional - Geofence endpoints`: Submit locations to the geofence service to generate geofencing events.

## Next Steps
If you are using the shared Queclink port of 9120, you will need to create an endpoint with the key matching the IMEI of your
Queclink device.  You can also import the `Onboard Queclink Device` template to create your first endpoint.

If you are using a dedicated UDP port, then endpoints will automatically be created as devices report into the server.

### Connecting your device
Using the Queclink programming tool for your device, configure the device with the following parameters:
- Main Server IP: udp-us.tartabit.com (or your appropriate regional/private URL)
- Main Server Port: 9120 or your dedicated UDP port
- Protocol: UDP
- Protocol Format: 0 ASCII
- SACK Enable: Receive SACK and check
- Buffer Mode: 1 Enable the buffer function

## Additional Resources
- UDP Service Documentation: <https://docs.tartabit.com/en/Topics/UDP>
- Getting started with ASCII delimited payloads: <https://docs.tartabit.com/en/Topics/Trigger-ASCII-Parsing>

## Release Notes
- v3
  - Initial Release of new quickstart.