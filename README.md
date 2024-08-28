# Matter EFR32 Dishwasher Example

## Software

[Matter EFR32 Dishwasher Example 2.3.0-1.3](https://github.com/SiliconLabs/matter/tree/release_2.3.0-1.3/silabs_examples/dishwasher-app/silabs):
An example showing the use of Matter on the Silicon Labs EFR32 MG12 and MG24 boards.


## Hardware

 - [Silicon Labs xG24 Explorer Kit](https://www.silabs.com/development-tools/wireless/efr32xg24-explorer-kit?tab=overview)
   - [Buy EFR32xG24 Explorer Kit](https://www.digikey.com/en/product-highlight/s/silicon-laboratories/efr32xg24-explorer-kit)


## Dishwasher Clusters

### Endpoint 1 / General / Dishwasher Mode


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

## Control

## Local

 **LED 0** shows the overall state of the device and its connectivity. The
 following states are possible:

| **State**                                      | **Description**                                                                                                |
|------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Short Flash On (50 ms on/950 ms off)           | The device is in the unprovisioned (unpaired) state and is waiting for a commissioning application to connect. |
| Rapid Even Flashing (100 ms on/100 ms off)     | The device is in the unprovisioned state and a commissioning application is connected through Bluetooth LE.    |
| SteteStatShort Flash Off ; (950ms on/50ms off) | The device is fully provisioned, but does not yet have full Thread network or service connectivity.            |
| Solid On                                       | The device is fully provisioned and has full Thread network and service connectivity.                          |
            
### Remote control with chip-tool

To control the device's operational state, act on the [OperationalState cluster](https://github.com/project-chip/connectedhomeip/blob/master/data_model/1.3/clusters/OperationalState.xml):

    chip-tool operationalstate start <node_id> <endpoint>
    chip-tool operationalstate stop <node_id> <endpoint>
    chip-tool operationalstate pause <node_id> <endpoint>

    chip-tool operationalstate start 1 1
    chip-tool operationalstate stop 1 1
    chip-tool operationalstate pause 1 1



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


