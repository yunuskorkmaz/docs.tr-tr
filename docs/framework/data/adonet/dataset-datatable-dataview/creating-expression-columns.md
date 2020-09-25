---
title: İfade Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: ad14e4d3d6a1107f994d9536485257f9dc1851f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166852"
---
# <a name="creating-expression-columns"></a>İfade Sütunları Oluşturma

Bir sütun için bir ifade tanımlayabilir, bu değerin aynı satırdaki diğer sütun değerlerinden veya tablodaki birden çok satırın sütun değerlerinden hesaplanan bir değer içermesini sağlayabilirsiniz. Değerlendirilecek ifadeyi tanımlamak için, <xref:System.Data.DataColumn.Expression%2A> hedef sütunun özelliğini kullanın ve <xref:System.Data.DataColumn.ColumnName%2A> ifadedeki diğer sütunlara başvurmak için özelliğini kullanın. <xref:System.Data.DataColumn.DataType%2A>İfade sütunu için, ifadenin döndürdüğü değer için uygun olmalıdır.  
  
 Aşağıdaki tabloda, bir tablodaki ifade sütunlarının birkaç olası kullanımı listelenmektedir.  
  
|İfade türü|Örnek|  
|---------------------|-------------|  
|Karşılaştırma|"Toplam >= 500"|  
|Hesaplamada|"BirimFiyat * miktar"|  
|Toplama|Toplam (fiyat)|  
  
 Var olan bir **DataColumn** nesnesi üzerinde **Expression** özelliğini ayarlayabilir veya özelliği <xref:System.Data.DataColumn> Aşağıdaki örnekte gösterildiği gibi oluşturucuya geçirilen üçüncü bağımsız değişken olarak ekleyebilirsiniz.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 İfadeler, diğer ifade sütunlarına başvurabilir; Ancak, iki ifadenin birbirini bildirdiği döngüsel bir başvuru, bir özel durum oluşturur. İfadeleri yazma hakkında kurallar için bkz <xref:System.Data.DataColumn.Expression%2A> . **DataColumn** sınıfının özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataTable Şema Tanımı](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
