---
title: DataRows ve DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 8a98dc44eda9ebda09235193c58bd831fc52d04d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205096"
---
# <a name="datarows-and-datarowviews"></a>DataRows ve DataRowViews
<xref:System.Data.DataView> ,<xref:System.Data.DataRowView> Nesnelerin sıralanabilir koleksiyonunu ortaya koyar. **DataRowView** nesneleri değerleri, temel tablodaki sütunun adı ya da Ordinal başvurusu tarafından dizine alınmış nesne dizileri olarak kullanıma sunar. DataRowView <xref:System.Data.DataRow>'ın <xref:System.Data.DataRowView.Row%2A> özelliğini kullanarak **DataRowView** tarafından açığa çıkarılan öğesine erişebilirsiniz.  
  
 Bir **DataRowView**kullanarak değerleri görüntülediğinizde, <xref:System.Data.DataView.RowStateFilter%2A> **DataView** özelliği temel alınan **DataRow** 'ın hangi satır sürümünün açığa çıkardığını belirler. Bir **DataRow**kullanarak farklı satır sürümlerine erişme hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).  
  
 Aşağıdaki kod örneği, bir tablodaki tüm geçerli ve orijinal değerleri görüntüler.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
