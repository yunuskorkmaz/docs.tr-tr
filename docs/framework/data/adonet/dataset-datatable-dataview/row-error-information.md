---
title: Satır hatası bilgileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b1f9070-d032-48c7-b030-bd8fbb2ca59a
ms.openlocfilehash: cf798ac88ba83e890086cec7424c8c363980718f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530551"
---
# <a name="row-error-information"></a>Satır hatası bilgileri
Değerleri düzenleme sırasında satır hatalar için yanıt zorunda kalmamak için bir <xref:System.Data.DataTable>, hata bilgilerini daha sonra kullanmak için bir satır ekleyebilirsiniz. <xref:System.Data.DataRow> Nesnesi sağlayan bir <xref:System.Data.DataRow.RowError%2A> bu amaçla her satırında özelliği. Veri ekleme **RowError** özelliği bir **DataRow** ayarlar <xref:System.Data.DataRow.HasErrors%2A> özelliği **DataRow** için **true**. Varsa **DataRow** parçası olan bir **DataTable**, ve **DataRow.HasErrors** olduğu **true**, **DataTable.HasErrors** özelliği de **true**. Bunun için de geçerlidir **veri kümesi** hangi **DataTable** ait. Hataları için test yapma, denetleyebilirsiniz **HasErrors** hata bilgisi için herhangi bir satır eklenip eklenmediğini belirlemek için özellik. Varsa **HasErrors** olduğu **true**, kullanabileceğiniz <xref:System.Data.DataTable.GetErrors%2A> yöntemi **DataTable** dönün ve aşağıdaki örnekte gösterildiği gibi yalnızca hataları olan satırlar inceleyin.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
