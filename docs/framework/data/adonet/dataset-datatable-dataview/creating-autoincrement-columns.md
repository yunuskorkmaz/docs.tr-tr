---
title: AutoIncrement Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 99c52b93cee858511d50aba2f30f2b9f96d91ccd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034378"
---
# <a name="creating-autoincrement-columns"></a>AutoIncrement Sütunları Oluşturma
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
