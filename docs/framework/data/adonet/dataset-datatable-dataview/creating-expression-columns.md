---
title: "İfade sütunları oluşturma"
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
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 315944262136e5db453ea01eae64fff6cb0d534d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-expression-columns"></a>İfade sütunları oluşturma
Bir ifadenin bir sütun için tanımlayabilirsiniz, bir değer içerecek şekilde etkinleştirme diğer sütun değerleri aynı satırda veya birden çok satır tablosundaki sütun değerlerinden hesaplanır. Değerlendirilecek ifade tanımlamak için <xref:System.Data.DataColumn.Expression%2A> ve hedef sütun kullanımı özelliği <xref:System.Data.DataColumn.ColumnName%2A> diğer sütunlara ifadede başvurmak için özellik. <xref:System.Data.DataColumn.DataType%2A> İfade için sütun için ifade döndürür değer uygun olmalıdır.  
  
 Aşağıdaki tabloda, bir tablodaki ifade sütunları birkaç olası kullanımları listeler.  
  
|İfade türü|Örnek|  
|---------------------|-------------|  
|Karşılaştırma|"Toplam > 500 ="|  
|Hesaplama|"UnitPrice * miktar"|  
|Toplama|SUM(price)|  
  
 Ayarlayabileceğiniz **ifade** varolan özelliğini **DataColumn** nesne veya içerebilir özelliği için geçirilen üçüncü bağımsız değişken olarak <xref:System.Data.DataColumn> aşağıdaki örnekte gösterildiği gibi Oluşturucusu.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 İfadeler diğer ifade sütunları başvurusu yapabilir; Ancak, iki ifadeye birbirine, başvuru bir döngüsel başvuru bir özel durum oluşturur. İfadeleri yazma hakkında daha fazla kuralları için bkz: <xref:System.Data.DataColumn.Expression%2A> özelliği **DataColumn** sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataTable şema tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
