# Matter EFR32 Dishwasher Example

## Software

[Matter EFR32 Dishwasher Example 2.3.0-1.3](https://github.com/SiliconLabs/matter/tree/release_2.3.0-1.3/silabs_examples/dishwasher-app/silabs):
An example showing the use of Matter on the Silicon Labs EFR32 MG12 and MG24 boards.


## Hardware

 - [Silicon Labs xG24 Explorer Kit](https://www.silabs.com/development-tools/wireless/efr32xg24-explorer-kit?tab=overview)
   - [Buy EFR32xG24 Explorer Kit](https://www.digikey.com/en/product-highlight/s/silicon-laboratories/efr32xg24-explorer-kit): $39.39


## Dishwasher Clusters

### Clusters on Endpoint 1 / Device Type(s): Dishwasher

- OperationalState Cluster on Endpoint 1 / ClusterId 96 (0x0060)
- [PowerSource Cluster](https://github.com/project-chip/connectedhomeip/blob/master/data_model/1.3/clusters/PowerSourceCluster.xml) on Endpoint 1 / ClusterId 47 (0x002f)

### Endpoint 2 / Measurement & Sensing

 - [ElectricalSensorManager.cpp](https://github.com/SiliconLabs/matter_extension/blob/main/silabs_examples/dishwasher-app/silabs/src/ElectricalSensorManager.cpp)
   - [ElectricalEnergyMeasurementInstance.cpp](https://github.com/SiliconLabs/matter_extension/blob/main/silabs_examples/dishwasher-app/silabs/src/ElectricalEnergyMeasurementInstance.cpp)
   - [ElectricalPowerMeasurementDelegate.cpp](https://github.com/SiliconLabs/matter_extension/blob/main/silabs_examples/dishwasher-app/silabs/src/ElectricalPowerMeasurementDelegate.cpp)

**Electrical Power Measurement**

| **Mode** | **Voltage** | **ActiveCurrent** | **ReactiveCurrent** | **ApparentCurrent** | **ActivePower** | **ReactivePower** | **ApparentPower** | **RMSVoltage** | **RMSCurrent** | **RMSPower** | **Frequency** | **PowerFactor** | **NeutralCurrent** |
|----------|:-----------:|:-----------------:|:-------------------:|:-------------------:|:---------------:|:-----------------:|:-----------------:|:--------------:|:--------------:|:------------:|:-------------:|:---------------:|:------------------:|
| Stopped  |   230'000   |         0         |          0          |          0          |        0        |         0         |         0         |     120'000    |        0       |       0      |       50      |      98'00      |          0         |
| Running  |   230'000   |       15'000      |        17'000       |        23'000       |     1800'000    |      2040'000     |      3000'000     |     120'000    |     15'000     |   1800'000   |       50      |      92'00      |       15'000       |
| Paused   |   230'000   |        125        |         150         |         190         |      17'000     |       18'000      |       25'000      |     120'000    |       125      |    17'000    |       50      |      95'00      |         125        |
| Error    |      0      |         0         |          0          |          0          |        0        |         0         |         0         |        0       |        0       |       0      |       0       |        0        |          0         |


**Electrical Energy Measurement**

TODO

## Control and Power Measurement

## Local

 **LED 0** shows the overall state of the device and its connectivity. The
 following states are possible:

| **State**                                      | **Description**                                                                                                |
|------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Short Flash On (50 ms on/950 ms off)           | The device is in the unprovisioned (unpaired) state and is waiting for a commissioning application to connect. |
| Rapid Even Flashing (100 ms on/100 ms off)     | The device is in the unprovisioned state and a commissioning application is connected through Bluetooth LE.    |
| SteteStatShort Flash Off ; (950ms on/50ms off) | The device is fully provisioned, but does not yet have full Thread network or service connectivity.            |
| Solid On                                       | The device is fully provisioned and has full Thread network and service connectivity.                          |


**LED 1** Shows the dishwasher working state following states are possible:

| **State**  | **Description**                     |
|------------|-------------------------------------|
| Solid On   | dishwasher is running               |
| Slow Blink | dishwasher is paused                |
| Off        | dishwasher is stopped               |
| Fast Blink | dishwasher has encountered an error |


**Push Button 0** Pairing

| **State**                | **Description**                                                                                                                                                                                              |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Press and Release        | Start, or restart, BLE advertisement in fast mode. It will advertise in this mode for 30 seconds. The device will then switch to a slower interval advertisement. After 15 minutes, the advertisement stops. |
| Pressed and hold for 6 s | Initiates the factory reset of the device. Releasing the button within the 6-second window cancels the factory reset procedure. **LEDs** blink in unison when the factory reset procedure is initiated.      |


**Push Button 1** Cycle the dishwasher operational states Running/Paused/Stopped

### Remote control with chip-tool

To control the device's operational state, act on the [OperationalState cluster](https://github.com/project-chip/connectedhomeip/blob/master/data_model/1.3/clusters/OperationalState.xml):

    chip-tool operationalstate start <node_id> <endpoint>
    chip-tool operationalstate stop <node_id> <endpoint>
    chip-tool operationalstate pause <node_id> <endpoint>

    chip-tool operationalstate start 1 1
    chip-tool operationalstate stop 1 1
    chip-tool operationalstate pause 1 1

#### Read ElectricalPowerMeasurement

[ElectricalPowerMeasurement](https://github.com/project-chip/connectedhomeip/blob/master/data_model/1.3/clusters/ElectricalPowerMeasurement.xml) ClusterId 144 (0x0090)

**Voltage**

    chip-tool electricalpowermeasurement read voltage 2 2

**Active-Power**

    chip-tool electricalpowermeasurement read active-power 2 2

**Active-Current**

    chip-tool electricalpowermeasurement read active-current 2 2



### Matter clusters with ZAP tool

![image](https://github.com/user-attachments/assets/91689a56-b549-4383-ab43-7b34babe7b3d)


![image](https://github.com/user-attachments/assets/7014801c-1377-4b34-8d91-7d775419445a)

### Endpoint 1 / General / Dishwasher Mode
![image](https://github.com/user-attachments/assets/03ce8ee9-f420-4479-9f80-3029ddbe82f1)


### Endpoint 2 / Measurement & Sensing

 - [ElectricalSensorManager.cpp](https://github.com/SiliconLabs/matter_extension/blob/main/silabs_examples/dishwasher-app/silabs/src/ElectricalSensorManager.cpp)
   - [ElectricalEnergyMeasurementInstance.cpp](https://github.com/SiliconLabs/matter_extension/blob/main/silabs_examples/dishwasher-app/silabs/src/ElectricalEnergyMeasurementInstance.cpp)
   - [ElectricalPowerMeasurementDelegate.cpp](https://github.com/SiliconLabs/matter_extension/blob/main/silabs_examples/dishwasher-app/silabs/src/ElectricalPowerMeasurementDelegate.cpp)


**Electrical Power Measurement**

![image](https://github.com/user-attachments/assets/ddfbb224-b11e-4a1e-93b2-d57f4dfb1e53)

**Electrical Energy Measurement**

![image](https://github.com/user-attachments/assets/b4cb7019-05ec-4fe5-ab12-23983e34067d)

## Home Assistant
 
**Clusters on Endpoint 2 / Device Type(s): Electrical Sensor**

![image](https://github.com/user-attachments/assets/659f1688-8b3e-408a-a861-bf7d006f6044)

**Electrical Power Measurement**

![image](https://github.com/user-attachments/assets/cd59a039-3d7d-40f3-a362-e76a5ec3d94a)


