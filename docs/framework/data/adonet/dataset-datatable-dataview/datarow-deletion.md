---
title: DataRow Silme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 2092d7319a398bbdeaef764d677818f78ddf9de9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153358"
---
# <a name="datarow-deletion"></a>DataRow Silme

Nesnesinden bir nesneyi silmek için kullanabileceğiniz iki yöntem vardır <xref:System.Data.DataRow> <xref:System.Data.DataTable> : nesnenin **Remove** yöntemi <xref:System.Data.DataRowCollection> ve <xref:System.Data.DataRow.Delete%2A> **DataRow** nesnesinin yöntemi. Yöntemi, <xref:System.Data.DataRowCollection.Remove%2A> **DataRowCollection**öğesinden bir **DataRow** siler, <xref:System.Data.DataRow.Delete%2A> Yöntem yalnızca silme satırını işaretler. Gerçek kaldırma, uygulama **AcceptChanges** yöntemini çağırdığında oluşur. Kullanarak <xref:System.Data.DataRow.Delete%2A> , kaldırma işleminin gerçekten kaldırılmadan önce hangi satırların silinmek üzere işaretlendiğini programlı bir şekilde denetleyebilirsiniz. Bir satır silinmek üzere işaretlendiğinde, <xref:System.Data.DataRow.RowState%2A> özelliği olarak ayarlanır <xref:System.Data.DataRow.Delete%2A> .  
  
 <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRowCollection.Remove%2A> Bir nesne üzerinden yineleme sırasında ForEach döngüsünde ne de çağrılmalıdır <xref:System.Data.DataRowCollection> . <xref:System.Data.DataRow.Delete%2A><xref:System.Data.DataRowCollection.Remove%2A>koleksiyonun durumunu da değiştirebilirsiniz.  
  
 Bir <xref:System.Data.DataSet> **DataAdapter** ve ilişkisel veri kaynağıyla birlikte bir veya **DataTable** kullanırken, satırı kaldırmak için **DataRow** 'ın **Delete** yöntemini kullanın. **Delete** yöntemi, satırı **DataSet** veya **DataTable** öğesinde **Deleted** olarak işaretler, ancak kaldırır. Bunun yerine, **DataAdapter** **Silinmiş**olarak işaretlenen bir satırla karşılaştığında, veri kaynağındaki satırı silmek için **DeleteCommand** yöntemini yürütür. Daha sonra satır, **AcceptChanges** yöntemi kullanılarak kalıcı olarak kaldırılabilir. Satırı silmek için **Kaldır** ' ı kullanırsanız, satır tamamen tablodan kaldırılır, ancak **DataAdapter** veri kaynağındaki satırı silmez.  
  
 **DataRowCollection** 'ın **Remove** yöntemi bir **DataRow** öğesini bağımsız değişken olarak alır ve aşağıdaki örnekte gösterildiği gibi koleksiyondan kaldırır.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Buna karşılık aşağıdaki örnek, **RowState** değerini **Deleted**olarak değiştirmek Için bir **DataRow** üzerinde **Delete** yönteminin nasıl çağrılacağını gösterir.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Bir satır silinmek üzere işaretlenmişse ve **DataTable** nesnesinin **AcceptChanges** metodunu çağırırsanız, satır **DataTable**'dan kaldırılır. Buna karşılık, **RejectChanges**öğesini çağırırsanız, satırın **RowState** 'ı **silindi**olarak işaretlenmeden önce ne olduğuna geri döner.  
  
> [!NOTE]
> Bir **DataRow** 'ın **RowState** değerini **eklendiyse**, bu, tabloya yalnızca eklenmiş olduğunu belirtir ve sonra **silindi**olarak işaretlenir, tablodan kaldırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
