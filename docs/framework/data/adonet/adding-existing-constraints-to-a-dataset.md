---
title: "Varolan kısıtlamaları bir veri kümesine ekleme"
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
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f2f6c60197b1d71feb13ca351ad19298e09ea56
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Varolan kısıtlamaları bir veri kümesine ekleme
**Doldurun** yöntemi **DataAdapter** doldurur bir <xref:System.Data.DataSet> yalnızca tablo sütunları ve satırları veri kaynağından; sahip ancak kısıtlamaları yaygın olarak ayarlanmış veri kaynağı tarafından **doldurun** yöntemi için bu şema bilgileri eklemez **DataSet** varsayılan olarak. Doldurmak için bir **DataSet** ya da arama yapabileceğiniz bir veri kaynağından var olan birincil anahtar kısıtlaması bilgilerle **FillSchema** yöntemi **DataAdapter**, veya ayarlayın **MissingSchemaAction** özelliği **DataAdapter** için **AddWithKey** çağırmadan önce **doldurun**. Bu birincil anahtara sağlayacak kısıtlamalar **veri kümesi** bu veri kaynağında yansıtır. Yabancı anahtar kısıtlaması bilgileri dahil değildir ve açıkça gösterildiği gibi oluşturulmalıdır [DataTable kısıtlamalarını](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Şema bilgilerini ekleme bir **DataSet** verilerle doldurma birincil anahtar kısıtlamalarını birlikte garantiler önce <xref:System.Data.DataTable> nesnelerini **DataSet**. Sonuç olarak, ek zaman doldurmak için çağrıları **DataSet** yapılan, birincil anahtar sütun bilgileri, veri kaynağından yeni satırlar her geçerli satır ile eşleştirmek için kullanılır **DataTable**ve geçerli verileri tabloları veri kaynağı ile yazılır. Veri kaynağından yeni satırlar eklenir şema bilgileri **DataSet**, yinelenen satırları sonuç.  
  
> [!NOTE]
>  Bir veri kaynağı bir sütunda otomatik artan olarak belirlenirse **FillSchema** yöntemini veya **doldurun** yöntemi ile bir **MissingSchemaAction** ,  **AddWithKey**, oluşturur bir **DataColumn** ile bir **AutoIncrement** özelliğini `true`. Ancak, ayarlamak gerekir **AutoIncrementStep değeri** ve **AutoIncrementSeed** kendiniz değerleri. Sütunları otomatik artırma hakkında daha fazla bilgi için bkz: [oluşturma AutoIncrement sütunları](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Kullanarak **FillSchema** veya ayar **MissingSchemaAction** için **AddWithKey** birincil anahtar sütunu bilgileri belirlemek için veri kaynağında ek işleme gerektirir. Bu ek işleme performansı düşürür. Tasarım zamanında birincil anahtar bilgilerini biliyorsanız, açıkça birincil anahtar sütunu veya sütun en iyi performans elde etmek için belirttiğiniz öneririz. Açıkça bir tablo için birincil anahtar bilgilerini ayarlama hakkında daha fazla bilgi için bkz: [tanımlama birincil anahtarlar](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aşağıdaki kod örneğinde, şema bilgi eklemek gösterilmiştir bir **DataSet** kullanarak **FillSchema**.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 Aşağıdaki kod örneğinde, şema bilgi eklemek gösterilmiştir bir **DataSet** kullanarak **MissingSchemaAction.AddWithKey** özelliği **doldurun** yöntemi.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>Birden çok sonuç kümesi işleme  
 Varsa **DataAdapter** döndürülen birden çok sonuç kümesi karşılaştığında **SelectCommand**, birden fazla tabloya oluşturacak **DataSet**. Tabloları bir sıfır tabanlı artımlı varsayılan adı verilen **tablo** *N*sürümünden itibaren **tablo** "Table0" yerine. Bağımsız değişken olarak bir tablo adı geçip geçmediğini **FillSchema** yöntemi, tablolar sıfır tabanlı bir artımlı adı verilir **TableName** *N* sürümündenitibaren**TableName** "TableName0" yerine.  
  
> [!NOTE]
>  Varsa **FillSchema** yöntemi **OleDbDataAdapter** nesne birden çok sonuç kümesi döndüren bir komutu için çağrılır, yalnızca şema bilgileri ilk sonuç kümesinden döndürülür. Birden çok sonuç için şema bilgileri döndüren zaman ayarlar kullanarak **OleDbDataAdapter**, önerilen, belirttiğiniz bir **MissingSchemaAction** , **AddWithKey** ve çağrılırken şema bilgileri elde **doldurun** yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
