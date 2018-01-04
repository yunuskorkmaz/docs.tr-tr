---
title: DataRelation gezinme
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
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d7d1dc98bdb235c6501ee503494d3c2bdc3a1820
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="navigating-datarelations"></a>DataRelation gezinme
Birincil işlevlerinden biri bir <xref:System.Data.DataRelation> Gezinti birinden izin <xref:System.Data.DataTable> içinde başka bir bir <xref:System.Data.DataSet>. Bu sayede tüm almak ilgili <xref:System.Data.DataRow> nesnelerini **DataTable** tek bir verildiğinde **DataRow** ilgili öğesinden **DataTable**. Örneğin, kurduktan sonra bir **DataRelation** Müşteriler tablosu ve Siparişler tablosu arasında kullanarak bir müşterinin satır için tüm sipariş satırları alabilirsiniz **GetChildRows**.  
  
 Aşağıdaki kod örneği oluşturur bir **DataRelation** arasında **müşteriler** tablo ve **siparişleri** tablosunun bir **DataSet** ve döndürür Tüm siparişleri her müşteri için.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Sonraki örnek dört tablonun birlikte ilgili ve bu ilişkilerinde gezinme önceki örnekte üzerinde oluşturur. Önceki örnekte olduğu gibi **CustomerID** ilişkili **müşteriler** tablosu **siparişleri** tablo. Her müşteri için **müşteriler** tablo, tüm alt satırları **siparişleri** tablo belirlenir, belirli bir müşterinin siparişleri sayısını döndürmek için ve bunların **OrderID** değerleri.  
  
 Genişletilmiş örnek değerleri de döndürür **sipariş ayrıntıları** ve **ürünleri** tabloları. **Siparişleri** tablo ile ilgili **sipariş ayrıntıları** kullanarak tablo **OrderID** belirlemek için her biri için müşteri siparişi, hangi ürünler ve miktarları sipariş edilen. Çünkü **sipariş ayrıntıları** tablosu yalnızca içerir **ProductID** sıralı, ürün **sipariş ayrıntıları** ilgili **ürünleri** kullanarak **ProductID** dönebilmek için **ProductName**. Bu ilişkiyi **ürünleri** üst bir tablodur ve **sipariş ayrıntılarını** tablodur alt. Üzerinden yineleme olduğunda sonuç olarak, **sipariş ayrıntıları** tablo **GetParentRow** ilgili almak için çağrılır **ProductName** değeri.  
  
 Fark olduğunda **DataRelation** için oluşturulan **müşteriler** ve **siparişleri** tabloları, herhangi bir değer için belirtilmişse **createConstraints**bayrağını (varsayılan **true**). Bu, tüm varsayar satırları **siparişleri** tablonuz bir **CustomerID** üst var. değer **müşteriler** tablo. Varsa bir **CustomerID** bulunmaktadır **siparişleri** bulunmayan tablo **müşteriler** tablo, bir <xref:System.Data.ForeignKeyConstraint> bir özel durum oluşturulmasına neden olur.  
  
 Alt sütun üst sütun içermiyor değerler içerebilecek ayarlanmadığında **createConstraints** bayrağını **false** eklerken **DataRelation**. Örnekte, **createConstraints** bayrağı ayarlanmış **false** için **DataRelation** arasında **siparişleri** tablo ve  **Sipariş Ayrıntıları** tablo. Bu uygulama tüm kayıtların dönüş sağlar **sipariş ayrıntıları** tablo ve yalnızca bir alt kümesini kayıtlarından **siparişleri** bir çalışma zamanı özel oluşturma olmadan tablo. Genişletilmiş örnek aşağıdaki biçimde bir çıktı üretir.  
  
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
  
 Aşağıdaki kod örneğinde genişletilmiş bir örnektir burada değerleri **sipariş ayrıntıları** ve **ürünleri** tabloları döndürüldü, yalnızca bir alt kümesini kayıtları ile **siparişleri**döndürülen tablo.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataSets, DataTables ve DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
