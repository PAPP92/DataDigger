---
title: Procedures in DataReader.p
---
This document will cover the procedures defined in the <SwmPath>[DataReader.p](DataReader.p)</SwmPath> file, including:

1. What the file does
2. The flow of the file
3. Detailed explanations of each procedure.

## What the File Does

The <SwmPath>[DataReader.p](DataReader.p)</SwmPath> file serves as a launcher for <SwmToken path="DataReader.p" pos="4:8:8" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`DataDigger`</SwmToken> in <SwmToken path="DataReader.p" pos="4:12:12" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`ReadOnly`</SwmToken> mode. It determines the directory from which it is running and then starts the actual <SwmToken path="DataReader.p" pos="4:8:8" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`DataDigger`</SwmToken> program by running <SwmPath>[DataDigger2.p](DataDigger2.p)</SwmPath> with a <SwmToken path="DataReader.p" pos="4:12:12" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`ReadOnly`</SwmToken> mode parameter.

## File Flow

The high-level flow of the <SwmPath>[DataReader.p](DataReader.p)</SwmPath> file is as follows:

1. Determine the directory from which the script is running.
2. Replace backslashes with forward slashes in the directory path.
3. Extract the directory path up to the last slash.
4. Run the <SwmPath>[DataDigger2.p](DataDigger2.p)</SwmPath> program with <SwmToken path="DataReader.p" pos="4:12:12" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`ReadOnly`</SwmToken> mode enabled.

<SwmSnippet path="/DataReader.p" line="1">

---

## Procedures

First, the <SwmPath>[DataReader.p](DataReader.p)</SwmPath> file defines a variable <SwmToken path="DataReader.p" pos="7:4:4" line-data="DEFINE VARIABLE gcProgramDir AS CHARACTER NO-UNDO.">`gcProgramDir`</SwmToken> to store the directory path. It then determines the directory from which the script is running by setting <SwmToken path="DataReader.p" pos="10:0:6" line-data="FILE-INFO:FILE-NAME = THIS-PROCEDURE:FILE-NAME.">`FILE-INFO:FILE-NAME`</SwmToken> to <SwmToken path="DataReader.p" pos="10:10:16" line-data="FILE-INFO:FILE-NAME = THIS-PROCEDURE:FILE-NAME.">`THIS-PROCEDURE:FILE-NAME`</SwmToken>. If the full pathname is not available, it replaces the <SwmToken path="DataReader.p" pos="3:5:6" line-data="  Name: DataReader.p">`.p`</SwmToken> extension with <SwmToken path="DataReader.p" pos="12:29:30" line-data="  FILE-INFO:FILE-NAME = REPLACE(THIS-PROCEDURE:FILE-NAME, &#39;.p&#39;, &#39;.r&#39;).">`.r`</SwmToken>.

```openedge abl
/*------------------------------------------------------------------------

  Name: DataReader.p
  Desc: Launcher for DataDigger in ReadOnly mode

  ----------------------------------------------------------------------*/
DEFINE VARIABLE gcProgramDir AS CHARACTER NO-UNDO.

/* Where are we running from? */
FILE-INFO:FILE-NAME = THIS-PROCEDURE:FILE-NAME.
IF FILE-INFO:FULL-PATHNAME = ? THEN
  FILE-INFO:FILE-NAME = REPLACE(THIS-PROCEDURE:FILE-NAME, '.p', '.r').

gcProgramDir = REPLACE(FILE-INFO:FULL-PATHNAME,"\","/").
gcProgramDir = SUBSTRING(gcProgramDir,1,R-INDEX(gcProgramDir,'/')).

/* Start the actual DataDigger program */
RUN VALUE(gcProgramDir + "DataDigger2.p") (INPUT TRUE).
```

---

</SwmSnippet>

<SwmSnippet path="/DataReader.p" line="14">

---

Next, the script replaces backslashes with forward slashes in the directory path and extracts the directory path up to the last slash. Finally, it runs the <SwmPath>[DataDigger2.p](DataDigger2.p)</SwmPath> program with <SwmToken path="DataReader.p" pos="4:12:12" line-data="  Desc: Launcher for DataDigger in ReadOnly mode">`ReadOnly`</SwmToken> mode enabled by passing <SwmToken path="DataReader.p" pos="18:16:18" line-data="RUN VALUE(gcProgramDir + &quot;DataDigger2.p&quot;) (INPUT TRUE).">`INPUT TRUE`</SwmToken> as a parameter.

```openedge abl
gcProgramDir = REPLACE(FILE-INFO:FULL-PATHNAME,"\","/").
gcProgramDir = SUBSTRING(gcProgramDir,1,R-INDEX(gcProgramDir,'/')).

/* Start the actual DataDigger program */
RUN VALUE(gcProgramDir + "DataDigger2.p") (INPUT TRUE).
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
