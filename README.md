# tec-ATOM-SMASHER
TEC-1 atom smasher using a simple particle accelerator

ion radiation, xrays, mercury vapour, the tec-1 ---- danger, danger, Will Robinson !

## redesign project to make safe
* photo diode on NE
* no looking into peep hole as there is x-rays, put shielding 
* eliminate mercury vapour by replacing vacuum system, 
* eg https://www.instructables.com/Personal-Research-Project-Into-Ultra-High-Vacuum-P/
* https://groups.google.com/g/diybio/c/CDIE0M9UGhs/m/Xi9fYgmfAwAJ?pli=1
* 



![](https://github.com/SteveJustin1963/tec-ATOM-SMASHER/blob/master/pics/1.png)
![](https://github.com/SteveJustin1963/tec-ATOM-SMASHER/blob/master/pics/2.png)
![](https://github.com/SteveJustin1963/tec-ATOM-SMASHER/blob/master/pics/3.png)
![](https://github.com/SteveJustin1963/tec-ATOM-SMASHER/blob/master/pics/4.png)
![](https://github.com/SteveJustin1963/tec-ATOM-SMASHER/blob/master/pics/5.png)
![](https://github.com/SteveJustin1963/tec-ATOM-SMASHER/blob/master/pics/6.png)



# Laboratory Manual: Construction and Operation of a Safe Electrostatic Particle Accelerator

## Safety Warning
This manual describes the construction and operation of a high-energy particle accelerator. Only attempt this project under proper supervision and with appropriate safety measures in place. High voltage and radiation hazards are present.

## Required Safety Equipment
- Lead apron and gloves
- Safety goggles with side shields
- High-voltage insulated gloves (rated for 400kV)
- Radiation dosimeter
- Emergency shutdown switch
- Fire extinguisher (Class C for electrical fires)
- First aid kit
- Warning signs and barrier tape

## Required Tools and Materials

### High Voltage System
- Van de Graaff generator (350kV rating)
- High-voltage cables (rated for 400kV)
- Precision resistors (100MΩ, 1% tolerance)
- Capacitive voltage dividers
- Acrylic sheets (1" thickness)
- Silicone insulation tape

### Vacuum System
- Turbomolecular pump (capable of 10^-6 Torr)
- Digital vacuum gauge
- Stainless steel vacuum chamber
- ISO-KF flanges and fittings
- Copper gaskets
- Vacuum-rated electrical feedthroughs

### Control and Measurement
- Arduino Mega 2560
- Digital microammeter
- LCD display module
- Temperature sensors
- Pressure sensors
- Data logging shield
- Shielded cables

### Shielding Materials
- Lead sheets (5mm thickness)
- Lead glass viewing window
- Aluminum framework
- Interlocking panels

## Construction Procedure

### Phase 1: Basic Structure Assembly

1. Framework Construction
   - Assemble aluminum framework using 80/20 extrusions
   - Ensure framework is level and stable
   - Install ground connections at each corner

2. Vacuum Chamber Preparation
   - Clean all vacuum components with acetone
   - Install ISO-KF flanges on chamber
   - Pressure test all connections
   - Mount digital vacuum gauge

3. Van de Graaff Generator Installation
   - Mount generator on insulated base
   - Install protective acrylic enclosure
   - Connect high-voltage cables through feedthroughs

### Phase 2: Accelerator Tube Assembly

1. Prepare Copper Tube
   - Clean interior with acetone
   - Install resistor rings every 3 inches
   - Verify resistance between each ring

2. Voltage Gradient Assembly
   ```
   Resistor Installation Pattern:
   Ring 1 -> 100MΩ -> Ring 2 -> 100MΩ -> Ring 3...
   ```

3. Vacuum Connection
   - Attach tube to vacuum chamber
   - Install all gaskets
   - Perform initial vacuum test

### Phase 3: Control System Integration

1. Arduino Setup
   ```arduino
   // Basic monitoring program
   void setup() {
     Serial.begin(9600);
     pinMode(VACUUM_SENSOR, INPUT);
     pinMode(CURRENT_SENSOR, INPUT);
     pinMode(EMERGENCY_STOP, INPUT_PULLUP);
   }

   void loop() {
     if (digitalRead(EMERGENCY_STOP) == LOW) {
       shutdownSystem();
     }
     readSensors();
     updateDisplay();
     logData();
     delay(100);
   }
   ```

2. Sensor Installation
   - Mount temperature sensors at critical points
   - Install current monitoring system
   - Connect pressure sensors

3. Safety Interlock Integration
   - Wire door sensors
   - Connect emergency stop buttons
   - Test all safety cutoffs

## Operating Procedures

### Pre-Operation Checklist

1. Safety Verification
   - [ ] All personnel wearing proper PPE
   - [ ] Warning signs posted
   - [ ] Radiation badges in place
   - [ ] Emergency stops tested
   - [ ] Fire extinguisher accessible

2. System Checks
   - [ ] Vacuum level below 10^-5 Torr
   - [ ] All sensors reporting correctly
   - [ ] Cooling systems functional
   - [ ] Data logging system active

### Startup Procedure

1. Vacuum System
   ```
   a. Start roughing pump
   b. Monitor pressure until below 10^-3 Torr
   c. Start turbomolecular pump
   d. Wait for pressure to reach 10^-5 Torr
   ```

2. High Voltage
   ```
   a. Enable safety interlocks
   b. Power on Van de Graaff at minimum setting
   c. Increase voltage in 50kV increments
   d. Monitor current at each step
   ```

### Experiment Operation

1. Beam Control
   - Adjust focusing elements
   - Monitor beam current
   - Record all parameters

2. Data Collection
   ```python
   # Example data logging format
   data_entry = {
     'timestamp': time.now(),
     'voltage': voltage_reading,
     'current': current_reading,
     'pressure': vacuum_reading,
     'temperature': temp_reading
   }
   ```

### Shutdown Procedure

1. Normal Shutdown
   ```
   a. Reduce voltage to zero
   b. Turn off Van de Graaff
   c. Wait 10 minutes for discharge
   d. Stop turbomolecular pump
   e. Vent system slowly
   ```

2. Emergency Shutdown
   - Press any emergency stop button
   - Evacuate area if necessary
   - Follow radiation safety protocols

## Maintenance Schedule

### Daily
- Check vacuum seals
- Test safety interlocks
- Verify sensor readings
- Review log files

### Weekly
- Clean insulator surfaces
- Check resistor values
- Calibrate pressure gauges
- Test emergency systems

### Monthly
- Full system pressure test
- Resistor chain verification
- Calibrate all sensors
- Update software/firmware

## Troubleshooting Guide

### Vacuum Issues
1. Poor Vacuum Level
   - Check all seals
   - Verify pump operation
   - Look for virtual leaks

2. Pressure Fluctuations
   - Monitor temperature
   - Check for outgassing
   - Verify gauge calibration

### Electrical Problems
1. Voltage Instability
   - Check corona points
   - Verify resistor values
   - Look for discharge paths

2. Current Issues
   - Verify beam alignment
   - Check sensor calibration
   - Monitor vacuum quality

## Emergency Procedures

### High Voltage Emergency
1. Press emergency stop
2. Evacuate area
3. Contact safety officer
4. Document incident

### Radiation Emergency
1. Shut down system
2. Check dosimeter readings
3. Follow radiation protocol
4. File incident report

## Data Analysis

### Required Measurements
1. Beam Current vs. Voltage
2. Pressure vs. Time
3. Temperature Distribution
4. Radiation Levels

### Analysis Methods
```python
# Example analysis script
def calculate_efficiency(voltage, current):
    power_input = voltage * current
    beam_power = measure_beam_power()
    efficiency = beam_power / power_input
    return efficiency
```

## References
1. IEEE Standards for High Voltage Labs
2. Vacuum Technology Handbook
3. Radiation Safety Guidelines
4. Arduino Programming Guide

## Appendix

### Safety Certifications Required
- High Voltage Safety
- Radiation Safety
- Vacuum Systems
- Emergency Response

### Maintenance Log Template
```
Date:
Operator:
System Hours:
Maintenance Performed:
Parts Replaced:
Notes:
```

### Emergency Contact Information
- Laboratory Director: [Contact]
- Safety Officer: [Contact]
- Medical Emergency: [Contact]
- Radiation Safety: [Contact]


# diagram showing the redesigned accelerator setup with safety features and digital components.

1. Van de Graaff Generator Section:
- Enclosed in acrylic shielding
- Proper insulation and safety features
- Voltage monitoring system

2. Accelerator Tube:
- Precision resistor rings for uniform field gradient
- Complete lead shielding enclosure
- Vacuum-sealed connections

3. Vacuum System:
- Modern turbomolecular pump
- Digital vacuum gauge
- Proper connections and monitoring

4. Control System:
- Arduino-based monitoring
- Digital display interface
- Safety interlocks and monitoring

5. Safety Features:
- Emergency stop button
- Radiation monitoring
- Multiple safety shields
- Proper grounding

6. Additional Components:
- Clear labeling
- Digital monitoring systems
- Proper connection routing

![image](https://github.com/user-attachments/assets/7c238d02-08b7-411c-ba86-dc0534009186)



