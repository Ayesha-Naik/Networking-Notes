# Networking Class 06 — OSI Model (7 Layers)

## OSI Model kya hai?
**OSI = Open Systems Interconnection.** Ye ek **7-manzila imaarat (building)** jaisा model hai jo batata hai ke data tumhare computer se doosre computer tak **kaise aur kis tarteeb mein** safar karta hai.

**Kyun banaya gaya?** Taake har cheez (data bhejna, IP dena, cable se guzarna) alag-alag hisson (layers) mein baanti jaye — har layer apna kaam kare, aage wali layer ko de de. Isse poora system samajhna aasaan ho jata hai.

**7 Layers (upar se neeche):**

| # | Layer ka naam |
|:---:|---|
| 7 | Application |
| 6 | Presentation |
| 5 | Session |
| 4 | Transport |
| 3 | Network |
| 2 | Data Link |
| 1 | Physical |

**Yaad rakhne ka trick (upar se neeche):**
**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing
(Application, Presentation, Session, Transport, Network, Data Link, Physical)

---

## Layer 7 — Application Layer

**Kaam:** Ye layer **tumhare (user) sabse najdeek** hai — jahan tum seedha kaam karti ho. Browser, WhatsApp, email — ye sab is layer pe "exist" karte hain.

**Kahan exist karti hai (real life):** Jab tum browser mein `google.com` type karti ho ya WhatsApp pe message likhti ho — **ye Application Layer hai.** Tum yahan seedha involved ho.

**Example:** Tum browser mein "google.com" likhti ho aur Enter dabati ho — yehi is layer ka kaam hai, tumhari **request yahan se shuru** hoti hai.

**Chhota extra:** Yahin par HTTP/HTTPS jaise "rules" (protocols) use hote hain jo batate hain browser aur server kaise baat karein.

---

## Layer 6 — Presentation Layer

**Kaam:** Data ko **sahi shakl (format)** mein badalna — taake dono taraf (bhejne wala, lene wala) samajh saken. Ye encryption (data ko chhupana) aur compression (chhota karna) bhi karti hai.

**Kahan exist karti hai:** Jab koi website `https://` (taala wali, secure) khulti hai — data **encrypt** hoke jata hai (koi beech mein padh na sake). Ye kaam Presentation Layer karti hai.

**Example:** Tum ek photo WhatsApp pe bhejti ho. Ye layer photo ko **sahi format** (JPEG) mein badalti hai aur agar zaroorat ho to chhota (compress) karti hai, taake jaldi bhej sake.

---

## Layer 5 — Session Layer

**Kaam:** Do computers ke beech **baatcheet (session) shuru, chalu, aur band** karna. Yaad rakhti hai ke connection kab shuru hua, kab tak chalu rahega.

**Kahan exist karti hai:** Jab tum kisi website pe **login** karti ho, to wo tumhari "session" bana leti hai — jab tak logout na karo, wo yaad rakhti hai tum login ho.

**Example:** Tum Facebook pe login karti ho. Jab tak browser band nahi karti, Facebook tumhe baar-baar login nahi poochta — kyunki **session chalu** hai. Ye Session Layer ka kaam hai.

---

## Layer 4 — Transport Layer

**Kaam:** Data ko **sahi tarteeb mein, poora aur bina kisi galti ke** pohanchana. Ye data ko **packets** mein todती hai (jo Class 4 mein padha tha).

**Chhota extra concept — Ports:** Is layer pe **Ports** use hote hain (jaise Port 80 = website, Port 443 = secure website) — taake pata chale data **kaunsi service (app)** ke liye hai.

**Kahan exist karti hai:** Jab tum ek badi file download karti ho aur wo **poori, bina kisi galti ke** aati hai — ye Transport Layer ka kaam hai (TCP protocol yahan chalta hai).

**Example:** Tum ek movie download karti ho. Movie ko chhote **packets** mein toड kar bheja jata hai, aur ye layer check karti hai sab packets **sahi tarteeb mein aur poore** pohanche — agar koi packet chhoot jaye to dobara maangti hai.

---

## Layer 3 — Network Layer

**Kaam:** Data ka **raasta (route)** decide karna — kaunsе router se hote hue manzil tak jaye. **IP Address** yahan kaam karta hai.

**Kahan exist karti hai:** Jab tumhara data ghar ke router se, phir ISP se, phir internet ke kai routers se ho kar Google ke server tak pohanchta hai — ye **raasta chunna** Network Layer ka kaam hai.

**Example:** Traceroute (jo pehle padha tha) yehi layer dikhata hai — data kaunse-kaunse routers (stops) se guzar kar manzil tak pohancha. Yahan **IP Address** hi raasta decide karta hai.

---

## Layer 2 — Data Link Layer

**Kaam:** Data ko **local network ke andar** sahi device tak pohanchana — **MAC Address** use hota hai. Switch is layer pe kaam karta hai.

**Kahan exist karti hai:** Ghar ke andar, jab router/switch decide karta hai data **kaunse device (MAC address)** ko bhejna hai — ye Data Link Layer hai.

**Example:** Tumhare ghar mein 5 devices WiFi se jude hain. Jab data aata hai, **switch/router MAC address dekh kar** sahi device (tumhara mobile) ko bhejta hai — baaki devices ko nahi. Ye is layer ka kaam hai.

---

## Layer 1 — Physical Layer

**Kaam:** Sabse **neeche wali, asli hardware** layer — cables, WiFi signal, NIC — jo asal mein data ko **electric signal ya radio wave** ki shakl mein bhejte hain.

**Kahan exist karti hai:** LAN cable, WiFi ka signal (radio waves), NIC (Network Card) — ye sab **Physical Layer** hain. Ye sabse "asli/chhoo sakne wali" layer hai.

**Example:** Jab tumhara mobile WiFi router se signal pakadता hai (hawa mein radio waves ke zariye), ya jab LAN cable se computer joड-ते ho — ye Physical Layer ka kaam hai. Yahan koi "samajh" nahi, sirf **bijli/signal ka aana-jana** hai.

---

## Poora Safar — ek message ka OSI Layers se guzarna

Jab tum WhatsApp pe message bhejti ho, wo **upar se neeche** (Layer 7 se 1 tak) guzarta hai (bhejte waqt), aur doosre banda ke paas **neeche se upar** (Layer 1 se 7 tak) jata hai (receive karte waqt):

```
TUM (bhejti ho):
Application (message likha) 
  → Presentation (format/encrypt) 
    → Session (connection chalu) 
      → Transport (packets bane, port lagi) 
        → Network (IP se raasta mila) 
          → Data Link (MAC se local device tak) 
            → Physical (WiFi signal se nikla)

DOOSRA BANDA (receive karta hai) — ulta:
Physical (signal aaya) 
  → Data Link (MAC se pehchana) 
    → Network (IP se confirm) 
      → Transport (packets jode) 
        → Session (connection maintain) 
          → Presentation (format wapas normal) 
            → Application (message screen pe dikha)
```

**Example:** Jaise chitthi bhejna — tum **likhti** ho (Application), **lifafe mein band** karti ho (Presentation), **daak-khana** connection banata (Session), **parcel** mein todती (Transport), **address** dekh kar raasta (Network), **mohalle mein sahi ghar** (Data Link), aur **asli daak-gaadi** chalti hai (Physical). Doosri taraf ulta khulti hai.

---

## Quick Revision:

| # | Layer | Kaam | Real Example |
|:---:|---|---|---|
| 7 | Application | user seedha yahan kaam karta | browser mein google.com likhna |
| 6 | Presentation | format/encrypt karna | https ka taala, photo format |
| 5 | Session | connection chalu/band rakhna | website login session |
| 4 | Transport | packets, poora+sahi pohanchana (Ports yahan) | movie download poori aana |
| 3 | Network | raasta (IP se) | traceroute, router ka raasta |
| 2 | Data Link | local device tak (MAC se) | switch sahi mobile ko bhejta |
| 1 | Physical | asli hardware/signal | WiFi signal, LAN cable |
