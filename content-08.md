# Networking Class 08 — TCP, UDP aur Handshake (Poori Detail)

## 1. TCP kya hai?

**TCP = Transmission Control Protocol.** Ye ek aisा tareeqa (protocol/rule) hai jisse do computers **pakka, poora, aur sahi tarteeb mein** data bhejte-lete hain.

**TCP ki khaasiyat (features):**

| Khaasiyat | Matlab |
|---|---|
| **Reliable (bharosemand)** | data confirm hoke pohanchta hai |
| **Ordered (tarteeb se)** | packets sahi number mein jode jate |
| **Error-checking** | agar packet kharab ho to dobara maangta |
| **Connection-based** | pehle "hello" (handshake) hota, phir data |
| **Dheema** | confirm karne mein thodа time lagta |

**Example:** Tum ek **badi file (movie)** download karti ho. TCP check karta hai har chhota tukda (packet) **sahi aur poora** aaya ya nahi. Agar koi tukda kharab/gum ho jaye, TCP use **dobara maangta** hai — taake poori file bilkul sahi ban jaye, ek bhi cheez chhoote nahi.

**Kahan use hota hai:** Website kholna, email, file download, WhatsApp message — jahan **har cheez poori aur sahi** aani zaroori hai.

---

## 2. UDP kya hai?

**UDP = User Datagram Protocol.** Ye bhi data bhejne ka tareeqa hai, par TCP se **bilkul ulta soch** rakhta hai — "jaldi bhejo, confirm karne mein time zaya mat karo."

**UDP ki khaasiyat:**

| Khaasiyat | Matlab |
|---|---|
| **Fast (tez)** | seedha bhej deta, ruk kar confirm nahi karta |
| **Unreliable** | data kho bhi sakta hai, koi guarantee nahi |
| **No ordering** | packets kisi bhi tarteeb mein pohanch sakte |
| **Connectionless** | koi pehle "hello" nahi — seedha data bhej deta |

**Example:** Tum kisi se **video call** kar rahi ho. Agar 1 second ka video/awaaz thodа kharab (glitch) ho jaye, koi baat nahi — call **rukti nahi**, aage badhti rehti hai. Kyunki agar UDP bhi TCP ki tarah "ruk kar confirm karo" wala kaam kare, to call baar-baar atkegi — jo live call mein bardaasht nahi.

**Kahan use hota hai:** Video call, live streaming (YouTube Live), online gaming, DNS (jaldi jawab chahiye) — jahan **speed zaroori hai, thodа data chhoot jaye to bhi chalega.**

---

## 3. TCP vs UDP — seedha muqaabla

| Cheez | TCP | UDP |
|---|---|---|
| Speed | Dheema | Tez |
| Reliability | Pakka (guarantee) | Koi guarantee nahi |
| Connection | Pehle handshake zaroori | Seedha bhej deta |
| Error check/dobara bhejna | Haan | Nahi |
| Use | Website, email, download | Video call, gaming, streaming |

**Sabse aasaan example (yaad rakhne ke liye):**
- **TCP = Registered daak** — post office confirm karta parcel pohancha, receipt milti hai, agar na pohanche to dobara bhejte
- **UDP = Normal daak (letterbox mein daal do)** — jaldi hai, par confirm nahi ke pohancha ya nahi

---

## 4. Handshake kya hai?

**Handshake** = do computers ke beech data bhejne se **pehle** ek "salam-dua" (confirmation) — taake dono taraf pakka ho jaye ke connection banane ke liye **dono ready hain.**

**Simple lafzon mein:** Jaise do log baat karne se pehle "Hello, sun rahe ho?" bolte hain, waise computers bhi data bhejne se pehle ek chhota sा "hello" karte hain.

---

## 5. TCP mein Handshake ka Role (Three-Way Handshake)

TCP hamesha data bhejne se **pehle** ek **3-step handshake** karta hai — isi liye TCP itna **bharosemand** hota hai.

**3 Steps:**

| Step | Kaun bolta | Kya bolta | Matlab |
|:---:|---|---|---|
| **1** | Client → Server | **SYN** | "Main connect karna chahti hoon" |
| **2** | Server → Client | **SYN-ACK** | "Theek hai, main bhi ready hoon" |
| **3** | Client → Server | **ACK** | "Chalo, ab shuru karte hain" |

**Poora process (step by step):**
1. Tumhara device (client) server ko **SYN** bhejta hai — "kya hum baat kar sakte hain?"
2. Server jawab deta hai **SYN-ACK** — "Haan, main sun raha hoon, tum bhi sunो"
3. Tumhara device confirm karta hai **ACK** — "Theek hai, shuru karte hain"
4. **Ab connection ban gaya** — asli data (jaise website ka page) transfer hona shuru hota hai

**Example:** Jaise **phone call**:
- Tum call karti ho → phone ring hoti hai (**SYN** — "sun rahi ho?")
- Doosra banda "Hello" bolta hai (**SYN-ACK** — "haan, bolo")
- Tum "Hello, kaise ho" bolti ho (**ACK** — "theek hai, baat shuru")
- Ab **asli baatcheet (data)** shuru hoti hai

**Handshake ka role/faida:**
- Confirm karta hai **dono taraf tayyar** hain
- Pata chalta hai connection **kharab to nahi** (agar jawab na aaye, matlab kuch masla hai)
- Isi wajah se TCP **bharosemand** hai — bina handshake ke seedha data bhejna galat/gum ho sakta

**UDP mein handshake nahi hota** — isi liye UDP tez hai (koi "hello" bole bina seedha data bhej deta), par bharosа kam.

---

## 6. Connection band karna (Handshake ka doosra hissa)

Jab data bhejna khatam ho jaye, TCP connection ko bhi **sahi tareeqe se band** karta hai (isko **FIN** — Finish — kehte hain):
```
Client: "FIN" (mujhe band karna hai)
Server: "ACK" (theek hai, samajh gaya)
Server: "FIN" (main bhi band kar rahi hoon)
Client: "ACK" (theek hai, done)
```

**Example:** Phone call khatam karte waqt — "Achha, main rakhti hoon" → "Theek hai" → dono taraf se phone kata jata hai. Aise hi seedha beech mein nahi kaat dete, pehle bata kar band karte hain.

---

## Quick Revision:

| Cheez | Matlab |
|---|---|
| TCP | pakka, poora, tarteeb se — dheema par bharosemand |
| UDP | tez, par confirm nahi — video call/gaming ke liye |
| Handshake | data se pehle "hello" — dono ready hain confirm karna |
| SYN | "connect karna chahti hoon" |
| SYN-ACK | "theek hai, main bhi ready" |
| ACK | "chalo shuru karte hain" |
| TCP mein handshake kyun | isi se TCP bharosemand banta — pehle confirm, phir data |
| UDP mein handshake | nahi hota — isi liye tez hai |
| FIN | connection sahi tareeqe se band karna |
