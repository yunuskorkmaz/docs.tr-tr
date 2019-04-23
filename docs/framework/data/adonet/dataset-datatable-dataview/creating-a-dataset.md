---
title: DataSet Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d2d17056e6dcd29ef9b5c5e8c3024a32fce32bd5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118189"
---
# <a name="creating-a-dataset"></a>DataSet Oluşturma
Örneğini oluşturduğunuz bir <xref:System.Data.DataSet> çağırarak <xref:System.Data.DataSet> Oluşturucusu. İsteğe bağlı olarak bir adı bağımsız değişkenini belirtin. İçin bir ad belirtmezseniz, <xref:System.Data.DataSet>, adı "İçin NewDataSet" olarak ayarlanır.  
  
 Ayrıca yeni bir oluşturabilirsiniz <xref:System.Data.DataSet> dayanan <xref:System.Data.DataSet>. Yeni <xref:System.Data.DataSet> varolan bir tam kopya olabilir <xref:System.Data.DataSet>; bir kopyasını <xref:System.Data.DataSet> ilişkisel yapısını veya şema kopyalar ancak, var olan verilerin hiçbirini içermez <xref:System.Data.DataSet>; veya bir alt kümesini <xref:System.Data.DataSet>, var olan yalnızca değiştirilen satırları içeren <xref:System.Data.DataSet> kullanarak <xref:System.Data.DataSet.GetChanges%2A> yöntemi. Daha fazla bilgi için [DataSet içeriklerini kopyalama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 Aşağıdaki kod örneği olgusu yapmayı gösteren bir <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapter’dan bir DataSet Doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
