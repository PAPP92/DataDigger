---
title: Overview of Configuration Settings
---
# Introduction to Configuration Settings

Configuration settings in <SwmToken path="DataDigger.i" pos="37:13:13" line-data="&amp;GLOBAL-DEFINE PINGBACKURL   https://is.gd/DataDigger">`DataDigger`</SwmToken> involve setting up various parameters and options to tailor the behavior and performance of the tool. These settings include defining global constants, setting maximum field lengths, specifying URLs for update checks, managing temporary tables, configuring caching options, and defining external procedures.

## Global Constants

Global constants like version, edition, and build information are defined to maintain consistency and manage different versions of the tool. These constants are essential for the tool's operation.

<SwmSnippet path="/DataDigger.i" line="13">

---

Defines global constants for version, edition, and build information.

```i
&GLOBAL-DEFINE version {version.i}
&GLOBAL-DEFINE edition Ironman
&GLOBAL-DEFINE build {build.i}
```

---

</SwmSnippet>

## Maximum Field Lengths

This section sets the maximum field lengths for editing character fields, ensuring data integrity and consistency.

<SwmSnippet path="/DataDigger.i" line="19">

---

Defines the maximum field length for editing character fields.

```i
/* Maximum field length for editing char fields */
&GLOBAL-DEFINE field-maxLength 2000
```

---

</SwmSnippet>

## URLs for Update Checks and Statistics

URLs for update checks and statistics collection are specified here, allowing the tool to stay updated and collect usage data.

<SwmSnippet path="/DataDigger.i" line="37">

---

Defines URLs for update checks and statistics collection.

```i
&GLOBAL-DEFINE PINGBACKURL   https://is.gd/DataDigger
&GLOBAL-DEFINE PINGBACKSTATS https://is.gd/stats.php?url=DataDigger
&GLOBAL-DEFINE LATESTVERSION https://is.gd/DataDigger26	
&GLOBAL-DEFINE EASTEREGG     https://is.gd/EasterEgg
```

---

</SwmSnippet>

## Temporary Tables (TTs)

Temporary tables are defined for various purposes, such as storing table data, field data, filter values, and user queries. These tables help in managing and organizing data efficiently.

<SwmSnippet path="/DataDigger.i" line="53">

---

Defines temporary tables for storing various types of data.

```i
DEFINE TEMP-TABLE ttLinkInfo NO-UNDO
  FIELD cField AS CHARACTER
  FIELD cValue AS CHARACTER
  INDEX idxPrim IS PRIMARY cField
  .

/* TT for the tables of a db */
DEFINE TEMP-TABLE ttTable NO-UNDO
  FIELD cSchemaHolder AS CHARACTER LABEL "SH"        FORMAT "X(12)"   
  FIELD cDatabase     AS CHARACTER LABEL "DB"        FORMAT "X(12)"
  FIELD cTableName    AS CHARACTER LABEL "Table"     FORMAT "X(32)"
  FIELD cCrc          AS CHARACTER LABEL "CRC"
  FIELD cCacheId      AS CHARACTER LABEL "CacheId"
  FIELD lShowInList   AS LOGICAL   LABEL "" /* for getTablesWithField */
  FIELD cTableDesc    AS CHARACTER LABEL "Desc"
  FIELD cTableLabel   AS CHARACTER LABEL "Label"
  FIELD cFields       AS CHARACTER LABEL "Fields"
  FIELD lHidden       AS LOGICAL   LABEL ""
  FIELD lFrozen       AS LOGICAL   LABEL ""
  FIELD iNumQueries   AS INTEGER   LABEL "#"         FORMAT "zzzzz"
  FIELD tLastUsed     AS DATETIME  LABEL "Last Used" FORMAT "99/99/9999 HH:MM:SS"
```

---

</SwmSnippet>

## Caching Options

Caching options are managed here, which can be enabled or disabled to optimize performance. This helps in reducing data retrieval times and improving the tool's efficiency.

<SwmSnippet path="/DataDigger.i" line="167">

---

Defines temporary tables used for caching to optimize performance.

```i
/* TTs Used for preCaching */
DEFINE TEMP-TABLE ttFieldCache NO-UNDO LIKE ttField
  INDEX idxTable IS PRIMARY cTableName
  .
DEFINE TEMP-TABLE ttColumnCache NO-UNDO LIKE ttColumn
  .

DEFINE DATASET dsFields FOR ttField, ttColumn.
DEFINE DATASET dsFieldCache FOR ttFieldCache, ttColumnCache.
```

---

</SwmSnippet>

## External Procedures

External procedures are defined for interacting with the Windows API, such as handling file operations and window updates. These procedures extend the functionality of the tool by leveraging external libraries.

<SwmSnippet path="/DataDigger2.p" line="49">

---

Defines an external procedure for interacting with the Windows API.

```openedge abl
PROCEDURE GetDriveTypeA EXTERNAL "kernel32.dll":
  DEFINE INPUT  PARAMETER lpRootPathName AS CHARACTER.
  DEFINE RETURN PARAMETER iType          AS LONG.
END PROCEDURE.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
