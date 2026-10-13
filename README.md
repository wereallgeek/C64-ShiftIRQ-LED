# C64 IRQ+Shift LED

## purpose

When I [built my Mechboard64](https://wereallgeeks.wordpress.com/2025/11/18/commodoremechboard/), I soon realized I didn't like to have the SHIFT-LOCK backlight as a lock indication, so I began using the [IRQ LED module from TEBL](https://github.com/tebl/C64-IRQ-LED), but as [a way to indicate Shift-LOCK on my Mechboard](https://wereallgeeks.wordpress.com/2025/11/27/mechboardled/). This wasn't the first time I used this circuit [for other purposes](https://wereallgeeks.wordpress.com/2023/06/19/cartled/#IRQ) and I was in known territory.

That said, adding this SHIFT-LOCK mod meant I lost the ability to add the [CPU usage indicator](https://wereallgeeks.wordpress.com/2023/04/24/irqmod/) and that is a shame as this is a fun mod to add to any commodore.

So I wondered if it is possible to alter the original circuitry to add a 3rd color (RGB LED?) - the power LED (green) remains ON except when the CPU is working (RED) but the caps-lock alters the color when it is activated.

The IRQ LED module is a simple design based on a 74LS04 logic chip.
[Here is the original design by TEBL](https://github.com/tebl/C64-IRQ-LED)

Half the chip turns out not being used, so altering to add another LED wasn't much of a problem.

The original design had the ability for a cut-off switch, but I have never implemented it, so it was removed to make room for the extra resistor for the 3rd color without increasing board size.

## Build and install
Most of the construction is straight forward, just follow the BOM below as well as the notices where you need to make a few decisions. Where do I connect the inputs? Does my RGB LED work?

You need to get a common cathode (*CC*) LED with more than one colour, ideally a tri colour one like so it will likely be RGB. **Don't** solder it into place until you've test-fitted it for length in place inside your C64 case, solder everything else instead.

![All together now](https://github.com/tebl/C64-IRQ-LED/raw/main/gallery/2020-11-21%2000.48.12.jpg)
![Fitting](https://github.com/tebl/C64-IRQ-LED/raw/main/gallery/2020-11-21%2000.47.35.jpg)

Next step is to remove the old power LED. The newer RGB LED might be a tight fit for the existing LED mount though it should fit - just apply some pressure on the front to snap it into place. Afterwards, add the module on top - it might stay on there by itself. if it doesn't you'll need to add some double-sided tape to the IC. Now you can probably solder the LED legs into place permanently - just take care not to melt your case!

![Adding wires](https://github.com/tebl/C64-IRQ-LED/raw/main/gallery/2020-11-21%2000.38.46.jpg)

The last piece of the puzzle is attaching the whole thing to the C64 motherboard, you can refer to the picture above as this is where I added the wires needed. I'm using a cut-off set of female dupont wires, the easiest is to wire them to the cartridge port and matching the female part of it to the **markings on the board** (pin order has been changed). Looking at the cartridge port as pictured above: 
- Pin 1, the blue wire, goes to GND (J1 pin 1)
- Pin 3, the green wire, goes to VCC (J1 pin 2)
- Pin 4, the yellow wire, goes to IRQ (J1 pin 3)

Before powering up, double-check that GND and VCC is in the correct spot, swapping them around will kill the IC on the IRQ LED board. Enjoy your freqeuently green power LED!

# BOM
Most parts should be easy to get a hold of from your favourite local electronic component shop, but since I don't have access to the more serious ones I'm mostly getting my components from ebay/AliExpress (free shipping most places, but plan on waiting 3-4 weeks though).

| Reference    | Item                                  | Count |
| ------------ | ------------------------------------- | ----- |
| PCB          | Fabricate using Gerber files          |     1 |
| D1 *         | 5mm RGB LED (common cathode)          |     1 |
| J1           | 4-pin right-angle header pins         |     1 |
| R1,R2,R3     | 330 ohm resistor                      |     2 | 
| U1           | 74LS04 or 74HCT04 (DIP-14)            |     1 |

*) These are 4 pin LEDs of the common cathode variety, check using diode test on a multimeter to ensure that the center pin is GND and that you know which colour goes where. Alternatively, jam a CR2032 battery between the pins. 

## 🛠️ Modifications & Changelog (CERN OHL v1.2 Compliance)

As required by the **CERN Open Hardware Licence v1.2**, here is the list of modifications made to the original design by **TEBL**:

- **3rd Color Integration:** Altered the original circuitry to support a full 3-color RGB LED.
- **Logic Chip Optimization:** Connected the remaining unused gates of the **74LS04** logic IC to successfully monitor and display the Shift-LOCK / Caps-Lock status alongside CPU usage.
- **Form Factor Maintenance:** Removed the optional cut-off switch from the original schematic. This freed up enough space to add the extra resistor required for the 3rd color without increasing the overall size of the PCB.

### ⚠️ Licensing & Attribution Notice
Any derivative work, manufacture, or commercial distribution of this modified board **MUST retain the original credits to TEBL and the modification credits to Marsupial ([://wordpress.com](https://://wordpress.com))**. All derivative hardware layouts and code must remain open-source under the CERN OHL v1.2 license terms.
