# Electrical System Documentation

## SECTION 1: POWER WIRING - INCOMER

### Circuit Purpose
Provides main 3-phase power input to the system with protection and voltage step-down for control circuits.

### Key Components and Functions:
- **Incoming Power**: 3-phase supply via conductors L1, L2, L3
- **Protection**:
  - MCB (-F1): Overcurrent and short circuit protection
- **Distribution**:
  - Terminal block X2: Distributes 3-phase power
- **Indication**:
  - Indicator lights (+H1, +H2, +H3): Phase energization status
- **Transformation**:
  - Isolation transformer (-T1): Steps down to control voltage (230V AC)
- **Output**:
  - Terminals P, N: Supply power to control circuit

---

## SECTION 2: POWER WIRING - MOTOR

### Circuit Purpose
Controls 3-phase motor with star-delta starting to reduce inrush current.

### Key Components:
- **Protection**:
  - MCB (-F3): Circuit protection
  - Overload relay (-F2): Motor overload protection
- **Contactors**:
  - Main (-Q1): Primary motor switch
  - Star (-Q2): Startup configuration
  - Delta (-Q3): Run configuration
- **Safety**:
  - PE connection: Fault current path

### Operation Sequence:
1. **Start**: -Q1 (main) and -Q2 (star) energize
2. **Transition**: Timer activates after delay
3. **Run**: -Q2 de-energizes, -Q3 (delta) energizes

---

## SECTION 3: CONTROL WIRING (Revised)

### Circuit Purpose
Manages contactor operation in power wiring with safety interlocks.

### Control Components:
- **Power Supply**: 230V AC (P, N)
- **Controls**:
  - Emergency stop (-S1)
  - Stop button (-S3)
  - Start button (-S4)
- **Protection**:
  - Overload relay contact (-S2)
- **Timing**:
  - Star-delta timer (-T1)
- **Indication**:
  - Running (-H5)
  - Off (-H4)
  - Overload (-H6)

### Critical Safety Feature: Electrical Interlocks
**Purpose**: Prevent simultaneous activation of star and delta contactors  
**Implementation**:
- Auxiliary NC contacts wired in series between -Q2 and -Q3
- Ensures one contactor must de-energize before the other can activate

**Why Essential**:
- Prevents dangerous short-circuit condition
- Protects equipment from damage
- Ensures proper motor starting sequence

### Operation Flow:
1. **Initiation**: Start button (-S4) pressed
2. **Start Mode**: -Q1 + -Q2 energized (Star configuration)
3. **Timing**: -T1 begins countdown
4. **Transition**: -T1 switches contactors
5. **Run Mode**: -Q1 + -Q3 energized (Delta configuration)
6. **Shutdown**: Via stop button, E-stop, or overload
