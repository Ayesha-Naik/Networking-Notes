# Networking Class 07 — TCP/IP Model (Detail)

## 1. TCP/IP Model kya hai?
**TCP/IP Model** = ek **4-layer** wala model jo asal mein **internet chalane** ke liye use hota hai. OSI Model 7 layers ka tha (sirf samajhne/seekhne ke liye), TCP/IP Model kam layers ka aur **asal duniya mein use hone wala** hai.

**Simple samajh:** OSI = theory ki kitaab (7 chapters). TCP/IP = wahi kaam, 4 chapters mein — jo internet pe waqai chalta hai.

**Naam kyun "TCP/IP"?** Kyunki iske 2 sabse zaroori protocols (rules) yehi hain — **TCP** aur **IP**. Poora model inhi ke naam pe rakha gaya.

---

## 2. TCP/IP ki 4 Layers

| # | Layer ka naam |
|:---:|---|
| 4 | Application |
| 3 | Transport |
| 2 | Internet |
| 1 | Network Access (Link) |

---

## 3. OSI vs TCP/IP — kaunsi layer kis mein gayi

| TCP/IP Layer | OSI ki kaunsi layers isme aayin |
|---|---|
| **Application** | Application + Presentation + Session |
| **Transport** | Transport (wahi) |
| **Internet** | Network (wahi) |
| **Network Access** | Data Link + Physical |

**Yaad rakho:** TCP/IP ne OSI ki upar ki 3 layers ko **ek** kiya, neeche ki 2 ko bhi **ek** kiya. Beech ki 2 (Transport, Internet) waisi hi rahin.

---

## 4. Layer 4 — Application Layer (detail)

**Kaam:** User ka seedha kaam — browser, WhatsApp, email. Ye tumhare **sabse najdeek** layer hai.

**Is layer ke protocols (rules) — kaam ke hisaab se:**

| Protocol | Kaam |
|---|---|
| **HTTP** | normal website kholna |
| **HTTPS** | secure (taala wali) website |
| **FTP** | files transfer karna |
| **SMTP** | email bhejna |
| **DNS** | naam ko IP mein badalna |

**Example:** Tum browser mein `google.com` likhti ho — **HTTP/HTTPS** yahin kaam karta hai. Email bhejti ho — **SMTP** kaam karta.

---

## 5. Layer 3 — Transport Layer (detail — TCP vs UDP)

**Kaam:** Data ko packets mein todna, **Ports** ka use, aur data ko **sahi tareeqe se** pohanchana. Yahan 2 zaroori protocols hain:

### TCP (Transmission Control Protocol)
- **Pakka aur poora** — data confirm hokar pohanchta hai
- Agar packet kho jaye, **dobara maangta** hai
- Dheema (thodа time lagta), par **bharosemand**
- Use hota: website, email, file download

### UDP (User Datagram Protocol)
- **Tez**, par confirm nahi (data kho bhi sakta)
- Dobara nahi maangta — bas bhej deta, chahe pohanche ya na pohanche
- Use hota: video call, live streaming, gaming, DNS

**Farak (example se):** TCP = **registered daak** (confirm hoti, dobara try karti agar na pohanche). UDP = **normal daak** (jaldi, par confirm nahi karti).

### TCP ka Three-Way Handshake (kaise connection banta hai)
TCP connection banane se pehle **3 steps** mein "salam-dua" karta hai:

| Step | Kya hota hai |
|:---:|---|
| 1 | Client server ko bolta: **"SYN"** (connect karna chahti hoon) |
| 2 | Server jawab deta: **"SYN-ACK"** (theek hai, main bhi ready hoon) |
| 3 | Client confirm karta: **"ACK"** (chalo shuru karte hain) |

**Example:** Jaise phone call se pehle: "Hello, sun rahe ho?" → "Haan, bolo" → "Theek hai, baat shuru karte hain" — 3 baar confirm hone ke baad hi asli baat (data) shuru hoti hai. Isi liye TCP **bharosemand** hai.

**Ports (Transport Layer mein):** Har service ka apna port hota hai taake data sahi app tak jaye — Port 80 (website), Port 443 (secure website), Port 22 (SSH). Ye humne pehle Ports wale topic mein detail mein padha tha.

---

## 6. Layer 2 — Internet Layer (detail)

**Kaam:** Data ka **raasta (route)** decide karna — **IP Address** yahan sabse zaroori cheez hai.

**Is layer ke protocols:**

| Protocol | Kaam |
|---|---|
| **IP** | address aur raasta (IPv4/IPv6) |
| **ICMP** | error batana, ping/traceroute isi se chalte |
| **ARP** | IP address ko MAC address mein badalna (local network mein) |

**Example:** `ping 8.8.8.8` jab chalati ho, to **ICMP** protocol hi check karta hai server zinda hai ya nahi. Router jab decide karta hai data kaunse raaste jaye — ye **IP** ka kaam hai.

---

## 7. Layer 1 — Network Access Layer (detail)

**Kaam:** Asli hardware — cable, WiFi, MAC address, NIC. Local network ke andar data ko sahi device tak pohanchana.

**Is mein kya shaamil hai:**
- **NIC** (network card)
- **MAC Address**
- **Cable / WiFi signal**
- **Switch/Hub**

**Example:** Tumhara WiFi router jab **MAC address** dekh kar decide karta hai data kis mobile ko bhejna hai — ye is layer ka kaam hai. Ye sabse "chhoo sakne wali, asli" layer hai.

---

## 8. Poora Safar — TCP/IP Model se ek website khulna

Jab tum `google.com` kholti ho, data TCP/IP ki **4 layers se guzarta hai**:

```
TUM (request bhejti ho):
Application  → browser "google.com" maangta hai (HTTP/HTTPS)
   ↓
Transport    → TCP handshake hota, packets banते, Port 443 lagti
   ↓
Internet     → IP Address se raasta milta (DNS naam ko IP mein badalta)
   ↓
Network Access → WiFi/cable se data ghar ke bahar nikalta

...poore internet ke raaste se guzar kar Google Server tak...

GOOGLE SERVER (jawab bhejta hai) — ulta:
Network Access → data wapas tumhare router tak signal se aata
   ↓
Internet     → IP se pehchana jata ye tumhare liye hai
   ↓
Transport    → TCP packets jode jate, sahi tarteeb mein
   ↓
Application  → page tumhare browser mein khul jata hai
```

**Example:** Jaise khaana order karna — tum order (Application) dete ho, waiter usko sahi tarteeb (Transport) mein kitchen tak le jata, raasta (Internet) dhoondh kar, asli chalna (Network Access) hota hai. Khana wapas usi tareeqe se ulta aata hai.

---

## 9. TCP/IP vs OSI — quick comparison

| Cheez | OSI Model | TCP/IP Model |
|---|---|---|
| Layers | 7 | 4 |
| Maqsad | Sirf samajhne/seekhne ke liye | Asal internet chalane ke liye |
| Use | Theory | Practical (waqai chalta hai) |
| Naam | Layer number se (1-7) | Naam se (Application, Transport...) |

---

## Quick Revision:

| # | Layer | Kaam | Protocols |
|:---:|---|---|---|
| 4 | Application | user ka kaam | HTTP, HTTPS, FTP, SMTP, DNS |
| 3 | Transport | packets, ports, reliable/fast | TCP (pakka), UDP (tez) |
| 2 | Internet | raasta, address | IP, ICMP, ARP |
| 1 | Network Access | hardware, local device | MAC, NIC, cable/WiFi |

**Sabse zaroori 3 cheezein yaad rakho:**
1. TCP = pakka (handshake ke saath), UDP = tez (bina confirm)
2. Handshake = SYN → SYN-ACK → ACK
3. TCP/IP = asal internet, OSI = sirf seekhne ke liye
