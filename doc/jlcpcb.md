# Using JLCPCB

[JLCPCB](https://jlcpcb.com) is a PCB manufacturing and assembly company located in China. They have a reputation for low cost, high quality work and can get you finished boards relatively quickly. They don't have native KiCAD support but a couple of plugins help smooth rough edges.

## Fabrication Plugin

Use KiCAD's Plugin and Content Manager to install the Fabrication Plugin. While it doesn't mention JLCPCB in its name, it can generate output in the format JLCPCB expects.

For each component in the Schematic Editor, add a "LCSC" field whose value is the LCSC/JLCPCB parts manager component ID.

## ImpartGUI Plugin

Use KiCAD's Plugin and Content Manager to install the ImpartGUI plugin. When you identify a part from JLCPCB, use the plugin to download the part's symbol, footprint and (if available) 3D model.

Note that on macOS, the plugin may throw an error saying it can't find the module "pydantic". See this [Github issue](https://github.com/Steffen-W/Import-LIB-KiCad-Plugin/issues/23) for more info. To fix this, run this command from the terminal:
```
/Applications/KiCad/KiCad.app/Contents/Frameworks/Python.framework/Versions/Current/bin/pip3.9 install pydantic
```

## Shipping

Shipping costs can equal the cost of manufacturing just a few PCBs. Batching up projects so that they ship together can help with this. You can also add projects to an existing order, which will extend its processing time until they're all completed.

