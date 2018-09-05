---
title: AcceptChanges ve RejectChanges
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: 30b2c303b1823430c480f0706500f8f7e7053c4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43660424"
---
# <a name="acceptchanges-and-rejectchanges"></a><span data-ttu-id="0c47e-102">AcceptChanges ve RejectChanges</span><span class="sxs-lookup"><span data-stu-id="0c47e-102">AcceptChanges and RejectChanges</span></span>
<span data-ttu-id="0c47e-103">Verilerde yapılan değişiklikleri doğruluğunu doğruladıktan sonra bir <xref:System.Data.DataTable>, kullanarak değişiklikleri kabul edebilir <xref:System.Data.DataRow.AcceptChanges%2A> yöntemi <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataSet>, hangi ayarlayacak **geçerli** satır değerlerinin **özgün** değerler ve ayarlar **RowState** özelliğini **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="0c47e-103">After verifying the accuracy of changes made to data in a <xref:System.Data.DataTable>, you can accept the changes using the <xref:System.Data.DataRow.AcceptChanges%2A> method of the <xref:System.Data.DataRow>, <xref:System.Data.DataTable>, or <xref:System.Data.DataSet>, which will set the **Current** row values to be the **Original** values and will set the **RowState** property to **Unchanged**.</span></span> <span data-ttu-id="0c47e-104">Kabul etme veya reddetme değişikliklerini temizler herhangi **RowError** bilgi ve kümelerini **HasErrors** özelliğini **false**.</span><span class="sxs-lookup"><span data-stu-id="0c47e-104">Accepting or rejecting changes clears out any **RowError** information and sets the **HasErrors** property to **false**.</span></span> <span data-ttu-id="0c47e-105">Kabul etme veya reddetme değişiklikleri güncelleştirme veri veri kaynağında da etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="0c47e-105">Accepting or rejecting changes can also affect updating data in the data source.</span></span> <span data-ttu-id="0c47e-106">Daha fazla bilgi için [güncelleştirme veri kaynaklarını DataAdapters ile](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="0c47e-106">For more information, see [Updating Data Sources with DataAdapters](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="0c47e-107">Yabancı anahtar kısıtlamalarını varsa **DataTable**, değişiklikleri kabul veya kullanarak **AcceptChanges** ve **RejectChanges** altsatırlarınadağıtılır **DataRow** göre **ForeignKeyConstraint.AcceptRejectRule**.</span><span class="sxs-lookup"><span data-stu-id="0c47e-107">If foreign key constraints exist on the **DataTable**, changes accepted or rejected using **AcceptChanges** and **RejectChanges** are propagated to child rows of the **DataRow** according to the **ForeignKeyConstraint.AcceptRejectRule**.</span></span> <span data-ttu-id="0c47e-108">Daha fazla bilgi için [DataTable kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="0c47e-108">For more information, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="0c47e-109">Aşağıdaki örnek, hataları olan satırlar için denetler uygunsa hataları giderir ve burada bir hata oluştu çözümlenemiyor satırları reddeder.</span><span class="sxs-lookup"><span data-stu-id="0c47e-109">The following example checks for rows with errors, resolves the errors where applicable, and rejects the rows where the error cannot be resolved.</span></span> <span data-ttu-id="0c47e-110">Hataları için çözümlenen Not **RowError** değeri, boş bir dize olarak sıfırlanır neden **HasErrors** ayarlamak için özellik **false**.</span><span class="sxs-lookup"><span data-stu-id="0c47e-110">Note that, for resolved errors, the **RowError** value is reset to an empty string, causing the **HasErrors** property to be set to **false**.</span></span> <span data-ttu-id="0c47e-111">Hata içeren tüm satırların çözülmüş veya reddedilen **AcceptChanges** tamamı için tüm değişiklikleri kabul etmek için çağrılan **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="0c47e-111">When all the rows with errors have been resolved or rejected, **AcceptChanges** is called to accept all changes for the entire **DataTable**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c47e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c47e-112">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="0c47e-113">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="0c47e-113">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="0c47e-114">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0c47e-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
