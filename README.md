# Design and Simulation of a Programmable Medicine Reminder System Using ATmega328P

**Author:** [Student Name]  
**Registration Number:** [Registration Number]  
**Department of Electronics and Communication Engineering**  
**SRM Institute of Science and Technology, Chennai, India  
**Course:** 21ECC301P – Microprocessor, Microcontroller and Interfacing Techniques  
**Academic Year:** 2026–2027

## Abstract

Medication adherence is an important aspect of healthcare, particularly for individuals who need to follow regular medication schedules. Forgetting scheduled doses may affect the effectiveness of treatment and create difficulties for patients and caregivers. This paper presents the design and proposed simulation of a programmable medicine reminder system using the ATmega328P microcontroller. The system integrates a real-time clock (RTC), liquid crystal display (LCD), push buttons, a buzzer, and LED indicators to provide scheduled reminders. Users can configure reminder times, monitor the current time, and acknowledge alerts through a push button. The microcontroller compares the real-time clock readings with the programmed schedule and activates an audible and visual alert when a reminder is due. The design is intended to be evaluated using circuit simulation software, allowing the operation of the system to be examined before physical implementation. The proposed system aims to provide a simple, low-cost, and user-friendly reminder solution. Its functionality and reliability will be assessed through test cases involving time configuration, reminder activation, alert acknowledgement, and repeated reminders.

**Index Terms—** ATmega328P, medicine reminder, microcontroller, real-time clock, LCD, medication adherence, circuit simulation.

## I. INTRODUCTION

Regular medication is necessary for many individuals managing short-term and long-term health conditions. However, maintaining a consistent medication schedule can be challenging when several medicines must be taken at different times of the day. Busy routines, memory limitations, and the absence of timely reminders may contribute to missed or delayed doses.

Conventional reminder methods include written schedules, alarms on mobile phones, and assistance from caregivers. Although these methods can be useful, they may require repeated manual configuration or access to a separate device. A dedicated electronic reminder can provide a simple interface for scheduling alerts and communicating reminder status.

Microcontrollers provide a practical platform for implementing such systems because they can process time information, monitor user inputs, control display modules, and generate alerts. The ATmega328P is selected for this project because it supports digital input/output, timer operations, and communication interfaces suitable for interfacing with common electronic modules.

The proposed system uses a real-time clock module to maintain the current time, an LCD to display information, and a buzzer and LED to indicate when a programmed reminder is due. Push buttons provide a simple interface for configuring reminder times and acknowledging alerts.

### A. Problem Statement

Users who follow scheduled medication routines may forget a dose or lose track of the prescribed timing. A simple electronic system is therefore required to provide programmable reminders, display relevant time information, and notify the user through audible and visual alerts.

### B. Objectives

The objectives of the project are:

1. To design a medicine reminder system using the ATmega328P microcontroller.
2. To interface a real-time clock module for timekeeping.
3. To implement user-configurable medicine reminder times.
4. To display the current time and reminder status on an LCD.
5. To activate a buzzer and LED when a scheduled reminder occurs.
6. To provide a button-based acknowledgement mechanism.
7. To simulate the circuit and evaluate its operation using defined test cases.

### C. Scope and Limitations

The project focuses on scheduling and indicating medicine reminders. The proposed prototype does not automatically verify whether medicine has been consumed, determine suitable medication schedules, or replace medical advice. Its reliability depends on correct time configuration, appropriate software logic, and the availability of power.

## II. LITERATURE REVIEW AND EXISTING SYSTEMS

Medicine reminders can be implemented using manual schedules, mobile applications, programmable alarms, or embedded electronic devices. Each approach provides different levels of convenience and functionality.

### A. Conventional Reminder Methods

Written schedules and medication charts are inexpensive and easy to prepare. However, they depend on the user remembering to check the schedule and may not provide an immediate notification.

### B. Mobile-Based Reminder Systems

Mobile applications can support multiple reminders and notifications. Their effectiveness may depend on device availability, notification settings, battery condition, and user familiarity with the application.

### C. Microcontroller-Based Reminder Systems

Embedded reminder systems can combine timekeeping, display, input controls, and alarms in a dedicated device. They offer opportunities for customization and can operate without requiring a smartphone application.

### D. Research Gap

The proposed project focuses on implementing a straightforward, programmable reminder system using an ATmega328P and commonly available electronic modules. The design emphasizes simple controls, local timekeeping, audible and visual alerts, and simulation-based evaluation.

A full literature review should be supported by verified journal articles, conference papers, or other reliable publications. Specific prior-study results should not be claimed without consulting the original sources.

## III. PROPOSED SYSTEM AND METHODOLOGY

### A. System Overview

The proposed system consists of an ATmega328P microcontroller, a DS3231 real-time clock module, an LCD, push buttons, a buzzer, and LED indicators.

The RTC supplies the current time to the microcontroller. The user configures one or more reminder times through the input buttons. The microcontroller compares the current time against the saved schedule. When a reminder is due, it activates the alarm outputs and displays a notification. The user can acknowledge the alert to stop the buzzer.

### B. System Architecture

The functional architecture consists of the following blocks:

1. **Input block:** Push buttons for configuration and acknowledgement.
2. **Timekeeping block:** DS3231 RTC module.
3. **Processing block:** ATmega328P microcontroller.
4. **Display block:** LCD for time and reminder messages.
5. **Alert block:** Buzzer and LED indicators.
6. **Power block:** A suitable regulated supply for the selected components.

### C. Working Principle

After power-up, the microcontroller initializes the display, input pins, RTC communication, and alert outputs. It reads the current time and displays it on the LCD. The user enters a reminder time through the push buttons.

The controller repeatedly reads the RTC and checks whether the current time matches a reminder that has not already been triggered for that scheduled occurrence. When a match is detected, the system activates the buzzer and LED and displays an alert message. After acknowledgement, the buzzer is stopped and the system resumes monitoring.

To prevent an alert from being triggered repeatedly during the same minute, the program should maintain a record of the reminder occurrence that has already been processed.

### D. Algorithm

1. Start the system.
2. Initialize the microcontroller peripherals.
3. Initialize the RTC and LCD.
4. Read the current time from the RTC.
5. Display the current time.
6. Read button inputs and update the reminder schedule when requested.
7. Compare the current time with the configured reminders.
8. If a reminder is due and has not already been triggered, activate the buzzer and LED.
9. Display the reminder message.
10. Wait for user acknowledgement and stop the alert when acknowledged.
11. Continue monitoring the time and repeat the process.

### E. Design Considerations

The design should account for button debouncing, correct RTC communication, reliable reminder matching, and suitable output drive circuitry. Reminder events should be handled once per scheduled occurrence rather than repeatedly during every program loop.

If reminder settings must be retained after a power interruption, non-volatile storage can be added. The RTC backup battery can preserve timekeeping, but it does not automatically preserve reminder settings stored only in volatile memory.

## IV. HARDWARE AND SOFTWARE DESIGN

### A. ATmega328P Microcontroller

The ATmega328P is an 8-bit AVR microcontroller that provides digital input/output pins, timers, analog input capability, and serial communication peripherals. It processes the time information, reads the buttons, updates the display, and controls the alarm outputs.

An Arduino Uno can be used as a convenient development platform because it incorporates an ATmega328P in the standard Uno configuration. The final implementation must clearly identify the actual controller and board used.

### B. DS3231 Real-Time Clock

The DS3231 is a real-time clock module with an I²C interface. It maintains time and date information and supports battery-backed timekeeping when correctly configured. In this project, the RTC supplies the current time for comparison with the programmed reminders.

### C. LCD Display

A 16 × 2 character LCD can display the current time, configuration instructions, and reminder status. A compatible interface library can simplify the display routines.

### D. Push Buttons

Push buttons provide a low-cost user interface. Depending on the final design, separate buttons may be assigned to menu selection, increasing values, confirming entries, and acknowledging alarms. Internal or external pull-up resistors and software debouncing should be considered.

### E. Buzzer and LED Indicators

The buzzer provides an audible notification, while an LED provides a visual indication. The buzzer must be connected according to its current requirements; a transistor driver may be necessary if the buzzer exceeds the microcontroller pin's safe output capability.

### F. Software Tools

The program can be developed using the Arduino IDE and suitable libraries for the RTC and LCD. Circuit behavior can be evaluated in a compatible simulator, such as Proteus or Wokwi, depending on the availability of the required components and model support.

### G. Proposed Component List

| Component | Function |
|---|---|
| ATmega328P / Arduino Uno | Processing and control |
| DS3231 RTC | Real-time clock |
| 16 × 2 LCD | User interface |
| Push buttons | Configuration and acknowledgement |
| Buzzer | Audible alert |
| LED and resistor | Visual alert |
| Regulated power source | Circuit supply |
| Simulation software | Circuit verification |

## V. IMPLEMENTATION AND SIMULATION

### A. Circuit Implementation

The RTC is connected to the controller using the I²C interface. On a standard Arduino Uno using the ATmega328P, the I²C signals are available on A4 (SDA) and A5 (SCL). The LCD, buttons, buzzer, and LED are connected to suitable digital pins selected during circuit design.

The final schematic should include the actual pin assignments, supply connections, ground connections, and any required current-limiting or driver components. All modules must use compatible logic and supply voltages.

### B. Program Implementation

The program is organized into the following functional modules:

- Peripheral initialization.
- RTC time acquisition.
- LCD update routines.
- Button reading and debouncing.
- Reminder-time configuration.
- Scheduled-event comparison.
- Buzzer and LED control.
- Alert acknowledgement.
- Prevention of duplicate triggering.

A complete implementation should also define how invalid time settings, RTC communication errors, and power interruptions are handled.

### C. Simulation Procedure

1. Assemble the circuit in the selected simulation environment.
2. Load the controller program.
3. Configure the RTC time and date.
4. Enter a test reminder time.
5. Advance or configure the simulated clock to approach the reminder time.
6. Observe the LCD, buzzer, and LED outputs.
7. Acknowledge the alert and verify that the buzzer stops.
8. Repeat the test for different reminder times and document the results.

The simulator must support the required RTC behavior. If the selected environment cannot model the RTC adequately, a clearly documented simulated-time input can be used for functional testing.

## VI. RESULTS AND DISCUSSION

The system should be evaluated using a predefined set of test cases. The following table specifies the intended tests; the results must be filled in after running the simulation.

**TABLE I. PROPOSED FUNCTIONAL TEST CASES**

| Test | Input or condition | Expected behavior | Observed result |
|---|---|---|---|
| 1 | Power on | Initialization message appears | To be measured |
| 2 | RTC provides valid time | Current time is displayed | To be measured |
| 3 | User configures a reminder | Selected time is accepted | To be measured |
| 4 | Current time reaches a reminder | Buzzer and LED activate | To be measured |
| 5 | User acknowledges the alert | Buzzer stops | To be measured |
| 6 | Same scheduled minute continues | No repeated triggering | To be measured |
| 7 | Another reminder is reached | Corresponding alert activates | To be measured |
| 8 | RTC communication fails | Error is handled safely | To be measured |

### A. Performance Evaluation

The following metrics may be used to evaluate the prototype:

1. **Reminder activation correctness:** Whether the alert activates at the configured time.
2. **Reminder timing error:** The difference between the scheduled reminder time and the observed alert time.
3. **Acknowledgement response time:** The interval between pressing the acknowledgement button and stopping the alert.
4. **Duplicate-trigger count:** The number of unintended repeated alerts during a single scheduled occurrence.
5. **Successful test-case ratio:** The number of test cases passed divided by the total number of test cases executed, multiplied by 100%.

The results should be obtained from actual simulation runs. Performance claims should not be inferred solely from the intended design.

### B. Discussion

The simulation can establish whether the controller correctly reads the RTC, processes user inputs, displays reminder information, and activates the alarm outputs. It can also reveal issues related to button debouncing, time matching, and repeated triggering.

Simulation results alone do not establish clinical effectiveness, long-term hardware reliability, or whether users actually take their medicines.

## VII. CONCLUSION AND FUTURE SCOPE

This paper presents the design of a programmable medicine reminder system based on the ATmega328P microcontroller. The proposed architecture combines an RTC module, LCD, push buttons, buzzer, and LED indicators
