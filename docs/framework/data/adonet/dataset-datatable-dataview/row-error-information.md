---
title: Satır hatası bilgileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: cf798ac88ba83e890086cec7424c8c363980718f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399043"
---
# <a name="row-error-information"></a><span data-ttu-id="15462-102">Satır hatası bilgileri</span><span class="sxs-lookup"><span data-stu-id="15462-102">Row Error Information</span></span>
<span data-ttu-id="15462-103">Değerleri düzenleme sırasında satır hatalar için yanıt zorunda kalmamak için bir <xref:System.Data.DataTable>, hata bilgilerini daha sonra kullanmak için bir satır ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15462-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="15462-104"><xref:System.Data.DataRow> Nesnesi sağlayan bir <xref:System.Data.DataRow.RowError%2A> bu amaçla her satırında özelliği.</span><span class="sxs-lookup"><span data-stu-id="15462-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="15462-105">Veri ekleme **RowError** özelliği bir **DataRow** ayarlar <xref:System.Data.DataRow.HasErrors%2A> özelliği **DataRow** için **true**.</span><span class="sxs-lookup"><span data-stu-id="15462-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="15462-106">Varsa **DataRow** parçası olan bir **DataTable**, ve **DataRow.HasErrors** olduğu **true**, **DataTable.HasErrors** özelliği de **true**.</span><span class="sxs-lookup"><span data-stu-id="15462-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="15462-107">Bunun için de geçerlidir **veri kümesi** hangi **DataTable** ait.</span><span class="sxs-lookup"><span data-stu-id="15462-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="15462-108">Hataları için test yapma, denetleyebilirsiniz **HasErrors** hata bilgisi için herhangi bir satır eklenip eklenmediğini belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="15462-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="15462-109">Varsa **HasErrors** olduğu **true**, kullanabileceğiniz <xref:System.Data.DataTable.GetErrors%2A> yöntemi **DataTable** dönün ve aşağıdaki örnekte gösterildiği gibi yalnızca hataları olan satırlar inceleyin.</span><span class="sxs-lookup"><span data-stu-id="15462-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15462-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15462-110">See Also</span></span>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="15462-111">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="15462-111">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="15462-112">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="15462-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
