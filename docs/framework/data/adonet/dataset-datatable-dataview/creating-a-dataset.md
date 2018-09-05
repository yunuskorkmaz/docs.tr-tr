---
title: Bir veri kümesi oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 43e2f7a1892459ca96d44350431935493b596a60
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509557"
---
# <a name="creating-a-dataset"></a>Bir veri kümesi oluşturma
Örneğini oluşturduğunuz bir <xref:System.Data.DataSet> çağırarak <xref:System.Data.DataSet> Oluşturucusu. İsteğe bağlı olarak bir adı bağımsız değişkenini belirtin. İçin bir ad belirtmezseniz, <xref:System.Data.DataSet>, adı "İçin NewDataSet" olarak ayarlanır.  
  
 Ayrıca yeni bir oluşturabilirsiniz <xref:System.Data.DataSet> dayanan <xref:System.Data.DataSet>. Yeni <xref:System.Data.DataSet> varolan bir tam kopya olabilir <xref:System.Data.DataSet>; bir kopyasını <xref:System.Data.DataSet> ilişkisel yapısını veya şema kopyalar ancak, var olan verilerin hiçbirini içermez <xref:System.Data.DataSet>; veya bir alt kümesini <xref:System.Data.DataSet>, var olan yalnızca değiştirilen satırları içeren <xref:System.Data.DataSet> kullanarak <xref:System.Data.DataSet.GetChanges%2A> yöntemi. Daha fazla bilgi için [DataSet içeriklerini kopyalama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 Aşağıdaki kod örneği olgusu yapmayı gösteren bir <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapter’dan bir DataSet Doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
