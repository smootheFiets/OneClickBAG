# OneClickBAG
Quick JOSM presets for BAG imports that work with a single click.  If you don't know what BAG imports are, this preset is probably not for you.  Also: `bagChecks.validator.mapcss` providing validator checks useful for maintaining the BAG import in NL.

#### Tagging preset 
'Is er nog': to be used on buildings that are still visible in PDOK, although they've been deleted from the BAG.  Replaces `ref:bag` with `ref:bag:old`, and sets `source=BAG;PDOK`, `source:date=2020` (to be updated once PDOK imagery from 2021+  becomes available).  This preset opens a GUI window, but no user input is requested (nor useful, typically).  This is due to a technical limitation of JOSM.

'Mest': to be used on storage tanks (I mostly see them on farms, hence the name).  The preset sets `building=storage_tank`, `man_made=storage_tank`.

Status: deletes tags `building` and `source:date`. Use on existing way before merging with newly imported way with updated status (typically: building=construction --> building=*); the validator auto-fix won't get rid of `building=construction`, so we need to help it a little bit.  Also useful on re-imported address nodes: apply to old node to delete `source:date` (most quickly from validator selection, then search `selected -new`), such that old and new node can be merged efficiently.

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
* 0.5, 2021-09-10: improve timestamp-check on non-BAG buildings
* 0.6, 2021-09-12: remove 'geometry' (validator fix takes care of this), add 'is er nog', reduce scope of 'mest'
* 0.7_2021-09-16: trim down 'status' preset, eliminate validator warning against houses w/o address node
