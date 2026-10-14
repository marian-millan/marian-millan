# Marian Millan’s Portfolio

## About me

Hi! I’m Marian, and I build things. From a custom MP3 player to a competition robot that competed at NASA Lunabotics, I’ve spent my time at NYU Tandon turning circuit ideas into working hardware. As the electrical team lead for our robotics team and Head TA for intro engineering, I’m as comfortable mentoring others as I am debugging a schematic at 2 a.m. My focus is embedded systems and circuit design, with experience in microcontrollers, PCB fabrication, and bringing ideas from breadboard to finished boards. I’m looking for opportunities to do meaningful hardware work at scale!

B.S. Electrical Engineering, NYU Tandon School of Engineering (Expected May 2028)
Electrical Team Lead, NYU Robotics Design Team
Head TA, Introduction to Engineering and Design

---

## Projects

### MP3 Player- Summer 2026

**Motivation**
I love music and wanted a way to listen to it without pulling out my phone every time. My friend and I decided to just build one ourselves, taking inspiration from the retro look and feel of Sony's Walkman.

**My Role**
We split the work depending on our strengths and majors. I handled all the hardware (schematic, component selection, and PCB layout), and he took care of the coding and custom 3D printed enclosure.

**Schematic Design**
I designed everything in KiCad, building the schematic around an ATmega328P, basically our own stripped-down Arduino Nano, paired with a DFPlayer Mini for audio playback and a jack socket. The power system took the most thought because I needed a USB-C charging circuit, battery protection, and a boost converter to bring the LiPo's 3.7V up to 5V for the microcontroller. On the user interface side, I added an OLED display, previous/next track buttons, and a rotary encoder for volume and pause.

**PCB Layout**
I went with a two-layer board and tried to keep the layout intentional rather than just functional. Peripherals are arranged along the edges, the volume encoder sits at the top, and all placement decisions (trace widths, bypass caps, clearances) were pulled directly from each component's datasheet. The retro aesthetic was always in the back of my mind throughout the layout process.

**Testing & Validation**

Once the board arrived, I probed the key nets with a multimeter to check for shorts before powering anything on. The DFPlayer kept resetting every few seconds, which I traced back to a misplaced decoupling capacitor that was too far from the chip. I hand-soldered a replacement closer to the component and noted it for the next revision. I also had to burn the bootloader onto the ATmega328P myself, using IC clips connected to an Arduino Uno set up as an ISP programmer.
After a few rounds of troubleshooting, the battery protection circuit, LiPo charging, and boost converter all validated successfully, and the power system performed as designed.
The whole process was tedious at times, but genuinely rewarding when the first song played through my headphones! For version 2, I'm planning better component placement and rethinking the programming method to improve the user experience.

**Video**

[MP3board (3).mp4](MP3board_(3).mp4)

**Schematic**

![image.png](image.png)

**PCB Layout**

![image.png](image%201.png)

**Finished Board**

![Screenshot 2026-06-20 212952.png](Screenshot_2026-06-20_212952.png)

![Screenshot 2026-06-20 212958.png](Screenshot_2026-06-20_212958.png)

### LUNA Rover

**Overview**
NYU's Robotics Design Team competes in NASA's Lunabotics Challenge every year, where student teams design, build, and operate a lunar excavator prototype capable of traversing extraterrestrial terrain and autonomously excavating regolith. The project follows NASA's Systems Engineering methodology and runs on Scrum, giving it a structure closer to an industry program than a typical student club.

**The Robot**
The excavator needed to handle three distinct functions: locomotion across uneven terrain, excavation of simulated lunar regolith, and deposition of the collected material. Each function was owned by a different subteam, which made integration the real engineering challenge.

**My Contribution**
I was part of the electrical and computer engineering subteam across two competition cycles. My work covered the full electrical system: wiring the robot end to end, integrating the locomotion, excavation, and deposition subsystems into a unified electrical architecture, and designing the custom PCBs that tied everything together. The control board and relay board (detailed in their own project entries) were both built for this robot.

Getting disparate subsystems built by different teams to communicate and operate reliably under competition conditions was the hardest part, and the most rewarding when it worked.

**Results**
Some results we're proud of for the 2026 edition: 

- 13th out of 47 university teams in construction
- Autonomous dig and dump fully operational during competition
- Won the award for lightest robot
- Our dust proofing was praised by engineers as the best across all teams

**Video**

[Rover operating live at NASA UCF Lunabotics Challenge 2026, driven through the control board I designed](RDT_Video.mp4)

Rover operating live at NASA UCF Lunabotics Challenge 2026, driven through the control board I designed

### Custom Relay Board and Teensy Control PCB for NASA Lunabotics Rover Spring 2025 and Spring 2026

**Overview**
These two boards worked together as the electrical foundation of our NASA Lunabotics rover. I designed both PCBs in KiCad: a Teensy-based control board that tied all the rover's subsystems together, and a relay control board that handled power distribution from our 24V and 12V batteries across the robot.

**Control Board**
The control board sat between the Teensy microcontroller and every major subsystem on the rover: load cells, motors, rotary encoders, and various sensors. I mapped out the GPIO assignments carefully from the start to avoid conflicts and leave room for changes as the rest of the team's subsystems evolved. Organized headers for each subsystem kept things modular, so we could plug in and debug components independently. Routing a mixed power and signal board on two layers required keeping noisy motor lines away from sensitive sensor traces, so I separated the power and signal domains intentionally and kept the layout readable for the whole team during integration. We assembled the board as a team, each handling soldering across both SMT and THT components. From there, we debugged GPIO conflicts and signal routing until everything communicated reliably.

**Relay Board**
The relay board handled power distribution and switching for the rover's subsystems. I designed the full schematic, selected components, and created custom footprints where needed. Trace widths and ground pours were sized for each subsystem’s current demands, with power integrity in mind throughout. Assembly was a team effort. We all soldered both SMT and THT components, then tested relay operation and verified power distribution before integration.

**Testing & Bring-up**
Both boards went through hands-on testing before competition. The control board took a few rounds of debugging to resolve GPIO conflicts, motor driver current, and signal routing issues. The relay board was validated for reliable switching and integrated into the rover's full electrical system (with an ESTOP) in time for competition.

**Control Board Schematic**

![image.png](image%202.png)

**Control Board Layout**

![image.png](image%203.png)

**Finished Control Board**

![image.png](image%204.png)

**Relay Board Schematic**

![image.png](image%205.png)

**Relay Board Layout**

![image.png](image%206.png)

**Finished Relay Board**

![image.png](d0b85eff-8a20-4004-91ac-f2b4cb413f06.png)

### Cooling Pillow- Spring 2025

**Overview**
JillowIce was my freshman year intro to engineering final project. The idea came from a simple observation: people sleep better on the cool side of the pillow, and traditional alarms are jarring. We wanted to fix both problems in one device.

**The Problem**
Standard pillows retain heat through the night, and clock alarms wake you (and everyone around you) abruptly. We set out to design a pillow that actively cools itself and wakes you up gently.

**Our Solution**
JillowIce circulates water through copper and vinyl tubing inside the pillow, cooled by a heat sink and fan. Four corner vibration motors deliver a silent alarm when the clock hits the set time. An Arduino handles the logic, with a WiFi sensor, temperature sensor, and a simple code flowchart driving the system.

**My Role**
This was a three-person team. I contributed to the design and build, working across the mechanical assembly, component integration, and testing. The project was a true intro to turning a concept into something physical.

**Outcome**
We successfully brought the temperature down and got the vibration alarm triggering on time. Future improvements we identified included adding a charging feature, a detachable system, and making the cooling circuit wireless and more robust.

**Images**

![Internal electronics and water-cooling system](image%207.png)

Internal electronics and water-cooling system

![image.png](image%208.png)

![Research Poster](image%209.png)

Research Poster

---

## Resume

[Marian Millán Resume Updated.pdf](Marian_Milln_Resume_Updated.pdf)