# Life-Link Protocol (LLP) Specification v0.1-Alpha

## 1. Introduction
The Life-Link Protocol (LLP) is a stateless, decentralized proximity communication protocol designed to facilitate anonymous human interaction within a 10-50m radius using Bluetooth Low Energy (BLE).

## 2. Physical Layer
- **Channel**: BLE Advertising Channels (37, 38, 39).
- **Service UUID**: `0x4C4C` (ASCII 'LL'). Mandatory for hardware-level filtering to ensure low power consumption on mobile devices.
- **Advertising Interval**: 
  - Standard: 1000ms
  - High-Priority/SOS: 100ms

## 3. Data Link Layer: Packet Structure
LLP utilizes the 31-byte BLE Advertising payload. The core frame (20-28 bytes) is defined as follows:

| Offset | Size (bit) | Field | Description |
| :--- | :--- | :--- | :--- |
| 0x00 | 8 | `VER` | Protocol Version (currently `0x01`). |
| 0x01 | 8 | `TYPE` | Message type (0x01: Shout, 0x02: Anchor, 0x03: Hello, 0xFF: SOS). |
| 0x02 | 32 | `E_ID` | Ephemeral ID. Randomized 32-bit integer, rotated with MAC address. |
| 0x06 | 16 | `D_CODE` | Dictionary Code. Refers to the standardized empathy codebook. |
| 0x08 | 16 | `PARAM` | Contextual parameters (e.g., quantity, intensity, or relative coordinates). |
| 0x0A | 96 | `SEC_TAG` | Security Tag. HMAC-SHA256 truncated signature + Timestamp window. |
| 0x16 | 16 | `CRC` | 16-bit Cyclic Redundancy Check for data integrity. |

## 4. Security & Privacy Framework
### 4.1 Physical Anonymity
All nodes MUST implement **Resolvable Private Address (RPA)**. The Bluetooth MAC address and `E_ID` must rotate synchronously every 15 minutes to prevent long-term tracking.

### 4.2 Anti-Replay Mechanism
Every packet contains a truncated timestamp. Receiving nodes MUST discard any packet with a timestamp deviation greater than 300 seconds (5 minutes) relative to local time.

### 4.3 Private Sessions (Whisper Mode)
For one-on-one encrypted chat, nodes perform an anonymous handshake using **Curve25519 (ECDH)**. Once a shared secret is established, the session transitions to an encrypted GATT or L2CAP channel.

## 5. Power Management
Nodes (Sentinels and Smartphones) MUST leverage hardware-level UUID filtering. The smartphone CPU should only be interrupted when a valid `0x4C4C` service packet is detected by the BLE controller.

## 6. Global Dictionary (The Codebook)
Codes are categorized to ensure cross-language compatibility:
- `0x0000 - 0x0FFF`: **Survival & SOS** (Emergency help, medical).
- `0x1000 - 0x1FFF`: **Mutual Aid** (Borrowing items, seeking directions).
- `0x2000 - 0x2FFF`: **Social Resonance** (Sharing vibes, common observations).
- `0x3000 - 0x3FFF`: **Etiquette & Exemption** (Apologies, social distancing).

---
*Status: Draft / Experimental*
*Editor: zhaibird*
