# 🏭 Modular Conveyor Control with Fault Latching & Batch Counting

![Status](https://img.shields.io/badge/status-complete-brightgreen)
![Difficulty](https://img.shields.io/badge/difficulty-intermediate-yellow)
![PLC](https://img.shields.io/badge/PLC-Siemens_S7--1200-blue)
![Language](https://img.shields.io/badge/Language-Ladder_Logic-orange)

---

## 📋 Project Information

| Field | Value |
|-------|-------|
| **Industry / Application** | Material Handling / Packaging Line Simulation |
| **PLC Platform** | Siemens S7-1200 DC/DC/DC |
| **Programming Language** | Ladder Logic (LD) |
| **My Role** | Sole designer, programmer, and tester |
| **Project Duration** | Ongoing (iterative learning) |

---

## ✅ Features Implemented

- ✓ Basic start/stop & E-stop
- ✓ Alignment fault with reset latch
- ✓ Batch count (10 products) with 10 sec dwell
- ✓ Batch count (20 products) with 10 sec dwell

---

## 📌 Problem Statement

> *A conveyor must start/stop safely, detect belt misalignment, and require a manual reset after fault clearance. Two modes are available:*
> - **Mode 1:** Automatically pause every 10 products for 10 seconds
> - **Mode 2:** Automatically pause every 20 products for 10 seconds

---

## 🧠 Core Logic Highlights

| Feature | Implementation |
|---------|----------------|
| **Safety E-stop** | Hardwired + logic interlock |
| **Belt alignment detection** | Both LS off while running → immediate stop |
| **Latched fault + reset button** | Prevents auto-restart after fault – real industrial requirement |
| **Reset interlock** | Motor cannot run even after fault fixed until reset pressed |
| **Batch counter with dwell (10 products)** | Photo sensor → count 10 → motor stops 10 sec → auto resume |
| **Batch counter with dwell (20 products)** | Photo sensor → count 20 → motor stops 10 sec → auto resume |
| **Mode selector** | Select between 10 or 20 product count |
| **Idle stop (starvation timer)** | If no product on belt for 10 sec → motor turns off |

---

## 🔌 Key I/O Used

| Inputs | Outputs |
|--------|---------|
| Start PB | Motor contactor |
| Stop PB | |
| E-Stop | |
| LS_Left (alignment) | |
| LS_Right (alignment) | |
| Photo sensor (counting) | |
| Reset PB | |
| Mode Selector (10/20) | |

---

## 📈 Results / Performance

| Metric | Outcome |
|--------|---------|
| Fault response time | < 1 scan cycle |
| Counting accuracy | 10/10 or 20/20 products |
| Reset required after fault | ✅ Yes (mimics safety relay behavior) |
| Unattended batch cycling | ✅ Continuous |

---

## 🧪 Testing Performed

- [x] Start/stop with E-stop interrupt
- [x] Simulated belt misalignment (both LS off) → motor stops → reset required
- [x] 10 product count → 10 sec dwell → auto restart → loop verified
- [x] 20 product count → 10 sec dwell → auto restart → loop verified
- [x] Mode selector → Mode 1: 10 products, Mode 2: 20 products → if switched in between, the timer resets and counts from 0
- [x] E-stop during counting → counting pauses, resumes correctly

---

## 📸 Screenshots

All 6 network ladder logic screenshots are in the [`02_Screenshots/`](02_Screenshots/) folder.

| Network | Function |
|---------|----------|
| Network 1 | Master start/stop with safety interlocks |
| Network 2 | Belt misalignment fault latch + reset |
| Network 3 | Counter to 10 products |
| Network 4 | 10-second dwell timer |
| Network 5 | Extended counter to 20 products |
| Network 6 | Starvation timer (no product for 10 sec → stop) |

---

## 🔜 Next Features Planned

- [ ] HMI screen with mode selection and fault history
- [ ] VFD speed control
- [ ] Data logging to SD card

---

## 📝 Author

**Afnan Jawad**

---

*Last updated: June 2026*
