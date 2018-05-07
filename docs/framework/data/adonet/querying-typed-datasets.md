---
title: Yazılan veri kümeleri sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 30a6512202615590a4b399b8ce7173b213a8873c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="querying-typed-datasets"></a>Yazılan veri kümeleri sorgulama
Varsa şeması <xref:System.Data.DataSet> bilinen uygulama tasarım zamanında yazılmış kullanmanızı öneririz <xref:System.Data.DataSet> kullanırken [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Yazılmış bir <xref:System.Data.DataSet> türeyen bir sınıf bir <xref:System.Data.DataSet>. Bu nedenle, tüm yöntemleri, olayları ve özelliklerini devralır bir <xref:System.Data.DataSet>. Ayrıca, yazılı <xref:System.Data.DataSet> kesin türü belirtilmiş yöntemleri, olayları ve özellikleri sağlar. Bu, tablolar ve sütunlar adıyla koleksiyon tabanlı yöntemleri kullanmak yerine erişebileceğiniz anlamına gelir. Bu sorgular daha basit ve daha okunabilir yapar. Daha fazla bilgi için bkz: [yazılan veri kümeleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Ayrıca yazılmış sorgulama destekler <xref:System.Data.DataSet>. İle yazılmış bir <xref:System.Data.DataSet>, genel kullanmak zorunda değil <xref:System.Data.DataRowExtensions.Field%2A> yöntemi veya <xref:System.Data.DataRowExtensions.SetField%2A> yöntemi sütun verilere erişme.  Özellik adları kullanılabilir derleme zamanında tür bilgiler dahil edilir çünkü <xref:System.Data.DataSet>. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] böylece kodu yerine çalışma zamanında derlenen türü uyuşmazlığı hataları yakalanan sütun değerlerini erişim doğru türü olarak sağlar.  
  
 Yazılmış bir sorgulama başlamadan önce <xref:System.Data.DataSet>, veri kümesi Tasarımcısı'nda kullanarak sınıfı oluşturmalıdır [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  Daha fazla bilgi için bkz: [oluşturma ve veri kümelerini yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgu yazılan gösterir <xref:System.Data.DataSet>:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSet’leri Sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Tablolar Arası Sorgular](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [Tek Tablolu Sorgular](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
