---
description: 'Daha fazla bilgi edinin: DataRow ve DataRowViews'
title: DataRows ve DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: d7700922a9ae76fb9898412b6a08394059e6e494
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724953"
---
# <a name="datarows-and-datarowviews"></a>DataRows ve DataRowViews

<xref:System.Data.DataView>, Nesnelerin sıralanabilir koleksiyonunu ortaya koyar <xref:System.Data.DataRowView> . **DataRowView** nesneleri değerleri, temel tablodaki sütunun adı ya da Ordinal başvurusu tarafından dizine alınmış nesne dizileri olarak kullanıma sunar. DataRowView <xref:System.Data.DataRow> 'ın özelliğini kullanarak **DataRowView** tarafından açığa çıkarılan öğesine erişebilirsiniz <xref:System.Data.DataRowView.Row%2A> .   
  
 Bir **DataRowView** kullanarak değerleri görüntülediğinizde, <xref:System.Data.DataView.RowStateFilter%2A> **DataView** özelliği temel alınan **DataRow** 'ın hangi satır sürümünün açığa çıkardığını belirler. Bir **DataRow** kullanarak farklı satır sürümlerine erişme hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).  
  
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
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
