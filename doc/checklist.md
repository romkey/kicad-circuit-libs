# My PCB Design Checklist

I design PCBs as [open source hardware](https://www.oshwa.org), not as products. My goals are that they be well documented and easy to work with and use. Design choices appropriate for these goals are not necessarily appropriate for other situations.

## Board Layout

Using a very regular consistent board layout makes case design easier.

- position the board at an easy to use origin - for instance (20, 20). Much easier to do math from easy to remember integer coordinates than a couple of random floating point numbers that happen to be where you dropped the corner of the board.

When there are no external constraints:

- choose easy to use board dimensions - go for a multiple of 5 or 10. So a simple sensor board might have corners at (20, 20), (20, 80), (60, 20) and (60, 80).

- remember to add mounting holes
  - use a standard screw size like m2 (2mm) or m2.5 (2.5mm)
  - use simple regular offsets for mounting holes, like 3 or 4 mm from board edges
  - add mounting holes to the board first and design around them
  - mounting holes should be marked as "not on schematic" so that they won't be lost if the PCB is updated from the schematic
  
## Documentation

General: try to include all the information users might want *on the board itself*. When there are space constraints, prioritize the most important most desired information. Make all the information available at the start of the documentaton in the board's repo.

- include the board name, design date, version number and a link to its public repo in text on the board
  - design date may often be more meaningful than the version number when looking through piles of old boards
- if there's room, include a QR code for the repo
- if there's room, include the board's dimensions and mounting hole size and offsets in the board's documentation
- when approporiate (especially for LEDs), include the power requirements (expected voltage and maximum current) in the board's documentation. If there are LEDs include the type and the count.
- if there's room, include images for open source hardware, KiCAD, any organizations like CTRLH or CETI that may be appropriate
- the QR code and any images should all be marked as "not on schematic" so that they won't be lost if the PCB is updated from the schematic
- apply for [OSHWA certification](https://application.oshwa.org/apply) and label the board with it 
