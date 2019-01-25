---
title: DataRow silme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 69bdf4d23463cc07259a2b1de6b9efaa78f0f0de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593764"
---
# <a name="datarow-deletion"></a>DataRow silme
Silmek için kullanabileceğiniz iki yöntem vardır bir <xref:System.Data.DataRow> nesnesinden bir <xref:System.Data.DataTable> nesne: **Kaldır** yöntemi <xref:System.Data.DataRowCollection> nesnesi ve <xref:System.Data.DataRow.Delete%2A> yöntemi **DataRow**nesne. Oysa <xref:System.Data.DataRowCollection.Remove%2A> yöntemi siler bir **DataRow** gelen **DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> yöntemi yalnızca satır silme işlemi için işaretler. Uygulama çağırdığında gerçek kaldırma gerçekleşir **AcceptChanges** yöntemi. Kullanarak <xref:System.Data.DataRow.Delete%2A>, hangi satırların gerçekten kaldırmadan önce silinmek üzere işaretlenmiş programlı olarak denetleyebilirsiniz. Satır silme için işaretlendiğinden kendi <xref:System.Data.DataRow.RowState%2A> özelliği <xref:System.Data.DataRow.Delete%2A>.  
  
 Ne <xref:System.Data.DataRow.Delete%2A> ya da <xref:System.Data.DataRowCollection.Remove%2A> bir foreach döngüsü içinde yineleme sırasında çağrılması gereken bir <xref:System.Data.DataRowCollection> nesne. <xref:System.Data.DataRow.Delete%2A> ya da <xref:System.Data.DataRowCollection.Remove%2A> koleksiyon durumunu değiştirin.  
  
 Kullanırken bir <xref:System.Data.DataSet> veya **DataTable** ile birlikte bir **DataAdapter** ve kullanmak, bir ilişkisel veri kaynağı **Sil** yöntemi  **DataRow** satırı Kaldır. **Sil** yöntemi satır olarak işaretler **silinmiş** içinde **veri kümesi** veya **DataTable** ancak bunu kaldırmaz. Bunun yerine, **DataAdapter** olarak işaretlenmiş bir satır karşılaştığında **silinmiş**, yürütür, **DeleteCommand** veri kaynağındaki satırı silmek için yöntemi. Satır sonra kalıcı olarak kullanılarak kaldırılabilir **AcceptChanges** yöntemi. Kullanırsanız **Kaldır** satırı silmek için satırın tablosundan tamamen kaldırılır ancak **DataAdapter** veri kaynağında satırın silinmesine neden olmaz.  
  
 **Kaldır** yöntemi **DataRowCollection** götüren bir **DataRow** bağımsız değişken olarak ve aşağıdaki örnekte gösterildiği gibi koleksiyondan kaldırır.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Buna karşılık, aşağıdaki örnekte nasıl çağrılacağını gösterir **Sil** metodunda bir **DataRow** değiştirmek için kendi **RowState** için **silinen** .  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Bir satırı silinmek üzere işaretlendiğinden ve çağırmanızı **AcceptChanges** yöntemi **DataTable** nesnesi, satır kaldırılır **DataTable**. Buna karşılık, çağırırsanız **RejectChanges**, **RowState** satırının ne olarak işaretlenmesi önce haline döner **silinmiş**.  
  
> [!NOTE]
>  Varsa **RowState** , bir **DataRow** olduğu **eklenen**, yani yalnızca eklendiğini tablosuna ve ardından olarak işaretlenmiş **silinmiş**, bu tablosundan kaldırıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
