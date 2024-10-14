---
title: Configuration Overview
---
# Configuration Overview

Configuration in <SwmToken path="DataDiggerHelp.ini" pos="1:1:1" line-data="[DataDigger:Help]">`DataDigger`</SwmToken> involves setting up various parameters and options that control how the application interacts with Progress/OpenEdge databases. It includes specifying database connection details, user preferences, and other settings that customize the behavior of the tool.

<SwmSnippet path="/DataDiggerHelp.ini" line="1">

---

The <SwmPath>[DataDiggerHelp.ini](DataDiggerHelp.ini)</SwmPath> file includes settings like the <SwmToken path="DataDiggerHelp.ini" pos="26:16:17" line-data="RereadNoLock:message             = You have not set the -rereadnolock startup parameter. This setting may increase the usability of DataDigger.~n~nFrom the progress help file:~n~nUse Reread Nolock ( -rereadnolock) to tell Progress that when it attempts to find a record with NO-LOCK, to re-read the record from the database, even if the record is already in a buffer. You can use this parameter to resolve client-server currency conflicts.">`-rereadnolock`</SwmToken> startup parameter, which can improve the usability of <SwmToken path="DataDiggerHelp.ini" pos="1:1:1" line-data="[DataDigger:Help]">`DataDigger`</SwmToken> by resolving <SwmToken path="DataDiggerHelp.ini" pos="26:145:147" line-data="RereadNoLock:message             = You have not set the -rereadnolock startup parameter. This setting may increase the usability of DataDigger.~n~nFrom the progress help file:~n~nUse Reread Nolock ( -rereadnolock) to tell Progress that when it attempts to find a record with NO-LOCK, to re-read the record from the database, even if the record is already in a buffer. You can use this parameter to resolve client-server currency conflicts.">`client-server`</SwmToken> currency conflicts.

```ini
[DataDigger:Help]
CannotCreateBackupFolder:canHide = FALSE
CannotCreateBackupFolder:message = Cannot create folder &1. ~n~nPlease check your settings.
CannotEditVst:message            = You cannot edit or delete VST files
ConfirmDelete:message            = Delete the &1 record(s) selected?
```

---

</SwmSnippet>

## User Preferences

User preferences can be configured to make <SwmToken path="DataDiggerHelp.ini" pos="1:1:1" line-data="[DataDigger:Help]">`DataDigger`</SwmToken> useful in multiple environments. This flexibility allows users to adapt the tool to their specific needs.

<SwmSnippet path="/DataDigger2.p" line="448">

---

This line in <SwmPath>[DataDigger2.p](DataDigger2.p)</SwmPath> highlights the importance of configuring user preferences for multiple environments.

```openedge abl
   * This can be useful when you use DD in multiple environments
```

---

</SwmSnippet>

## Customization Options

Options such as using multiple favorites groups and specifying a different work folder can be configured to customize the tool's behavior. These customization options enhance the user experience by allowing more personalized settings.

## Default Settings

If certain settings are not defined, default settings are used to ensure the application runs smoothly. This fallback mechanism ensures that the tool remains functional even if some configurations are missing.

<SwmSnippet path="/DataDiggerLib.p" line="1260">

---

This line in <SwmPath>[DataDiggerLib.p](DataDiggerLib.p)</SwmPath> indicates that default settings are used when specific configurations are not defined.

```openedge abl
  /* If it is not defined use default setting */
```

---

</SwmSnippet>

## Preventing Actions

Configuration can also be used to prevent certain actions, such as delete or save operations, enhancing control over the application's behavior. This feature adds an extra layer of security and control for users.

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
