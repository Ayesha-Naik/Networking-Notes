# Networking Class 01 — Basics (Network, Router, IP, LAN/WAN)

## 1. Network kya hai?
**Network** = do ya zyada devices (computer, mobile, printer) jo aapas mein **jude** hon aur data (message, file) share kar saken.

**Example:** Tumhare ghar mein WiFi se laptop, mobile, TV sab jude hain aur aapas mein baat kar sakte hain — ye ek **network** hai. Bina jude, har device akela hai; jud jaayen to network ban gaya.

---

## 2. Network banane ke kitne tarike hain?
Network kai tareeqon se ban sakta hai:

**1. Wired (cable se):** Devices ko **LAN cable (wire)** se jodo. Tez aur mehfooz. (Office/lab mein)

**2. Wireless (WiFi se):** Bina cable, **WiFi signal** se jodo. Aasaan, ghar mein aam. (Mobile, laptop)

**3. Bluetooth se:** Chhoti duri ke liye (do phone, headphone)

**4. Router/Switch se:** Ek central device se kai devices jodo (sabse aam tareeqa)

**Yaad rakho:** network banane ke 2 main tareeqe — **wired** (cable) aur **wireless** (WiFi). Baaki inhi ke roop hain.

---

## 3. Networking kya hai?
**Network** = jude hue devices (cheez).
**Networking** = un devices ko **jodne, chalane aur manage karne ka poora kaam/tareeqa** (amal).

**Example:** Agar network ek "dosti" hai (do log jude), to networking us dosti ko "banana aur nibhana" (kaise judte, kaise baat karte, kaise chalti rehti) hai. Yani networking = network banane aur chalane ki poori vidya.

---

## 4. Router se network kaise banta hai? (WiFi ka example)
**Router** = wo device jo internet ko tumhare gharke sab devices tak pohanchata hai (WiFi ke zariye).

**Ghar ka poora scene:**
1. Tumhare ghar ke **bahar ek chhoti yellow device** dikhti hai — us mein se kai (jaise 5) taar (cables) nikalte hain jo alag-alag gharon ko jaate hain. **Ye device ISP (internet company) ka hai** — ye internet ko har ghar tak baant-ta hai. Isko aksar **splitter/junction box** ya ISP ka distribution point kehte hain.
2. Us yellow device se ek cable **tumhare ghar ke router** mein aata hai — ye router ko internet deta hai.
3. Router us internet ko **WiFi signal** bana kar tumhare ghar mein phaila deta hai.
4. Tumhare laptop, mobile us WiFi se judte hain — aur internet mil jata hai.

**Ek line mein:** Internet company (ISP) → bahar wali yellow device → cable se → tumhara router → WiFi → tumhare devices.

**Example:** Yellow device ek **paani ki bari tanki** jaisी hai jo mohalle ko paani (internet) deti hai. Har ghar mein ek chhota nal/motor (router) hai jo us paani ko ghar ke sab kamron (devices) tak pohanchata hai.

---

## 5. ISP kya hai?
**ISP = Internet Service Provider** = wo **company** jo tumhe internet **bechti/deti** hai (jaise PTCL, Jazz, Nayatel).

**Example:** Jaise bijli company ghar tak bijli laati hai, waise ISP ghar tak internet laata hai. Internet ISP ke bade servers se hote hue tumhare router tak aata hai.

**Poora raasta:** Internet (duniya) → ISP → bahar wali yellow device → tumhara router → tumhare devices.

---

## 6. Client-Server Model kya hai?
Internet pe do tarah ke computer hote hain:
- **Client** = jo **maangta** hai (tumhara laptop/mobile jab website kholta hai)
- **Server** = jo **deta** hai (Google, YouTube ka computer jo page bhejta hai)

**Example:** Tum **restaurant mein customer (client)** ho — khana maangti ho. Restaurant ka **kitchen (server)** khana bana kar deta hai. Internet pe bhi wahi — tum maangti ho (client), server deta hai.

**Ek line:** Client poochta hai, Server jawab deta hai.

---

## 7. MAC Address vs IP Address (detail mein)
Dono device ka "pata" hain, par alag tarah ke:

**MAC Address:**
- Device ke **network card ka permanent number** (factory mein fix)
- Kabhi nahi badalta
- Misaal: `00:1A:2B:3C:4D:5E`
- Ye device ki **hardware ID** hai

**IP Address:**
- Device ka **network mein pata** (jise network deta hai)
- **Badal sakta hai** (jagah/network badle to badal jaye)
- Misaal: `192.168.1.5`

**Farak (example se):**
- **MAC** = tumhara **CNIC/ID card number** — kabhi nahi badalta, hamesha wahi
- **IP** = tumhara **ghar ka abhi ka pata** — sheher badlo to pata badal jata

**Ek line:** MAC = permanent (hardware), IP = badalne wala (network deta hai).

### NIC (Network Interface Card) kya hai?
**NIC** = ek **hardware chip/card** (bilkul CPU, RAM ki tarah asli cheez) jo computer ke andar (motherboard pe) lagi hoti hai, aur jiski wajah se device network/internet se judta hai. Iske bina computer network se baat hi nahi kar sakta.

**Zaroori farak:**
- **IP aur MAC** = sirf **numbers** (pehchan/pata) — dikhte nahi
- **NIC** = **asli hardware** (chip) — jise haath se chhoo sakti ho, aur jispe MAC number likha hota hai

**2 tarah ke:** Wired NIC (LAN cable wala) aur Wireless NIC (WiFi wala).

**Example:** NIC ek **SIM card** jaisा hai. SIM asli cheez hai (haath mein pakad sakti ho) aur us pe ek number juda hota hai. NIC bhi asli chip hai, aur uspe MAC number juda hota hai. SIM bina phone network se nahi judta — NIC bina computer network se nahi judta. Yani NIC = kaan aur zubaan, jisse device network se sunta aur bolta hai.

```bash
ip a        # apne device ke NIC aur unke IP/MAC dekho
```

---

## 8. IP kaise milta hai — DHCP vs Manual
Device ko IP address 2 tareeqon se milta hai:

**DHCP (automatic):**
- Router **apne aap** har device ko IP de deta hai
- Tumhe kuch nahi karna, WiFi se jude aur IP mil gaya
- DHCP = **D**ynamic **H**ost **C**onfiguration **P**rotocol
- **Aam tareeqa** (ghar/office mein yehi hota)

**Manual (khud se):**
- Tum **khud haath se** IP set karti ho har device pe
- Mushkil, aur zyada dhyan chahiye
- Servers/khaas cases mein use hota

**Farak:**
- **DHCP** = router khud IP baant-ta hai (auto, aasaan)
- **Manual** = tum khud IP daalti ho (haath se, mushkil)

**Example:** DHCP = hotel mein pohanchte hi receptionist khud kamra number de deta hai (auto). Manual = tum khud jaa kar kamra chun kar number likhti ho (haath se).

---

## 9. Peer-to-Peer (P2P) Network kya hai?
**P2P** = jab devices **seedha ek doosre se** jude hon, beech mein koi server na ho. Har device dono kaam kar sakta — de bhi aur le bhi.

**Example:** Do laptop ko seedha ek cable ya Bluetooth se joड kar file share karna — ye P2P hai. Koi bada server nahi, dono barabar.

**Sawaal: Kya internet ke bina network ban sakta hai?**
**Haan!** Network aur internet **alag** cheezein hain:
- **Network** = jude hue devices (internet zaroori nahi)
- **Internet** = poori duniya ka sabse bada network

Tum ghar ke 2 computer bina internet ke bhi cable/WiFi se joड sakti ho — wo ek network hai (bas internet nahi). Yani **internet ke bina bhi network ban sakta hai.**

---

## 10. LAN, MAN, WAN (network ke types — size ke hisaab se)

**LAN (Local Area Network):**
- Chhota network — ek ghar, ek office, ek building
- Example: tumhare ghar ka WiFi network (LAN hai)

**MAN (Metropolitan Area Network):**
- Bada — poore **sheher** ka network
- Example: ek sheher ke kai offices ka juda network, ya sheher ki cable TV

**WAN (Wide Area Network):**
- Sabse bada — **sheher/mulk ke paar**
- Example: **Internet khud** sabse bada WAN hai (poori duniya juda)

**Yaad rakhne ka short:**
- **LAN** = chhota (ghar/office)
- **MAN** = sheher
- **WAN** = mulk/duniya (internet)

**Example:** LAN = tumhara **mohalla**. MAN = poora **sheher**. WAN = poora **mulk/duniya**. Jitna bada area, utna bada network.

---

## 11. Switch vs Hub (farak)
Dono kai devices ko jodne wale device hain, par tareeqa alag:

**Hub:**
- Jo data aata, use **sabko** bhej deta (bina soche)
- Dheema aur kam mehfooz (faltu traffic)
- Purana

**Switch:**
- Data **sirf sahi device** ko bhejta (MAC address dekh kar)
- Tez aur mehfooz (samajhdar)
- Aaj kal yehi use hota

**Farak (example):**
- **Hub** = ek aadmi jo har baat **poore kamre mein cheekh** kar bolta (sab sunein, faltu)
- **Switch** = ek aadmi jo baat **sirf us shakhs ke kaan mein** bolta jise kehni hai (samajhdar, tez)

**Ek line:** Hub = sabko bhejta (bewqoof). Switch = sirf sahi ko bhejta (samajhdar).

---

## 12. Router kaise IP address deta hai? (poora process)
Router ke andar ek chhota system hota hai (DHCP) jo IP address baant-ta hai. Process aise:

1. Tumhara device (mobile) WiFi se **judne ki request** bhejta hai
2. Router (DHCP) ke paas IP addresses ka ek **pool (dher)** hota hai — jaise 192.168.1.2, .3, .4... waghera
3. Router us pool mein se ek **khaali IP** utha kar tumhare device ko de deta hai
4. Router us IP ko apni **table (list)** mein **save** kar leta hai — "ye IP is device (MAC) ko diya"
5. Ab jab tumhara device data bhejta/leta hai, router us table se pehchan leta hai ke kaunsा IP kis device ka hai
6. Jab device disconnect ho jaye, router wo IP **wapas** le kar pool mein daal deta hai (doosre ko de sake)

**Router ki table (kitni devices?):** Router apni memory mein ek list rakhta hai jisme har jude device ka **MAC + IP** hota hai. Ek normal router 100-250 tak devices sambhal sakta hai (model pe depend).

**Example:** Router ek **parking wala** hai. Har aane wali gaadi (device) ko ek **parking number (IP)** deta hai, aur apni copy (table) mein likh leta hai "ye number is gaadi ka". Gaadi chali jaye to wo number wapas le kar doosri gaadi ko de deta hai. Aise router har device ko alag IP deta aur yaad rakhta hai.

---

## Quick Revision:
| Cheez | Matlab |
|-------|--------|
| Network | jude hue devices |
| Networking | network banane/chalane ka kaam |
| Router | internet ko WiFi bana kar phailata |
| ISP | internet dene wali company |
| Client / Server | maangne wala / dene wala |
| MAC / IP | permanent ID / badalne wala pata |
| NIC | asli hardware chip jisse device network se judta |
| DHCP / Manual | auto IP / haath se IP |
| P2P | seedha device-to-device (bina server) |
| LAN / MAN / WAN | ghar / sheher / duniya |
| Hub / Switch | sabko bhejta / sirf sahi ko bhejta |
| Router IP process | pool se IP deta, table mein save karta |
