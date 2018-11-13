![Spec schema](https://github.com/HendriXML/KiCad-BOM-reporter/blob/master/Wiki/Comment%20images/SpecSchema.png
)

I made the above database schema to share my thoughts on the following. 
## But first what will be the benefits?
- Cascading specification values (no need to duplicate values like powerrating of resistors within a category)
- Uniform descriptions that are in sync with specifications
- Units are defined at property type level (and not on value level)
- "Parts" could be matched automatic with schema specifications, no need for MetaParts.
- Better performance?

## How?
With the introduction of SpecNodes which can (only) have dynamic properties. These properties are for example:
- resistance
- capacitance
- tolerance
- powerrating
- voltagerating
- footprint

Like PartParameters but handled by different tables for different datatypes. Descriptions should be generated from those parameters (and maybe exist in a cached form?). A property type could also contain info on how to match this property on a schema part (specification). For instance %2 tolerance is ok when requesting only %5.

SpecNodes replace categories and parts, which in the suggested situation now references a SpecNode). So a single SpecNode can be assigned to multiple parts (at different storage locations, of different prices/qualities).

SpecNodes could be displayed like a tree, in the way categories are shown in a tree now. But only if they aren't leave nodes. The leave nodes are displayed like the current parts.

A SpecNode inherits all the properties (specification values) of its parent. Which Properties can be set are defined by the SpecClass of the SpecNode. These could be displayed even when they aren't set. So no need to add a property by hand.

## How could this made to perform?

For property values (SpecProperty%) create covered indexes. Read them sorted by (SpecNodeID, PropertyTypeID) and merge them with the SpecNodes. This can be done at a very high reading speed. (like 50 MB/s).

Properties that aren't set don't take up space!
Properties are cascaded, so don't need to be set as much!

For the Text datatype it might be an idea to use a (webserver cached) text reference to a TextData table, which records are not allowed to be updated only created new. And use delayed loading of those (but only ones -> cache).


## Can it be done?

My experience in php is zero, but I think in a object oriented environment it could be done. But it means all the data should be implemented as objects. Which then interact with the user interface. This extra level is needed to keep it maintainable. But I don't know whether this is possible in the current framework.
