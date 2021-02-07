---
description: 'Hakkında daha fazla bilgi edinin: veri kümesi oluşturma'
title: DataSet Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 7a52c6e73b5ab3ba4bf384d6bab3640b85929fcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739657"
---
# <a name="creating-a-dataset"></a>DataSet Oluşturma

Oluşturucuyu çağırarak bir örneğini oluşturabilirsiniz <xref:System.Data.DataSet> <xref:System.Data.DataSet> . İsteğe bağlı olarak bir ad bağımsız değişkeni belirtin. İçin bir ad belirtmezseniz, <xref:System.Data.DataSet> ad "NewDataSet" olarak ayarlanır.  
  
 Ayrıca, <xref:System.Data.DataSet> varolan bir temelinde yeni bir oluşturabilirsiniz <xref:System.Data.DataSet> . Yeni, <xref:System.Data.DataSet> var olan öğesinin tam bir kopyası olabilir <xref:System.Data.DataSet> <xref:System.Data.DataSet> . Bu, ilişkisel yapıyı veya şemayı kopyalayan, ancak var olan bir veri kümesini ya da bir alt kümesini içeren, ancak, <xref:System.Data.DataSet> <xref:System.Data.DataSet> yalnızca var olan bir ' ın <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> . Daha fazla bilgi için bkz. [DataSet Içeriğini kopyalama](copying-dataset-contents.md).  
  
 Aşağıdaki kod örneği, bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Data.DataSet> .  
  
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
