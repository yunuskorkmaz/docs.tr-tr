---
title: Satır Hatası Bilgileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: 5ede6e2cd52ad55f8c35a42d137044dd1ceea400
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785960"
---
# <a name="row-error-information"></a><span data-ttu-id="f46f7-102">Satır Hatası Bilgileri</span><span class="sxs-lookup"><span data-stu-id="f46f7-102">Row Error Information</span></span>
<span data-ttu-id="f46f7-103">İçindeki değerleri düzenlenirken satır hatalarına yanıt vermekten kaçınmak için <xref:System.Data.DataTable>, daha sonra kullanmak üzere satıra hata bilgilerini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46f7-103">To avoid having to respond to row errors while editing values in a <xref:System.Data.DataTable>, you can add the error information to the row for later use.</span></span> <span data-ttu-id="f46f7-104">Nesnesi bu amaçla her <xref:System.Data.DataRow.RowError%2A> satırda bir özellik sağlar. <xref:System.Data.DataRow></span><span class="sxs-lookup"><span data-stu-id="f46f7-104">The <xref:System.Data.DataRow> object provides a <xref:System.Data.DataRow.RowError%2A> property on each row for this purpose.</span></span> <span data-ttu-id="f46f7-105">Bir **DataRow** <xref:System.Data.DataRow.HasErrors%2A> 'ın **RowError** özelliğine veri eklemek, **DataRow** 'ın özelliğini **true**olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f46f7-105">Adding data to the **RowError** property of a **DataRow** sets the <xref:System.Data.DataRow.HasErrors%2A> property of the **DataRow** to **true**.</span></span> <span data-ttu-id="f46f7-106">**DataRow** bir **DataTable**'ın parçasıysa ve **DataRow. HasErrors** **true**ise, **DataTable. HasErrors** özelliği de **doğrudur**.</span><span class="sxs-lookup"><span data-stu-id="f46f7-106">If the **DataRow** is part of a **DataTable**, and **DataRow.HasErrors** is **true**, the **DataTable.HasErrors** property is also **true**.</span></span> <span data-ttu-id="f46f7-107">Bu, **DataTable** 'ın ait olduğu **veri kümesine** de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f46f7-107">This applies as well to the **DataSet** to which the **DataTable** belongs.</span></span> <span data-ttu-id="f46f7-108">Hatalar için test edilirken **HasErrors** özelliğini denetleyerek herhangi bir satıra hata bilgilerinin eklenip eklenmediğine bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46f7-108">When testing for errors, you can check the **HasErrors** property to determine if error information has been added to any rows.</span></span> <span data-ttu-id="f46f7-109">**HasErrors** **true**ise, aşağıdaki örnekte gösterildiği gibi, <xref:System.Data.DataTable.GetErrors%2A> yalnızca hataları olan satırları döndürmek ve incelemek için **DataTable** 'ın yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f46f7-109">If **HasErrors** is **true**, you can use the <xref:System.Data.DataTable.GetErrors%2A> method of the **DataTable** to return and examine only the rows with errors, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f46f7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f46f7-110">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="f46f7-111">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="f46f7-111">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="f46f7-112">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f46f7-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
