****Modular Conveyor Control with Fault Latching & Batch Counting****


**Industry / Application :** Material Handling / Packaging Line Simulation
**PLC Platform :** Siemens S7-1200 DC/DC/DC
**Programming Language :** Ladder Logic (LD)
**My Role :** Sole designer, Programmer and tester
**Project Duration :** Ongoing (iterative learning)


✓ Basic start/stop & E-stop
✓ Alignment fault with reset latch 
✓ Batch count (10 Products) with 10 sec dwell
✓ Batch count (20 Products) with 10 sec dwell


**📌 Problem Statement**

A conveyor must start/stop safely, detect belt misalignment, and require a manual reset after fault clearance. I will have 2 modes where in Mode-1 automatically pause every 10 products for 10 seconds and Mode-2 automatically pause every 20 products for 10 seconds.


**🧠 Core Logic Highlights**

Safety E-stop : Hardwired + logic interlock
Belt alignment detection : Both LS off while running → immediate stop
Latched fault + reset button : Prevents auto-restart after fault – real industrial requirement
Reset interlock : Motor cannot run even after fault fixed until reset pressed
Batch counter with dwell : Photo sensor → count 10 → motor stops 10 sec → auto resume
Batch counter with dwell : Photo sensor → count 20 → motor stops 10 sec → auto resume
Mode selector : There will be two modes to select the product count, i.e, 10 or 20 products
Idle stop : If there is no product on the belt for 10 sec the motor will be turned off



**Key I/O Used**
**Inputs**
Start PB, Stop PB, E-Stop
LS_Left, LS_Right (alignment)
Photo sensor (counting)
Reset PB
**Outputs**
Motor contactor


**📈 Result / Performance**
- Fault response time ~ < 1 scan cycle
- Counting accuracy ~ 10/10 products OR 20/20 products
- Reset required after fault ~ ✅ Yes (mimics safety relay behavior)
- Unattended batch cycling ~ ✅ Continuous

**🧪 Testing Performed**
- Start/stop with E-stop interrupt
- Simulated belt misalignment (both LS off) → motor stops → reset required
- 10 product count → 10 sec dwell → auto restart → loop verified
- 20 product count → 10 sec dwell → auto restart → loop verified
- Mode selector→ 1st mode: 10 products, 2nd mode: 20 products → if switched in between the other timer is reset and counts   from 0
- E-stop during counting → counting pauses, resumes correctly
