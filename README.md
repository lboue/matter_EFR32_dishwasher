# Matter EFR32 Dishwasher Example

## Hardware

 - [Silicon Labs xG24 Explorer Kit](https://www.silabs.com/development-tools/wireless/efr32xg24-explorer-kit?tab=overview)

[Matter EFR32 Dishwasher Example 2.3.0-1.3](https://github.com/SiliconLabs/matter/tree/release_2.3.0-1.3/silabs_examples/dishwasher-app/silabs)

## Dishwasher Clusters


### ZAP tool

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

| **Mode** | **Voltage** | **ActiveCurrent** | **ReactiveCurrent** | **ApparentCurrent** | **ActivePower** | **ReactivePower** | **ApparentPower** | **RMSVoltage** | **RMSCurrent** | **RMSPower** | **Frequency** | **PowerFactor** | **NeutralCurrent** |
|----------|:-----------:|:-----------------:|:-------------------:|:-------------------:|:---------------:|:-----------------:|:-----------------:|:--------------:|:--------------:|:------------:|:-------------:|:---------------:|:------------------:|
| Stopped  |   230'000   |         0         |          0          |          0          |        0        |         0         |         0         |     120'000    |        0       |       0      |       50      |      98'00      |          0         |
| Running  |   230'000   |       15'000      |        17'000       |        23'000       |     1800'000    |      2040'000     |      3000'000     |     120'000    |     15'000     |   1800'000   |       50      |      92'00      |       15'000       |
| Paused   |   230'000   |        125        |         150         |         190         |      17'000     |       18'000      |       25'000      |     120'000    |       125      |    17'000    |       50      |      95'00      |         125        |
| Error    |      0      |         0         |          0          |          0          |        0        |         0         |         0         |        0       |        0       |       0      |       0       |        0        |          0         |


**Electrical Energy Measurement**

![image](https://github.com/user-attachments/assets/b4cb7019-05ec-4fe5-ab12-23983e34067d)

## Home Assistant

![image](https://github.com/user-attachments/assets/659f1688-8b3e-408a-a861-bf7d006f6044)

![image](https://github.com/user-attachments/assets/42361092-52d8-4ce0-b1d7-04949613785b)


## Control

Control the operational mode:


    chip-tool operationalstate start <node_id> <endpoint>
    chip-tool operationalstate stop <node_id> <endpoint>
    chip-tool operationalstate pause <node_id> <endpoint>

    chip-tool operationalstate start 1 1
    chip-tool operationalstate stop 1 1
    chip-tool operationalstate pause 1 1

