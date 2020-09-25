---
title: AcceptChanges ve RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: e29d2404d6d593b9a5b905206af3cdd3bc1a3e51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177598"
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges ve RejectChanges

İçindeki verilerde yapılan değişikliklerin doğruluğunu doğruladıktan sonra, <xref:System.Data.DataTable> <xref:System.Data.DataRow.AcceptChanges%2A> veya, <xref:System.Data.DataRow> <xref:System.Data.DataTable> <xref:System.Data.DataSet> **geçerli** satır değerlerini **orijinal** değerler olarak ayarlanacak ve **RowState** özelliğini **değiştirilmemiş**olarak ayarlanacak olan, veya yöntemini kullanarak değişiklikleri kabul edebilirsiniz. Değişiklikleri kabul etmek veya reddetmek, tüm **RowError** bilgilerini temizler ve **HasErrors** özelliğini **false**olarak ayarlar. Değişiklikleri kabul etme veya reddetme, veri kaynağındaki verileri güncelleştirmeyi de etkileyebilir. Daha fazla bilgi için bkz. [veri kaynaklarını DataAdapter Ile güncelleştirme](../updating-data-sources-with-dataadapters.md).  
  
 **DataTable**üzerinde yabancı anahtar kısıtlamaları varsa, **AcceptChanges** ve **RejectChanges** kullanılarak kabul edilen veya reddedilen değişiklikler, **ForeignKeyConstraint. AcceptRejectRule**öğesine göre **DataRow** 'ın alt satırlarına yayılır. Daha fazla bilgi için bkz. [DataTable kısıtlamaları](datatable-constraints.md).  
  
 Aşağıdaki örnek, hataları olan satırları denetler, uygun olduğunda hataları çözer ve hatanın çözümlenemediği satırları reddeder. Çözümlenen hatalar için **RowError** değeri ' nin boş bir dizeye sıfırlandığını ve **HasErrors** özelliğinin **false**olarak ayarlanmasına neden olduğunu unutmayın. Hata içeren tüm satırlar çözümlendiğinde veya reddedildiğinde, **AcceptChanges** tüm **DataTable**için tüm değişiklikleri kabul etmek üzere çağırılır.  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
