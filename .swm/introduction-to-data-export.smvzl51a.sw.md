---
title: Introduction to Data Export
---
# Introduction to Data Export

Data export, also known as data dumping, is the process of exporting data from a database into a file format. This is typically done for purposes such as backup, analysis, or migration.

# DumpAndLoad Window

In <SwmToken path="dDumpDf.w" pos="15:2:2" line-data="{ DataDigger.i }">`DataDigger`</SwmToken>, data export can be performed through the DumpAndLoad window. This window allows users to export data to a TXT file. The process can be aborted if needed, providing flexibility and control over the operation.

# Filename Handling

<SwmToken path="dDumpDf.w" pos="15:2:2" line-data="{ DataDigger.i }">`DataDigger`</SwmToken> ensures that the correct file name is used during the dump, even if the filename contains special characters like underscores. This feature helps maintain consistency and avoid errors during the export process.

# Main Functions

There are several main functions involved in the data export process. Two of the key functions are <SwmToken path="dDumpDf.w" pos="257:13:13" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _PROCEDURE dumpDF Dialog-Frame ">`dumpDF`</SwmToken> and <SwmToken path="generate-DumpLoad-Procedure.w" pos="7:4:8" line-data="  Name: generate-DumpLoad-Procedure.w">`generate-DumpLoad-Procedure`</SwmToken>.

<SwmSnippet path="/dDumpDf.w" line="257">

---

## <SwmToken path="dDumpDf.w" pos="257:13:13" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _PROCEDURE dumpDF Dialog-Frame ">`dumpDF`</SwmToken>

The <SwmToken path="dDumpDf.w" pos="257:13:13" line-data="&amp;ANALYZE-SUSPEND _UIB-CODE-BLOCK _PROCEDURE dumpDF Dialog-Frame ">`dumpDF`</SwmToken> procedure is responsible for executing the progress procedure for dumping data. It ensures that the data is correctly exported from the database.

```c
&ANALYZE-SUSPEND _UIB-CODE-BLOCK _PROCEDURE dumpDF Dialog-Frame 
PROCEDURE dumpDF :
/* Execute progress procedure for dumping 
*/  
```

---

</SwmSnippet>

<SwmSnippet path="/generate-DumpLoad-Procedure.w" line="1">

---

## <SwmToken path="generate-DumpLoad-Procedure.w" pos="7:4:8" line-data="  Name: generate-DumpLoad-Procedure.w">`generate-DumpLoad-Procedure`</SwmToken>

The <SwmToken path="generate-DumpLoad-Procedure.w" pos="7:4:8" line-data="  Name: generate-DumpLoad-Procedure.w">`generate-DumpLoad-Procedure`</SwmToken> file includes the setup and definitions necessary for generating dump and load procedures. It defines the window and frame settings, control definitions, and runtime attributes required for the data dumping process.

```c
&ANALYZE-SUSPEND _VERSION-NUMBER AB_v10r12 GUI
&ANALYZE-RESUME
&Scoped-define WINDOW-NAME C-Win
&ANALYZE-SUSPEND _UIB-CODE-BLOCK _CUSTOM _DEFINITIONS C-Win 
/*------------------------------------------------------------------------

  Name: generate-DumpLoad-Procedure.w
  Desc: Generate dump/load procedure for current file

  ----------------------------------------------------------------------*/
/*          This .W file was created with the Progress AppBuilder.      */
/*----------------------------------------------------------------------*/
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
