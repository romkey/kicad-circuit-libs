# KiCAD Lib

This repo contains "libraries" of circuits in KiCAD intended for re-use in projects as well as notes on using the circuits and notes on various other topics that may be helpful.

Circuit fragments will usually include components that are tagged with JLCPCB/LCSC component numbers, making it easy to submit them for assembly.

**IMPORTANT**

Using these designs does not excuse you from understanding how the circuits work and confirming their correct design. Just
blindly dropping these into designs can lead to shorts, fried components, just
plain not working PCBs. Anything working with power is extra risky,
especially LiPo batteries. You may damage USB ports, destroying
components and batteries that catch fire or explode.

If you don't understand at least the basics of voltage and current, diodes, Ohm's law, you're not ready to work with this stuff.

Nothing in this repo is intended as a tutorial. These designs are simply bookmarks, shorthand, time savers to avoid having to look up pinouts or component models or needed support circuitry, for people who already know what they're doing.

**USE AT YOUR OWN RISK**

## About I2C and Pull-Up Resistors

The I2C bus *requires* pull-up resistors on the SDA and SCL lines. If it works without them it's accidental and cannot be relied
upon. You'll generally want a single set of them per bus. Having multiple will work but isn't optimal and wastes space and money.
Multiple pull-up resistors will also be in parallel, which reduces total resistance. If there are enough of them the pull-ups
will stop working effectively.

If a CPU board has I2C devices on it, it should include a single set of pull-up resistors for each separate I2C bus.

If a CPU board has no I2C devices on it but a way to connect external I2C devices, like a Qwiic/STEMMA QT connector, it should
not include pull-up resistors and should instead assume they'll be provided by any external devices.

Each circuit fragment with an I2C device includes pull-up resistors for that device.

Each circuit fragment with a CPU includes pull-up resistors for the first I2C bus.

If you combine them, you should eliminate any duplicate pull-up resistors and leave only one set. 4.7K to 10K is usually a
good range of values for the resistors.

On most PCBs you can place pull-up resistors wherever is convenient. By convention they're often placed at the start of the I2C
bus, near the CPU if the CPU is on the board.

## About Bypass Capacitors

Many circuit fragments will include a pair of bypass capacitors, often 10µF and 0.1µF. These help protect against low
and high frequency noise in the power supply. Sensors should always include these. Bypass capacitors should always be
placed as close to the chip they're protecting as possible.

Do not treat bypass capacitors like pull-up resistors and do not attempt to combine bypass capacitors for multiple chips.

## Circuits

All circuit fragments are under the `hw` directory. Most are just schematics without a PCB. Some (like the AHT20 which has a
cutout on the PCB for thermal isolation) include a PCB if there are useful features on it.

### 3.3V Regulator

Simple 3.3V regulator using an LD1117 LDO, good for batteries, USB and unregulated power sources up to 15V (do not recommend
running it maximum voltage however). Maximum current out 800mA.

### AHT20

AHT20 I2C temperature and humidity sensor. The example PCB includes a cutout to help thermal isolation of the sensor.
This is useful on boards with CPUs on them as CPUs often run hot and can throw off the sensor. It's not useful on boards
with just the sensor.

### LiPo Charger

LiPO battery connector and charging circuitry.

## LiPo Fuel Gauge

I2C LiPo battery "fuel gauge" that estimates current battery charge.

## Qwiic/STEMMA QT connector

Very simple circuit with labelled connectors for Adafruit's "STEMMA QT" and Sparkfun's "Qwiic" I2C connector.

## Small Switches

An assortment of small SPST SMD switches of several sizes that were in
stock at JLCPCB when I created this.

## Notes

- [Using JLCPCB](doc/jlcpcb.md)

- [Using OSHPark](doc/oshpark.md)

- [My PCB Design Checklist](doc/checklist.md)

