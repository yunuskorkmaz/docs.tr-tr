---
title: AcceptChanges ve RejectChanges
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4c7d86aed61957d15d9c37f494bf80088b164dea
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChanges ve RejectChanges
Verilerde yapılan değişiklikleri doğruluğunu doğruladıktan sonra bir <xref:System.Data.DataTable>, kullanarak değişikliği kabul edebilen <xref:System.Data.DataRow.AcceptChanges%2A> yöntemi <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataSet>, hangi ayarlayacak **geçerli** satır değerleri **özgün** değerleri ve ayarlar **RowState** özelliğine **Unchanged**. Değişiklikleri kabul veya reddetmek temizler herhangi **RowError** bilgi ve kümelerini **HasErrors** özelliğine **false**. Ayrıca veri kaynağındaki güncelleştirme veri değişiklikleri kabul veya reddetmek etkileyebilir. Daha fazla bilgi için bkz: [veri kaynaklarıyla güncelleştirme DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Yabancı anahtar kısıtlamaları üzerinde varsa **DataTable**, değişiklikleri kabul veya kullanarak **AcceptChanges** ve **RejectChanges** altsatırlarınayayılır **DataRow** göre **ForeignKeyConstraint.AcceptRejectRule**. Daha fazla bilgi için bkz: [DataTable kısıtlamalarını](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Aşağıdaki örnek, hatalarla satırları denetler uygunsa hataları giderir ve burada hata çözümlenemiyor satırları reddeder. Hatalar için çözümlenen Not **RowError** değeri, boş bir dize olarak sıfırlanır neden **HasErrors** ayarlamak için özellik **false**. Hataları olan tüm satırları çözülmüş veya reddedilen **AcceptChanges** tüm için tüm değişiklikleri kabul etmek için çağrılan **DataTable**.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
