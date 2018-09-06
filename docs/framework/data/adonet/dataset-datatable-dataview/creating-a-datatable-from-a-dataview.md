---
title: Dataview'den DataTable oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d45cf41-d8ae-4409-af3e-a96a7e476d85
ms.openlocfilehash: ccf95ff250cc7c23b1ff981087de0f1310472880
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43806156"
---
# <a name="creating-a-datatable-from-a-dataview"></a><span data-ttu-id="d6517-102">Dataview'den DataTable oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6517-102">Creating a DataTable from a DataView</span></span>
<span data-ttu-id="d6517-103">Verileri bir veri kaynağından alınan ve doldurduktan sonra bir <xref:System.Data.DataTable> verilerle, sıralama, filtreleme veya aksi halde tekrar almadan döndürülen verileri sınırlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6517-103">Once you have retrieved data from a data source, and have filled a <xref:System.Data.DataTable> with the data, you may want to sort, filter, or otherwise limit the returned data without retrieving it again.</span></span> <span data-ttu-id="d6517-104"><xref:System.Data.DataView> Sınıfı bunu mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="d6517-104">The <xref:System.Data.DataView> class makes this possible.</span></span> <span data-ttu-id="d6517-105">Ayrıca, yeni bir oluşturmanız gerekir, <xref:System.Data.DataTable> gelen <xref:System.Data.DataView>, kullanabileceğiniz <xref:System.Data.DataView.ToTable%2A> tüm satırları ve sütunları veya verilerin bir alt kümesini yeni kopyalamak için yöntemi <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="d6517-105">In addition, if you need to create a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView>, you can use the <xref:System.Data.DataView.ToTable%2A> method to copy all the rows and columns, or a subset of the data into a new <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d6517-106"><xref:System.Data.DataView.ToTable%2A> Yöntemi için aşırı yüklemeler sağlar:</span><span class="sxs-lookup"><span data-stu-id="d6517-106">The <xref:System.Data.DataView.ToTable%2A> method provides overloads to:</span></span>  
  
-   <span data-ttu-id="d6517-107">Oluşturma bir <xref:System.Data.DataTable> sütunların bir alt kümesi olan sütunlar içeren <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="d6517-107">Create a <xref:System.Data.DataTable> containing columns that are a subset of the columns in the <xref:System.Data.DataView>.</span></span>  
  
-   <span data-ttu-id="d6517-108">Oluşturma bir <xref:System.Data.DataTable> yalnızca ayrı satırları içeren <xref:System.Data.DataView>, Transact-SQL'de DISTINCT anahtar sözcüğüne öğesine için.</span><span class="sxs-lookup"><span data-stu-id="d6517-108">Create a <xref:System.Data.DataTable> that includes only distinct rows from the <xref:System.Data.DataView>, analogously to the DISTINCT keyword in Transact-SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6517-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6517-109">Example</span></span>  
 <span data-ttu-id="d6517-110">Aşağıdaki konsol uygulama örneği oluşturur bir <xref:System.Data.DataTable> verileri içeren **Person.Contact** tablosundaki **AdventureWorks** örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="d6517-110">The following console application example creates a <xref:System.Data.DataTable> that contains data from the **Person.Contact** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="d6517-111">Ardından, örnek bir sıralanmış oluşturur ve filtrelenmiş <xref:System.Data.DataView> göre <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="d6517-111">Next, the example creates a sorted and filtered <xref:System.Data.DataView> based on the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="d6517-112">İçeriğini görüntüleme sonra <xref:System.Data.DataTable> ve <xref:System.Data.DataView>, yeni bir örnek oluşturur <xref:System.Data.DataTable> gelen <xref:System.Data.DataView> çağırarak <xref:System.Data.DataView.ToTable%2A> kullanılabilir sütunların yalnızca bir alt seçme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d6517-112">After displaying the contents of the <xref:System.Data.DataTable> and the <xref:System.Data.DataView>, the example creates a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView> by calling the <xref:System.Data.DataView.ToTable%2A> method, selecting only a subset of the available columns.</span></span> <span data-ttu-id="d6517-113">Son olarak, örnek yeni içeriğini görüntüler <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="d6517-113">Finally, the example displays the contents of the new <xref:System.Data.DataTable>.</span></span>  
  
```vb  
Private Sub DemonstrateDataView()  
    ' Retrieve a DataTable from the AdventureWorks sample database.  
    ' connectionString is assumed to be a valid connection string.  
    Dim adapter As New SqlDataAdapter( _  
       "SELECT FirstName, LastName, EmailAddress FROM Person.Contact WHERE FirstName LIKE 'Mich%'", connectionString)  
    Dim table As New DataTable  
  
    adapter.Fill(table)  
    Console.WriteLine("Original table name: " & table.TableName)  
    ' Print current table values.  
    PrintTableOrView(table, "Current Values in Table")  
  
    ' Now create a DataView based on the DataTable.  
    ' Sort and filter the data.  
    Dim view As DataView = table.DefaultView  
    view.Sort = "LastName, FirstName"  
    view.RowFilter = "LastName > 'M'"  
    PrintTableOrView(view, "Current Values in View")  
  
    ' Create a new DataTable based on the DataView,  
    ' requesting only two columns with distinct values  
    ' in the columns.  
    Dim newTable As DataTable = view.ToTable("UniqueLastNames", True, "FirstName", "LastName")  
    PrintTableOrView(newTable, "Table created from DataView")  
    Console.WriteLine("New table name: " & newTable.TableName)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
    End Sub  
  
Private Sub PrintTableOrView(ByVal dv As DataView, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
    Dim table As DataTable = dv.Table  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the view.  
    For Each rowView As DataRowView In dv  
        sw = New System.IO.StringWriter  
  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(rowView(col.ColumnName).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
End Sub  
  
Private Sub PrintTableOrView(ByVal table As DataTable, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the table.  
    For Each row As DataRow In table.Rows  
        sw = New System.IO.StringWriter  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(row(col).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
    End Sub  
End Module  
```  
  
```csharp  
private static void DemonstrateDataView()  
{  
// Retrieve a DataTable from the AdventureWorks sample database.  
// connectionString is assumed to be a valid connection string.  
SqlDataAdapter adapter = new SqlDataAdapter(  
    "SELECT FirstName, LastName, EmailAddress " +  
    "FROM Person.Contact WHERE FirstName LIKE 'Mich%'",   
       GetConnectionString());  
DataTable table = new DataTable();  
  
adapter.Fill(table);  
Console.WriteLine("Original table name: " + table.TableName);  
// Print current table values.  
PrintTableOrView(table, "Current Values in Table");  
  
// Now create a DataView based on the DataTable.  
// Sort and filter the data.  
DataView view = table.DefaultView;  
view.Sort = "LastName, FirstName";  
view.RowFilter = "LastName > 'M'";  
PrintTableOrView(view, "Current Values in View");  
  
// Create a new DataTable based on the DataView,  
// requesting only two columns with distinct values  
// in the columns.  
DataTable newTable = view.ToTable("UniqueLastNames",  
     true, "FirstName", "LastName");  
PrintTableOrView(newTable, "Table created from DataView");  
Console.WriteLine("New table name: " + newTable.TableName);  
  
Console.WriteLine("Press any key to continue.");  
Console.ReadKey();  
}  
  
private static void PrintTableOrView(DataView dv, string label)  
{  
System.IO.StringWriter sw;  
string output;  
DataTable table = dv.Table;  
  
Console.WriteLine(label);  
  
// Loop through each row in the view.  
foreach (DataRowView rowView in dv)  
{  
    sw = new System.IO.StringWriter();  
  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(rowView[col.ColumnName].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
}  
Console.WriteLine();  
}  
  
private static void PrintTableOrView(DataTable table, string label)  
{  
System.IO.StringWriter sw;  
string output;  
  
Console.WriteLine(label);  
  
// Loop through each row in the table.  
foreach (DataRow row in table.Rows)  
{  
    sw = new System.IO.StringWriter();  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(row[col].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
} //  
Console.WriteLine();  
}  
```  
  
 <span data-ttu-id="d6517-114">}</span><span class="sxs-lookup"><span data-stu-id="d6517-114">}</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6517-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6517-115">See Also</span></span>  
 <xref:System.Data.DataView.ToTable%2A>  
 [<span data-ttu-id="d6517-116">DataViews</span><span class="sxs-lookup"><span data-stu-id="d6517-116">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="d6517-117">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d6517-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
