# Networking Class 10 — ARP (Address Resolution Protocol)

## 1. ARP kya hai?
**ARP = Address Resolution Protocol.** Ye ek chhota "rule/tareeqa" hai jo **IP Address ko MAC Address mein badalne** ke kaam aata hai — sirf **local network (LAN) ke andar.**

**Kyun zaroori hai?** Yaad karo — IP address se pata chalta hai data **kis device** ko jana hai, par asal mein data bhejne ke liye **MAC address** chahiye hota hai (kyunki Data Link Layer MAC se hi kaam karti hai). To beech mein IP ko MAC mein badalne wala **ARP** kaam aata hai.

**Simple line:** ARP poochta hai — "ye IP address kis device ka hai? Mujhe uska MAC address chahiye."

---

## 2. Data kaise travel karta hai — bina kisi server ke (ARP ka poora process)

Yahan **koi server involve nahi hota** — ye sirf tumhare **ghar/office ke andar (LAN)** hota hai, jab ek device doosre local device se baat karna chahti hai.

**Example scenario:** Tumhara laptop, doosre device (jaise printer) ko data bhejna chahta hai — dono ek hi WiFi/network pe hain.

**Poora process (step by step):**

**Step 1 — Laptop ko IP pata hai, MAC nahi**
Laptop ko pata hai printer ka **IP address** (jaise `192.168.1.10`), par usse baat karne ke liye **MAC address** chahiye — jo abhi nahi pata.

**Step 2 — ARP Request (Broadcast)**
Laptop poore network mein **cheekh kar poochta hai** (ise "broadcast" kehte hain — sabko ek saath bhejna):
```
"Kis ke paas IP 192.168.1.10 hai? Apna MAC address batao!"
```
Ye message **sab devices** tak jata hai (printer, mobile, doosra laptop — sab ko).

**Step 3 — Sirf sahi device jawab deta hai**
Sab devices ye request sunte hain, par **sirf printer** (jiska IP `192.168.1.10` hai) jawab deta hai — baaki chup rehte hain (kyunki unka IP match nahi karta).

**Step 4 — ARP Reply**
Printer seedha laptop ko (is baar sabko nahi, sirf laptop ko — "unicast") jawab deta hai:
```
"Mera IP 192.168.1.10 hai, mera MAC address ye hai: AA:BB:CC:DD:EE:FF"
```

**Step 5 — Laptop yaad rakhta hai (ARP Cache/Table)**
Laptop is jawab ko apni ek chhoti list (**ARP Table/Cache**) mein **save** kar leta hai:
```
IP: 192.168.1.10  →  MAC: AA:BB:CC:DD:EE:FF
```
Ab agli baar laptop ko printer se baat karni ho, to **dobara poochne ki zaroorat nahi** — seedha table se MAC nikaal lega.

**Step 6 — Data bhejna**
Ab laptop ko MAC mil gaya hai, to seedha us MAC address pe **data bhej deta hai** — bina kisi server ke, sirf local network ke andar hi poora kaam ho gaya.

---

## 3. Example — poore ghar wala scene

Socho tumhare ghar mein 5 log hain, aur tumhe ek naye mehmaan (printer) ko kuch dena hai, par uska naam pata hai, chehra nahi pehchanti:

1. Tum poore kamre mein **zor se poochti ho**: "Jiska naam Ali hai, wo haath uthaye!" (**ARP Request — broadcast**)
2. Sab log sunte hain, par sirf **Ali haath uthata** hai (baaki chup)
3. Ali bolta hai: "Main Ali hoon, ye raha mera chehra" (**ARP Reply**)
4. Tum ab Ali ka **chehra yaad rakh lo** (**ARP Cache mein save**) — agli baar seedha pehchan logi, poochna nahi parega
5. Ab tum seedha Ali ko cheez de dеti ho (**data bhejna**)

---

## 4. ARP Table / ARP Cache kya hai?
**ARP Table (Cache)** = har device ke andar ek **chhoti list** jisme **IP + MAC** jode save hote hain — taake baar-baar poochna na pare.

```bash
arp -a          # apne computer ki ARP table dekho (kaunse IP-MAC yaad hain)
```

**Example output:**
```
IP: 192.168.1.10   MAC: AA:BB:CC:DD:EE:FF
IP: 192.168.1.15   MAC: 11:22:33:44:55:66
```

**Zaroori baat:** Ye table **hamesha ke liye nahi** rehti — thodे waqt (kuch minute) baad **khud khatam (expire)** ho jaati hai, taake purana/galat data na reh jaye. Phir zaroorat pade to dobara ARP Request hoti hai.

---

## 5. Broadcast vs Unicast (ARP mein dono use hote hain)

| Type | Matlab | ARP mein kahan |
|---|---|---|
| **Broadcast** | ek saath **sab** ko bhejna | ARP Request (sabse poochta) |
| **Unicast** | sirf **ek** device ko bhejna | ARP Reply (sirf poochne wale ko jawab) |

**Example:** Broadcast = poore kamre mein cheekh kar poochna (sab sunte). Unicast = sirf ek shakhs ke kaan mein jawab dena (sirf tumhe sunai deta).

---

## 6. ARP kyun zaroori hai? (asli faida)

- **Local network mein data bhejne** ke liye MAC chahiye, IP se kaam nahi chalta — ARP ye kaam karta hai
- **Server ki zaroorat nahi** — ye sirf tumhare apne network ke andar (bina internet ke bhi) ho jata hai
- **Table (cache) se speed** milti hai — baar-baar poochna nahi parta

**Yaad rakho:** ARP sirf **LAN (local network) ke andar** kaam karta hai — internet pe doosre mulk ke server se ARP nahi hota (wahan DNS aur IP kaam karte hain, jo humne pehle padha).

---

## Quick Revision:

| Cheez | Matlab |
|---|---|
| ARP | IP ko MAC mein badalne wala tareeqa |
| Kahan kaam karta | sirf LAN (local network) ke andar |
| ARP Request | broadcast — "ye IP kis ka hai?" (sabko poochta) |
| ARP Reply | unicast — sirf sahi device jawab deta |
| ARP Table/Cache | IP+MAC ki save ki hui list, thodе waqt baad expire |
| Broadcast | sabko bhejna |
| Unicast | sirf ek ko bhejna |
| Server involve? | nahi, ye sirf local devices ke beech hota |
