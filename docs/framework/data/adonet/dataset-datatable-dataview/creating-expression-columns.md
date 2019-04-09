---
title: İfade Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 6e19e4e7cc0ea92e9d93e45c2a50d009e46b78c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175506"
---
# <a name="creating-expression-columns"></a>İfade Sütunları Oluşturma
Bir ifadenin bir sütun için tanımlayabileceğiniz, bir değer içermesi için etkinleştirme ile aynı satırdaki diğer sütun değerleri veya birden çok satır'tablosundaki sütun değerlerini hesaplanır. Değerlendirilecek ifade tanımlamak için <xref:System.Data.DataColumn.Expression%2A> ve hedef sütun kullanımı özelliği <xref:System.Data.DataColumn.ColumnName%2A> ifade diğer sütunlara başvurmak için özellik. <xref:System.Data.DataColumn.DataType%2A> Sütun ifade için ifadenin döndürdüğü değeri uygun olmalıdır.  
  
 Aşağıdaki tabloda, bir tablodaki ifade sütunları birkaç olası kullanımları listeler.  
  
|İfade türü|Örnek|  
|---------------------|-------------|  
|Karşılaştırma|"Toplam > 500 ="|  
|Hesaplama|"UnitPrice * Quantity"|  
|Toplama|SUM(price)|  
  
 Ayarlayabileceğiniz **ifade** var olan bir özellik **DataColumn** nesne veya içerebilir özelliği için geçirilen üçüncü bağımsız değişken olarak <xref:System.Data.DataColumn> oluşturucusu, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 İfadeler, diğer ifade sütunları başvurabilir; Ancak, iki ifadeleri birbiriyle başvuru döngüsel bir başvuru, bir özel durum oluşturur. İfadeler yazma hakkında daha fazla kuralları için bkz: <xref:System.Data.DataColumn.Expression%2A> özelliği **DataColumn** sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
