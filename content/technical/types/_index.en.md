---
menu:
  main:
    name: "types"
    identifier: "technical/types"
    parent: "technical"
---
# Easydb Types

This section describes the types used by the easydb API. Unless otherwise stated, the types are represented
as JSON objects. For the attributes description, the following rules apply:

- attributes are present in a response unless they are "write-only" or "optional" and not set
- attributes must be given in a request unless they are marked as "optional"
- if an optional attribute does not specify a default value, it is null or an empty list
- unique attributes are marked as "unique"
- foreign keys are marked as using "ref" followed by the type and column referenced
- IDs are generated by easydb. They are only given in a request to identify elements
- When specifying lists, "1+" means that at least one element must be given

# Search

The Easydb types that can appear as results in [/api/search](/en/technical/api/search) have an additional column.
This column tells if and how a field is indexed . If nothing is specified, the field is not indexed,
which means it cannot be used as a valid field value in /api/search for searching, sorting or faceting. If the column
contains "*not present*", it means that the field is not stored in the index, which means that it will not be visible
in search results.

If the field is index, the column has the following information:

`<type>[ (all)]`

The search types are:

- Number: an integer or decimal number.
- Text: a text that is interpreted as a succession of words. A "match" search will match beginning of words.
- L10n: a localized text (search can be specified for one or more languages)
- String: a text that is interpreted as a whole word (for example, a book signature). A "match" search will match also inside a word.
- NotAnalyzed: a text which is not analyzed and can be therefore only searched as a whole word (for example, a type).
- Date: a date with support for timezones, B.C. dates and time. A "range" search is possible for this type.

The [/api/search](/en/technical/api/search) documentation specifies which types can be used in each part of the
search definition. For instance, the search parameter "match" only accepts Text, String and L10n fields.

`(all)` means that the field will be searched if no fields are given (search in "all" fields).