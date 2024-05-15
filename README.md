# ifc-tweak


Discussions around the next major scheme version for [Industry Foundation Classes (IFC)](https://www.buildingsmart.org/standards/bsi-standards/industry-foundation-classes/), IFC5, often focus around the need to "blow up and start over". The premise is that IFC as it is today (IFC 4.3) has introduced too many complexities, edge cases, and options to be fixable without a clean slate approach. The promise of a green field effort is appealing, but the un(der)spoken reality is that the world's open building data is stored in the IFC major releases we already have. Corporations, munipalities, and governments depend on IFC data to last _a long time_ - as long as the buildings, bridges, and tunnels they represent. A green field effort without a strategy for incremental migration of exsting IFC data is fundamentally at odds with the need of the broader community.

`ifc-tweak` is a demonstration that meaningful evolution of the IFC schema can occur through incremental changes ("tweaks") to the existing EXPRESS schema. Rather than starting from scratch, `ifc-tweak` start from the [existing IFC release](https://standards.buildingsmart.org/IFC/RELEASE/IFC4_3/HTML/IFC4X3_ADD2.exp), and imposes as series of small, incremental "tweaks" (represented as Github feature branches) to streamline its structure. Each change on its own doesn't "fix IFC", but when layered on top of each other shows how a pragmatic IFC5 can evolve while respecting the needs for continuity with existing data. 


The repositories branches follow a common structure, with the `schema.exp` file at its center:
- `main` always tracks the current official IFC release (i.e., `schema.exp` represents IFC 4.3)
- `tweak/<descriptor>` branches identify a particular tweak. Tweaks adopted from the BuildingSmart [NextGen-IFC](https://github.com/buildingSMART/NextGen-IFC/issues) are specifically named according to `tweak/nextgen-<issue-number>`. 
- `future*` branches identify an an [octopus merge](https://www.freblogg.com/git-octopus-merge) of one or more `tweak` branches.

Some low-hanging fruit for IFC `tweaks` include:
- Replacing IfcLogical with OPTIONAL IfcBoolean [#92](https://github.com/buildingSMART/NextGen-IFC/issues/92) - `tweak/nextgen-92`
- Removing LIST OF LISTS [#91](https://github.com/buildingSMART/NextGen-IFC/issues/91)
- Fixing inconsistent use of IfcInteger [#80](https://github.com/buildingSMART/NextGen-IFC/issues/80)
- Replacing ARRAYS with LISTS [#21](https://github.com/buildingSMART/NextGen-IFC/issues/21)
- Replacing STRING types with Where Rules with Enumerations [#82](https://github.com/buildingSMART/NextGen-IFC/issues/82)

Addressing and merging simple tweaks makes larger changes easier and more practical to tackle. 