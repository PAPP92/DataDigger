---
title: Schema Management in Helpers
---
# Introduction to Schema Management in Helpers

Schema Management involves handling the structure and organization of database schemas within the application. In Helpers, Schema Management includes generating dummy data for testing purposes and retrieving the schema of the <SwmToken path="getSchema.p" pos="3:15:15" line-data="  Desc : Get the schema of the dictdb database">`dictdb`</SwmToken> database.

## Generating Dummy Data

The <SwmPath>[getDummyScheme.p](getDummyScheme.p)</SwmPath> file defines procedures to create fields and indexes with predefined attributes, which helps in testing the generation procedures. This is useful for creating a controlled environment to test how the application handles different schema configurations.

<SwmSnippet path="/getDummyScheme.p" line="1">

---

The <SwmPath>[getDummyScheme.p](getDummyScheme.p)</SwmPath> file defines procedures to create fields and indexes with predefined attributes, which helps in testing the generation procedures.

```openedge abl
/*------------------------------------------------------------------------

  Name: getDummyScheme.p
  Desc: Generate some dummy data for testing generate procedures

  ----------------------------------------------------------------------*/

{ DataDigger.i }

DEFINE OUTPUT PARAMETER TABLE FOR ttField.
DEFINE OUTPUT PARAMETER TABLE FOR ttIndex.

RUN createFields.
RUN createIndexes.

PROCEDURE createFields:

  CREATE ttField. 
  ASSIGN 
    ttField.cFieldName = 'rep-nr'      
    ttField.lShow      = TRUE 
```

---

</SwmSnippet>

## Retrieving Schema Information

The <SwmPath>[getSchema.p](getSchema.p)</SwmPath> file retrieves the schema of the <SwmToken path="getSchema.p" pos="3:15:15" line-data="  Desc : Get the schema of the dictdb database">`dictdb`</SwmToken> database by reading it statically, which is faster than using a dynamic query. It assigns various attributes to the schema tables and fields, categorizing them based on their table names and numbers. This helps in efficiently managing and accessing the schema information.

<SwmSnippet path="/getSchema.p" line="1">

---

The <SwmPath>[getSchema.p](getSchema.p)</SwmPath> file retrieves the schema of the <SwmToken path="getSchema.p" pos="3:15:15" line-data="  Desc : Get the schema of the dictdb database">`dictdb`</SwmToken> database by reading it statically, which is faster than using a dynamic query.

```openedge abl
/*------------------------------------------------------------------------
  Name : getSchema.p
  Desc : Get the schema of the dictdb database

  Notes:
    This is in a separate .p because the alias is set for the dictdb.
    The reason this is done is because reading the schema statically
    is much faster than reading it via a dynamic query (factor 4 or 5)

  Input parameter ttTable should be passed BY-REFERENCE
  ----------------------------------------------------------------------*/

{DataDigger.i}

DEFINE INPUT PARAMETER TABLE FOR ttTable.

DEFINE BUFFER bDb    FOR dictdb._Db.
DEFINE BUFFER bFile  FOR dictdb._File.
DEFINE BUFFER bField FOR dictdb._Field.
DEFINE BUFFER bTable FOR ttTable.
```

---

</SwmSnippet>

## Main Functions

There are several main functions in Schema Management. Some of them are <SwmToken path="getDummyScheme.p" pos="13:2:2" line-data="RUN createFields.">`createFields`</SwmToken>, <SwmToken path="getDummyScheme.p" pos="14:2:2" line-data="RUN createIndexes.">`createIndexes`</SwmToken>, and <SwmToken path="getSchema.p" pos="2:5:5" line-data="  Name : getSchema.p">`getSchema`</SwmToken>. We will dive a little into <SwmToken path="getDummyScheme.p" pos="13:2:2" line-data="RUN createFields.">`createFields`</SwmToken> and <SwmToken path="getSchema.p" pos="2:5:5" line-data="  Name : getSchema.p">`getSchema`</SwmToken>.

### <SwmToken path="getDummyScheme.p" pos="13:2:2" line-data="RUN createFields.">`createFields`</SwmToken>

The <SwmToken path="getDummyScheme.p" pos="13:2:2" line-data="RUN createFields.">`createFields`</SwmToken> procedure is responsible for creating dummy fields with predefined attributes. This is useful for testing purposes, allowing developers to simulate various field configurations without needing actual database entries.

<SwmSnippet path="/getDummyScheme.p" line="16">

---

The <SwmToken path="getDummyScheme.p" pos="16:2:2" line-data="PROCEDURE createFields:">`createFields`</SwmToken> procedure creates dummy fields with predefined attributes for testing purposes.

```openedge abl
PROCEDURE createFields:

  CREATE ttField. 
  ASSIGN 
    ttField.cFieldName = 'rep-nr'      
    ttField.lShow      = TRUE 
    ttField.cDataType  = 'INTEGER'   
    ttField.cFormat    = '>>>9'  
    ttField.cLabel     = 'Rep nr'.
  
  CREATE ttField. 
  ASSIGN 
    ttField.cFieldName = 'rep-name'    
    ttField.lShow      = TRUE 
    ttField.cDataType  = 'CHARACTER' 
    ttField.cFormat    = 'x(30)' 
    ttField.cLabel     = 'Rep name'.
  
  CREATE ttField. 
  ASSIGN 
    ttField.cFieldName = 'region'      
```

---

</SwmSnippet>

### <SwmToken path="getDummyScheme.p" pos="14:2:2" line-data="RUN createIndexes.">`createIndexes`</SwmToken>

The <SwmToken path="getDummyScheme.p" pos="14:2:2" line-data="RUN createIndexes.">`createIndexes`</SwmToken> procedure creates dummy indexes with specific attributes. This helps in testing index-related functionalities by providing a controlled set of index data.

<SwmSnippet path="/getDummyScheme.p" line="54">

---

The <SwmToken path="getDummyScheme.p" pos="54:2:2" line-data="PROCEDURE createIndexes:">`createIndexes`</SwmToken> procedure creates dummy indexes with specific attributes for testing purposes.

```openedge abl
PROCEDURE createIndexes:

  CREATE ttIndex. 
  ASSIGN 
    ttIndex.cIndexName  = 'iPrim'   
    ttIndex.cIndexFlags = 'P U' 
    ttIndex.cFieldList  = 'rep-nr'.
  
  CREATE ttIndex. 
  ASSIGN 
    ttIndex.cIndexName  = 'iRegion' 
    ttIndex.cIndexFlags = ''    
    ttIndex.cFieldList  = 'region,rep-name'.   

END PROCEDURE. /* createIndexes */
```

---

</SwmSnippet>

### <SwmToken path="getSchema.p" pos="2:5:5" line-data="  Name : getSchema.p">`getSchema`</SwmToken>

The <SwmToken path="getSchema.p" pos="2:5:5" line-data="  Name : getSchema.p">`getSchema`</SwmToken> procedure retrieves the schema of the <SwmToken path="getSchema.p" pos="3:15:15" line-data="  Desc : Get the schema of the dictdb database">`dictdb`</SwmToken> database. It reads the schema statically, which is faster than using a dynamic query. The procedure assigns various attributes to the schema tables and fields, categorizing them based on their properties and relationships.

<SwmSnippet path="/getSchema.p" line="1">

---

The <SwmToken path="getSchema.p" pos="2:5:5" line-data="  Name : getSchema.p">`getSchema`</SwmToken> procedure retrieves the schema of the <SwmToken path="getSchema.p" pos="3:15:15" line-data="  Desc : Get the schema of the dictdb database">`dictdb`</SwmToken> database by reading it statically.

```openedge abl
/*------------------------------------------------------------------------
  Name : getSchema.p
  Desc : Get the schema of the dictdb database

  Notes:
    This is in a separate .p because the alias is set for the dictdb.
    The reason this is done is because reading the schema statically
    is much faster than reading it via a dynamic query (factor 4 or 5)

  Input parameter ttTable should be passed BY-REFERENCE
  ----------------------------------------------------------------------*/

{DataDigger.i}

DEFINE INPUT PARAMETER TABLE FOR ttTable.

DEFINE BUFFER bDb    FOR dictdb._Db.
DEFINE BUFFER bFile  FOR dictdb._File.
DEFINE BUFFER bField FOR dictdb._Field.
DEFINE BUFFER bTable FOR ttTable.
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBRGF0YURpZ2dlciUzQSUzQVBBUFA5Mg==" repo-name="DataDigger"><sup>Powered by [Swimm](/)</sup></SwmMeta>
