---
title: Data Viewing Overview
---
# Data Viewing Overview

Data Viewing refers to the functionality that allows users to interact with and visualize their database data. It provides a graphical interface where users can query, browse, and analyze the data stored in their Progress/OpenEdge databases.

## Key Components

The <SwmPath>[query-data.w](query-data.w)</SwmPath> file is a key component in the Data Viewing process, defining the window and control structures for displaying data.

## Safe Data Viewing

The <SwmPath>[DataReader.p](DataReader.p)</SwmPath> script launches the <SwmToken path="DataReader.p" pos="4:8:8" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`DataDigger`</SwmToken> application in read-only mode, ensuring that users can safely view data without making modifications.

<SwmSnippet path="/DataReader.p" line="1">

---

The <SwmPath>[DataReader.p](DataReader.p)</SwmPath> script initializes the <SwmToken path="DataReader.p" pos="4:8:8" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`DataDigger`</SwmToken> application in read-only mode, preventing any data modifications.

```openedge abl
/*------------------------------------------------------------------------

  Name: DataReader.p
  Desc: Launcher for DataDigger in ReadOnly mode

  ----------------------------------------------------------------------*/
DEFINE VARIABLE gcProgramDir AS CHARACTER NO-UNDO.

/* Where are we running from? */
FILE-INFO:FILE-NAME = THIS-PROCEDURE:FILE-NAME.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
