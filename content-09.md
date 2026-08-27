# Networking Class 09 — Data, Frontend/Backend, aur Firewall (Detail)

## 1. Data kya hota hai?
**Data** = koi bhi cheez jo computer store, process, ya bhej sakta hai — text, photo, video, numbers, messages — sab **data** hai.

**Data kahan-kahan store hota hai?**

| Jagah | Kya hota hai |
|---|---|
| **RAM** | temporary — abhi ka kaam (bijli jaye to gayab) |
| **Hard Disk/SSD** | permanent — files, photos, apps |
| **Cloud (server)** | internet pe kisi doosre computer mein (Google Drive) |
| **Database** | tarteeb se rakha data (jaise Facebook ke sab users ka data) |

**Example:** Tum WhatsApp pe photo bhejti ho — photo pehle tumhare **phone (Hard Disk)** mein hoti hai, bhejte waqt **RAM** mein aati hai (kaam karne ke liye), phir **internet ke zariye server (cloud)** pe jaa kar doosre ke phone tak pohanchti hai.

---

## 2. Frontend aur Backend kya hai?
Har website/app **2 hisson** mein bani hoti hai:

**Frontend (jo tum dekhti ho):**
- Wo hissa jo user **seedha dekhta aur use karta** hai — buttons, design, colors, text
- Jaise ek dukaan ka **saamne wala hissa** (jahan customer aata, cheezein dekhta)

**Backend (jo peeche chalta hai, dikhta nahi):**
- Wo hissa jo **peeche kaam karta** hai — data store karna, hisaab karna, security
- Jaise dukaan ka **godown/office** (jahan customer nahi jata, par asli kaam wahin hota)

**Example:** Facebook kholti ho — jo tum **dekhti ho** (photos, posts, buttons) = **Frontend**. Jab tum kisi post pe like karti ho aur wo **save ho jata hai server pe** = **Backend** ka kaam.

**Ek line:** Frontend = jo dikhta hai (saamne). Backend = jo peeche chupa hai (asli kaam).

---

## 3. Firewall kya hai?
**Firewall** = ek **security guard/deewaar** jo tumhare computer/network ko **khatarnak data** se bachata hai. Ye check karta hai kaunsа data andar aane diya jaye, kaunsa roka jaye.

**Example:** Firewall ghar ke **darwaze pe khada chowkidar** hai — har aane-jaane wale (data) ko check karta, sahi ko andar jaane deta, khatarnak/anjaan ko rok deta.

---

## 4. Firewall ke 2 Types

### (A) Software Firewall
- Ek **program/app** hai jo computer ke andar install hota hai
- Har computer pe **alag-alag** lagta hai
- Example: Windows Defender Firewall

**Kaam:** Ek hi computer ko bachata hai — jaise ghar ke **andar har kamre mein alag chowkidar.**

### (B) Hardware Firewall
- Ek **physical device** hai (jaise ek chhota box), jo poore network ke **darwaze pe** lagta hai
- Poore ghar/office ke **sab devices ko ek saath** bachata hai
- Companies/offices mein use hota hai

**Kaam:** Poore network ko bachata hai — jaise ghar ke **mukhya darwaze pe ek bada chowkidar**, jo andar sab kamron ko bachata hai.

**Farak (example se):** Software firewall = har kamre ka apna taala. Hardware firewall = ghar ke bahar wala mukhya gate ka guard.

---

## 5. Firewall Rules — Allow aur Block

Firewall ek **list of rules** follow karta hai — kya andar aane do, kya roko:

```
allow  = is cheez ko andar aane do
block/deny = is cheez ko rok do
```

**Rules kis cheez pe lagते hain?** Zyada tar **Ports** pe (jo humne pehle padha tha):

**Example rules:**
```
Allow Port 80   → website (HTTP) chalne do
Allow Port 443  → secure website (HTTPS) chalne do
Block Port 23   → Telnet (purana, unsafe) rok do
Allow Port 22   → sirf SSH (agar zaroorat ho)
```

**Simple samajh:** Har **khula port ek khula darwaza** hai. Firewall decide karta hai kaunsa darwaza khula rahe (allow), kaunsa band ho (block). Sirf zaroori ports allow karo, baaki block — taake koi hacker khule darwaze se andar na aa sake.

**Example:** Socho ghar ke 5 darwaze hain. Chowkidar (firewall) sirf **zaroori** darwaze khule rakhta (jaise mukhya gate = allow), baaki sab **band** kar deta (jo use hi nahi hote = block) — taake chor ghusne ka mauka na paye.

---

## 6. Ports ki Table (firewall rules samajhne ke liye)

| Port | Service | Kaam |
|:---:|---|---|
| 20/21 | FTP | file transfer |
| 22 | SSH | secure remote login |
| 23 | Telnet | remote login (unsafe, purana) |
| 25 | SMTP | email bhejna |
| 53 | DNS | naam ko IP mein badalna |
| 80 | HTTP | normal website |
| 443 | HTTPS | secure website |
| 3306 | MySQL | database |
| 3389 | RDP | Windows remote desktop |

**Firewall in sab ports ko check karta hai** — zaroori (jaise 80, 443) allow karta, khatarnak/faltu (jaise 23) block karta.

---

## 7. Stateless vs Stateful Firewall (sabse important)

Firewall 2 tareeqon se kaam karta hai — **yaad rakhta hai ya nahi** ke pehle kya hua tha:

### Stateless Firewall
- Har packet ko **akela, bina yaad rakhe** check karta hai
- Pichhle packet se koi lena-dena nahi — **har baar naye sire se check**
- **Tez** hai (kam kaam), par **kam samajhdar**

**Example:** Ek chowkidar jo **har baar tumhe pehli martaba** dekh raha hai jaisa behave karta hai — chahe tum 10 baar aa-jaa chuke ho, har baar poora ID check karega, pehchan-ta nahi.

### Stateful Firewall
- Poori **connection ko yaad rakhta** hai — kaun kis se, kab se baat kar raha
- Pichhla context dekh kar decide karta hai — "ye packet ek chalte connection ka hissa hai, allow karo"
- **Zyada samajhdar aur secure**, par thodа dheema (zyada kaam)

**Example:** Ek chowkidar jo tumhe **pehchan-ta** hai — "Achha, ye Ayesha hai, pehle bhi aayi thi, andar hi hai" — poori situation yaad rakhta, sirf naye/anjaan logon ko rokta hai.

### Farak — ek table mein

| Cheez | Stateless | Stateful |
|---|---|---|
| Yaad rakhta hai? | Nahi (har packet alag) | Haan (poori connection yaad) |
| Speed | Tez | Thodа dheema |
| Security | Kam samajhdar | Zyada samajhdar |
| Kaam | Sirf rule ke hisaab se check | Connection ka context dekh kar check |

**Ek line yaad rakho:** Stateless = **bhoolne wala** chowkidar (har baar naya check). Stateful = **yaad rakhne wala** chowkidar (connection pehchan-ta hai).

---

## Quick Revision:

| Cheez | Matlab |
|---|---|
| Data | koi bhi cheez jo store/bheja jaye (text, photo) |
| Data storage | RAM (temporary), Disk (permanent), Cloud |
| Frontend | jo user dekhta hai (design) |
| Backend | jo peeche kaam karta hai (server, data) |
| Firewall | security guard — khatarnak data roke |
| Software Firewall | ek computer ke andar (app) |
| Hardware Firewall | poore network ke liye (physical device) |
| Allow/Block | darwaza kholo / band karo |
| Stateless | har packet akela check (bhoolne wala) |
| Stateful | poori connection yaad rakhta (samajhdar) |
