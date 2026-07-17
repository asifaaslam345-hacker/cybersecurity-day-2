# cybersecurity-day-2# CPU, Memory & Buses — Notes 🖥️

Study notes covering memory types, CPU internal working, system buses, and BIOS/POST — for Information Technology coursework.

---

## Table of Contents

1. [Memory Types aur CPU ka Basic Kaam](#1-memory-types-aur-cpu-ka-basic-kaam)
2. [Buses (CPU aur RAM k Darmiyan Lines)](#2-buses-cpu-aur-ram-k-darmiyan-lines)
3. [CPU ka Internal Kaam aur Data Traveling System](#3-cpu-ka-internal-kaam-aur-data-traveling-system)
4. [Example: Ctrl+S ka Case](#4-example-ctrls-ka-case)
5. [ROM aur BIOS](#5-rom-aur-bios)

---

## 1. Memory Types aur CPU ka Basic Kaam

### Volatile vs Non-Volatile Memory

| Memory | Type | Power Off hone par |
|---|---|---|
| **RAM** | Volatile | Data delete ho jata hai |
| **SSD** | Non-volatile | Data safe rehta hai |

### CPU, RAM aur SSD ka Relation

- CPU zyada kaam **RAM** k sath karwata hai (RAM se data lekar process karta hai).
- Jab hum koi data change karte hain (jaise kisi file ko edit karna), to yeh kaam **CPU aur SSD** k beech bhi hota hai.
- CPU RAM ko task **assign** karta hai, aur RAM aage SSD se related kaam karti hai.
- Yeh sara process direct nahi hota — beech mein CPU ki speed aur **cache** ka role hota hai, jo cheezon ko fast karta hai.

---

## 2. Buses (CPU aur RAM k Darmiyan Lines)

CPU aur RAM k darmiyan data **bus** k zariye travel karta hai (bus ek "rasta" hai jahan se data guzarta hai). CPU aur RAM k darmiyan total **3 lines (buses)** hoti hain:

| Bus | Kaam |
|---|---|
| **Address Bus** | Batata hai k data **"kahan"** hai ya kahan jana hai (location bataata hai) |
| **Data Bus** | **Actual data** ko transfer karta hai — **dono directions** (two-way) mein travel kar sakta hai |
| **Control Bus** | Batata hai k **"kya karna hai"** — operation kya hoga: read ya write |

---

## 3. CPU ka Internal Kaam aur Data Traveling System

### CPU ki Apni Fast Memory — Register

- CPU k andar ek **Register** hota hai, jo CPU ki sabse **fast memory** hoti hai.
- Register data ko temporarily store karta hai jab CPU us par kaam kar raha hota hai.

### RAM se CPU tak Data Kaise Jata Hai

1. Jab hum koi kaam start karte hain (jaise koi file open karna), pehle system **RAM** ko check karta hai.
2. Agar data RAM mein pehle se maujood hai, to wahin se mil jata hai.
3. Agar RAM **empty** hai (data nahi hai), to phir system **SSD** se data leta hai.
4. SSD se data ek certain **path** se guzar kar RAM tak pohanchta hai, aur RAM us data ko **fetch** karti hai.
5. Uske baad **CPU** us data ko:
   - **Fetch** karta hai (data ko le kar aata hai)
   - **Decode** karta hai (samajhta hai k kya karna hai)
   - **Execute** karta hai (actual kaam perform karta hai)

Yeh poora cycle **Fetch → Decode → Execute** kehlata hai, jo CPU baar baar repeat karta hai.

### Example: Calculation aur Result Store Hona

Jab CPU koi simple calculation karta hai (jaise addition, 5 + 8), to result nikalne k baad wo:

1. Pehle **Register** mein store hota hai — `13`
2. Phir **RAM** mein store hota hai
3. Agar permanent save karna ho to aakhir mein **SSD** mein store ho jata hai

---

## 4. Example: Ctrl+S ka Case

Jab hum kisi **Word file** par kaam kar rahe hote hain aur usmein type karte hain → data abhi sirf **RAM** mein hai (temporary).

- Agar **Ctrl+S** dabate hain → CPU us data ko RAM se leta hai aur SSD par write kar deta hai. Ab wo data **SSD** mein permanently save ho gaya hai (RAM mein nahi).
- Agar **Ctrl+S** nahi dabaein aur computer band ho jaye, to RAM ka wo data delete ho jayega, kyunki RAM kabhi permanent nahi hoti.

> **Key point:** RAM hamesha temporary hi store karti hai — chahe Ctrl+S karein ya na karein, RAM ka kaam sirf temporary storage hota hai jab tak power on hai. RAM kabhi bhi "permanent" nahi hoti.
>
> Jo cheez permanent karti hai wo **Ctrl+S** ka action hai — jo data RAM mein (temporary) tha, us data ki ek copy SSD mein likh di jati hai. Wo copy jo SSD mein gayi, wahi permanent ban jati hai (kyunki SSD **non-volatile** hai, power off hone k baad bhi wo data rehta hai).

---

## 5. ROM aur BIOS

- **ROM** ek type ki memory hoti hai.
- **BIOS** ek **code/program** hai jo is **ROM** k andar (ya kabhi kabhi ek chip jise EEPROM/Flash kehte hain) store hota hai.
- Yeh BIOS computer **start hote hi sabse pehle chalta hai** — RAM, operating system, ya kisi bhi software se pehle — aur basic instructions deta hai taake system boot ho sake.

### BIOS (Basic Input Output System) ka Kaam

1. **POST** (Power-On Self Test) karta hai — yani check karta hai k computer k saare parts (RAM, keyboard, hard disk, etc.) sahi se kaam kar rahe hain ya nahi.
2. Agar sab theek ho, to BIOS operating system ko dhundta hai (jaise Windows) jo storage (SSD/HDD) mein hota hai.
3. Phir wo operating system ko load karna start karta hai, taake computer aage boot ho sake.

### Analogy

Jaise koi ghar ka chowkidar subah sabse pehle uthta hai, ghar k saare darwaze/lights check karta hai (**POST**), phir baaki ghar walon (**operating system**) ko jaga kar apna kaam start karwata hai — bilkul waisay hi **BIOS** computer k saath karta hai.

---

### Quick Reference

​```
Fetch → Decode → Execute   (CPU cycle)
Register → RAM → SSD       (data permanence, fastest → slowest)
Address Bus | Data Bus | Control Bus   (CPU–RAM communication)
​```

---
