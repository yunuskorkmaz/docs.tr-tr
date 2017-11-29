---
title: "DataView oluşturma"
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 28a2f6f299d2f904dc3f842c0c778f30081240b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-dataview"></a>DataView oluşturma
Oluşturmanın iki yolu vardır bir <xref:System.Data.DataView>. Kullanabileceğiniz **DataView** Oluşturucusu veya bir başvuru oluşturabilirsiniz <xref:System.Data.DataTable.DefaultView%2A> özelliği <xref:System.Data.DataTable>. **DataView** Oluşturucusu boş olabilir veya ya da alabilir bir **DataTable** tek bir bağımsız değişken olarak veya bir **DataTable** filtre ölçütü, sıralama ölçütü ve bir satır ile birlikte Durum Filtresi. İle kullanılmak üzere kullanılabilir ek değişkenleri hakkında daha fazla bilgi için **DataView**, bkz: [sıralama ve filtreleme verilerini](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Çünkü dizini bir **DataView** hem olduğunda yerleşik **DataView** oluşturulduğu ve herhangi biri seçildiğinde **sıralama**, **RowFilter**, veya  **RowStateFilter** özellikleri değiştirildiğinde, tüm başlangıç sıralama düzeni sağlayan veya oluşturduğunuzda filtreleme ölçütleri oluşturucu bağımsız değişken olarak en iyi performans elde **DataView**. Oluşturma bir **DataView** sıralama veya filtre ölçütünü belirterek ve ardından ayarlar olmadan **sıralama**, **RowFilter**, veya **RowStateFilter** özellikleri daha sonra en az iki kez oluşturulacak dizin neden olur: sonra zaman **DataView** oluşturulduğu ve yeniden sıralama veya filtre özelliklerden herhangi biri değiştirildiği.  
  
 Oluşturduğunuz gerçekleştiriyorsanız bir **DataView** herhangi bir bağımsız değişken almaz Oluşturucusu kullanarak, kullanmanız mümkün olmayacaktır **DataView** ayarladığınız kadar **tablo** özelliği .  
  
 Aşağıdaki kod örneğinde nasıl oluşturulduğunu gösteren bir **DataView** kullanarak **DataView** Oluşturucusu. A **RowFilter**, **sıralama** sütun ve **DataViewRowState** ile birlikte sağlanan **DataTable**.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 Aşağıdaki kod örneği, varsayılan bir başvuru almak gösterilmiştir **DataView** , bir **DataTable** kullanarak **DefaultView** tablo özelliğidir.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Verileri sıralama ve filtreleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
