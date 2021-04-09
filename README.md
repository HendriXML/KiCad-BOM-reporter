# KiCad-BOM-reporter
Reports a bill of material list from KiCad 5 - specifications are matched with a PartKeepr database

See [wiki](https://github.com/HendriXML/KiCad-BOM-reporter/wiki), [screenshots](https://github.com/HendriXML/KiCad-BOM-reporter/wiki/Screenshots) or [features](https://github.com/HendriXML/KiCad-BOM-reporter/wiki/Features) for more details.

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
