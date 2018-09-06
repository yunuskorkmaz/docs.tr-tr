---
title: DataRelations ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: d0f481979ead7af775d462a2624ec43080e2c5a9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891086"
---
# <a name="adding-datarelations"></a>DataRelations ekleme
İçinde bir <xref:System.Data.DataSet> birden çok <xref:System.Data.DataTable> nesnelerini kullanabileceğiniz <xref:System.Data.DataRelation> diğerine tabloları gidin ve ilişkili tablodan alt veya üst satırlar döndürülecek bir tablo ilişkilendirmek için nesneleri.  
  
 Oluşturmak için gereken bağımsız değişkenler bir **DataRelation** için bir adı olan **DataRelation** oluşturulan ve bir dizi veya birden fazla <xref:System.Data.DataColumn> üst ve alt hizmet sütunlara yönelik başvurulara İlişki sütun. Oluşturduktan sonra bir **DataRelation**, tablolar arasında gezinmek için ve değerleri almak için kullanabilirsiniz.  
  
 Ekleme bir **DataRelation** için bir <xref:System.Data.DataSet> ekler, varsayılan olarak, bir <xref:System.Data.UniqueConstraint> üst tabloya ve <xref:System.Data.ForeignKeyConstraint> alt tablo için. Bu varsayılan kısıtlamaları hakkında daha fazla bilgi için bkz: [DataTable kısıtlamaları](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Aşağıdaki kod örneği oluşturur bir **DataRelation** iki kullanarak <xref:System.Data.DataTable> nesneler bir <xref:System.Data.DataSet>. Her <xref:System.Data.DataTable> adlı bir sütun içeren **CustId**, ikisi arasında bir bağlantı olarak görev gören <xref:System.Data.DataTable> nesneleri. Tek bir örnek ekler **DataRelation** için **ilişkileri** koleksiyonunu <xref:System.Data.DataSet>. Örnekteki ilk bağımsız değişken adını belirten **DataRelation** oluşturuluyor. İkinci bağımsız değişkeni üst ayarlar **DataColumn** ve üçüncü bağımsız değişken alt ayarlar **DataColumn**.  
  
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
  
 A **DataRelation** de sahip bir **iç içe** özelliği, ayarlandığında **true**, üst tablodan ilgili satır içinde iç içe alt tablosundan satırları neden olur XML öğeleri kullanarak yazılırken <xref:System.Data.DataSet.WriteXml%2A> . Daha fazla bilgi için [kullanarak bir veri kümesi XML'de](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
