---
title: Database Operations Overview
---
# Database Operations Overview

Database operations refer to the various actions that can be performed on a database, such as creating, reading, updating, and deleting data. In <SwmToken path="dCloneDatabase.w" pos="15:2:2" line-data="{ DataDigger.i }">`DataDigger`</SwmToken>, these operations include creating an empty clone of a database, dumping database definitions, generating bulk delete statements, assigning statements, generating active record classes, temporary table includes, and <SwmToken path="generate-DumpLoad-Procedure.w" pos="8:6:8" line-data="  Desc: Generate dump/load procedure for current file">`dump/load`</SwmToken> procedures. These operations allow users to interact with their Progress/OpenEdge databases efficiently, providing functionalities to manage and manipulate database data.

<SwmSnippet path="/dCloneDatabase.w" line="100">

---

## Creating a Clone Database

The <SwmPath>[dCloneDatabase.w](dCloneDatabase.w)</SwmPath> file includes functionality for creating an empty clone of a database. This operation is useful for testing or backup purposes.

```c
         TITLE "Create an empty Clone Database"
         DEFAULT-BUTTON Btn_OK CANCEL-BUTTON Btn_Cancel.


/* *********************** Procedure Settings ************************ */

&ANALYZE-SUSPEND _PROCEDURE-SETTINGS
/* Settings for THIS-PROCEDURE
   Type: Dialog-Box
   Allow: Basic,Browse,DB-Fields,Query
   Other Settings: COMPILE
 */
&ANALYZE-RESUME _END-PROCEDURE-SETTINGS



/* ***********  Runtime Attributes and AppBuilder Settings  *********** */

&ANALYZE-SUSPEND _RUN-TIME-ATTRIBUTES
/* SETTINGS FOR DIALOG-BOX Dialog-Frame
   FRAME-NAME                                                           */
```

---

</SwmSnippet>

<SwmSnippet path="/dDumpDf.w" line="76">

---

## Dumping Database Definitions

The <SwmPath>[dDumpDf.w](dDumpDf.w)</SwmPath> file handles the operation of dumping database definitions. This is useful for exporting the structure of the database for documentation or migration purposes.

```c
"&Database [db]", "db",
```

---

</SwmSnippet>

<SwmSnippet path="/generate-Bulk-Delete.w" line="123">

---

## Generating Bulk Delete Statements

The <SwmPath>[generate-Bulk-Delete.w](generate-Bulk-Delete.w)</SwmPath> file supports generating bulk delete statements, which can be used to efficiently remove large amounts of data from the database.

```c
     SIZE-PIXELS 165 BY 17 TOOLTIP "use lower case for keywords" NO-UNDO.
```

---

</SwmSnippet>

<SwmSnippet path="/generate-Active-Record-Class.w" line="160">

---

## Generating Active Record Classes

The <SwmPath>[generate-Active-Record-Class.w](generate-Active-Record-Class.w)</SwmPath> file includes functionality for generating active record classes, which are useful for object-relational mapping and simplifying database interactions.

```c
     SIZE-PIXELS 160 BY 17 TOOLTIP "use lower case for keywords" NO-UNDO.

DEFINE VARIABLE tgSelectedOnly AS LOGICAL INITIAL no 
     LABEL "&Selected fields only" 
     VIEW-AS TOGGLE-BOX
     SIZE-PIXELS 160 BY 17 TOOLTIP "export only the fields that are selected in the main window" NO-UNDO.

DEFINE VARIABLE tgShortTypes AS LOGICAL INITIAL no 
     LABEL "&Short datatypes" 
     VIEW-AS TOGGLE-BOX
     SIZE-PIXELS 130 BY 17 TOOLTIP "use abbreviated datatypes (e.g. INT instead of INTEGER)" NO-UNDO.
```

---

</SwmSnippet>

<SwmSnippet path="/generate-TempTable-Include.w" line="217">

---

## Temporary Table Includes

The <SwmPath>[generate-TempTable-Include.w](generate-TempTable-Include.w)</SwmPath> file supports generating temporary table includes, which can be used for temporary data storage and manipulation within the database.

```c
     SIZE-PIXELS 160 BY 17 TOOLTIP "use lower case for keywords" NO-UNDO.

DEFINE VARIABLE tgSelectedOnly AS LOGICAL INITIAL no 
     LABEL "&Selected fields only" 
     VIEW-AS TOGGLE-BOX
     SIZE-PIXELS 160 BY 17 TOOLTIP "export only the fields that are selected in the main window" NO-UNDO.

DEFINE VARIABLE tgSerial AS LOGICAL INITIAL no 
     LABEL "Serialization" 
     VIEW-AS TOGGLE-BOX
     SIZE-PIXELS 110 BY 17 NO-UNDO.

DEFINE VARIABLE tgShortTypes AS LOGICAL INITIAL no 
     LABEL "&Short datatypes" 
     VIEW-AS TOGGLE-BOX
     SIZE-PIXELS 130 BY 17 TOOLTIP "use abbreviated datatypes (e.g. INT instead of INTEGER)" NO-UNDO.
```

---

</SwmSnippet>

<SwmSnippet path="/generate-DumpLoad-Procedure.w" line="139">

---

## <SwmToken path="generate-DumpLoad-Procedure.w" pos="8:6:8" line-data="  Desc: Generate dump/load procedure for current file">`dump/load`</SwmToken> Procedures

The <SwmPath>[generate-DumpLoad-Procedure.w](generate-DumpLoad-Procedure.w)</SwmPath> file handles the generation of <SwmToken path="generate-DumpLoad-Procedure.w" pos="8:6:8" line-data="  Desc: Generate dump/load procedure for current file">`dump/load`</SwmToken> procedures, which are essential for exporting and importing data to and from the database.

```c
     SIZE-PIXELS 165 BY 17 TOOLTIP "use lower case for keywords" NO-UNDO.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
