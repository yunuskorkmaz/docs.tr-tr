---
title: DataRelations Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 5fe2bd45e0abada1f9ec7071e3863da853479b51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202389"
---
# <a name="adding-datarelations"></a>DataRelations Ekleme

<xref:System.Data.DataSet>Birden çok nesne ile <xref:System.Data.DataTable> , bir <xref:System.Data.DataRelation> tabloyu başka bir tabloyla ilişkilendirmek, tablolar arasında gezinmek ve ilişkili bir tablodan alt veya üst satırları döndürmek için nesneleri kullanabilirsiniz.  
  
 Bir **DataRelation** oluşturmak için gereken bağımsız değişkenler, oluşturulmakta olan **DataRelation** için bir addır ve <xref:System.Data.DataColumn> ilişkide üst ve alt sütunları olarak işlev gösteren sütunlara bir veya daha fazla başvuru dizisi. Bir **DataRelation**oluşturduktan sonra, tablolar arasında gezinmek ve değerleri almak için kullanabilirsiniz.  
  
 ' A bir **DataRelation** eklemek <xref:System.Data.DataSet> , varsayılan olarak bir <xref:System.Data.UniqueConstraint> üst tabloya ve <xref:System.Data.ForeignKeyConstraint> alt tablosuna bir ekler. Bu varsayılan kısıtlamalar hakkında daha fazla bilgi için bkz. [DataTable kısıtlamaları](datatable-constraints.md).  
  
 Aşağıdaki kod örneği, bir içinde iki nesne kullanarak bir **DataRelation** oluşturur <xref:System.Data.DataTable> <xref:System.Data.DataSet> . Her biri <xref:System.Data.DataTable> , iki nesne arasında bağlantı görevi gören **CustId**adlı bir sütun içerir <xref:System.Data.DataTable> . Örnek, **ilişki** koleksiyonuna tek bir **DataRelation** ekler <xref:System.Data.DataSet> . Örnekteki ilk bağımsız değişken, oluşturulmakta olan **DataRelation** 'ın adını belirtir. İkinci bağımsız değişken üst **DataColumn** ' i ayarlar ve üçüncü bağımsız değişken alt **DataColumn**' i ayarlar.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 Bir **DataRelation** Ayrıca, **true**olarak ayarlandığında, alt TABLODAKI satırların, kullanılarak XML öğeleri olarak yazıldığında üst tablodaki iç Içe olmasına neden olan **iç içe** bir özelliği vardır <xref:System.Data.DataSet.WriteXml%2A> . Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
