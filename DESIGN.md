# System Design

This document describes the conceptual architecture and workflow of the encrypted communication system.

---

## System Components

### Control Center
- Central orchestration authority
- Distributes channel lists and encryption keys
- Registers active devices
- Maintains communication backups for authorized decoding

### Channels
- Logical communication paths
- Each channel has a unique encryption key
- Keys may be time-limited or revoked

### Device
- Wearable communication unit
- Stores encrypted channel data and keys
- Enforces access control and destruction logic
- Performs local authentication

### Fingerprint Detector
- Reads the operator’s fingerprint
- Used to authenticate access to the device
- Assumed to be physically bound to the operator

### Voice Recognition Module
- Accepts a predefined destruction command
- Allows manual data wipe in emergency situations

---

## Device Operations

### Initiate Connection
- Establishes or re-establishes a link with the operator
- Requires biometric authentication
- Unlocks access to encrypted communication data

### Transfer Connection
- Allows transferring the device to another operator
- Ensures controlled handover without requiring prior deactivation

### Destroy Connection
- Deletes all stored data:
  - Channels
  - Encryption keys
  - Biometric references

### Switch Channel
- Rotates active communication channel
- Uses pre-authorized channel list

---

## Workflow

### Initial Device Connection
1. Operator receives an encryption key and channel list from the control center
2. Control center registers the operator as an active channel member
3. Operator wears the device
4. Operator presses **Initiate Connection**
5. Device authenticates the operator using fingerprint input
6. Device enables communication and displays *Connection Established*

### Reconnecting an Existing Device
1. Operator wears the device again
2. Fingerprint detector is attached
3. Operator presses **Initiate Connection**
4. Device attempts to authenticate by unlocking stored encrypted material

### Transfer Connection
1. Current operator presses **Transfer Connection**
2. Device starts a **1-minute window** for transfer
3. New user authenticates with their fingerprint
4. Device is now transferred and linked to the new operator

### Loss-of-Operator Handling
1. Device detects heart rate drop to zero and lack of movement
2. A 1.5-minute grace period begins
3. If signals do not recover:
   - Device attempts to notify the control center
   - Device wipes all sensitive data regardless of transmission success
