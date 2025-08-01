---
title: Table.Name Property (Microsoft.Web.Management.DatabaseManager)
description: Describes the Table.Name property and provides the property's namespace, assembly, syntax, remarks, examples, and permissions.
TOCTitle: Name Property
ms:assetid: P:Microsoft.Web.Management.DatabaseManager.Table.Name
ms:mtpsurl: https://msdn.microsoft.com/library/microsoft.web.management.databasemanager.table.name(v=VS.90)
ms:contentKeyID: 20476466
ms.date: 05/02/2012
mtps_version: v=VS.90
f1_keywords:
- Microsoft.Web.Management.DatabaseManager.Table.Name
- Microsoft.Web.Management.DatabaseManager.Table.get_Name
- Microsoft.Web.Management.DatabaseManager.Table.set_Name
dev_langs:
- csharp
- jscript
- vb
- cpp
api_location:
- Microsoft.Web.Management.DatabaseManager.dll
api_name:
- Microsoft.Web.Management.DatabaseManager.Table.get_Name
- Microsoft.Web.Management.DatabaseManager.Table.Name
- Microsoft.Web.Management.DatabaseManager.Table.set_Name
api_type:
  - Assembly
topic_type:
- apiref
product_family_name: VS
ms.custom: sfi-ropc-nochange
---

# Table.Name Property

Gets or sets the name for a table.

**Namespace:**  [Microsoft.Web.Management.DatabaseManager](microsoft-web-management-databasemanager-namespace.md)  
**Assembly:**  Microsoft.Web.Management.DatabaseManager (in Microsoft.Web.Management.DatabaseManager.dll)

## Syntax

```vb
'Declaration
Public Overridable Property Name As String
'Usage
Dim instance As Table
Dim value As String

value = instance.Name

instance.Name = value
```

```csharp
public virtual string Name { get; set; }
```

```cpp
public:
virtual property String^ Name {
    String^ get ();
    void set (String^ value);
}
```

```jscript
function get Name () : String
function set Name (value : String)
```

### Property Value

Type: [System.String](https://msdn.microsoft.com/library/s1wwdcbf)  
The name for a table.  

## Remarks

The Name property specifies the name of a table in a database.

## Examples

The following code sample implements the GetTables method to retrieve the list of tables for an OLEDB connection by using the connection string that the database manager provides.

```vb

    Public Function GetTables(ByVal connectionString As String) As System.Collections.Generic.ICollection(Of Table) Implements Microsoft.Web.Management.DatabaseManager.IDbTableManager.GetTables
        Dim tables As List(Of Table) = New List(Of Table)
        ' Create a connection to the database.
        Dim connection As OleDbConnection = New OleDbConnection(connectionString)
        ' Open the connection to the database.
        connection.Open()
        Dim restrictions() As String = New String((4) - 1) {}
        restrictions(3) = "TABLE"
        ' Open the schema information for the tables.
        Dim schema As DataTable = connection.GetSchema(OleDbMetaDataCollectionNames.Tables, restrictions)
        ' Enumerate the list of tables.
        For Each row As DataRow In schema.Rows
            ' Create a new table object.
            Dim table As Table = New Table
            ' Specify the table name.
            table.Name = CType(row("TABLE_NAME"), String)
            ' Test for a creation date.
            If Not DBNull.Value.Equals(row("DATE_CREATED")) Then
                ' Create a date/time object.
                Dim createDate As DateTime = New DateTime
                ' Parse the creation date for the table.
                If DateTime.TryParse(row("DATE_CREATED").ToString, createDate) Then
                    ' Specify the creation date for the table.
                    table.CreateDate = createDate
                End If
            End If
            ' Specify the table schema.
            If Not DBNull.Value.Equals(row("TABLE_SCHEMA")) Then
                table.Schema = CType(row("TABLE_SCHEMA"), String)
            Else
                table.Schema = String.Empty
            End If
            ' Add the table to the list of tables.
            tables.Add(table)
        Next
        ' Return the list of tables.
        Return tables

    End Function

```

```csharp

        // Retrieve the list of tables.
        public ICollection<Table> GetTables(string connectionString)
        {
            List<Table> tables = new List<Table>();

            // Create a connection to the database.
            using (OleDbConnection connection = new OleDbConnection(connectionString))
            {
                // Open the connection to the database.
                connection.Open();
                string[] restrictions = new string[4];
                restrictions[3] = "TABLE";

                // Open the schema information for the tables.
                DataTable schema = connection.GetSchema(OleDbMetaDataCollectionNames.Tables, restrictions);
                // Enumerate the list of tables.
                foreach (DataRow row in schema.Rows)
                {
                    // Create a new table object.
                    Table table = new Table();
                    // Specify the table name.
                    table.Name = (string)row["TABLE_NAME"];
                    // Test for a creation date.
                    if (row["DATE_CREATED"] != DBNull.Value)
                    {
                        // Create a date/time object.
                        DateTime createDate = new DateTime();
                        // Parse the creation date for the table.
                        if (DateTime.TryParse(row["DATE_CREATED"].ToString(),out createDate))
                        {
                            // Specify the creation date for the table.
                            table.CreateDate = createDate;
                        }
                    }
                    // Specify the table schema.
                    table.Schema = (string)(row["TABLE_SCHEMA"] == DBNull.Value ? String.Empty : row["TABLE_SCHEMA"]);
                    // Add the table to the list of tables.
                    tables.Add(table);
                }
            }
            // Return the list of tables.
            return tables;
        }

```

## Permissions

  - Full trust for the immediate caller. This member cannot be used by partially trusted code. For more information, see [Using Libraries from Partially Trusted Code](https://msdn.microsoft.com/library/8skskf63).

## See Also

### Reference

[Table Class](table-class-microsoft-web-management-databasemanager.md)

[Microsoft.Web.Management.DatabaseManager Namespace](microsoft-web-management-databasemanager-namespace.md)
