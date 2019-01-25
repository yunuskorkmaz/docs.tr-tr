---
title: AutoIncrement sütunları oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: b4beffb3c5072e9eaa398e7433b363babadbb9eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528647"
---
# <a name="creating-autoincrement-columns"></a>AutoIncrement sütunları oluşturma
Benzersiz sütun değerlerini sağlamak için tabloya yeni satır eklendiğinde otomatik olarak artırmak için sütun değerlerini ayarlayabilirsiniz. Bir otomatik artan oluşturmak için <xref:System.Data.DataColumn>ayarlayın <xref:System.Data.DataColumn.AutoIncrement%2A> sütununun özellik **true**. <xref:System.Data.DataColumn> Ardından tanımlanan değer ile başlayan <xref:System.Data.DataColumn.AutoIncrementSeed%2A> özelliği ve değeri ile her bir satır eklenmiştir **AutoIncrement** sütun tanımlı değer artırılır <xref:System.Data.DataColumn.AutoIncrementStep%2A> özelliği sütunun.  
  
 İçin **AutoIncrement** sütun öneririz, <xref:System.Data.DataColumn.ReadOnly%2A> özelliği **DataColumn** ayarlanması **true**.  
  
 Aşağıdaki örnek, 200 değeri ile başlar ve artımlı olarak 3 adımda ekleyen bir sütun oluşturmak nasıl gösterir.  
  
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
- [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
