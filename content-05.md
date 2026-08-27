# Networking Class 05 — Hexadecimal to Binary aur IPv6

## 1. Hexadecimal kya hai?
IPv4 mein hum **decimal** (0-255) use karte the. IPv6 mein hum **Hexadecimal (Hex)** use karte hain.

**Farak samjho:**
- **Decimal** = 10 digits hote hain (0,1,2,3,4,5,6,7,8,9)
- **Hexadecimal** = 16 digits hote hain (0 se 9, phir A,B,C,D,E,F)

**Zaroori baat:** IPv4 ka har box (octet) **8-bit** ka tha. Hexadecimal ka har digit sirf **4-bit** ka hota hai.

---

## 2. Hexadecimal ke Digits (0 se F tak)

Jab 9 khatam ho jata hai, to hexadecimal mein letters use hote hain — har letter ek number ki jagah leta hai:

| Hex Digit | Decimal Value |
|:---:|:---:|
| 0 | 0 |
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |
| 4 | 4 |
| 5 | 5 |
| 6 | 6 |
| 7 | 7 |
| 8 | 8 |
| 9 | 9 |
| **A** | **10** |
| **B** | **11** |
| **C** | **12** |
| **D** | **13** |
| **E** | **14** |
| **F** | **15** |

**Yaad rakho:** A=10, B=11, C=12, D=13, E=14, F=15. Isse aage koi hex digit nahi hota (F sabse bada hai).

---

## 3. Master Table — Har Hex Digit ka Binary (4-bit)

Har hex digit ko binary mein badalne ke liye ek **4-bit table** use hoti hai — is baar values **8, 4, 2, 1** hain (kyunki sirf 4 bit hain, IPv4 ke 8-bit octet jaisa 128-64-32-16 nahi):

| Hex | Decimal | 8 | 4 | 2 | 1 | Binary |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **0** | 0 | 0 | 0 | 0 | 0 | `0000` |
| **1** | 1 | 0 | 0 | 0 | 1 | `0001` |
| **2** | 2 | 0 | 0 | 1 | 0 | `0010` |
| **3** | 3 | 0 | 0 | 1 | 1 | `0011` |
| **4** | 4 | 0 | 1 | 0 | 0 | `0100` |
| **5** | 5 | 0 | 1 | 0 | 1 | `0101` |
| **6** | 6 | 0 | 1 | 1 | 0 | `0110` |
| **7** | 7 | 0 | 1 | 1 | 1 | `0111` |
| **8** | 8 | 1 | 0 | 0 | 0 | `1000` |
| **9** | 9 | 1 | 0 | 0 | 1 | `1001` |
| **A** | 10 | 1 | 0 | 1 | 0 | `1010` |
| **B** | 11 | 1 | 0 | 1 | 1 | `1011` |
| **C** | 12 | 1 | 1 | 0 | 0 | `1100` |
| **D** | 13 | 1 | 1 | 0 | 1 | `1101` |
| **E** | 14 | 1 | 1 | 1 | 0 | `1110` |
| **F** | 15 | 1 | 1 | 1 | 1 | `1111` |

**Ye table kaise padho:** jahan `1` likha hai, us column ki value (8/4/2/1) jodo — decimal mil jayega.

**Example:** Digit **`6`** ki row dekho → `0,1,1,0` → jodo: `4+2 = 6` ✓. Binary = `0110`.

**Yaad rakhne ka short:** Har hex digit **hamesha 4 binary digits** banata hai. Ye poori table ek baar samajh lo, phir kabhi bhi kisi hex digit ko seedha uthake dekh sakti ho.

---

## 4. Example — 6 ko Binary mein badalna (poora tareeqa)

Chalo ek digit **step by step** karte hain, wahi subtraction wala tareeqa jo IPv4 mein kiya tha:

| Value | Check (6 mein se) | Result | Bacha |
|:---:|:---:|:---:|:---:|
| 8 | 6 ≥ 8 nahi | **0** | 6 |
| 4 | 6 ≥ 4 | **1** | 6−4=2 |
| 2 | 2 ≥ 2 | **1** | 2−2=0 |
| 1 | 0 ≥ 1 nahi | **0** | 0 |

**Result: 6 = `0110`**

Bilkul yehi tareeqa har hex digit (0 se F tak) pe chalta hai — bas values ab 8,4,2,1 hain (IPv4 wale 128,64,32,16 nahi).

---

## 5. IPv6 kya hai?

**IPv6** = internet address ka **naya, lamba tareeqa** — kyunki IPv4 ke sab addresses (0.0.0.0 se 255.255.255.255) khatam hone lage hain (duniya mein devices bohat badh gayi).

**IPv6 kaisa dikhta hai?**
```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

**Structure samjho:**
- IPv6 mein **8 groups** hote hain (colon `:` se alag)
- Har group mein **4 hexadecimal digits** hote hain
- Har group = 4 digits × 4 bit = **16 bit**
- Total = 8 groups × 16 bit = **128 bit** (IPv4 sirf 32 bit tha — isi liye IPv6 mein bohat zyada address ban sakte hain)

**Example (real IPv6 address):**
```
2001 : 0db8 : 85a3 : 0000 : 0000 : 8a2e : 0370 : 7334
```

---

## 6. IPv6 Address ko Binary mein Convert Karna (poora example)

Chalo upar wale address ka **pehla group `2001`** poora convert karte hain, digit-by-digit, master table se seedha uthake:

**Group 1 = `2001`**

| Hex Digit | Master Table se Binary |
|:---:|:---:|
| **2** | `0010` |
| **0** | `0000` |
| **0** | `0000` |
| **1** | `0001` |

**Result: `2001` = `0010 0000 0000 0001`**

---

**Ab poora address, saare 8 groups, ek saath (master table se seedha uthake):**

| Group | Hex | Binary (16-bit) |
|:---:|:---:|:---:|
| 1 | `2001` | `0010 0000 0000 0001` |
| 2 | `0db8` | `0000 1101 1011 1000` |
| 3 | `85a3` | `1000 0101 1010 0011` |
| 4 | `0000` | `0000 0000 0000 0000` |
| 5 | `0000` | `0000 0000 0000 0000` |
| 6 | `8a2e` | `1000 1010 0010 1110` |
| 7 | `0370` | `0000 0011 0111 0000` |
| 8 | `7334` | `0111 0011 0011 0100` |

**Poora IPv6 address binary mein:**
```
0010000000000001 : 0000110110111000 : 1000010110100011 : 0000000000000000 :
0000000000000000 : 1000101000101110 : 0000001101110000 : 0111001100110100
```

**Yaad rakho:** Har group ke 4 hex digits, master table (Section 3) se seedha dekh kar binary mil jate hain — koi lambi calculation nahi karni parti, bas table yaad ho to seedha uthao.

---

## 7. IPv4 vs IPv6 — quick farak

| Cheez | IPv4 | IPv6 |
|---|---|---|
| Format | Decimal (192.168.1.5) | Hexadecimal (2001:0db8::...) |
| Groups | 4 box (octet) | 8 groups |
| Har box/group | 8-bit | 16-bit (4 hex digit) |
| Total length | 32-bit | 128-bit |
| Digits ka type | 0-255 (numbers) | 0-9 + A-F (hex) |

---

## Quick Revision:

|Cheez| Matlab |
|---|---|
| Hexadecimal | 16 digits: 0-9, A-F |
| A / B / C / D / E / F | 10 / 11 / 12 / 13 / 14 / 15 |
| Har hex digit | 4-bit binary banata hai |
| Bit values (hex ke liye) | 8, 4, 2, 1 |
| IPv6 | naya, lamba address (128-bit) |
| IPv6 structure | 8 groups, har group 4 hex digit |
| Conversion tareeqa | master table se seedha dekho |
