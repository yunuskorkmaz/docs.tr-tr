---
title: Türü belirtilmiş DataSet'leri sorgulama
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44200951"
---
# <a name="query-typed-datasets"></a>Türü belirlenmiş veri kümelerini sorgulayın

Varsa şemasını <xref:System.Data.DataSet> bilinen uygulama tasarım zamanında bir türü belirtilmiş kullanmanızı öneririz <xref:System.Data.DataSet> LINQ to DataSet kullanarak. Bir türü belirtilmiş <xref:System.Data.DataSet> türetildiği bir sınıf olan bir <xref:System.Data.DataSet>. Bu nedenle, tüm yöntemler, olaylar ve özelliklerini devralır bir <xref:System.Data.DataSet>. Ayrıca, belirlenmiş <xref:System.Data.DataSet> kesin türü belirtilmiş yöntemler, olaylar ve özellikleri sağlar. Bu, tablolar ve sütunlar adıyla koleksiyon tabanlı bir yöntem kullanmak yerine erişebileceği anlamına gelir. Bu sorgular daha basit ve daha okunabilir kolaylaştırır. Daha fazla bilgi için [yazılan veri kümeleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet da destekler yazılmış üzerinde sorgulama <xref:System.Data.DataSet>. İle yazılmış bir <xref:System.Data.DataSet>, genel kullanmak zorunda değil <xref:System.Data.DataRowExtensions.Field%2A> yöntemi veya <xref:System.Data.DataRowExtensions.SetField%2A> sütun verilerine erişmek için yöntemi. Özellik adları kullanılabilir derleme zamanında tür bilgilerini bulunduğundan <xref:System.Data.DataSet>. LINQ to DataSet, sütun değerlere erişim için doğru tür olarak sağlar, böylece yerine çalışma zamanında derlenen kod türü uyuşmazlığı hatalar yakalanır.

Türü belirtilmiş bir sorgulama başlamadan önce <xref:System.Data.DataSet>, kullanarak bir sınıf oluşturmanız gerekir **veri kümesi Tasarımcısı** Visual Studio'da. Daha fazla bilgi için [oluşturun ve veri kümeleri yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Örnek

Aşağıdaki örnek bir sorgu yazılı gösterir <xref:System.Data.DataSet>:

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

- [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Tablolar Arası Sorgular](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Tek Tablolu Sorgular](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
