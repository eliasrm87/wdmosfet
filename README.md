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

## Bill Of Material

You could consider using the included [Interactive Bill of Material](https://htmlpreview.github.io/?https://raw.githubusercontent.com/eliasrm87/wdssr/master/bom/WDSSR_ibom.html) for a better assembly experience.

|Qty|Reference(s)              |Value           |Part Number                                               |LCSC Part #                                                                  |
|---|--------------------------|----------------|----------------------------------------------------------|-----------------------------------------------------------------------------|
|1  |C1                        |100n            |                                                          |C14663                                                                       |
|1  |C2                        |1u              |                                                          |C15849                                                                       |
|1  |C3                        |10n             |                                                          |C14663                                                                       |
|1  |D1                        |ABS6            |                                                          |C169532                                                                      |
|2  |D2, D4                    |BAV70           |                                                          |C68978                                                                       |
|1  |D3                        |LED_G           |                                                          |C72043                                                                       |
|1  |D5                        |LED_R           |                                                          |C2286                                                                        |
|1  |D6                        |D_Zener         |MM3Z12VB                                                  |C891576                                                                      |
|1  |J1                        |B2B-XH-A(LF)(SN)|B3B-XH-AM(LF)(SN)                                         |C161870                                                                      |
|1  |J2                        |1714968         |1714968                                                   |C95692                                                                       |
|1  |J3                        |Conn_01x02_Male |                                                          |C160332                                                                      |
|2  |Q1, Q2                    |IRFR7440TRPBF   |IRFR7440TRPBF                                             |C97244                                                                       |
|2  |Q3, Q4                    |BC846B,215      |                                                          |C87062                                                                       |
|2  |R1, R12                   |2K              |                                                          |C21190                                                                       |
|6  |R2, R5, R11, R14, R15, R16|10K             |                                                          |C25804                                                                       |
|5  |R3, R7, R8, R9, R13       |100K            |                                                          |C25803                                                                       |
|1  |R4                        |1K              |                                                          |C21190                                                                       |
|2  |R6, R17                   |100             |                                                          |C22775                                                                       |
|1  |U1                        |LM358DT         |                                                          |C9418                                                                        |
|1  |U2                        |TLP185          |                                                          |C7240                                                                        |

## Limitations

This design is not bullet proof and may fail to achieve it’s objective in certain cases:
 - The series safety Mosfet may overheat and fail exactly at the same time as the switching Mosfet
 - It is only tested and verified to work with resistive loads, like heaters. Uses of this design with inductive loads has not been yet tested and may need hardware modifications

### Front

![PCB front](https://github.com/eliasrm87/wdssr/raw/master/docs/images/front.png)

### Back

![PCB back](https://github.com/eliasrm87/wdssr/raw/master/docs/images/back.png)

