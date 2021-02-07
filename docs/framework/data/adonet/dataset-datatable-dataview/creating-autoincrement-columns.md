---
description: 'Daha fazla bilgi edinin: AutoIncrement sütunları oluşturma'
title: AutoIncrement Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 7568b1013b7af5aef7a6fc1f28dc163a082743a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739644"
---
# <a name="creating-autoincrement-columns"></a>AutoIncrement Sütunları Oluşturma

Benzersiz sütun değerlerini sağlamak için, tabloya yeni satırlar eklendiğinde sütun değerlerini otomatik olarak artır olarak ayarlayabilirsiniz. Otomatik artırma oluşturmak için <xref:System.Data.DataColumn> <xref:System.Data.DataColumn.AutoIncrement%2A> sütunun özelliğini **true** olarak ayarlayın. <xref:System.Data.DataColumn>Sonra, özelliğinde tanımlanan değerle başlar <xref:System.Data.DataColumn.AutoIncrementSeed%2A> ve her satır, **AutoIncrement** sütununun değeri sütunun özelliğinde tanımlanan değere göre artar <xref:System.Data.DataColumn.AutoIncrementStep%2A> .  
  
 **AutoIncrement** sütunları Için, <xref:System.Data.DataColumn.ReadOnly%2A> **DataColumn** özelliğinin özelliğinin **true** olarak ayarlanması önerilir.  
  
 Aşağıdaki örnek, 200 değeriyle başlayan ve adım adım 3 ' ü ekleyen bir sütunun nasıl oluşturulacağını gösterir.  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumn>
- [DataTable Şema Tanımı](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
