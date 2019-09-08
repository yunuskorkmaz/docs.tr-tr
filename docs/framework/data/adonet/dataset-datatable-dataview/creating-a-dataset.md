---
title: DataSet Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786500"
---
# <a name="creating-a-dataset"></a>DataSet Oluşturma
Oluşturucuyu çağırarak bir <xref:System.Data.DataSet> örneğini oluşturabilirsiniz. <xref:System.Data.DataSet> İsteğe bağlı olarak bir ad bağımsız değişkeni belirtin. İçin <xref:System.Data.DataSet>bir ad belirtmezseniz, ad "NewDataSet" olarak ayarlanır.  
  
 Ayrıca, varolan <xref:System.Data.DataSet>bir temelinde yeni <xref:System.Data.DataSet> bir oluşturabilirsiniz. Yeni <xref:System.Data.DataSet> , var olan <xref:System.Data.DataSet>öğesinin tam bir kopyası olabilir. bunun bir kopyası, ilişkisel <xref:System.Data.DataSet> yapıyı veya şemayı kopyalayan ancak var <xref:System.Data.DataSet>olan veya öğesinin <xref:System.Data.DataSet>bir alt kümesindeki verilerin hiçbirini içermeyen bir kopyasıdır. yalnızca, <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> yöntemi kullanılarak var olan değiştirilen satırları içerir. Daha fazla bilgi için bkz. [DataSet Içeriğini kopyalama](copying-dataset-contents.md).  
  
 Aşağıdaki kod örneği, bir <xref:System.Data.DataSet>örneğinin nasıl oluşturulacağını göstermektedir.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapter’dan bir DataSet Doldurma](../populating-a-dataset-from-a-dataadapter.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
