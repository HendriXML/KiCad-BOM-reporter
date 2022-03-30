# KiCad-BOM-reporter
Reports a bill of material list from KiCad 5/6 - specifications are matched with a PartKeepr database

See [wiki](https://github.com/HendriXML/KiCad-BOM-reporter/wiki), [screenshots](https://github.com/HendriXML/KiCad-BOM-reporter/wiki/Screenshots) or [features](https://github.com/HendriXML/KiCad-BOM-reporter/wiki/Features) for more details.

## Changelog version 3.0
* Tested with KiCad 6.0
* Version 7.0 of the XML interpreter
* File restructuring, renaming and clean up
* Improved/changed config settings
* Configuration echo: shows which config values are actualy being used
* Improved capacitor technology items: aluminum electrolytic, tantalum electrolytic, niobium electrolytic
* Set matching, requested (schematic) components can specify multiple values on enumeration based fields like: "aluminum electrolytic, tantalum electrolytic"
* New tasks which determines the best combination of (available) components (resistors, capacitors of inductors) for a replacement value
* Reporting of (sub)sheet info, the level of detail is configurable: SheetInfo=None|Root|All
* Ini files can be saved and loaded from the config tabsheet. Also using the AltConfig command line option with a nonexistent file, does not result in an error message. So its ok to have a default /AltConfig "%O-bom.ini" option in KiCad. For project specific settings when required.
* Easy change of report language using /LanguageCode commandline option and corresponding specifier usable when importing files. Defaults to active language of the interpreter.
* Fixed some issues with task dependencies

## Changelog version 2.0
* Version 6.5 of the XML interpreter
* File restructuring and clean up
* New datatype for values (32 decimals floating point BCD combined with unit)
* Main program is now task based. Which tasks (Bom, BomEEVBlog, BomDokuWiki, BomDesignators, BomOrderPicking, Stock, StorageLocations, PartKeeprProjects) will be executed can be set on commandline. For example:
  *   /var Unattended Bom,BomDesignators,BomOrderPicking
* Some report fields (ESerieOfValue, ResistorMaxAmpVolt, ZenerDiodeMaxAmp, Footprint) can be hidden using the commandline. For example:
  *   /var HideSpecs ESerieOfValue,ResistorMaxAmpVolt,ZenerDiodeMaxAmp,Footprint
* A report tab can be activated from the commandline. For example:
  *   /ActivateReportTarget StorageLocationReport
* Add 1 additional componentkind
* Add device mappings
* Ranges are displayed differently
* Report tabs are simplified
