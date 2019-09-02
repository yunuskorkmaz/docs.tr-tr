---
title: DataSet Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 19badb009ebe95c52ab1dbbaef96f280c769553b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205162"
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
