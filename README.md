# 📢 ShoutOut / Life-Link Protocol (v0.1-Alpha)

> **"We live in the most connected age, yet we exist as isolated islands."**

Life-Link (LLP) is a decentralized, anonymity-first proximity communication protocol based on Bluetooth Low Energy (BLE). It turns physical proximity into a digital connection, allowing you to "Shout Out" to the world around you without relying on central servers, internet access, or surveillance-heavy platforms.

---

### 🌟 Why Life-Link?
In 2026, we are trapped in digital silos. We can talk to someone 10,000 miles away but remain silent to the person sitting next to us on a train. Life-Link aims to reclaim our physical space sovereignty.

#### **Real-world Scenarios:**
* **The Camping Help:** Forgot to buy leeks for your outdoor cooking? Don't be shy; "Shout Out" to nearby campers. Someone 50 meters away might have plenty to share.
* **The Train Apology:** Had an embarrassing moment (like an accidental noise or smell) on a crowded Osaka train? Send an anonymous, sincere apology to the cabin. Turn awkwardness into empathy.
* **The Digital Flare:** In a disaster where cell towers are down, every Life-Link node becomes a "Digital Flare," guiding rescuers to your location via a decentralized mesh.

---

### 🛠 Technical Highlights
* **Zero-Power Standby**: Uses a dedicated Service UUID `0x4C4C` for hardware-level filtering. Your phone only wakes up when a real "Shout" is detected.
* **16-Byte Dictionary Encoding**: High-efficiency packets that transcend language barriers. A "Help" code is received as "Help" in English, "救命" in Chinese, or "助けて" in Japanese.
* **Physical Anonymity**: Mandatory MAC address rotation (RPA) and Ephemeral IDs ensure you cannot be tracked in the physical world.
* **Sentinel Infrastructure**: Cheap microcontrollers (ESP32/nRF52) act as "Sentinels" (Physical Anchors) in coffee shops or malls to facilitate connections.

---

### 🤝 Join the Movement
This is a non-profit, open-source initiative born in an old house in **Osaka**. We don't want your data; we want your connection.

* **Geeks:** Help us refine the `PROTOCOL.md`.
* **Developers:** Build the first "ShoutOut" app.
* **Humans:** Wear the "Sentinel" pendant and start sensing the world again.

**Let the world hear your shout.**

---

### 📜 License
Licensed under the [MIT License](LICENSE).

*Crafted with ❤️ in Osaka, Japan.*
