# OneClickNL
Quick JOSM presets for BAG imports that work with a single click.  If you don't know what BAG imports are, this preset is probably not for you.

Geometry: delete key/value pairs source:date and start_date. Use on existing way before merging with newly imported way with updated geometry.

Status: as geometry, delete building and construction, too.  Use on existing way before merging with newly imported way with updated status (typically: building=construction --> building=*)

Mest: to be used on storage tanks that are still present in PDOK imagery but deleted from the BAG.  This appears to happen frequently, at least in the are I'm familiar with.  Manually change ref:BAG to ref:BAG:old (or is there a way to make the preset make that change?  I couldn't find one), then apply this preset.  It will set building=storage_tank, man_made=storage_tank, source="BAG;PDOK", source:date=2020 (to be updated once PDOK imagery from 2021+ becomes available).
## Version history
* 0.1, 2021-05-09: first test version on Github

