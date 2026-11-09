# SmartThings Edge four-key scene remote

An independent SmartThings Edge driver publication for the Tuya Zigbee remote with manufacturer `_TZ3000_dziaict4` and model `TS0044`. The driver package matches this fingerprint only. It is intended for a four-button device, including the six-endpoint firmware `0x48` scenario described in the source project.

## Features

- Four button components, `button1` through `button4`, with `pushed`, `double`, and `held` events when supported reports are received.
- Battery capability and refresh on the main component; actual reporting depends on the device.
- The profile exposes four button components, not separate controls for endpoints 5 and 6. This does **not** guarantee that reports from those endpoints are safely ignored.

## Installation

1. Back up or document automations and device settings before removing or re-pairing the remote. Removing a device can break automations and require them to be recreated.
2. Open the [SmartThings driver channel](https://callaway.smartthings.com/channels/a13c3aba-4114-4f63-a6a6-c331e44907df?status=accepted), enroll, and install **Tuya TS0044 6-endpoint Button** on the target compatible SmartThings hub, if available.
3. If replacing an existing pairing, remove the existing device and any associated child devices as appropriate.
4. Reset the remote according to its manufacturer instructions and add it again through SmartThings.
5. Verify the selected driver, battery reading, and all button actions, then restore or recreate automations as needed.

Channel access and driver operation have not been independently verified for this publication. Availability and behavior may vary by hub, firmware, device and account.

## Important limitations

- The source maps incoming endpoint numbers to component names without a bounds or existence check before emitting events. Reports from endpoints 5 or 6, or other unexpected endpoints, may therefore cause errors rather than being ignored.
- The driver's `added` lifecycle handler sends Zigbee `RemoveAllGroups` to the device. Pairing or re-adding it may remove Zigbee group memberships; document and restore any needed group configuration.
- Other manufacturer/model combinations are not matched by this package. No firmware is included.

## License and attribution

This project includes and adapts parts of [obmaz/smartthings_edge_driver](https://github.com/obmaz/smartthings_edge_driver), licensed under the Apache License 2.0. See [LICENSE](LICENSE); existing source license notices are retained. In this publication copy, historical Zigbee log examples and an unnecessary third-party file-sharing link were removed from source comments. Runtime logic was not changed by those comment edits.
