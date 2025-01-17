---
menu:
  main:
    name: "5.85 (June 2021)"
    identifier: "5.85"
    parent: "releases"
    weight: -585
---

> No re-index is required for this release.

> This version includes the update of elasticsearch to version 7.11. It does not understand the setting `reclaim_deletes_weight` any more. If you have problems see [these instructions to remove it](/en/technical/elasticsearch/updates/version_7.11).

# Version 5.85.2

*Published 30.06.2021*

## Web front end

### Fixed

* fixed wrong mask selection for linked objects in editor

## Plugins

### Fixed

* fixed URL encoding for retrieving data in IUCN plugin

# Version 5.85.1

*Published 22.06.2021*

## Web front end

### Fixed

* fixed download of presentations


# Version 5.85.0

*Published 16.06.2021*

## Web front end

### New

* use new system right parameter `enable_ignore_linked_objects_filter` (see server part) to skip filter for linked objects
* option to show only first row of nested field in PDF creator

### Improved

* disable save button when there is an email action in workflows without recipients
* accessibility improvements
* sort masks alphabetically in datamodel editor
* show first letter of tag if it has no icon set
* standard support for custom data type "location"

### Fixed

* fixed linked object hierarchy visibility
* add filters in expert search for linked objects
* encoding fix for asset upload in CSV importer
* fix visibility of fields in filters
* hide system users in email workflows
* fix saving of asset in nested inside nested table
* fix detail deeplink problem
* fix problem when switching between objects in fullscreen detail view

## Server

### New 

* new param `enable_ignore_linked_objects_filter` for `system.frontend_features` (replaces `system.disable_linked_objects_filter`)
* asset deletion simulation (disabled by default). This may be used to find errors before actually cleaning up images

### Improved

* asset URL output in CSV export
* better error handling when running Node.js scripts

### Fixed
* no attempt to send mails to archived users in groups (failed before)
* removed unused data from user "short" format
* link used assets in preparation for removal (on startup, `use debug.disable_collect_missing_asset_links: true` in case of errors)
* remove interal data from objects

# Checksums

Here are the checksums of our Docker images (latest version):

```ini
docker.easydb.de/pf/chrome               sha256:effcf603c923c8cafc5b302b717353bb43a447a9df858ce0e66e263fae4f93f3
docker.easydb.de/pf/eas                  sha256:3f5d195b23c53768d860d60b343358497296f8f78d5db918cd032fcb80882e74
docker.easydb.de/pf/elasticsearch        sha256:8ed3f3d5a05436c8297b2bf3aa1d359aa1256dc89ceaa429b1daa7c11e4f1ea4
docker.easydb.de/pf/fylr                 sha256:766441fba764067ab9b2aa6674490cbe53f74a2db70a5fd436b80b7fd7ce297b
docker.easydb.de/pf/postgresql-11        sha256:88f53efde21bbf527ae3aea5022f5657c89d7ac8fa75a11c22ffa955ce207012
docker.easydb.de/pf/server-base          sha256:564e41d86bcbaaf3275e3957d58e1b34e6ab93a4454c31fe8040657e7e2ae1bd
docker.easydb.de/pf/webfrontend          sha256:ea21e1fef1e4761fcebfe62660d9c39514f83bf00b3cf3a89deb17447bb62c6b
```
