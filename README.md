# WDSSR

WDSSR is a low side DC Mosfet based SSR board designed to drive resistive loads with and integrated watchdog able to detect some of the more common faults, report and protect it self from fire hazard.

## Watchdog capabilities

The integrated, fully analog, free of firmware, watchdog has the ability to detect:
 - Broken cable
 - Shorted switching Mosfet

For any of the cases described above, the board will “open” the series safety Mosfet and will trigger an alarm open collector signal for the control system to take further action, reducing the fire hazard resulting from an uncontrolled thermal runaway or defective wiring.

## Simplified principle of operation

 - The resistive load pulls the Drain to VCC
 - When Control is pulled up, the MOSFET “closes”, pulling its Drain close GND
 - Comparing voltages at Drain and Gate, a faulty MOSFET can be detected

| Gate | Drain | Result                                 |
| ---- | ----- | -------------------------------------- |
| Low  | Low   | Faulty - Source and drain  shorted     |
| High | Low   | Normal - ON                            |
| Low  | High  | Normal - OFF                           |
| High | High  | Faulty – Open or gate shorted to drain |

![Operation diagram](https://github.com/eliasrm87/wdssr/raw/master/docs/images/operation_diagram.png)

## Limitations

This design is not bullet proof and may fail to achieve it’s objective in certain cases:
 - The series safety Mosfet may overheat and fail exactly at the same time as the switching Mosfet
 - It is only tested and verified to work with resistive loads, like heaters. Uses of this design with inductive loads has not been yet tested and may need hardware modifications

### Front

![PCB front](https://github.com/eliasrm87/wdssr/raw/master/docs/images/front.png)

### Back

![PCB back](https://github.com/eliasrm87/wdssr/raw/master/docs/images/back.png)

