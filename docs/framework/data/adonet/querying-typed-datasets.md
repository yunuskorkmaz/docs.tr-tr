---
description: 'Hakkında daha fazla bilgi edinin: sorgu türü belirtilmiş veri kümeleri'
title: Türü Belirtilmiş DataSet’leri Sorgulama
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 5bcf8bb587a0ed0eaca1bbe9b3a7d7143757780e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723705"
---
# <a name="query-typed-datasets"></a>Sorgu türü belirtilmiş veri kümeleri

Şeması <xref:System.Data.DataSet> uygulama tasarım zamanında biliniyorsa, LINQ to DataSet kullanırken bir tür kullanmanızı öneririz <xref:System.Data.DataSet> . Türü <xref:System.Data.DataSet> , bir sınıfından türetilen bir sınıftır <xref:System.Data.DataSet> . Bu nedenle, tüm yöntemleri, olayları ve özelliklerini devralır <xref:System.Data.DataSet> . Ayrıca, türü <xref:System.Data.DataSet> kesin belirlenmiş Yöntemler, olaylar ve özellikler sağlar. Bu, koleksiyon tabanlı yöntemler kullanmak yerine tablolara ve sütunlara ada göre erişebileceğiniz anlamına gelir. Bu, sorguları daha basit ve daha okunaklı hale getirir. Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri](./dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet, bir tür üzerinde sorgu yapmayı da destekler <xref:System.Data.DataSet> . Yazılı <xref:System.Data.DataSet> olarak, <xref:System.Data.DataRowExtensions.Field%2A> <xref:System.Data.DataRowExtensions.SetField%2A> sütun verilerine erişmek için genel yöntemi veya yöntemini kullanmanız gerekmez. Özellik adları derleme zamanında kullanılabilir, çünkü tür bilgileri içine dahil edilmiştir <xref:System.Data.DataSet> . LINQ to DataSet, doğru tür olarak sütun değerlerine erişim sağlar. böylece, kod çalışma zamanı yerine kod derlendiğinde tür uyuşmazlığı hataları yakalanır.

Bir türü sorgulamaya başlayabilmeniz için <xref:System.Data.DataSet> , Visual Studio 'Da **veri kümesi tasarımcısını** kullanarak sınıfı oluşturmanız gerekir. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Örnek

Aşağıdaki örnek, yazılı bir sorgu gösterir <xref:System.Data.DataSet> :

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a>Ayrıca bkz.

- [DataSet’leri Sorgulama](querying-datasets-linq-to-dataset.md)
- [Tablolar Arası Sorgular](cross-table-queries-linq-to-dataset.md)
- [Tek Tablolu Sorgular](single-table-queries-linq-to-dataset.md)
