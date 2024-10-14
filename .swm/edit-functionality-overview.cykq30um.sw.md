---
title: Edit Functionality Overview
---
# Understanding Edit Functionality

Edit functionality allows users to modify existing records in the database. It provides an interface where users can change the values of the fields in a selected record.

## Structure and Behavior

The <SwmPath>[wEdit.w](wEdit.w)</SwmPath> file defines the structure and behavior of the edit window, including the buttons and fields available for interaction. Temporary tables like <SwmToken path="wEdit.w" pos="52:6:6" line-data="DEFINE TEMP-TABLE ttRecordMapping NO-UNDO">`ttRecordMapping`</SwmToken> are used to keep track of the records being edited.

## Main Functions

Several main functions are defined in the <SwmPath>[wEdit.w](wEdit.w)</SwmPath> file to handle different aspects of the edit functionality. These include <SwmToken path="wEdit.w" pos="104:2:2" line-data="FUNCTION increaseCharValue RETURNS CHARACTER">`increaseCharValue`</SwmToken>, <SwmToken path="wEdit.w" pos="90:2:2" line-data="btnOk btnClose tgWriteTrigger btnIncrease btnDatePicker btnEditor btnEncode ~">`btnClose`</SwmToken>, <SwmToken path="wEdit.w" pos="90:8:8" line-data="btnOk btnClose tgWriteTrigger btnIncrease btnDatePicker btnEditor btnEncode ~">`btnDatePicker`</SwmToken>, <SwmToken path="wEdit.w" pos="89:15:15" line-data="&amp;Scoped-Define ENABLED-OBJECTS brRecord tgSelAll fiNumRecords btnDecrease ~">`btnDecrease`</SwmToken>, <SwmToken path="wEdit.w" pos="130:4:4" line-data="DEFINE BUTTON btnEditor  NO-FOCUS FLAT-BUTTON">`btnEditor`</SwmToken>, <SwmToken path="wEdit.w" pos="134:4:4" line-data="DEFINE BUTTON btnEncode  NO-FOCUS FLAT-BUTTON">`btnEncode`</SwmToken>, <SwmToken path="wEdit.w" pos="90:6:6" line-data="btnOk btnClose tgWriteTrigger btnIncrease btnDatePicker btnEditor btnEncode ~">`btnIncrease`</SwmToken>, <SwmToken path="wEdit.w" pos="91:0:0" line-data="btnListEdit btnLowerCase btnUpperCase btnWordCase ">`btnListEdit`</SwmToken>, <SwmToken path="wEdit.w" pos="91:2:2" line-data="btnListEdit btnLowerCase btnUpperCase btnWordCase ">`btnLowerCase`</SwmToken>, <SwmToken path="wEdit.w" pos="90:0:0" line-data="btnOk btnClose tgWriteTrigger btnIncrease btnDatePicker btnEditor btnEncode ~">`btnOk`</SwmToken>, <SwmToken path="wEdit.w" pos="91:4:4" line-data="btnListEdit btnLowerCase btnUpperCase btnWordCase ">`btnUpperCase`</SwmToken>, and <SwmToken path="wEdit.w" pos="91:6:6" line-data="btnListEdit btnLowerCase btnUpperCase btnWordCase ">`btnWordCase`</SwmToken>.

### <SwmToken path="wEdit.w" pos="104:2:2" line-data="FUNCTION increaseCharValue RETURNS CHARACTER">`increaseCharValue`</SwmToken>

The <SwmToken path="wEdit.w" pos="104:2:2" line-data="FUNCTION increaseCharValue RETURNS CHARACTER">`increaseCharValue`</SwmToken> function is used to increment the value of a character field. This function is essential for operations that require character manipulation within the edit window.

<SwmSnippet path="/wEdit.w" line="104">

---

The <SwmToken path="wEdit.w" pos="104:2:2" line-data="FUNCTION increaseCharValue RETURNS CHARACTER">`increaseCharValue`</SwmToken> function definition in the <SwmPath>[wEdit.w](wEdit.w)</SwmPath> file.

```c
FUNCTION increaseCharValue RETURNS CHARACTER
  ( pcCharValue AS CHARACTER
  , piDelta     AS INTEGER) FORWARD.

/* _UIB-CODE-BLOCK-END */
```

---

</SwmSnippet>

### <SwmToken path="wEdit.w" pos="130:4:4" line-data="DEFINE BUTTON btnEditor  NO-FOCUS FLAT-BUTTON">`btnEditor`</SwmToken>

The <SwmToken path="wEdit.w" pos="130:4:4" line-data="DEFINE BUTTON btnEditor  NO-FOCUS FLAT-BUTTON">`btnEditor`</SwmToken> button provides an interface for editing the selected record. It triggers the edit functionality, allowing users to modify the values of the fields in the record.

<SwmSnippet path="/wEdit.w" line="130">

---

The <SwmToken path="wEdit.w" pos="130:4:4" line-data="DEFINE BUTTON btnEditor  NO-FOCUS FLAT-BUTTON">`btnEditor`</SwmToken> button definition in the <SwmPath>[wEdit.w](wEdit.w)</SwmPath> file.

```c
DEFINE BUTTON btnEditor  NO-FOCUS FLAT-BUTTON
     LABEL "Edit" 
     SIZE-PIXELS 30 BY 23 TOOLTIP "view-as editor (F3)".

DEFINE BUTTON btnEncode  NO-FOCUS FLAT-BUTTON
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
