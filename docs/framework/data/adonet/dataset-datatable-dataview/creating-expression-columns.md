---
title: İfade Sütunları Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 1c4e0b368a8eb154207382ae70b9767f5a5fe64d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785440"
---
# <a name="creating-expression-columns"></a>İfade Sütunları Oluşturma
Bir sütun için bir ifade tanımlayabilir, bu değerin aynı satırdaki diğer sütun değerlerinden veya tablodaki birden çok satırın sütun değerlerinden hesaplanan bir değer içermesini sağlayabilirsiniz. Değerlendirilecek ifadeyi tanımlamak için, hedef sütunun <xref:System.Data.DataColumn.Expression%2A> özelliğini kullanın ve ifadedeki diğer sütunlara başvurmak için <xref:System.Data.DataColumn.ColumnName%2A> özelliğini kullanın. İfade <xref:System.Data.DataColumn.DataType%2A> sütunu için, ifadenin döndürdüğü değer için uygun olmalıdır.  
  
 Aşağıdaki tabloda, bir tablodaki ifade sütunlarının birkaç olası kullanımı listelenmektedir.  
  
|İfade türü|Örnek|  
|---------------------|-------------|  
|Karşılaştırma|"Toplam > = 500"|  
|Hesaplamada|"BirimFiyat * miktar"|  
|Toplama|Toplam (fiyat)|  
  
 Var olan bir **DataColumn** nesnesi üzerinde <xref:System.Data.DataColumn> **Expression** özelliğini ayarlayabilir veya özelliği aşağıdaki örnekte gösterildiği gibi oluşturucuya geçirilen üçüncü bağımsız değişken olarak ekleyebilirsiniz.  
  
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
