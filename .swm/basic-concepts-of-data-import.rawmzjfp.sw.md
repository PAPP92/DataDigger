---
title: Basic Concepts of Data Import
---
# Basic Concepts of Data Import

Data import refers to the functionality that allows users to bring external data into the system. It involves selecting files, loading them, and processing the data to be integrated into the database. The user interface provides various controls and steps to facilitate this process, ensuring that the data is correctly mapped and validated before being imported.

## Import Process Overview

The import process involves three main steps: selecting files, loading data, and processing data. Each step ensures that the data is correctly mapped and validated before being imported into the database.

<SwmSnippet path="/wImportSel.w" line="66">

---

## Selecting Files

The file <SwmPath>[wImportSel.w](wImportSel.w)</SwmPath> defines the user interface elements for selecting files to be imported, such as buttons and input fields. These elements include buttons for adding files, navigating back, and proceeding to the next step.

```c
/* Definitions of the field level widgets                               */
DEFINE BUTTON btnAddFile 
     LABEL "+" 
     SIZE-PIXELS 25 BY 21 TOOLTIP "add file".

DEFINE BUTTON btnBack DEFAULT 
     LABEL "&Back" 
     SIZE-PIXELS 75 BY 24 TOOLTIP "cancel load data"
     BGCOLOR 8 .

DEFINE BUTTON btnGetFile 
     LABEL "..." 
     SIZE-PIXELS 25 BY 21 TOOLTIP "add one or more files".

DEFINE BUTTON BtnNext 
     LABEL "&Next" 
     SIZE-PIXELS 75 BY 24 TOOLTIP "analyze files"
     BGCOLOR 8 .

DEFINE VARIABLE edFileList AS CHARACTER 
     VIEW-AS EDITOR NO-WORD-WRAP SCROLLBAR-HORIZONTAL SCROLLBAR-VERTICAL
```

---

</SwmSnippet>

<SwmSnippet path="/wImportLoad.w" line="18">

---

## Loading Data

The file <SwmPath>[wImportLoad.w](wImportLoad.w)</SwmPath> defines the parameters and variables needed to load the selected data into the system. This includes input parameters for database and table names, as well as output parameters for success status and reposition ID.

```c
DEFINE INPUT PARAMETER plReadOnlyDigger   AS LOGICAL   NO-UNDO.
DEFINE INPUT PARAMETER TABLE-HANDLE pihXmlTable.
DEFINE INPUT PARAMETER picDatabase        AS CHARACTER NO-UNDO.
DEFINE INPUT PARAMETER picTableName       AS CHARACTER NO-UNDO.
DEFINE INPUT PARAMETER TABLE FOR ttField.
DEFINE INPUT PARAMETER TABLE FOR ttColumn.
DEFINE OUTPUT PARAMETER polSuccess        AS LOGICAL   NO-UNDO INITIAL ?.
DEFINE OUTPUT PARAMETER porRepositionId   AS ROWID     NO-UNDO.
```

---

</SwmSnippet>

## Processing Data

The file `wImport.w` defines the parameters and variables needed to process the loaded data and integrate it into the database. This step ensures that the data is correctly mapped and validated before being imported.

## Main Functions

Several main functions are used during the import process to log messages and handle errors. These functions include <SwmToken path="wImportCheck.w" pos="79:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addError wImport ">`addError`</SwmToken>, <SwmToken path="wImportCheck.w" pos="88:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addInfo wImport ">`addInfo`</SwmToken>, <SwmToken path="wImportCheck.w" pos="97:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addMessage wImport ">`addMessage`</SwmToken>, <SwmToken path="wImportCheck.w" pos="107:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addWarning wImport ">`addWarning`</SwmToken>, and <SwmToken path="wImportCheck.w" pos="116:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD hasWarnings wImport ">`hasWarnings`</SwmToken>.

<SwmSnippet path="/wImportCheck.w" line="79">

---

### <SwmToken path="wImportCheck.w" pos="79:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addError wImport ">`addError`</SwmToken>

The <SwmToken path="wImportCheck.w" pos="79:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addError wImport ">`addError`</SwmToken> function is used to log error messages during the import process. It ensures that any issues encountered are recorded for further review.

```c
&ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addError wImport 
FUNCTION addError RETURNS LOGICAL
  ( piFileNr  AS INTEGER
  , pcMessage AS CHARACTER
  )  FORWARD.

/* _UIB-CODE-BLOCK-END */
```

---

</SwmSnippet>

<SwmSnippet path="/wImportCheck.w" line="88">

---

### <SwmToken path="wImportCheck.w" pos="88:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addInfo wImport ">`addInfo`</SwmToken>

The <SwmToken path="wImportCheck.w" pos="88:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addInfo wImport ">`addInfo`</SwmToken> function is used to log informational messages. This helps in tracking the progress and status of the import process.

```c
&ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addInfo wImport 
FUNCTION addInfo RETURNS LOGICAL
  ( piFileNr  AS INTEGER
  , pcMessage AS CHARACTER
  )  FORWARD.

/* _UIB-CODE-BLOCK-END */
```

---

</SwmSnippet>

<SwmSnippet path="/wImportCheck.w" line="97">

---

### <SwmToken path="wImportCheck.w" pos="97:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addMessage wImport ">`addMessage`</SwmToken>

The <SwmToken path="wImportCheck.w" pos="97:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addMessage wImport ">`addMessage`</SwmToken> function is used to log general messages. It provides a way to record various types of messages that are not strictly errors or informational.

```c
&ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addMessage wImport 
FUNCTION addMessage RETURNS LOGICAL
  ( piFileNr  AS INTEGER
  , piType    AS INTEGER
  , pcMessage AS CHARACTER
  )  FORWARD.

/* _UIB-CODE-BLOCK-END */
```

---

</SwmSnippet>

<SwmSnippet path="/wImportCheck.w" line="107">

---

### <SwmToken path="wImportCheck.w" pos="107:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addWarning wImport ">`addWarning`</SwmToken>

The <SwmToken path="wImportCheck.w" pos="107:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addWarning wImport ">`addWarning`</SwmToken> function is used to log warning messages. It helps in identifying potential issues that may not be critical but should be addressed.

```c
&ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD addWarning wImport 
FUNCTION addWarning RETURNS LOGICAL
  ( piFileNr  AS INTEGER
  , pcMessage AS CHARACTER
  )  FORWARD.

/* _UIB-CODE-BLOCK-END */
```

---

</SwmSnippet>

<SwmSnippet path="/wImportCheck.w" line="116">

---

### <SwmToken path="wImportCheck.w" pos="116:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD hasWarnings wImport ">`hasWarnings`</SwmToken>

The <SwmToken path="wImportCheck.w" pos="116:15:15" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD hasWarnings wImport ">`hasWarnings`</SwmToken> function checks if there are any warning messages logged. This is useful for determining if the import process encountered any non-critical issues.

```c
&ANALYZE-SUSPEND _UIB-CODE-BLOCK _FUNCTION-FORWARD hasWarnings wImport 
FUNCTION hasWarnings RETURNS LOGICAL
  ( /* parameter-definitions */ )  FORWARD.

/* _UIB-CODE-BLOCK-END */
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
