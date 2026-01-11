# Threat Model

This threat model defines the assumptions, adversaries, and attack surfaces considered in this design.

---

## Assumptions

- The operating environment may be hostile
- Network traffic may be monitored or intercepted
- Devices may be physically captured
- Operators may be coerced or incapacitated
- Sensors may fail or produce noisy data

---

## Adversary Capabilities

### Physical Adversary
- Can seize the device
- Can attempt forced removal
- May attempt biometric spoofing

### Network Adversary
- Can intercept, replay, or delay messages
- Cannot trivially break strong cryptography

### Insider Threat
- May have partial access to control center systems
- May attempt unauthorized key usage

---

## Assets to Protect

- Encryption keys
- Communication content
- Operator identity
- Channel membership
- Historical communication data

---

## Attack Surfaces

- Biometric sensors
- Physiological sensors
- Device firmware
- Network channels
- Control center infrastructure

---

## Security Goals

- Prevent unauthorized access to communication channels
- Minimize data exposure after compromise
- Ensure rapid response to loss of operator control
- Prefer data destruction over uncertain security states
