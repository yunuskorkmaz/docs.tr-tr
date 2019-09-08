---
title: Türü Belirtilmiş DataSet’leri Sorgulama
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782970"
---
# <a name="query-typed-datasets"></a>Sorgu türü belirtilmiş veri kümeleri

Şeması <xref:System.Data.DataSet> uygulama tasarım zamanında biliniyorsa, LINQ to DataSet kullanırken bir tür <xref:System.Data.DataSet> kullanmanızı öneririz. Türü <xref:System.Data.DataSet> , bir <xref:System.Data.DataSet>sınıfından türetilen bir sınıftır. Bu nedenle, tüm yöntemleri, olayları ve özelliklerini <xref:System.Data.DataSet>devralır. Ayrıca, türü <xref:System.Data.DataSet> kesin belirlenmiş Yöntemler, olaylar ve özellikler sağlar. Bu, koleksiyon tabanlı yöntemler kullanmak yerine tablolara ve sütunlara ada göre erişebileceğiniz anlamına gelir. Bu, sorguları daha basit ve daha okunaklı hale getirir. Daha fazla bilgi için bkz. [türü belirtilmiş veri kümeleri](./dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet, bir tür <xref:System.Data.DataSet>üzerinde sorgu yapmayı da destekler. Yazılı <xref:System.Data.DataSet>olarak, sütun verilerine erişmek için genel <xref:System.Data.DataRowExtensions.Field%2A> yöntemi veya <xref:System.Data.DataRowExtensions.SetField%2A> yöntemini kullanmanız gerekmez. Özellik adları derleme zamanında kullanılabilir, çünkü tür bilgileri içine <xref:System.Data.DataSet>dahil edilmiştir. LINQ to DataSet, doğru tür olarak sütun değerlerine erişim sağlar. böylece, kod çalışma zamanı yerine kod derlendiğinde tür uyuşmazlığı hataları yakalanır.

Bir türü <xref:System.Data.DataSet>sorgulamaya başlayabilmeniz için, Visual Studio 'da **veri kümesi tasarımcısını** kullanarak sınıfı oluşturmanız gerekir. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Örnek

Aşağıdaki örnek, yazılı <xref:System.Data.DataSet>bir sorgu gösterir:

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
