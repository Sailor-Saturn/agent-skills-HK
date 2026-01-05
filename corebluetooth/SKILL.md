---
name: corebluetooth
description: Apple Core Bluetooth framework for BLE and Bluetooth Classic. Use for scanning, connecting, advertising, service and characteristic discovery, read/write, notifications, L2CAP, background or state restoration, and error handling in iOS, macOS, tvOS, watchOS, or visionOS apps.
---

# Core Bluetooth

## Workflow

- Identify whether the app acts as a central, a peripheral, or both.
- Wait for the manager state to be `poweredOn` before issuing BLE operations.
- Follow the role checklist to keep discovery and connection order correct.
- Open `corebluetooth/corebluetooth.md` for API reference; search within it instead of reading the whole file.

## Central checklist

1. Create a `CBCentralManager` with a delegate and queue.
2. Handle `centralManagerDidUpdateState(_:)` and gate scanning on `.poweredOn`.
3. Scan with `scanForPeripherals(withServices:options:)` and stop when the target is found.
4. Connect, set the `CBPeripheral` delegate, and discover services and characteristics.
5. Read, write, or subscribe to characteristic notifications as needed.

## Peripheral checklist

1. Create a `CBPeripheralManager` with a delegate and queue.
2. Wait for the state to become `.poweredOn`.
3. Define services and characteristics, then add them to the manager.
4. Start advertising with service UUIDs and optional local name.
5. Respond to read and write requests; publish updates to subscribed centrals.

## Reminders

- Retain discovered `CBPeripheral` instances to keep them alive.
- Use notifications for streaming data; use write-without-response only when `canSendWriteWithoutResponse` is true.
- Use L2CAP only for use cases that do not fit GATT characteristics.
