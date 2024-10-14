---
title: Overview of Settings
---
# Overview of Settings

Settings refer to the configuration options available within the <SwmToken path="wSettings.w" pos="15:2:2" line-data="{ DataDigger.i }">`DataDigger`</SwmToken> user interface. These settings allow users to customize various aspects of the application to suit their preferences and requirements.

## Settings Organization

Settings are organized into different tabs, each focusing on specific areas such as general preferences, database configurations, and user interface adjustments.

## Accessing Settings

Users can access these settings through the designated settings window, which provides a structured and user-friendly interface for making changes.

## Controls in Settings

The settings window includes various controls such as buttons, checkboxes, and input fields to facilitate easy modification of the application's behavior.

## Applying Changes

Changes made in the settings are typically applied immediately or upon restarting the application, ensuring that users can quickly see the effects of their adjustments.

# Main Functions

There are several main functions in this folder. Some of them are <SwmToken path="wSettings.w" pos="40:2:2" line-data="PROCEDURE SetScrollPos EXTERNAL &quot;USER32.DLL&quot;:">`SetScrollPos`</SwmToken> and <SwmToken path="wSettings.w" pos="47:2:2" line-data="PROCEDURE PostMessageA EXTERNAL &quot;USER32.DLL&quot;:">`PostMessageA`</SwmToken>. We will dive a little into <SwmToken path="wSettings.w" pos="40:2:2" line-data="PROCEDURE SetScrollPos EXTERNAL &quot;USER32.DLL&quot;:">`SetScrollPos`</SwmToken> and <SwmToken path="wSettings.w" pos="47:2:2" line-data="PROCEDURE PostMessageA EXTERNAL &quot;USER32.DLL&quot;:">`PostMessageA`</SwmToken>.

<SwmSnippet path="/wSettings.w" line="40">

---

### <SwmToken path="wSettings.w" pos="40:2:2" line-data="PROCEDURE SetScrollPos EXTERNAL &quot;USER32.DLL&quot;:">`SetScrollPos`</SwmToken>

The <SwmToken path="wSettings.w" pos="40:2:2" line-data="PROCEDURE SetScrollPos EXTERNAL &quot;USER32.DLL&quot;:">`SetScrollPos`</SwmToken> function is an external procedure that interacts with the <SwmToken path="wSettings.w" pos="40:7:9" line-data="PROCEDURE SetScrollPos EXTERNAL &quot;USER32.DLL&quot;:">`USER32.DLL`</SwmToken> to set the scroll position of a window. This function is crucial for managing the scroll behavior within the settings window, ensuring that users can navigate through the settings smoothly.

```c
PROCEDURE SetScrollPos EXTERNAL "USER32.DLL":
  DEFINE INPUT PARAMETER pHwnd   AS LONG  NO-UNDO.
  DEFINE INPUT PARAMETER pNBar   AS SHORT NO-UNDO.
  DEFINE INPUT PARAMETER pNPos   AS SHORT NO-UNDO.
  DEFINE INPUT PARAMETER pRedraw AS SHORT NO-UNDO.
END PROCEDURE.
```

---

</SwmSnippet>

<SwmSnippet path="/wSettings.w" line="47">

---

### <SwmToken path="wSettings.w" pos="47:2:2" line-data="PROCEDURE PostMessageA EXTERNAL &quot;USER32.DLL&quot;:">`PostMessageA`</SwmToken>

The <SwmToken path="wSettings.w" pos="47:2:2" line-data="PROCEDURE PostMessageA EXTERNAL &quot;USER32.DLL&quot;:">`PostMessageA`</SwmToken> function is another external procedure that sends a message to the specified window or windows. This function is used to handle various user interactions within the settings window, such as button clicks or other control events, by posting messages to the window's message queue.

```c
PROCEDURE PostMessageA EXTERNAL "USER32.DLL":
  DEFINE INPUT  PARAMETER pHwnd    AS LONG NO-UNDO.
  DEFINE INPUT  PARAMETER pMsg     AS LONG NO-UNDO.
  DEFINE INPUT  PARAMETER pWparam  AS LONG NO-UNDO.
  DEFINE INPUT  PARAMETER pLparam  AS LONG NO-UNDO.
END PROCEDURE.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
