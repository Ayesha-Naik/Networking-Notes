# Networking Class 03 — IP Address, Types, Public/Private, NAT

## 1. IP Address kya hai? (yaad dilana)
**IP Address** = har device ka network mein apna **unique number (pata)**. Isi se pata chalta hai data kis device ko bhejna/lena hai.

**Device ko pehchanne ke liye:** Har device ka apna alag IP address hota hai (network ke andar), aur network isi IP se dekh kar samajhta hai "ye kaunsа device hai" aur data sahi jagah bhejta hai — bilkul jaise ghar ka pata dekh kar postman sahi ghar tak chitthi pohanchata hai.

---

## 2. IP Address ke Types
IP address ki 2 tarah se types hoti hain:

### (A) IPv4 aur IPv6 (banawat ke hisaab se)
- **IPv4** = purana, aam tareeqa. Format: `192.168.1.5` (4 numbers, dot se alag)
- **IPv6** = naya, lamba tareeqa (kyunki IPv4 ke numbers khatam ho rahe). Format: lamba, letters+numbers wala

**Abhi zyada tar IPv4 hi use hota hai.**

### (B) Public IP aur Private IP (jagah ke hisaab se)
Ye sabse zaroori farak hai — aage detail mein.

---

## 3. Public IP vs Private IP

**Private IP:**
- Ye IP tumhare **ghar/office ke andar** (local network) use hota hai
- Router tumhare sab devices (mobile, laptop) ko private IP deta hai
- Ye IP **duniya (internet) se seedha nazar nahi aata**
- Sirf tumhare ghar ke andar kaam karta hai

**Public IP:**
- Ye IP **poori duniya (internet) mein pehchana** jata hai
- Tumhara **router** (poora ghar) ek hi public IP se internet se juda hota hai
- Ye IP ISP tumhare router ko deta hai

**Example:** Socho tumhara **ghar ek building** hai:
- **Public IP** = building ka **bahar wala address** (jo poore sheher/duniya ko pata hai — "Building 123, Main Road")
- **Private IP** = building ke **andar har flat ka number** (Flat 1, Flat 2, Flat 3) — ye sirf building ke andar wale jaante hain, bahar wale nahi

Yani tumhare ghar mein 5 devices hain — sabka **ek hi Public IP** (ghar ka bahar wala pata), par har device ka apna **alag Private IP** (andar ka number).

---

## 4. Private IP ki Ranges (poori range ke saath)
Private IP hamesha in **teen fix ranges** mein se hota hai:

| Range shuru | Range khatam |
|-------------|--------------|
| `10.0.0.0` | `10.255.255.255` |
| `172.16.0.0` | `172.31.255.255` |
| `192.168.0.0` | `192.168.255.255` |

Yani:
- **`10.0.0.0` se `10.255.255.255`** tak — bade networks ke liye
- **`172.16.0.0` se `172.31.255.255`** tak — darmiyane networks ke liye
- **`192.168.0.0` se `192.168.255.255`** tak — **sabse aam**, ghar/office ka network

**Sabse aam (ghar/office mein):** `192.168.x.x` — isi liye tumhare router ka IP aksar `192.168.1.1` hota hai.

**Yaad rakho:** agar IP `192.168...` ya `10...` ya `172.16-31...` se shuru ho, to wo **Private** hai (local network ka).

---

## 5. Public IP ki Range
Public IP baaki **saare** numbers hote hain jo upar wali 3 private ranges mein nahi aate — yani duniya ke internet pe jitne bhi IP hain (private ranges chhod kar), wo sab **Public** hain.

**Example:** `8.8.8.8` (Google ka server) — ye Public IP hai, poori duniya se pohanchne layak. Ye upar wali kisi bhi private range mein nahi aata, isliye Public hai.

---

## 6. IP Classes (A, B, C, D, E) — poori range ke saath

IP address ka **pehla number** dekh kar pata chalta hai wo kis Class ka hai. Har class ki apni **poori range** (shuru se aakhir tak) hoti hai:

| Class | Range shuru | Range khatam | Pehla number | Kiske liye |
|-------|-------------|---------------|----------------|------------|
| **A** | `1.0.0.0` | `126.255.255.255` | 1 – 126 | Bade networks (bohat saari devices, badi company) |
| **B** | `128.0.0.0` | `191.255.255.255` | 128 – 191 | Darmiyani (medium) networks (university, medium company) |
| **C** | `192.0.0.0` | `223.255.255.255` | 192 – 223 | Chhote networks — **ghar/office ke liye sabse aam** |
| **D** | `224.0.0.0` | `239.255.255.255` | 224 – 239 | Special (multicast) kaam, aam use nahi |
| **E** | `240.0.0.0` | `255.255.255.255` | 240 – 255 | Research/testing, aam use nahi |

**Samajhne ka tareeqa:** Sirf IP ka **pehla number** dekho, table se Class pata chal jayegi.

**Example:**
- `10.0.0.5` → pehla number `10` → **Class A** ki range (`1.0.0.0` – `126.255.255.255`) mein aata hai
- `172.16.5.1` → pehla number `172` → **Class B** ki range (`128.0.0.0` – `191.255.255.255`) mein aata hai
- `192.168.1.5` → pehla number `192` → **Class C** ki range (`192.0.0.0` – `223.255.255.255`) mein aata hai ← sabse aam

**Yaad rakho:** Class A = sabse bada network (kam networks, bohat saari devices har ek mein). Class C = sabse chhota network (zyada networks, kam devices har ek mein) — isi liye ghar/office mein Class C (`192.168.x.x`) use hoti hai.

---

## 7. NAT kya hai?
**NAT = Network Address Translation.**

**Kya karta hai?** NAT **Private IP** ko **Public IP** mein badal-ta hai (aur wapas), taake ghar ke andar ke sab devices (jinke Private IP hain) internet (jo Public IP maangta) use kar saken.

**Kaam kaise karta hai?**
1. Tumhara mobile (Private IP `192.168.1.5`) internet pe request bhejta hai
2. Router (NAT) us request ko apne **Public IP** mein "translate/badal" deta hai jab bahar bhejta hai
3. Internet ko lagta hai request seedha router (Public IP) se aayi
4. Jawab wapas router ke Public IP pe aata hai
5. Router NAT ki madad se yaad rakhta hai ye jawab **kis Private IP (mobile) ke liye** tha, aur usi ko wapas bhej deta hai

**Yani NAT translator ka kaam karta hai — Private ↔ Public ke beech.**

**Example:** NAT ek **hotel ka reception** jaisа hai. Hotel ke andar 50 kamre (Private IP) hain, par bahar duniya ko sirf **hotel ka ek address** (Public IP) pata hai. Jab bahar se koi chitthi aati hai, reception dekh kar sahi kamre tak pohanchata hai. Har kamre ka apna number hai (Private), par bahar sirf hotel ka ek hi address dikhta (Public) — NAT wahi reception ka kaam karta hai.

---

## 8. Har device ka IP alag kyun hota hai? (reason)
Har device ka IP alag isliye hota hai taake **network sahi se pehchan sake data kis device ko bhejna hai.**

**Agar sab devices ka IP same ho jaye to kya ho?** Router confuse ho jayega — data kis device ko bheje? Jaise agar ek building ke sab flats ka number "1" ho jaye, to postman ko pata hi nahi chalega kis flat mein chitthi de.

**Isi liye:**
- Har device ko **alag Private IP** milta hai (router deta hai, DHCP se)
- Isse data **sahi device tak** pohanchta hai, confusion nahi hoti

---

## Quick Revision:
| Cheez | Matlab |
|-------|--------|
| IPv4 / IPv6 | purana chhota format / naya lamba format |
| Private IP | ghar/office ke andar (`192.168.x.x` sabse aam) |
| Public IP | poori duniya mein pehchana (router ka) |
| Private range 1 | `10.0.0.0` – `10.255.255.255` |
| Private range 2 | `172.16.0.0` – `172.31.255.255` |
| Private range 3 | `192.168.0.0` – `192.168.255.255` |
| Class A | `1.0.0.0` – `126.255.255.255` (bada network) |
| Class B | `128.0.0.0` – `191.255.255.255` (medium) |
| Class C | `192.0.0.0` – `223.255.255.255` (chhota, aam) |
| NAT | Private↔Public IP translate karta (router mein) |
| Alag IP kyun | taake data sahi device tak pohanche, confusion na ho |
