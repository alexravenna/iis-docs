---
title: QueryResult.ColumnMetadata Property (Microsoft.Web.Management.DatabaseManager)
description: The QueryResult.ColumnMetadata property returns a list of column metadata for a query result.
TOCTitle: ColumnMetadata Property
ms:assetid: P:Microsoft.Web.Management.DatabaseManager.QueryResult.ColumnMetadata
ms:mtpsurl: https://msdn.microsoft.com/library/microsoft.web.management.databasemanager.queryresult.columnmetadata(v=VS.90)
ms:contentKeyID: 20476453
ms.date: 05/02/2012
mtps_version: v=VS.90
ms.author: johnhart
f1_keywords:
- Microsoft.Web.Management.DatabaseManager.QueryResult.ColumnMetadata
- Microsoft.Web.Management.DatabaseManager.QueryResult.get_ColumnMetadata
dev_langs:
- csharp
- jscript
- vb
- cpp
api_location:
- Microsoft.Web.Management.DatabaseManager.dll
api_name:
- Microsoft.Web.Management.DatabaseManager.QueryResult.ColumnMetadata
- Microsoft.Web.Management.DatabaseManager.QueryResult.get_ColumnMetadata
api_type:
  - Assembly
topic_type:
- apiref
product_family_name: VS
ms.custom: sfi-ropc-nochange
---

# QueryResult.ColumnMetadata Property

Returns a list of column metadata for a query result.

**Namespace:**  [Microsoft.Web.Management.DatabaseManager](microsoft-web-management-databasemanager-namespace.md)  
**Assembly:**  Microsoft.Web.Management.DatabaseManager (in Microsoft.Web.Management.DatabaseManager.dll)

## Syntax

```vb
'Declaration
Public ReadOnly Property ColumnMetadata As IList(Of QueryColumnMetadata)
'Usage
Dim instance As QueryResult
Dim value As IList(Of QueryColumnMetadata)

value = instance.ColumnMetadata
```

```csharp
public IList<QueryColumnMetadata> ColumnMetadata { get; }
```

```cpp
public:
property IList<QueryColumnMetadata^>^ ColumnMetadata {
    IList<QueryColumnMetadata^>^ get ();
}
```

```jscript
function get ColumnMetadata () : IList<QueryColumnMetadata>
```

### Property Value

Type: [System.Collections.Generic.IList](https://msdn.microsoft.com/library/5y536ey6)\<[QueryColumnMetadata](querycolumnmetadata-class-microsoft-web-management-databasemanager.md)\>  
An IList interface that contains a collection of [QueryColumnMetadata](querycolumnmetadata-class-microsoft-web-management-databasemanager.md) objects.  

## Remarks

The column metadata for a query contains information about the columns within the query results. For example, the metadata contains the column width and type information for a column.

## Examples

The following code sample implements the GetData method to retrieve the data in a database table from an OLEDB data source.

> [!NOTE]  
> This example also provides helper methods that perform additional database tasks.

```vb

    ' Retrieve data from a database.
    Public Function GetData( _
            ByVal connectionString As String, _
            ByVal tableName As String, _
            ByVal schema As String) _
            As Microsoft.Web.Management.DatabaseManager.QueryResult _
            Implements Microsoft.Web.Management.DatabaseManager.IDbTableDataManager.GetData

        ' Create a new query result object.
        Dim queryResult As QueryResult = New QueryResult
        ' Create a connection to the database.
        Dim connection As OleDbConnection = New OleDbConnection(connectionString)
        ' Open the database connection.
        connection.Open()

        Dim columns As List(Of Column) = New List(Of Column)
        GetColumns(connection, tableName, schema, columns)
        Dim metadata As IList(Of QueryColumnMetadata) = New List(Of QueryColumnMetadata)

        For Each c As Column In columns
            Dim m As QueryColumnMetadata = New QueryColumnMetadata
            m.Name = c.Name
            m.ColumnWidth = c.Length
            m.IsNullable = c.AllowNulls
            m.TypeInfo = c.TypeInfo
            metadata.Add(m)
        Next

        Dim fields As StringBuilder = New StringBuilder

        If (metadata.Count = 0) Then
            ' When the table is not found, adding an asterix returns an error message.
            fields.Append("*")
        Else
            Dim fieldCount As Integer = metadata.Count
            Dim isFirst As Boolean = True
            Dim i As Integer = 0
            For i = 0 To (fieldCount - 1)
                Dim m As QueryColumnMetadata = metadata(i)
                If (isFirst = False) Then
                    fields.Append(",")
                End If
                isFirst = False
                fields.Append(EscapeName(m.Name))
                queryResult.ColumnMetadata.Add(m)
            Next
        End If

        ' Create a new query object.
        Dim query As Query = New Query
        ' Create a SQL query statement.
        query.Statement = "SELECT " + fields.ToString + " FROM " + EscapeName(tableName)
        ' retrieve the query results.
        Dim results() As QueryResult = ExecuteQuery(connectionString, query)
        ' Add the query results to the list.
        queryResult.QueryResults.AddRange(results(0).QueryResults)

        ' Return the query result.
        Return queryResult

    End Function



...



    Friend Shared Function EscapeName(ByVal name As String) As String
        ' Test if the value is already escaped.
        If (name.StartsWith("[", StringComparison.Ordinal) AndAlso name.EndsWith("]", StringComparison.Ordinal)) Then
            ' Return the string with no changes.
            Return name
        End If
        ' Create a new string builder for the escaped string.
        Dim escapedName As StringBuilder = New StringBuilder
        ' Prepend the string with an opening bracket.
        escapedName.Append(Microsoft.VisualBasic.ChrW(91))
        ' Loop through the string.
        Dim i As Integer = 0
        Do While (i < name.Length)
            Dim c As Char = name(i)
            If (c = Microsoft.VisualBasic.ChrW(93)) Then
                escapedName.Append(Microsoft.VisualBasic.ChrW(93))
            End If
            escapedName.Append(c)
            i = (i + 1)
        Loop
        ' Append the string with an opening bracket.
        escapedName.Append(Microsoft.VisualBasic.ChrW(93))
        ' Return the escaped string.
        Return escapedName.ToString
    End Function

```

```csharp

        // Retrieve data from a database.
        public QueryResult GetData(string connectionString, string tableName, string schema)
        {
            // Create a new query result object.
            QueryResult queryResult = new QueryResult();

            // Create a connection to the database.
            using (OleDbConnection connection = new OleDbConnection(connectionString))
            {
                // Open the database connection.
                connection.Open();

                List<Column> columns = new List<Column>();
                GetColumns(connection, tableName, schema, columns);
                IList<QueryColumnMetadata> metadata = new List<QueryColumnMetadata>();

                foreach (Column c in columns)
                {
                    QueryColumnMetadata m = new QueryColumnMetadata();
                    m.Name = c.Name;
                    m.ColumnWidth = c.Length;
                    m.IsNullable = c.AllowNulls;
                    m.TypeInfo = c.TypeInfo;
                    metadata.Add(m);
                }

                StringBuilder fields = new StringBuilder();

                if (metadata.Count == 0)
                {
                    // When the table is not found, adding an asterix returns an error message.
                    fields.Append("*");
                }
                else
                {
                    int fieldCount = metadata.Count;

                    bool isFirst = true;
                    for (int i = 0; i < fieldCount; i++)
                    {
                        QueryColumnMetadata m = metadata[i];
                        if (isFirst == false)
                        {
                            fields.Append(',');
                        }
                        isFirst = false;
                        fields.Append(EscapeName(m.Name));
                        queryResult.ColumnMetadata.Add(m);
                    }
                }

                // Create a new query object.
                Query query = new Query();

                // Create a SQL query statement.
                query.Statement = "SELECT " + fields.ToString() + " FROM " + EscapeName(tableName);

                // retrieve the query results.
                QueryResult[] results = ExecuteQuery(connectionString, query);

                // Add the query results to the list.
                queryResult.QueryResults.AddRange(results[0].QueryResults);
            }

            // Return the query result.
            return queryResult;
        }



...



        internal static string EscapeName(string name)
        {
            // Test if the value is already escaped.
            if (name.StartsWith("[", StringComparison.Ordinal) && name.EndsWith("]", StringComparison.Ordinal))
            {
                // Return the string with no changes.
                return name;
            }
            // Create a new string builder for the escaped string.
            StringBuilder escapedName = new StringBuilder();
            // Prepend the string with an opening bracket.
            escapedName.Append('[');
            // Loop through the string.
            for (int i = 0; i < name.Length; i++)
            {
                char c = name[i];
                if (c == ']')
                {
                    escapedName.Append(']');
                }
                escapedName.Append(c);
            }
            // Append the string with an opening bracket.
            escapedName.Append(']');
            // Return the escaped string.
            return escapedName.ToString();
        }

```

## Permissions

  - Full trust for the immediate caller. This member cannot be used by partially trusted code. For more information, see [Using Libraries from Partially Trusted Code](https://msdn.microsoft.com/library/8skskf63).

## See Also

### Reference

[QueryResult Class](queryresult-class-microsoft-web-management-databasemanager.md)

[Microsoft.Web.Management.DatabaseManager Namespace](microsoft-web-management-databasemanager-namespace.md)
