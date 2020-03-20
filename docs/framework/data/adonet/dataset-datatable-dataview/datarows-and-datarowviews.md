---
title: DataRows ve DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 14e7e1ccb051410c351e49afee9f2d6809264833
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151305"
---
# <a name="datarows-and-datarowviews"></a>DataRows ve DataRowViews
A, <xref:System.Data.DataView> sayısal bir <xref:System.Data.DataRowView> nesne koleksiyonunu ortaya çıkarır. **DataRowView** nesneleri, alttaki tablodaki sütunun adı veya ordinal başvurusu tarafından dizilen nesne dizileri olarak değerleri ortaya çıkarır. <xref:System.Data.DataRow> **DataRowView'ın**özelliğini <xref:System.Data.DataRowView.Row%2A> kullanarak **DataRowView** tarafından ortaya çıkarılanlara erişebilirsiniz.  
  
 **Verileri Bir DataRowView**kullanarak görüntülediğinizde, **DataView'ın** <xref:System.Data.DataView.RowStateFilter%2A> özelliği, alttaki **DataRow'un** hangi satır sürümünün açıkta olduğunu belirler. **Bir DataRow**kullanarak farklı satır sürümlerine erişim hakkında bilgi için [bkz.](row-states-and-row-versions.md)  
  
 Aşağıdaki kod örneği, tablodaki tüm geçerli ve özgün değerleri görüntüler.  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
