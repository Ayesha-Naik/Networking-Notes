# Networking Class 04 — Router Working, IP Allocation, Packets, IPv4 Structure

## 1. Router kaise kaam karta hai?
**Router** ke 3 main kaam hote hain:
- **Connect karna** — devices ko network se jodna (WiFi/cable se)
- **IP dena** — har device ko apna unique IP (DHCP se)
- **Raasta dikhana (Routing)** — data ko sahi jagah bhejna (isi se naam "Router" — **route** = raasta)

**Example:** Router ek **chowk ka traffic controller** hai — decide karta hai kaunsi gaadi (data) kis raaste jaye, taake sab sahi jagah pohanchein.

---

## 2. Router IP kaise deta hai? Kahan store hota hai?

**Process (DHCP se):**
1. Device (mobile) router se judti hai (WiFi se)
2. Device poochti hai: "mujhe IP chahiye"
3. Router ke paas IP addresses ka ek **pool** hota hai — jaise `192.168.1.2` se `192.168.1.254` tak
4. Router ek **khaali IP** device ko de deta hai
5. Router us IP ko apni **table** mein save kar leta hai

**Router ki DHCP table (jaisi andar store hoti hai):**

| IP Address | Device (MAC) | Valid tak |
|---|---|---|
| 192.168.1.5 | mobile ka MAC | 24 ghante |
| 192.168.1.6 | laptop ka MAC | 24 ghante |

Jab device disconnect ho, router wo IP **wapas pool** mein daal deta hai.

**Public aur Private IP ka role:**
- Router **ghar ke devices** ko jo IP deta hai — wo **Private IP** hai (sirf ghar ke andar chalta)
- Router khud, bahar (internet) ki taraf, ek **Public IP** rakhta hai
- Jab tumhara device (Private IP) internet pe jata hai, router **NAT** se use Public IP mein badal deta hai

**Ek line:** Router andar sabko Private IP deta hai, bahar khud Public IP se pehchana jata hai.

---

## 3. Data Packets kya hain aur kaise travel karte hain?

**Data Packet** = internet pe data **chhote tukdon** mein toड kar bheja jata hai, har tukda ek Packet.

**Ek packet ke andar:**

| Hissa | Kya batata hai |
|---|---|
| Source IP | kahan se aaya |
| Destination IP | kahan jana hai |
| Data | asli cheez (chhota hissa) |
| Sequence number | ye kaunse number ka tukda hai |

**Packet ka safar:**
1. Badi file/message **chhote packets** mein toड di jati hai
2. Har packet apna **raasta khud dhoondta** hai
3. Har router packet ko **agle sahi router** ki taraf bhejta hai (Destination IP dekh kar)
4. Sab packets manzil (server) tak pohanch jate hain
5. Server unko **sequence number** se dobara sahi tarteeb mein **jod deta hai**

**Example:** Ek badi kitaab ko post karna ho, use chhote parcels mein baant do, har parcel pe number (1,2,3) likh do. Har parcel alag daak-gaadi se bhi jaa sakta, par sab ek hi pate pohanchte. Wahan number dekh kar sahi tarteeb mein jod diya jata hai.

---

## 4. IPv4 kya hai aur iski Structure (4-Box Concept)

**IPv4** = 4 numbers se bana address, dot (.) se alag:

| Box 1 | Box 2 | Box 3 | Box 4 |
|:---:|:---:|:---:|:---:|
| 192 | 168 | 1 | 5 |

**Har box (octet) ki khaasiyat:**
- Har box mein **0 se 255** tak koi bhi number ho sakta hai
- 4 box milkar poora IP address banaте hain
- Har box ko technical zabaan mein **"octet"** kehte hain

**Kyun 0-255 tak hi?** Har box **8-bit** (binary) ka hota hai, aur 8-bit mein sirf 0 se 255 tak hi numbers ban sakte hain.

**IPv4 ki poori range:** `0.0.0.0` se `255.255.255.255` tak.

---

## 5. Binary aur Decimal — IP Address ke andar

Computer sirf **0 aur 1 (Binary)** samajhta hai, par hum IP address **decimal** (192, 168) mein likhte hain. In dono ke beech convert karna zaroori hai.

### Bit Position Table (ye hamesha yaad rakho — fix rehti hai)

| Bit Position | 2⁷ | 2⁶ | 2⁵ | 2⁴ | 2³ | 2² | 2¹ | 2⁰ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **Value** | **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |

**Check:** `128+64+32+16+8+4+2+1 = 255` — isi liye har box max 255 tak jata hai.

---

### Decimal → Binary (Manual Subtraction Method)

**Tareeqa:** Bit table ki har value ko 128 se 1 tak, ek-ek karke check karo:
- Value ≤ bacha hua number → **1** likho, value ghata do
- Value > bacha hua number → **0** likho, aage badho

**Example — 192 ko Binary mein badlo:**

| Value | Check | Result | Bacha Number |
|:---:|:---:|:---:|:---:|
| 128 | 192 ≥ 128 | **1** | 192 − 128 = 64 |
| 64 | 64 ≥ 64 | **1** | 64 − 64 = 0 |
| 32 | 0 ≥ 32 nahi | **0** | 0 |
| 16 | 0 ≥ 16 nahi | **0** | 0 |
| 8 | 0 ≥ 8 nahi | **0** | 0 |
| 4 | 0 ≥ 4 nahi | **0** | 0 |
| 2 | 0 ≥ 2 nahi | **0** | 0 |
| 1 | 0 ≥ 1 nahi | **0** | 0 |

**Result: 192 = `11000000`**

---

### Poora IP Address Example — 192.168.1.5

**Box 2 = 168:**

| Value | Check | Result | Bacha |
|:---:|:---:|:---:|:---:|
| 128 | 168 ≥ 128 | **1** | 40 |
| 64 | 40 ≥ 64 nahi | **0** | 40 |
| 32 | 40 ≥ 32 | **1** | 8 |
| 16 | 8 ≥ 16 nahi | **0** | 8 |
| 8 | 8 ≥ 8 | **1** | 0 |
| 4 | 0 | **0** | 0 |
| 2 | 0 | **0** | 0 |
| 1 | 0 | **0** | 0 |

**Result: 168 = `10101000`**

**Box 3 = 1:** → sirf aakhri jagah 1, baaki sab 0 → **Result: `00000001`**

**Box 4 = 5:**

| Value | Check | Result | Bacha |
|:---:|:---:|:---:|:---:|
| 128 | nahi | 0 | 5 |
| 64 | nahi | 0 | 5 |
| 32 | nahi | 0 | 5 |
| 16 | nahi | 0 | 5 |
| 8 | nahi | 0 | 5 |
| 4 | 5 ≥ 4 | **1** | 1 |
| 2 | 1 ≥ 2 nahi | **0** | 1 |
| 1 | 1 ≥ 1 | **1** | 0 |

**Result: 5 = `00000101`**

**Poora IP `192.168.1.5` binary mein:**

| Decimal | 192 | 168 | 1 | 5 |
|---|:---:|:---:|:---:|:---:|
| **Binary** | `11000000` | `10101000` | `00000001` | `00000101` |

---

### Binary → Decimal (ulta process)

Jahan bhi `1` ho, us jagah ki **value jod** do:

**Example: `11000000`**

| Bit | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Value | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

Jahan 1 hai wahan jod do: `128 + 64 = 192` ✓

**Example: `10101000`**

| Bit | 1 | 0 | 1 | 0 | 1 | 0 | 0 | 0 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Value | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

`128 + 32 + 8 = 168` ✓

---

### Yaad rakhne ka short tareeqa
1. **Table yaad karo:** 128, 64, 32, 16, 8, 4, 2, 1
2. **Decimal → Binary:** baari-baari poocho "ye value ghat sakti hai?" — ha to 1 (ghatao), na to 0
3. **Binary → Decimal:** jahan 1 ho, us jagah ki value jod do
4. Har IP ke 4 box aise hi alag-alag karne hote hain

---

## 6. Default Gateway aur Subnet Mask

### Default Gateway kya hai?
**Default Gateway** = router ka **Private IP** (jaise `192.168.1.1`) jo local network ka "bahar jaane ka darwaza" hai. Data ghar se **bahar (internet)** jaane se pehle isi se guzarta hai.

**Example:** Default Gateway = ghar ka **mukhya darwaza** — andar kahin bhi ho, bahar jaane ke liye isi se guzarna parta hai.

### Subnet Mask kya hai?
**Subnet Mask** (jaise `255.255.255.0`) batata hai IP ka **kitna hissa network ka hai, aur kitna device ka.**

**Example:** `255.255.255.0` ka matlab — pehle 3 box (network ka pata) fix hain, sirf **aakhri box** (0-255) devices ke liye khaali hai. Yani is network mein 254 tak devices aa sakte hain.

---

## Quick Revision:

| Cheez | Matlab |
|---|---|
| Router ke kaam | connect, IP dena, raasta dikhana |
| DHCP table | router ki list — kaunsа IP kis device ka |
| Private IP | router andar sabko deta |
| Public IP | router khud bahar isi se pehchana jata |
| Data Packet | data ke chhote tukde (Source, Destination, number) |
| IPv4 | 4 box (octet), har box 0-255 |
| Bit Position Table | 128, 64, 32, 16, 8, 4, 2, 1 |
| Decimal→Binary | value ghat sake to 1, warna 0 |
| Binary→Decimal | jahan 1 ho wahan value jod do |
| Default Gateway | router ka IP — bahar jaane ka darwaza |
| Subnet Mask | batata hai network kitna bada hai |
