# Hi, I'm Marian

**Electrical Engineering @ NYU Tandon** · Embedded Systems · Circuit & PCB Design

I love building things. From a custom MP3 player to a rover that competed at NASA Lunabotics, I've spent my time at NYU Tandon turning circuit ideas into working hardware. As electrical team lead for the NYU Robotics Design Team and Head TA for Intro to Engineering, I'm as comfortable mentoring others as I am debugging a schematic at 2 a.m.

My focus is embedded systems and circuit design: microcontrollers, PCB design and fabrication, and taking ideas from breadboard to finished board. I'm looking for opportunities to do meaningful hardware work at scale.

- **B.S. Electrical Engineering**, NYU Tandon School of Engineering (expected May 2028)
- **Electrical Team Lead**, NYU Robotics Design Team
- **Head TA**, Introduction to Engineering and Design
- [Resume](Marian_Milln_Resume_Updated.pdf)

### Tools & Skills

`KiCad` · `Schematic Capture` · `2-Layer PCB Layout` · `SMT & THT Soldering` · `ATmega328P` · `Teensy` · `Arduino` · `ISP Programming` · `Power Electronics (LiPo charging, boost conversion, relays)` · `Board Bring-up & Debugging`

---

## Projects

| Project | When | Highlights |
|---|---|---|
| [MP3 Player](#mp3-player) | Summer 2026 | Custom ATmega328P board, USB-C LiPo charging, boost converter |
| [LUNA Rover — NASA Lunabotics](#luna-rover--nasa-lunabotics) | 2025–2026 | Full rover electrical system, 13th of 47 in construction |
| [Teensy Control & Relay PCBs](#teensy-control-board--relay-board) | Spring 2025 & 2026 | Mixed-signal control board + 24V/12V power distribution |
| [JillowIce Cooling Pillow](#jillowice-cooling-pillow) | Spring 2025 | Water-cooled pillow with silent vibration alarm |

---

## MP3 Player
*Summer 2026*

**Motivation**
I love music and wanted a way to listen without pulling out my phone every time. So a friend and I built our own, inspired by the retro look and feel of Sony's Walkman.

**My Role**
We split the work by strengths: I owned all the hardware (schematic, component selection, and PCB layout), while he handled the firmware and the custom 3D-printed enclosure.

**Schematic Design**
I designed the board in KiCad around an **ATmega328P** (essentially our own stripped-down Arduino Nano), paired with a **DFPlayer Mini** for audio playback and a headphone jack.

- **Power:** the part that took the most thought — a USB-C charging circuit, LiPo battery protection, and a boost converter stepping the battery's 3.7V up to 5V for the microcontroller.
- **User interface:** an OLED display, previous/next track buttons, and a rotary encoder for volume and pause.

**PCB Layout**
A two-layer board where I aimed for intentional, not just functional. Peripherals run along the edges with the volume encoder up top, and trace widths, bypass capacitors, and clearances all came straight from each component's datasheet. The retro aesthetic stayed in the back of my mind throughout.

**Testing & Validation**
- Probed key nets with a multimeter to check for shorts before first power-on.
- Tracked down a DFPlayer that kept resetting every few seconds to a decoupling capacitor placed too far from the chip. I hand-soldered a replacement closer in and logged it for the next revision.
- Burned the bootloader onto the ATmega328P myself, using IC clips and an Arduino Uno configured as an ISP programmer.
- After a few rounds of troubleshooting, the battery protection, LiPo charging, and boost converter all validated — the power system performed as designed.

It was tedious at times, but hearing the first song play through my headphones made it all worth it.

**Next revision:** improved component placement and a friendlier programming method.

**Demo**

[Watch the board in action](MP3board_(3).mp4)

| Schematic | PCB Layout |
|---|---|
| ![MP3 player schematic](image.png) | ![MP3 player PCB layout](image%201.png) |

**Finished Board**

<p>
  <img src="Screenshot_2026-06-20_212952.png" alt="Finished MP3 player board, view 1" width="48%">
  <img src="Screenshot_2026-06-20_212958.png" alt="Finished MP3 player board, view 2" width="48%">
</p>

---

## LUNA Rover — NASA Lunabotics
*2025–2026*

**Overview**
Every year, NYU's Robotics Design Team competes in NASA's Lunabotics Challenge, where university teams design, build, and operate a lunar excavator prototype that can traverse extraterrestrial terrain and autonomously excavate regolith. The project follows NASA's Systems Engineering methodology and runs on Scrum, making it feel closer to an industry program than a typical student club.

**The Robot**
The excavator has three core functions — **locomotion** over uneven terrain, **excavation** of simulated lunar regolith, and **deposition** of the collected material. Each is owned by a different subteam, which makes integration the real engineering challenge.

**My Contribution**
Across two competition cycles on the electrical and computer engineering subteam, I worked on the rover's full electrical system:

- Wired the robot end to end
- Integrated the locomotion, excavation, and deposition subsystems into one unified electrical architecture
- Designed the custom PCBs that tie it all together — the [control board and relay board](#teensy-control-board--relay-board)

Getting subsystems built by different teams to communicate and run reliably under competition conditions was the hardest part, and the most rewarding when it all came together.

**2026 Results**
- **13th of 47** university teams in construction
- **Autonomous dig and dump** fully operational during competition
- **Lightest Robot** award
- Dust-proofing praised by competition engineers as the **best across all teams**

**Demo**

[Rover operating live at the NASA Lunabotics Challenge 2026 at UCF, driven through the control board I designed](RDT_Video.mp4)

---

## Teensy Control Board & Relay Board
*NASA Lunabotics Rover · Spring 2025 & Spring 2026*

**Overview**
These two boards form the electrical foundation of our Lunabotics rover. I designed both in KiCad: a **Teensy-based control board** that connects all of the rover's subsystems, and a **relay board** that distributes power from our 24V and 12V batteries across the robot.

### Control Board
The control board sits between the Teensy microcontroller and every major subsystem: load cells, motors, rotary encoders, and assorted sensors.

- **GPIO planning:** mapped pin assignments up front to avoid conflicts and leave headroom as other subsystems evolved.
- **Modularity:** organized headers per subsystem so components could be plugged in and debugged independently.
- **Mixed-signal routing:** on a two-layer board, I deliberately separated power and signal domains to keep noisy motor lines away from sensitive sensor traces, while keeping the layout readable for the whole team during integration.

| Schematic | Layout | Finished Board |
|---|---|---|
| ![Control board schematic](image%202.png) | ![Control board layout](image%203.png) | ![Finished control board](image%204.png) |

### Relay Board
The relay board handles power distribution and switching for the rover's subsystems.

- Designed the full schematic, selected components, and created custom footprints where needed.
- Sized trace widths and ground pours to each subsystem's current demands, with power integrity in mind throughout.

| Schematic | Layout | Finished Board |
|---|---|---|
| ![Relay board schematic](image%205.png) | ![Relay board layout](image%206.png) | ![Finished relay board](d0b85eff-8a20-4004-91ac-f2b4cb413f06.png) |

### Assembly, Testing & Bring-up
We assembled both boards as a team, everyone soldering a mix of SMT and THT components.

- **Control board:** took several debugging rounds to resolve GPIO conflicts, motor driver current issues, and signal routing problems before everything communicated reliably.
- **Relay board:** validated for reliable switching and correct power distribution, then integrated into the rover's full electrical system — including the E-stop — in time for competition.

---

## JillowIce Cooling Pillow
*Spring 2025 · Intro to Engineering final project*

**The Problem**
People sleep better on the cool side of the pillow, but standard pillows trap heat through the night. And traditional alarms are jarring, waking you (and everyone around you) abruptly.

**Our Solution**
JillowIce solves both in one device:

- **Active cooling:** water circulates through copper and vinyl tubing inside the pillow, cooled by a heat sink and fan.
- **Silent alarm:** four corner vibration motors gently wake you at the set time.
- **Control:** an Arduino runs the logic, with a WiFi sensor, a temperature sensor, and a straightforward code flowchart driving the system.

**My Role**
On a three-person team, I contributed across design and build — mechanical assembly, component integration, and testing. It was my first real experience turning a concept into something physical.

**Outcome**
We successfully lowered the pillow's temperature and got the vibration alarm triggering on time. Future improvements we identified: a charging feature, a detachable system, and a wireless, more robust cooling circuit.

| Internal electronics & water cooling | Prototype | Research Poster |
|---|---|---|
| ![Internal electronics and water-cooling system](image%207.png) | ![JillowIce prototype](image%208.png) | ![JillowIce research poster](image%209.png) |

---

<p align="center"><i>Thanks for stopping by! Feel free to reach out if you're working on something hardware-related.</i></p>
