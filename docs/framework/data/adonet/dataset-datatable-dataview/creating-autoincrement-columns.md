---
title: "AutoIncrement sütunlar oluşturma"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7bc71e3ae817bbdaf5dc14f22041e297cab949b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-autoincrement-columns"></a>AutoIncrement sütunlar oluşturma
Benzersiz sütun değerlerini sağlamak için yeni satırlar tabloya eklendiğinde otomatik olarak artırmak için sütun değerlerini ayarlayabilirsiniz. Bir otomatik artırma oluşturmak için <xref:System.Data.DataColumn>ayarlayın <xref:System.Data.DataColumn.AutoIncrement%2A> sütuna özelliğinin **doğru**. <xref:System.Data.DataColumn> Tanımlanan değer ile başlayan <xref:System.Data.DataColumn.AutoIncrementSeed%2A> özelliği ve her satırın değerini eklenen **AutoIncrement** sütun artırır tanımlanan değere göre <xref:System.Data.DataColumn.AutoIncrementStep%2A> sütunun özelliği.  
  
 İçin **AutoIncrement** sütun öneririz <xref:System.Data.DataColumn.ReadOnly%2A> özelliği **DataColumn** ayarlanabilir **doğru**.  
  
 Aşağıdaki örnek, 200 değeri ile başlar ve artımlı olarak 3 adımda eklediği bir sütun oluşturmak gösterilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataColumn>  
 [DataTable şema tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
