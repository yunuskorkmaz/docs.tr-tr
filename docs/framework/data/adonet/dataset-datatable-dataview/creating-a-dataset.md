---
title: "Bir veri kümesi oluşturma"
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
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16ab7a7ba65e915ec8bede1d075625c00e90960c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-dataset"></a>Bir veri kümesi oluşturma
Bir örneğini oluşturmak bir <xref:System.Data.DataSet> çağırarak <xref:System.Data.DataSet> Oluşturucusu. İsteğe bağlı olarak bir adı bağımsız değişkenini belirtin. İçin bir ad belirtmezseniz, <xref:System.Data.DataSet>, adı "NewDataSet" ayarlanır.  
  
 Ayrıca, yeni bir oluşturabilirsiniz <xref:System.Data.DataSet> var olan temel <xref:System.Data.DataSet>. Yeni <xref:System.Data.DataSet> var olan tam bir kopyasını olabilir <xref:System.Data.DataSet>; bir kopyasını <xref:System.Data.DataSet> ilişkisel yapısı veya şema kopyalar ancak, varolan verilerin içermediğinden <xref:System.Data.DataSet>; veya bir alt kümesini <xref:System.Data.DataSet>, Mevcut kümeden yalnızca değiştirilen satırları içeren <xref:System.Data.DataSet> kullanarak <xref:System.Data.DataSet.GetChanges%2A> yöntemi. Daha fazla bilgi için bkz: [kopyalama DataSet içeriği](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).  
  
 Aşağıdaki kod örneğinde olgusu yapmayı gösteren bir <xref:System.Data.DataSet>.  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapter kümesinden doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Veri kümeleri, DataTable ve DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
