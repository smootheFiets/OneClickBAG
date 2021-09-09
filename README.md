# OneClickBAG
Quick JOSM presets for BAG imports that work with a single click.  If you don't know what BAG imports are, this preset is probably not for you.  Also: `bagChecks.validator.mapcss` providing validator checks useful for maintaining the BAG import in NL.

#### Tagging preset (mostly obsolete)
Geometry: delete key/value pairs source:date and start_date. Use on existing way before merging with newly imported way with updated geometry.

Status: as geometry, delete building and construction, too.  Use on existing way before merging with newly imported way with updated status (typically: building=construction --> building=*)

Mest: to be used on storage tanks that are still present in PDOK imagery but deleted from the BAG.  This appears to happen frequently, at least in the area I'm familiar with.  Manually change ref:BAG to ref:BAG:old (or is there a way to make the preset make that change?  I couldn't find one), then apply this preset.  It will set `building=storage_tank`, `man_made=storage_tank`, `source="BAG;PDOK"`, `source:date=2020` (to be updated once PDOK imagery from 2021+ becomes available).

#### Validator
Throws warnings at a couple BAG problems I've encountered in the wild:
* BAG buildings without `start_date` (should it really be a `static_caravan` or a `houseboat`?)
* Nodes with `ref:bag` (should be on the building outline)
* Areas with `ref:bag` without `building`, `landuse=houseboat` or `landuse=static_caravan` (building tag missing?)
* Non-BAG buildings that haven't been touched since 2020-01-01 (date subject to change)
* houses/apartments without an address node (address node missing / moved elsewhere accidentally?)

An error is thrown at address nodes that are part of a way; this can happen accidentally when iD users pan the map.

## Version history
* 0.1, 2021-05-09: first version on Github
* 0.2, 2021-05-12: allow 'geometry' and 'status' on (address) nodes, too
* 0.3, 2021-09-06: add bagChecks.validator.mapcss
* 0.4, 2021-09-09: expand bagChecks.validator.mapcss, update README.md
