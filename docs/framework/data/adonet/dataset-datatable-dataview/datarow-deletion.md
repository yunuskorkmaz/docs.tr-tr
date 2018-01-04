---
title: DataRow silme
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
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7f20fdebe101665e681597db0c55b7ced7853f9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datarow-deletion"></a>DataRow silme
Silmek için kullanabileceğiniz iki yöntem vardır bir <xref:System.Data.DataRow> nesnesinin bir <xref:System.Data.DataTable> nesne: **kaldırmak** yöntemi <xref:System.Data.DataRowCollection> nesnesi ve <xref:System.Data.DataRow.Delete%2A> yöntemi **DataRow**nesnesi. Oysa <xref:System.Data.DataRowCollection.Remove%2A> yöntemi siler bir **DataRow** gelen **DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> yöntemi yalnızca satır silme işlemi için işaretler. Uygulama çağırdığında gerçek kaldırma oluşur **AcceptChanges** yöntemi. Kullanarak <xref:System.Data.DataRow.Delete%2A>, hangi satırların gerçekten kaldırmadan önce silinmek üzere işaretlenmiş program aracılığıyla kontrol edebilirsiniz. Bir satır silinmek üzere işaretli olduğunda, <xref:System.Data.DataRow.RowState%2A> özelliği ayarlanmış <xref:System.Data.DataRow.Delete%2A>.  
  
 Ne <xref:System.Data.DataRow.Delete%2A> ya da <xref:System.Data.DataRowCollection.Remove%2A> üzerinden yineleme sırasında bir foreach döngüsü çağrılmalıdır bir <xref:System.Data.DataRowCollection> nesnesi. <xref:System.Data.DataRow.Delete%2A>ya da <xref:System.Data.DataRowCollection.Remove%2A> koleksiyon durumunu değiştirin.  
  
 Kullanırken bir <xref:System.Data.DataSet> veya **DataTable** ile birlikte bir **DataAdapter** ve kullanmak, bir ilişkisel veri kaynağı **silmek** yöntemi  **DataRow** satır kaldırmak için. **Silmek** yöntemi satır olarak işaretler **silinmiş** içinde **DataSet** veya **DataTable** ancak onu kaldırmaz. Bunun yerine, **DataAdapter** olarak işaretlenmiş bir satır karşılaştığında **silinmiş**, yürütülmeden kendi **DeleteCommand** veri kaynağında satır silme yöntemi. Satır sonra kalıcı olarak kullanılarak kaldırılabilir **AcceptChanges** yöntemi. Kullanırsanız **kaldırmak** satırı silmek için Satırı tablosundan tamamen kaldırılır ancak **DataAdapter** veri kaynağında satır silmez.  
  
 **Kaldırmak** yöntemi **DataRowCollection** geçen bir **DataRow** bağımsız değişken olarak ve aşağıdaki örnekte gösterildiği gibi koleksiyondan kaldırır.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Buna karşılık, aşağıdaki örnekte nasıl çağırılacağını **silmek** yöntemi bir **DataRow** değiştirmek için kendi **RowState** için **silinmiş** .  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Bir satır silinmek üzere işaretlenmiş ve çağırmanız **AcceptChanges** yöntemi **DataTable** nesne satır kaldırılır **DataTable**. Buna karşılık, çağırırsanız **RejectChanges**, **RowState** satırının ne olarak işaretlenen önce haline döner **silinmiş**.  
  
> [!NOTE]
>  Varsa **RowState** , bir **DataRow** olan **eklenen**, yani yalnızca eklendi tabloya ve ardından olarak işaretlenmiş **silinmiş**, bu tablosundan kaldırıldı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
