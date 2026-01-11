# Known Limitations & Design Risks

This section documents known weaknesses and unresolved risks in the current design.

---

## Biometric Limitations
- Fingerprints are low-entropy and not secret
- Biometrics cannot be rotated if compromised
- Sensors may fail due to injury, dirt, or stress
- Direct biometric-derived cryptography is unsafe

---

## Physiological Sensor Risks
- Heart rate sensors may produce false zero readings
- Temporary signal loss could trigger unintended data destruction
- Environmental conditions may affect readings

---

## Centralization Risks
- Control center represents a high-value target
- Key escrow weakens forward secrecy
- Compromise of the control center affects all users

---

## Voice Command Risks
- Voice recognition is susceptible to spoofing
- Stress and noise may cause false activation
- Destructive commands lack secondary confirmation

---

## Transfer Connection Risks
- Short transfer window (1 minute) may be rushed in practice
- New operator must authenticate successfully; failed attempts could lock device
- Transfer procedure requires physical proximity
- Protocol for audit/logging of transfer events is underspecified

---

## Design Tradeoff Summary

This design prioritizes **confidentiality and compromise containment** over availability and convenience.  
Many choices intentionally favor fail-safe destruction, even at the risk of accidental data loss.

Future iterations would need:
- Secure hardware enclaves
- Multi-signal confirmation logic
- Reduced reliance on centralized authorities
- Formal cryptographic review
