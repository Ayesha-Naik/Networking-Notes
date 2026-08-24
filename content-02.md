# Networking Class 02 — Client-Server Model and Request Process

## 1. Client-Server Model 

**Client kya hota hai?**
Client = wo device (tumhara mobile/laptop) jo kisi cheez ki **request (maang)** karta hai. Client khud kuch data nahi rakhta — wo maangta hai.

**Server kya hota hai?**
Server = wo bada computer jo **data rakhta** hai aur client ki request pe wo data **wapas bhejta** hai. Server hamesha "on" rehta hai, request ka intezaar karta.

**Example:** Tum **hotel mein customer (client)** ho — khana maangti ho. Hotel ka **kitchen (server)** khana bana kar deta hai. Google.com ek server hai — tumhara mobile ek client hai jo us se page maangta hai.

**Ek line:** Client = maangne wala. Server = dene wala.

---

## 2. Full Process — Device se Google.com tak request:

Ab poora safar, step by step — pehle device connect hoti hai, phir IP milta hai, phir google khulta hai.

### Step 1 — Device WiFi se kaise connect hoti hai?
1. Tum apne mobile mein WiFi ka naam (jaise "Ayesha-WiFi") dekhti ho aur us pe click karti ho
2. Mobile router ko ek **"connect karna hai"** wala signal bhejta hai
3. Agar password sahi ho, to router mobile ko **connect kar leta hai**
4. Ab mobile aur router **jud gaye** (network ban gaya) — par abhi mobile ke paas IP nahi hai

### Step 2 — Router IP address kaise deta hai?
1. Connect hote hi mobile router se poochta hai: **"mujhe IP address do"** (ye DHCP request hai)
2. Router ke paas IP addresses ka ek **pool (dher)** hota hai
3. Router ek **khaali IP** (jaise `192.168.1.5`) mobile ko de deta hai
4. Router apni **table** mein likh leta hai: "IP `192.168.1.5` = is mobile (MAC address) ka"
5. Ab mobile ke paas IP hai — connection **poora ban gaya**

**Yahan tak:** Mobile ↔ Router connected, mobile ko IP mil chuka. Ab internet use karne ke liye tayyar.

### Step 3 — Router internet se kaise juda hai?
Router khud akela internet nahi banata — usse aage **ISP** (Internet company) se juda hota hai:
```
Router → cable → ISP ki yellow device (ghar ke bahar) → ISP ke bade servers → poora internet
```
Yani router ke paas internet **ISP se aata hai** (jo tumne pehli class mein padha tha).

### Step 4 — Tum google.com likhti ho, request kaise jaati hai?
1. Tum browser mein `google.com` likhti ho, Enter dabati ho
2. Tumhara mobile ye request pehle **router ko** bhejta hai
3. Router request ko **ISP ke router/server ko** bhejta hai
4. Beech mein **DNS** kaam karta hai — `google.com` (naam) ko uske **asli IP address** (number) mein badalta hai (kyunki internet naam se nahi, number se chalta)
5. Ab ISP wo request us IP (Google ka server) tak **poore internet ke raaste** se bhejta hai (kai routers se guzar kar)
6. Request Google ke **server** tak pohanch jaati hai

### Step 5 — Server jawab kaise deta hai, wapas kaise aata hai?
1. Google ka server request leta hai, samajhta hai "isko google.com ka page chahiye"
2. Server wo **page (data) tayyar** karta hai
3. Wapas bhejta hai — **usi raaste se ulta**: Server → internet ke raaste → ISP → tumhara router
4. Router ye data leta hai — ab usse pata karna hai ye data **kis device** ka hai

### Step 6 — Router data ko sahi device tak kaise pohanchata hai?
1. Router apni **table** (jo Step 2 mein banayi thi) check karta hai
2. Table mein likha hai: "IP `192.168.1.5` = is mobile ka"
3. Router samajh jata hai ye data isi mobile ke liye hai
4. Router data **sirf tumhare mobile ko** bhej deta hai (baaki devices ko nahi)
5. Tumhare browser mein **google.com ka page khul jata hai**

**Poora safar ek line mein:**
```
Mobile → Router (connect + IP mila) → ISP → DNS (naam→IP) → Internet ke raaste → Google Server 
→ (wapas) → ISP → Router (table se pehchana) → Mobile → Screen pe page khula
```

**Ye sab 1-2 second mein ho jata hai!**

**Example:** Jaise tum khana order karti ho — order (request) waiter (router) ke paas, waiter restaurant office (ISP) ko batata, kitchen (server) khana banata, wapas waiter se hote hue tumhare table (device) tak aata hai. Waiter jaanta hai kaunsा khana kis table ka hai — router bhi jaanta hai kaunsa data kis device ka hai (table ki wajah se).

---

## 3. Doosra Process — Bina Internet ke (sirf apne computer ke andar)

Ab jab tumhare paas **internet bilkul nahi** hai (WiFi off, koi server approach nahi ho raha), tab bhi jab tum apne computer/laptop pe kuch search/click karti ho, to computer ke **andar** ek process chalta hai. Ye internet wala process nahi — ye sirf **tumhare apne computer ke andar** hai.

**Jab tum apne computer mein kuch dhoondhti/click karti ho (bina internet):**
1. Tum koi command/click karti ho (jaise file dhoondhna, ya koi app kholna)
2. Ye request tumhare computer ke **OS (Operating System)** ke paas jaati hai
3. OS us request ko samajhta hai — "isko kya chahiye"
4. OS **CPU** ko hukum deta hai kaam karne ka
5. CPU **Fetch → Decode → Execute** cycle se kaam karta hai (jo humne pehle padha tha)
6. Agar file chahiye ho, to OS **Hard Disk/SSD** se file **RAM** mein laata hai
7. Kaam poora hota hai, result **screen** pe dikh jata hai

**Farak (internet wale process se):**
- **Internet wala process** = tumhara device se **bahar** (router, ISP, doosre server tak) jaata hai
- **Ye process** = sab kuch tumhare **apne computer ke andar** hota hai (bahar kahin nahi jata)

**Example:** Internet wala process = tum kisi ko chitthi bhejti ho, wo doosre sheher (server) tak jaati hai aur jawab aata hai. Ye (bina internet wala) process = tum apne ghar ke andar hi almari se kitaab (file) nikaal kar padh rahi ho — kahin bahar jaane ki zaroorat nahi, sab ghar (computer) ke andar hi ho gaya.

**Ek line:** Internet ka kaam = device se baahar (network) tak jaana. Bina internet ka kaam = sab kuch computer ke **andar hi** (CPU, RAM, Disk ke beech) ho jata hai.

---

## 4. Mobile Data (Sim Package) — kya WiFi jaisa hi hota hai?

Jab tum **WiFi ke bajaye mobile data (sim package)** use karti ho, to "Router" hota hi nahi is scenario mein. To phir process kaise hota hai?

**Jawab:** Process wahi hai, bas **Router ki jagah Mobile Tower** aa jata hai.

| WiFi wala | Mobile data wala |
|-----------|-------------------|
| Mobile → **ghar ka Router** | Mobile → **Mobile Tower** |
| Router → ISP (cable se)     | Tower → seedha mobile company ke network mein |
| IP router deta hai          | IP mobile company (Jazz/Zong) deti hai |

**Baaki poora process same hai** — DNS se naam ko IP mein badalna, request server tak jaana, jawab wapas aana — kyunki mobile company (Jazz/Zong/Telenor) khud bhi ek **ISP** hai (jaise PTCL ghar ko internet deta, waise Jazz mobile ko internet deta).

**Example:** WiFi wala tareeqa ek **ghar ka landline** hai (ek fix jagah se connect). Mobile data ek **mobile call** jaisा hai — kahin bhi ho, seedha tower se juड jaati ho, ghar ke router ki zaroorat nahi.

**Ek line:** WiFi mein beech mein "Router" hota hai. Mobile data mein "Mobile Tower" us jagah le leta hai — baaki sab (DNS, server tak jaana) **same** rehta hai.

---

## Ek nazar mein poora Class 2
| Step | Kya hota hai |
|------|---------------|
| Client | maangne wala (tumhara device) |
| Server | dene wala (Google ka computer) |
| Device→Router connect | WiFi se judna |
| Router→IP | DHCP se IP milta, table mein save |
| Request bhejna | Router→ISP→DNS(naam→IP)→Server |
| Jawab wapas | Server→ISP→Router |
| Router→Device | table se pehchan kar sahi device ko data |
| Bina internet process | sab computer ke andar hi (OS→CPU→RAM/Disk→screen) |
