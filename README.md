# Interfacing-DAC-with-8086
## 4. DAC Interfacing

### INTERFACING DAC WITH 8086 KIT AND GENERATING SAWTOOTH AND SQUARE WAVEFORMS

---

### AIM
To write an assembly language program in 8086 to generate Sawtooth and Square waveforms using DAC.

---

### APPARATUS REQUIRED

| S. No | Item                   | Specification     | Quantity |
|-------|------------------------|-------------------|----------|
| 1     | Microprocessor kit     | 8086              | 1        |
| 2     | Power Supply           | +5 V DC, +12 V DC | 1        |
| 3     | DAC Interface board    | -                 | 1        |

---

### ALGORITHM

#### Measurement of Analog Voltage
- Send the digital value to DAC  
- Read the corresponding analog value at its output  

#### Waveform Generation

**Square Waveform**
- Send low value (00H) to the DAC  
- Introduce suitable delay  
- Send high value (FFH) to DAC  
- Introduce delay  
- Repeat the above procedure  

**Sawtooth Waveform**
- Load low value (00H) to accumulator  
- Send this value to DAC  
- Increment the accumulator  
- Repeat until value reaches FFH  
- Repeat from beginning  

---

### PROGRAMS

#### Program: Square Wave

| Memory Location | Program        | Comments                        |
|-----------------|---------------|--------------------------------|
| 1000            | MOV AL,00H    | Load 00H in Accumulator        |
| 1003            | OUT 0C8H,AL   | Send through output port       |
| 1005            | CALL 1100     | Call delay program             |
| 1008            | MOV AL,0FFH   | Load FFH in Accumulator        |
| 100A            | OUT 0C8H,AL   | Send through output port       |
| 100D            | CALL 1100     | Call delay program             |

#### Delay Program

| Memory Location | Program     | Comments                      |
|-----------------|------------|-------------------------------|
| 1100            | MOV CX,0505| Load 0505H in register        |
| 1103            | DEC CX     | Decrement CX                  |
| 1105            | JNZ 1103   | Repeat until zero             |
| 1108            | RET        | Return to main program        |

---

#### Program: Sawtooth Wave

| Memory Location | Program Instruction | Comments                         |
|-----------------|--------------------|----------------------------------|
| 1000            | START: MOV AL,00H  | Load 00H in accumulator          |
| 1003            | LOOP: OUT 0C8H,AL  | Send through output port         |
| 1005            | INC AL             | Increment accumulator            |
| 1007            | JNC LOOP           | Repeat until carry occurs        |
| 1009            | JMP START          | Restart the process              |

---

### TABULATION

| Waveform  | Amplitude | Time Period |
|-----------|----------|-------------|
| Sawtooth  |          |             |
| Square    |          |             |

---

### MODEL GRAPH
**<img width="836" height="480" alt="image" src="https://github.com/user-attachments/assets/81014941-1542-495b-b3c7-c903198d5108" />**
# OUTPUT IMAGE OF DAC(SAWTOOTH WAVE FROM DSO AND SQUARE WAVE FROM DSO)
<img width="802" height="1600" alt="image" src="https://github.com/user-attachments/assets/722adcd1-bc79-4770-bfa0-40a2cd94d7cb" />
<img width="888" height="1553" alt="image" src="https://github.com/user-attachments/assets/18870c06-1d66-4807-96a8-3669da462cc1" />

# Result
Thus, the DAC was interfaced with 8086 and different waveforms were successfully generated

