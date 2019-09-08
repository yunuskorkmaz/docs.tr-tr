---
title: AutoIncrement Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5e4a36829107480a44980c7210b39c21231c67f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786447"
---
# <a name="creating-autoincrement-columns"></a>AutoIncrement Sütunları Oluşturma
Benzersiz sütun değerlerini sağlamak için, tabloya yeni satırlar eklendiğinde sütun değerlerini otomatik olarak artır olarak ayarlayabilirsiniz. Otomatik artırma <xref:System.Data.DataColumn>oluşturmak için sütunun <xref:System.Data.DataColumn.AutoIncrement%2A> özelliğini **true**olarak ayarlayın. Sonra, <xref:System.Data.DataColumn.AutoIncrementSeed%2A> özelliğinde tanımlanan değerle başlar ve her satır, **AutoIncrement** sütununun değeri sütunun <xref:System.Data.DataColumn.AutoIncrementStep%2A> özelliğinde tanımlanan değere göre artar. <xref:System.Data.DataColumn>  
  
 **AutoIncrement** sütunları için, <xref:System.Data.DataColumn.ReadOnly%2A> **DataColumn** özelliğinin özelliğinin **true**olarak ayarlanması önerilir.  
  
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
