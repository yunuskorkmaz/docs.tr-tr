---
title: DataRelations içinde gezinme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 1819d468d12c03ce0c4faac11f4b20b8fe0f9c33
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731280"
---
# <a name="navigating-datarelations"></a>DataRelations içinde gezinme
Birincil işlevlerinden biri bir <xref:System.Data.DataRelation> bir gezinti izin vermesidir <xref:System.Data.DataTable> diğerine içinde bir <xref:System.Data.DataSet>. Bu sayede tüm almak ilgili <xref:System.Data.DataRow> birindeki nesnelerin **DataTable** tek bir verildiğinde **DataRow** ilgili gelen **DataTable**. Örneğin, kurduktan sonra bir **DataRelation** tablosu müşteriler ve Siparişler tablosunun arasında kullanarak bir müşterinin satır için tüm sipariş satırları alabilirsiniz **GetChildRows**.  
  
 Aşağıdaki kod örneği oluşturur bir **DataRelation** arasında **müşteriler** tablo ve **siparişler** tablosunun bir **veri kümesi** ve döndürür Tüm siparişleri her müşteri için.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Sonraki örnekte, dört tablo birlikte ilgili ve bu ilişkilerinde gezinme önceki örnekte üzerinde oluşturur. Önceki örnekte olduğu gibi **CustomerID** ilişkili **müşteriler** tablo **siparişler** tablo. Her müşteri için **müşteriler** tablo, tüm alt satırları **siparişler** tablo belirlenir, belirli bir müşterinin siparişlerinin sayısını döndürmek için ve bunların **OrderID** değerleri.  
  
 Genişletilmiş örnek değerlerinin de döndürür **OrderDetails** ve **ürünleri** tablolar. **Siparişler** tablo ilgili **OrderDetails** kullanarak tablo **OrderID** belirlemek için her biri için müşteri siparişi hangi ürün ve miktarların düzenlenebiliyordu. Çünkü **OrderDetails** yalnızca tablo içeren **ProductID** sıralı bir ürünün **OrderDetails** ilgili **ürünleri** kullanarak **ProductID** döndürmek için **ProductName**. Bu ilişkiyi **ürünleri** üst tablodur ve **sipariş ayrıntıları** alt bir tablodur. Yineleme sırasında bir sonucu olarak **OrderDetails** tablo **GetParentRow** ilgili almak için çağırılır **ProductName** değeri.  
  
 Kullanırken dikkat edin **DataRelation** için oluşturulan **müşteriler** ve **siparişler** tablolar, herhangi bir değer için belirtilmişse **createConstraints**bayrağını (varsayılan değer **true**). Bu, tüm varsayar satırlarda **siparişler** tablonuz bir **CustomerID** üst var. değer **müşteriler** tablo. Varsa bir **CustomerID** var. **siparişler** yok tablo **müşteriler** tablo, bir <xref:System.Data.ForeignKeyConstraint> bir özel durum oluşturulmasına neden olur.  
  
 Alt sütun üst sütun içermediğinden değerler içerdiğinde ayarlamak **createConstraints** bayrak **false** eklerken **DataRelation**. Örnekte, **createConstraints** bayrağı ayarlandığında **false** için **DataRelation** arasında **siparişler** tablo ve  **OrderDetails** tablo. Bu uygulamanın den tüm kayıtları döndüren sağlar **OrderDetails** tablo ve yalnızca bir alt kümesini kayıtlardan **siparişler** tablo olmadan bir çalışma zamanı özel durumu oluşturuluyor. Genişletilmiş örnek çıktısı aşağıdaki biçimde oluşturur.  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 Aşağıdaki kod örneği bir genişletilmiş bir örnektir burada değerlerinden **OrderDetails** ve **ürünleri** tablolar döndürülür, yalnızca bir alt kümesi ile kayıtlara **siparişler**döndürülen tablo.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
