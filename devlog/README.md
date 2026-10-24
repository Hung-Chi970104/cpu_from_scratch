# Build log: 4-bit CPU from Complete Scratch

I've always dreamed of building a CPU from scratch, which means only transistors, resistors and
capacitors are allowed.

I posted these as devlogs on [Hack Club Flavortown](https://flavortown.hackclub.com/projects/2847) while building the project: 24 entries and 34 h 0 min of logged work, 28 Dec 2025 to 13 Mar 2026. The text is lightly edited for spelling and clarity; dates are UTC.

| # | Date | Logged | Entry |
|---|---|---|---|
| 1 | 28 Dec 2025 | 1 h 28 min | [First up: the adder](#1--first-up-the-adder) |
| 2 | 28 Dec 2025 | 1 h 5 min | [Breadboard AND and OR gates](#2--breadboard-and-and-or-gates) |
| 3 | 28 Dec 2025 | 1 h 8 min | [Learning the XOR gate](#3--learning-the-xor-gate) |
| 4 | 29 Dec 2025 | 2 h 10 min | [Gate schematics](#4--gate-schematics) |
| 5 | 29 Dec 2025 | 1 h 15 min | [Gate PCBs, ordered](#5--gate-pcbs-ordered) |
| 6 | 29 Dec 2025 | 1 h 17 min | [XOR schematic: diode or resistor?](#6--xor-schematic-diode-or-resistor) |
| 7 | 29 Dec 2025 | 31 min | [XOR PCB](#7--xor-pcb) |
| 8 | 29 Dec 2025 | 1 h 44 min | [Full-adder schematic](#8--full-adder-schematic) |
| 9 | 30 Dec 2025 | 1 h 11 min | [Simulating in KiCad](#9--simulating-in-kicad) |
| 10 | 30 Dec 2025 | 1 h 37 min | [Testing every case: one fails](#10--testing-every-case-one-fails) |
| 11 | 30 Dec 2025 | 51 min | [Found it: missing base resistors](#11--found-it-missing-base-resistors) |
| 12 | 30 Dec 2025 | 1 h 44 min | [The 4-bit adder, and fan-out](#12--the-4-bit-adder-and-fan-out) |
| 13 | 31 Dec 2025 | 1 h 7 min | [Full-adder PCB routed](#13--full-adder-pcb-routed) |
| 14 | 31 Dec 2025 | 2 h 16 min | [Subtraction and the SR latch](#14--subtraction-and-the-sr-latch) |
| 15 | 1 Jan 2026 | 1 h 31 min | [The 4-bit adder works](#15--the-4-bit-adder-works) |
| 16 | 1 Jan 2026 | 33 min | [The 4-bit adder as a sub-sheet](#16--the-4-bit-adder-as-a-sub-sheet) |
| 17 | 1 Jan 2026 | 1 h 27 min | [The subtractor won't cooperate](#17--the-subtractor-wont-cooperate) |
| 18 | 2 Jan 2026 | 1 h 43 min | [A better XOR, isolated gates, and the ALU](#18--a-better-xor-isolated-gates-and-the-alu) |
| 19 | 2 Jan 2026 | 1 h 40 min | [Panelising with V-cuts](#19--panelising-with-v-cuts) |
| 20 | 16 Jan 2026 | 2 h 18 min | [Soldering the gates](#20--soldering-the-gates) |
| 21 | 5 Feb 2026 | 2 h 3 min | [Final schematic](#21--final-schematic) |
| 22 | 12 Feb 2026 | 1 h 44 min | [Testing the first XOR gate](#22--testing-the-first-xor-gate) |
| 23 | 20 Feb 2026 | 1 h 14 min | [Routed](#23--routed) |
| 24 | 13 Mar 2026 | 23 min | [README, release and render](#24--readme-release-and-render) |

---

## 1 · First up: the adder
<sub>28 Dec 2025 · 1 h 28 min logged</sub>

I've finally started my journey towards a fully functional CPU. First up, the adder:

- A design that can add two numbers
- How binary is used
- How logic gates are built and used, including AND, OR, NAND, NOR and XOR

<p>
<img src="media/3765-1.jpg" width="49%">
<img src="media/3765-2.jpg" width="49%">
</p>

---

## 2 · Breadboard AND and OR gates
<sub>28 Dec 2025 · 1 h 5 min logged</sub>

Frustrating, but I finally finished my breadboard prototypes of the AND and OR gates. It was my
first time using transistors, so it took a fair while.

Things to watch out for:

- Put the LED and resistors on the collector side, both to pull up and to make sure current flows
  from base to emitter.
- Put resistors on both the transistors and the buttons. I burnt out two of them.

<p>
<img src="media/3783-1.jpg" width="49%">
<img src="media/3783-2.jpg" width="49%">
</p>

---

## 3 · Learning the XOR gate
<sub>28 Dec 2025 · 1 h 8 min logged</sub>

For the past hour I was learning how to build an XOR gate; it's essentially a NAND, an AND and an
OR together.

- Learning resource (Ben Eater, the GOAT): https://www.youtube.com/watch?v=sTu3LwpF6XI&t=1s
- It took a while to work out the circuit, because I didn't want to just copy it.

<p>
<img src="media/3797-1.jpg" width="49%">
<img src="media/3797-2.jpg" width="49%">
</p>

---

## 4 · Gate schematics
<sub>29 Dec 2025 · 2 h 10 min logged</sub>

Completed the schematics for the AND, OR, NAND and NOR gates. I can't believe how fast that went;
KiCad made it far easier than prototyping on a breadboard.

<p>
<img src="media/3901-1.png" width="70%">
</p>

---

## 5 · Gate PCBs, ordered
<sub>29 Dec 2025 · 1 h 15 min logged</sub>

Completed the PCB design for the four gates, and this time I also ordered the PCBs.

<p>
<img src="media/3917-1.png" width="32%">
<img src="media/3917-2.png" width="32%">
<img src="media/3917-3.png" width="32%">
</p>

---

## 6 · XOR schematic: diode or resistor?
<sub>29 Dec 2025 · 1 h 17 min logged</sub>

Finally completed the XOR gate schematic. Even after building it on the breadboard, I went back and
forth on whether to use a diode or a resistor. After some research I chose a diode, for these
reasons:

- A resistor does limit the current, but by R = V/I, so the voltage drop isn't fixed.
- A diode gives a fixed 0.7 V threshold, which stops current from leaking.

<p>
<img src="media/4091-1.png" width="70%">
</p>

---

## 7 · XOR PCB
<sub>29 Dec 2025 · 31 min logged</sub>

Completed the XOR gate's PCB, keeping it as compact as possible.

Next: time to build a full adder.

<p>
<img src="media/4100-1.png" width="49%">
<img src="media/4100-2.png" width="49%">
</p>

---

## 8 · Full-adder schematic
<sub>29 Dec 2025 · 1 h 44 min logged</sub>

Completed the full-adder schematic. Some of the changes:

- Added an inverter to each gate's output.
- Added diodes (I'm honestly still not sure whether diodes or resistors are better here).
- Created hierarchical sheets for the AND, OR and XOR gates, which turned out to be extremely
  useful.

<p>
<img src="media/4151-1.png" width="32%">
<img src="media/4151-2.png" width="32%">
<img src="media/4151-3.png" width="32%">
<img src="media/4151-4.png" width="32%">
</p>

---

## 9 · Simulating in KiCad
<sub>30 Dec 2025 · 1 h 11 min logged</sub>

I didn't know KiCad could simulate circuits. Big success. The truth tables I tested (input 1,
input 2, output):

- AND: (0, 0, 0), (1, 0, 0), (0, 1, 0), (1, 1, 1)
- XOR: (0, 0, 0), (1, 0, 1), (0, 1, 1), (1, 1, 0)

If you need the SPICE model for the 2N3904:
https://drive.google.com/file/d/1D6OUzF6kyITwRnlAD-tuOaJGhS3EWNvB/view

<p>
<img src="media/4307-1.png" width="49%">
<img src="media/4307-2.png" width="49%">
</p>

---

## 10 · Testing every case: one fails
<sub>30 Dec 2025 · 1 h 37 min logged</sub>

Fixed and tested all the truth tables for the schematic, and not all of them passed. Only one case
seemed to fail (the one with only Cin on), but for some reason no current was flowing through one of
the transistors in the XOR gate, so I had to investigate.

The images are all different cases, even though they look alike.

<p>
<img src="media/4503-1.png" width="32%">
<img src="media/4503-2.png" width="32%">
<img src="media/4503-3.png" width="32%">
<img src="media/4503-4.png" width="32%">
<img src="media/4503-5.png" width="32%">
<img src="media/4503-6.png" width="32%">
<img src="media/4503-7.png" width="32%">
<img src="media/4503-8.png" width="32%">
</p>

---

## 11 · Found it: missing base resistors
<sub>30 Dec 2025 · 51 min logged</sub>

I found the issue: I had forgotten resistors on the base of each transistor. I had only put
resistors directly after A, B and Cin, so the transistor bases in each sheet had none of their own,
which would burn them out.

<p>
<img src="media/4519-1.png" width="70%">
</p>

---

## 12 · The 4-bit adder, and fan-out
<sub>30 Dec 2025 · 1 h 44 min logged</sub>

For the past hour and a half I've been building a 4-bit adder, and fan-out is definitely my enemy:
the 5 V drops to 4.53 V because of the transistors. I tried adding two inverters at the end, but
that didn't help.

<p>
<img src="media/4609-1.png" width="49%">
<img src="media/4609-2.png" width="49%">
</p>

---

## 13 · Full-adder PCB routed
<sub>31 Dec 2025 · 1 h 7 min logged</sub>

Finished routing the full-adder PCB. I can't believe how compact it is compared with the breadboard
prototype.

<p>
<img src="media/4686-1.png" width="32%">
<img src="media/4686-2.png" width="32%">
<img src="media/4686-3.png" width="32%">
</p>

---

## 14 · Subtraction and the SR latch
<sub>31 Dec 2025 · 2 h 16 min logged</sub>

I spent a little over two hours learning about negative numbers (for subtraction) and the SR latch,
which is easily turned into a D latch. Why they matter:

- Negative numbers: subtraction is obviously essential.
- SR / D latch: SR stands for Set and Reset. Set makes the state 1 and Reset returns it to 0, and
  that property can be used to store data.

To make a positive number negative:

1. Invert every bit (7, which is 0111, becomes 1000).
2. Add one (1000 + 1 = 1001).

And 1001 represents −7, as the image shows. The image only covers the subtractor; I'll show how the
registers work in videos later.

<p>
<img src="media/4926-1.jpg" width="32%">
<img src="media/4926-2.png" width="32%">
<img src="media/4926-3.png" width="32%">
</p>

---

## 15 · The 4-bit adder works
<sub>1 Jan 2026 · 1 h 31 min logged</sub>

My 4-bit adder works perfectly, especially after adding buffers to each split. I spent the whole
session fixing it, because KiCad's SPICE doesn't really recognise GND: you have to use 0V instead.

<p>
<img src="media/4974-1.png" width="70%">
</p>

---

## 16 · The 4-bit adder as a sub-sheet
<sub>1 Jan 2026 · 33 min logged</sub>

Moved the whole circuit into a sub-sheet, so it's officially the 4-bit adder. I also recorded a
short video: https://hc-cdn.hel1.your-objectstorage.com/s/v3/226f3b5086f14841_2025-12-31_21-21-35.mkv

<p>
<img src="media/4983-1.png" width="49%">
<img src="media/4983-2.png" width="49%">
</p>

---

## 17 · The subtractor won't cooperate
<sub>1 Jan 2026 · 1 h 27 min logged</sub>

I spent an hour and a half on the subtractor, trying to complete the ALU, but KiCad was behaving
very strangely. The 4-bit adder works perfectly, yet the subtractor just won't cooperate.

<p>
<img src="media/5203-1.png" width="70%">
</p>

---

## 18 · A better XOR, isolated gates, and the ALU
<sub>2 Jan 2026 · 1 h 43 min logged</sub>

What I did over the past hour and a half:

- Learned and built another kind of XOR gate. It's better, because each input now drives one
  transistor instead of two.
- Designed an isolated AND gate schematic.
- Designed an isolated OR gate schematic.
- Simulated the ALU (adder plus subtractor).

This time every transistor has its own base resistor.

<p>
<img src="media/5529-1.png" width="32%">
<img src="media/5529-2.png" width="32%">
<img src="media/5529-3.png" width="32%">
</p>

---

## 19 · Panelising with V-cuts
<sub>2 Jan 2026 · 1 h 40 min logged</sub>

Time to test all my logic gates. I spent the past hour learning to use V-cuts, since the boards are
all very small and it isn't sensible to order each one separately. Merging the AND and OR gates was
tedious.

<p>
<img src="media/5558-1.png" width="32%">
<img src="media/5558-2.png" width="32%">
<img src="media/5558-3.png" width="32%">
</p>

---

## 20 · Soldering the gates
<sub>16 Jan 2026 · 2 h 18 min logged</sub>

I soldered the AND, OR, NAND and NOR gates. Because I forgot to cut the wires before powering them
on, I burnt the OR and NOR gates. The AND and NAND gates worked well:

- 10k resistors on the bases
- Diodes to stop current leaking

<p>
<img src="media/12642-1.jpg" width="70%">
</p>

---

## 21 · Final schematic
<sub>5 Feb 2026 · 2 h 3 min logged</sub>

I finalised the schematic after putting it off for a month (I got a little lazy). Next, I'll route
the full adder and order it. I also tested every case to make sure I get it right first time.

<p>
<img src="media/19824-1.png" width="70%">
</p>

---

## 22 · Testing the first XOR gate
<sub>12 Feb 2026 · 1 h 44 min logged</sub>

Tested my first-version XOR gate; unfortunately it didn't work as well as I'd hoped.

- 4.7 kΩ base resistors
- 1 kΩ pull-up

(I did this two days earlier but forgot to log it.)

▶ [Video (5.2 MB)](media/21856-1.mp4)

---

## 23 · Routed
<sub>20 Feb 2026 · 1 h 14 min logged</sub>

Routed everything and added some final touches.

<p>
<img src="media/24233-1.png" width="70%">
</p>

---

## 24 · README, release and render
<sub>13 Mar 2026 · 23 min logged</sub>

Updated the README and the release. This is honestly the best project I've ever made, even if it
looks a little intimidating. I also rendered it, and this is exactly how the final product will
look.

<p>
<img src="media/31002-1.png" width="70%">
</p>
