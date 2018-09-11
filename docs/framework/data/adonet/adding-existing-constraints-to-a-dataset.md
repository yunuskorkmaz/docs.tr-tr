---
title: DataSet'e var olan kısıtlamaları ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 90aa1e5dceb3cac87d330837496b9dc467dc1876
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260064"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>DataSet'e var olan kısıtlamaları ekleme
**Dolgu** yöntemi **DataAdapter** dolduran bir <xref:System.Data.DataSet> yalnızca tablo sütunları ve satırları bir veri kaynağından; ile ancak kısıtlamaları yaygın olarak ayarlanmış veri kaynağı tarafından **doldurun** yöntemi için bu şema bilgileri eklemez **veri kümesi** varsayılan olarak. Doldurmak için bir **veri kümesi** bir veri kaynağından varolan birincil anahtar kısıtlaması bilgilerle çağrısı yapabilirsiniz **FillSchema** yöntemi **DataAdapter**, veya ayarlama **MissingSchemaAction** özelliği **DataAdapter** için **AddWithKey** çağırmadan önce **dolgu**. Bu birincil anahtara sağlayacak kısıtlamalarını **veri kümesi** bu veri kaynağında yansıtır. Yabancı anahtar kısıtlaması bilgileri dahil değildir ve açıkça gösterildiği oluşturulmalıdır [DataTable kısıtlamaları](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Şema bilgileri ekleme bir **veri kümesi** verilerle doldurma birincil anahtar kısıtlamalarını birlikte olmasını sağlar önce <xref:System.Data.DataTable> nesneler **veri kümesi**. Sonuç olarak, ek zaman doldurmak için çağrıları **veri kümesi** yapılır, birincil anahtar sütun bilgileri, veri kaynağından yeni satırlar her geçerli satır ile eşleştirmek için kullanılır **DataTable**ve geçerli verileri tablolar, veri kaynağı ile yazılır. Veri kaynağından yeni satırlar eklenir şema bilgileri **veri kümesi**, yinelenen satırları imzalanmayarak.  
  
> [!NOTE]
>  Bir sütun bir veri kaynağındaki otomatik artan olarak belirlenirse **FillSchema** yöntemi veya **dolgu** yöntemi ile bir **MissingSchemaAction** ,  **AddWithKey**, oluşturur bir **DataColumn** ile bir **AutoIncrement** özelliğini `true`. Ancak, ayarlanacak ihtiyacınız olacak **AutoIncrementStep değeri** ve **AutoIncrementSeed** kendiniz değerleri. Sütunları otomatik olarak artırma hakkında daha fazla bilgi için bkz. [AutoIncrement sütunları oluşturma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 Kullanarak **FillSchema** veya ayarı **MissingSchemaAction** için **AddWithKey** birincil anahtar sütunu bilgileri belirlemek için veri kaynağında ek işleme gerektirir. Bu ek işleme performansı düşürür. Tasarım zamanında birincil anahtar bilgilerine biliyorsanız, açıkça birincil anahtar sütun veya sütunlar en iyi performans elde etmek için belirtmenizi öneririz. Bir tablonun birincil anahtar bilgileri açıkça ayarlama hakkında daha fazla bilgi için bkz. [birincil anahtarlar tanımlama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aşağıdaki kod örneği için şema bilgileri ekleme gösteren bir **veri kümesi** kullanarak **FillSchema**.  
  
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
  
 Aşağıdaki kod örneği için şema bilgileri ekleme gösteren bir **veri kümesi** kullanarak **MissingSchemaAction.AddWithKey** özelliği **dolgu** yöntemi.  
  
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
 Varsa **DataAdapter** döndürülen birden çok sonuç kümesi karşılaştığında **SelectCommand**, birden çok tablodan oluşturacağı **veri kümesi**. Tablolar, sıfır tabanlı artımlı varsayılan bir ad verilir **tablo** *N*ile başlayan **tablo** "Table0" yerine. Bağımsız değişkeni olarak bir tablo adı geçip geçmediğini **FillSchema** yöntemi, tabloları sıfır tabanlı bir artımlı adı verilir **TableName** *N* ilebaşlayan**TableName** "TableName0" yerine.  
  
> [!NOTE]
>  Varsa **FillSchema** yöntemi **OleDbDataAdapter** nesne birden çok sonuç kümesi döndüren bir komut çağrıldığında, yalnızca şema bilgileri ilk sonuç kümesinden döndürülür. Birden çok sonuç için şema bilgileri döndüren zaman ayarlar kullanarak **OleDbDataAdapter**, belirttiğiniz önerilir bir **MissingSchemaAction** , **AddWithKey** ve şema bilgilerini çağrılırken elde **dolgu** yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
