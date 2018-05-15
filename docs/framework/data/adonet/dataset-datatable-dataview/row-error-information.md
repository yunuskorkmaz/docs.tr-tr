---
title: Satır hata bilgileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 6f3f332d4b9bd0be9934c7bf7722e8ff71c4eb2f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="row-error-information"></a><span data-ttu-id="55fd0-102">Satır hata bilgileri</span><span class="sxs-lookup"><span data-stu-id="55fd0-102">Row Error Information</span></span>
<span data-ttu-id="55fd0-103">Satır hataları değerleri düzenlerken yanıt zorunda kalmamak için bir <xref:System.Data.DataTable>, daha sonra kullanmak için satır hata bilgilerini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55fd0-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="55fd0-104"><xref:System.Data.DataRow> Nesne sağlayan bir <xref:System.Data.DataRow.RowError%2A> bu amaç için her satırda özelliği.</span><span class="sxs-lookup"><span data-stu-id="55fd0-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="55fd0-105">Veri ekleme **RowError** özelliği bir **DataRow** ayarlar <xref:System.Data.DataRow.HasErrors%2A> özelliği **DataRow** için **doğru**.</span><span class="sxs-lookup"><span data-stu-id="55fd0-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="55fd0-106">Varsa **DataRow** parçası olan bir **DataTable**, ve **DataRow.HasErrors** olan **true**, **DataTable.HasErrors** özelliktir de **doğru**.</span><span class="sxs-lookup"><span data-stu-id="55fd0-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="55fd0-107">Bunun için de geçerlidir **DataSet** hangi **DataTable** ait.</span><span class="sxs-lookup"><span data-stu-id="55fd0-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="55fd0-108">Hatalar için test edilirken kontrol edebilirsiniz **HasErrors** özelliği hata bilgileri için herhangi bir satır eklenip eklenmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="55fd0-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="55fd0-109">Varsa **HasErrors** olan **true**, kullanabileceğiniz <xref:System.Data.DataTable.GetErrors%2A> yöntemi **DataTable** dönün ve aşağıdaki örnekte gösterildiği gibi yalnızca hatalar, satırları inceleyin.</span><span class="sxs-lookup"><span data-stu-id="55fd0-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
workTable.Columns.Add("CustID", Type.GetType("System.Int32"))  
workTable.Columns.Add("Total", Type.GetType("System.Double"))  
  
AddHandler workTable.RowChanged, New DataRowChangeEventHandler(AddressOf OnRowChanged)  
  
Dim i  As Int32  
  
For i  = 0 To 10  
  workTable.Rows.Add(New Object() {i , i *100})  
Next  
  
If workTable.HasErrors Then  
  Console.WriteLine("Errors in Table " & workTable.TableName)  
  
  Dim myRow As DataRow  
  
  For Each myRow In workTable.GetErrors()  
    Console.WriteLine("CustID = " & myRow("CustID").ToString())  
    Console.WriteLine(" Error = " & myRow.RowError & vbCrLf)  
  Next  
End If  
  
Private Shared Sub OnRowChanged( _  
    sender As Object, args As DataRowChangeEventArgs)  
  ' Check for zero values.  
  If CDbl(args.Row("Total")) = 0 Then args.Row.RowError = _  
      "Total cannot be 0."  
End Sub  
```  
  
```csharp  
DataTable  workTable = new DataTable("Customers");  
workTable.Columns.Add("CustID", typeof(Int32));  
workTable.Columns.Add("Total", typeof(Double));  
  
workTable.RowChanged += new DataRowChangeEventHandler(OnRowChanged);  
  
for (int i = 0; i < 10; i++)  
  workTable.Rows.Add(new Object[] {i, i*100});  
  
if (workTable.HasErrors)  
{  
  Console.WriteLine("Errors in Table " + workTable.TableName);  
  
  foreach (DataRow myRow in workTable.GetErrors())  
  {  
    Console.WriteLine("CustID = " + myRow["CustID"]);  
    Console.WriteLine(" Error = " + myRow.RowError + "\n");  
  }  
}  
  
protected static void OnRowChanged(  
    Object sender, DataRowChangeEventArgs args)  
{  
  // Check for zero values.  
  if (args.Row["Total"].Equals(0D))  
    args.Row.RowError = "Total cannot be 0.";  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="55fd0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55fd0-110">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="55fd0-111">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="55fd0-111">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="55fd0-112">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="55fd0-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
