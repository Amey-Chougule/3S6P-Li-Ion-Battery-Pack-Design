# 🔋 Safety Notes — 3S6P Lithium-Ion Battery Pack

**Project:** 3S6P Li-Ion Battery Pack Design  
**Configuration:** 3S6P — 18 × 18650 cells  
**Nominal Voltage:** 11.1 V  
**Maximum Charge Voltage:** 12.6 V  
**Capacity:** 12 Ah  
**Nominal Energy:** 133.2 Wh  
**BMS:** 3S 40 A protection and balancing BMS  
**Author:** Amey Chougule

------------------------------------------------------------------------

## 1. Purpose

This document defines the primary safety considerations for the design,
assembly, charging, handling, storage, and testing of the 3S6P
lithium-ion battery pack.

Lithium-ion cells can deliver high current and contain significant
stored energy. Incorrect assembly, charging, short-circuiting,
mechanical damage, or thermal abuse can result in cell failure, fire, or
other hazardous conditions.

This document should be used together with the selected cell
manufacturer’s datasheet, the BMS manufacturer’s specifications, and the
charger manufacturer’s instructions.

------------------------------------------------------------------------

## 2. Battery Configuration

The battery contains:

- 18 × 18650 lithium-ion cells
- 3 series-connected groups
- 6 cells in parallel per series group
- 11.1 V nominal pack voltage
- 12.6 V maximum charging voltage
- 12 Ah nominal capacity
- Approximately 133.2 Wh nominal energy

### Electrical configuration

``` text
             3S6P Battery Pack

      Group 1       Group 2       Group 3
     ┌────────┐    ┌────────┐    ┌────────┐
     │ 6 × 18650│   │ 6 × 18650│   │ 6 × 18650│
     │   6P   │────│   6P   │────│   6P   │
     └────────┘    └────────┘    └────────┘

        3.7 V          3.7 V          3.7 V
              → 11.1 V nominal
```

------------------------------------------------------------------------

## 3. Cell Selection and Matching

Only cells that are suitable for the intended battery design should be
used.

### Required checks

- Use cells of the same chemistry and compatible specifications.
- Prefer cells from a reliable manufacturer and known source.
- Verify cell capacity before pack assembly.
- Check cell open-circuit voltage.
- Inspect every cell for dents, corrosion, damaged insulation, leakage,
  swelling, overheating marks, or other physical damage.
- Do not use cells with damaged positive-terminal insulation.
- Do not mix cells with significantly different capacities, ages, or
  conditions.
- Cells connected in parallel should be closely matched in voltage
  before connection.

### Important

Never connect cells at substantially different voltages directly in
parallel. A large equalization current can flow between the cells.

------------------------------------------------------------------------

## 4. Physical Construction

The cells must be mechanically secured so that they cannot move, rotate,
or contact conductive parts unintentionally.

### Recommended precautions

- Use appropriate cell holders, spacers, or a mechanically secure
  enclosure.
- Insulate the cell bodies and series interconnects.
- Use fish-paper or equivalent electrical insulation around appropriate
  terminals.
- Protect positive terminals from accidental short circuits.
- Keep conductive tools away from exposed battery terminals.
- Prevent metal parts of the enclosure from contacting live electrical
  nodes.
- Provide adequate strain relief for power and balance wiring.
- Secure the BMS so vibration cannot damage the PCB or connections.

------------------------------------------------------------------------

## 5. Electrical Connections

The 3S BMS must be connected according to the exact wiring sequence
specified by the BMS manufacturer.

### BMS connections

Typical connections include:

- Battery negative
- Series-group sensing connections
- Pack positive
- Pack negative
- Balance leads

The exact terminal naming and wiring order vary between BMS designs.

**Do not assume that two BMS boards with the same current rating have
identical terminal arrangements.**

Always verify the BMS datasheet or manufacturer documentation before
connection.

------------------------------------------------------------------------

## 6. Balance Connector Safety

The 4-pin balance connector provides access to the three series-group
voltages and the corresponding reference points.

Before connecting a charger or measurement equipment:

1.  Verify the balance-wire order.
2.  Measure the voltage between adjacent balance points.
3.  Confirm that each reading corresponds to one series group.
4.  Confirm that the total balance voltage corresponds to the pack
    voltage.
5.  Check for accidental shorts between balance leads.

A reversed or incorrectly connected balance harness can damage the BMS
and cells.

------------------------------------------------------------------------

## 7. BMS Protection

The installed 3S 40 A BMS is intended to provide battery protection
functions such as:

- Overcharge protection
- Over-discharge protection
- Over-current protection
- Short-circuit protection
- Passive cell balancing

The BMS should not be treated as a replacement for correct battery
design.

The BMS current rating, cutoff thresholds, balancing behavior, MOSFET
ratings, temperature limits, and wiring requirements must be compatible
with the selected cells.

------------------------------------------------------------------------

## 8. Charging Safety

The pack requires a charger specifically intended for a **3-series
lithium-ion pack** with an appropriate **12.6 V
constant-current/constant-voltage charging profile**.

### Charging precautions

- Use a charger compatible with 3S Li-ion chemistry.
- Do not use a charger intended for a different series count.
- Do not exceed the manufacturer’s specified charge current.
- Inspect the pack before every charging cycle.
- Do not charge a visibly damaged, swollen, leaking, or overheated pack.
- Place the pack on a suitable non-combustible surface during charging.
- Do not leave the pack unattended during charging.
- Stop charging if abnormal heat, smell, smoke, swelling, or unusual
  electrical behavior is observed.
- Verify the BMS and charger compatibility before charging.

------------------------------------------------------------------------

## 9. Discharge and Load Testing

The modeled design evaluates operation up to 30 A.

At the 20 mΩ model resistance:

- Voltage drop at 30 A ≈ **0.60 V**
- I²R loss at 30 A ≈ **18 W**
- Modeled loaded voltage ≈ **10.5 V**
- Modeled load power ≈ **315 W**
- Modeled efficiency ≈ **94.6%**

These values are **engineering calculations based on the simplified
resistance model**. They should not be interpreted as a guarantee that
the physical pack can safely deliver 30 A continuously.

The allowable continuous and peak current must be established from:

- Cell manufacturer’s continuous discharge rating
- BMS current rating
- Interconnect capability
- Wire and connector ratings
- Thermal behavior
- Enclosure design
- Ambient temperature

------------------------------------------------------------------------

## 10. High-Current Testing

High-current testing should be performed using controlled equipment.

### Recommended practice

- Use a properly rated electronic load.
- Verify polarity before connection.
- Use appropriately rated wiring and connectors.
- Start at a low current.
- Increase current gradually.
- Monitor pack voltage continuously.
- Monitor individual series-group voltages.
- Monitor cell and BMS temperature.
- Stop the test if abnormal voltage sag or heating occurs.

Never deliberately short-circuit the battery to evaluate its protection
system.

------------------------------------------------------------------------

## 11. Thermal Safety

Heat generation increases with current approximately according to:

`P_loss = I² × R`

For the 20 mΩ model:

`P_loss = 30² × 0.020 = 18 W`

Actual heat generation can be higher because losses also occur in:

- Cell internal resistance
- Nickel/bus interconnects
- Wires
- Connectors
- BMS MOSFETs
- Protection devices
- Contact resistance

Temperature should therefore be monitored during sustained high-current
operation.

------------------------------------------------------------------------

## 12. Short-Circuit Protection

A 12 Ah lithium-ion pack can deliver very high fault current.

### Prevent accidental shorts

- Never place metal objects across the battery terminals.
- Keep tools insulated where practical.
- Cover exposed terminals.
- Protect the XT60 connector from accidental conductive contact.
- Keep balance wires insulated and secured.
- Avoid loose conductive hardware inside the enclosure.

Do not intentionally short the pack, even if the BMS has short-circuit
protection.

------------------------------------------------------------------------

## 13. Storage

For extended storage:

- Store the battery in a cool, dry, ventilated environment.
- Avoid direct sunlight and high temperatures.
- Keep the pack away from combustible materials.
- Avoid storing the battery fully discharged.
- Avoid unnecessary long-term storage at maximum state of charge.
- Inspect the pack periodically for swelling, leakage, corrosion, or
  physical damage.

Follow the cell manufacturer’s recommended storage voltage and
temperature range.

------------------------------------------------------------------------

## 14. Transportation and Handling

During handling and transportation:

- Prevent the terminals from shorting.
- Protect the pack from impact and crushing.
- Keep the battery mechanically secured.
- Avoid excessive vibration.
- Do not carry loose conductive objects together with the battery.
- Follow applicable lithium-battery transportation regulations when
  transporting the pack outside the laboratory/workshop.

------------------------------------------------------------------------

## 15. Inspection Before Operation

Before connecting a load or charger, verify:

- [ ] No cell has visible mechanical damage.
- [ ] Cell insulation is intact.
- [ ] No exposed conductor can cause an accidental short.
- [ ] Series and parallel connections are correct.
- [ ] BMS wiring is correctly connected.
- [ ] Balance connector wiring is correctly ordered.
- [ ] XT60 polarity is correct.
- [ ] Pack voltage is within the expected range.
- [ ] No abnormal heating or smell is present.
- [ ] Wiring and connectors are appropriately rated.
- [ ] The enclosure mechanically secures the cells.

------------------------------------------------------------------------

## 16. Abnormal Conditions

Immediately stop operation if any of the following occurs:

- Rapid or unexpected temperature rise
- Swelling
- Smoke
- Hissing or unusual sound
- Strong chemical or burning smell
- Leakage
- Sudden voltage collapse
- Unexpected BMS shutdown
- Repeated over-current protection
- Excessive voltage difference between series groups
- Damaged wiring or connectors

Do not continue charging or discharging a battery showing abnormal
behavior.

------------------------------------------------------------------------

## 17. Emergency Considerations

If a lithium-ion battery becomes hot, swells, vents, smokes, or catches
fire:

- Move people away from the immediate hazard.
- Do not handle a damaged or actively venting cell.
- Do not attempt to open the pack.
- Follow the emergency procedures and fire-safety practices applicable
  to the facility where testing is performed.
- Contact emergency services when required.
- Do not reuse cells that have experienced severe thermal or mechanical
  damage.

Emergency response should follow local fire-safety guidance and the
procedures of the laboratory/workplace.

------------------------------------------------------------------------

## 18. Design-Specific Safety Summary

| Item                        | Project Value / Requirement |
|-----------------------------|-----------------------------|
| Battery configuration       | 3S6P                        |
| Total cells                 | 18                          |
| Nominal voltage             | 11.1 V                      |
| Maximum charge voltage      | 12.6 V                      |
| Capacity                    | 12 Ah                       |
| Nominal energy              | 133.2 Wh                    |
| BMS                         | 3S 40 A                     |
| Modeled pack resistance     | 20 mΩ                       |
| Modeled voltage drop @ 30 A | 0.60 V                      |
| Modeled I²R loss @ 30 A     | 18 W                        |
| Modeled efficiency @ 30 A   | ≈94.6%                      |
| Charger                     | 3S Li-ion, 12.6 V CC/CV     |
| Main connector              | XT60                        |
| Balance connector           | 4-pin                       |

------------------------------------------------------------------------

## 19. Important Engineering Disclaimer

The electrical calculations in this repository are based on the stated
cell ratings and a simplified 20 mΩ pack-resistance model.

Actual battery behavior depends on cell manufacturer, cell condition,
temperature, state of charge, interconnect resistance, BMS losses,
wiring, connectors, charging conditions, and load profile.

This document is intended as engineering project documentation and does
not replace the manufacturer’s cell/BMS specifications, applicable
electrical safety standards, or professional battery-safety procedures.

**Always use the most restrictive applicable specification when
determining operating limits.**
