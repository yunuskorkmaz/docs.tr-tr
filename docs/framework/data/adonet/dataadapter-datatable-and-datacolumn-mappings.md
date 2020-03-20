---
title: DataAdapter DataTable ve DataColumn Eşlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151565"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable ve DataColumn Eşlemeleri
**DataAdapter,** **TableMappings** özelliğinde <xref:System.Data.Common.DataTableMapping> sıfır veya daha fazla nesne koleksiyonu içerir. **DataTableMapping,** bir sorgudan bir veri kaynağına karşı döndürülen <xref:System.Data.DataTable>veriler ile bir . **DataTableMapping** adı **DataTable** adının yerine **DataAdapter'ın** **Dolgu** yöntemine geçirilebilir. Aşağıdaki örnek, **Yazarlar** tablosu için **Yazarlar Eşleme** adlı bir **DataTableMapping** oluşturur.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping,** veritabanındakilerden farklı bir **DataTable'da** sütun adlarını kullanmanıza olanak tanır. **DataAdapter,** tablo güncelleştirildiğinde sütunları eşleştirmek için eşleci kullanır.  
  
 DataAdapter'ın **Dolgu** veya **Güncelleştirme** yöntemini ararken bir **TableName** veya **DataTableMapping** adı belirtmezseniz, **DataAdapter**"Tablo" adlı bir **DataTableMapping eşlemesi** arar. **DataAdapter** Bu **DataTableMapping** yoksa, **DataTable** **Tablo Adı** "Tablo"dur. "Tablo" adında bir **DataTableMapping** oluşturarak varsayılan bir **DataTableMapping** belirtebilirsiniz.  
  
 Aşağıdaki kod örneği bir **DataTableMapping** <xref:System.Data.Common> (ad alanından) oluşturur ve "Tablo" adını vererek belirtilen **DataAdapter** için varsayılan eşleme yapar. Örnek daha sonra sorgu sonucu **(Northwind** veritabanının **Müşteriler** tablosu) ilk tablodan **northwind Müşteriler** tablosunda daha kullanıcı dostu <xref:System.Data.DataSet>adlar kümesi için sütuneşler . Eşlenen olmayan sütunlar için, veri kaynağından sütunadı kullanılır.  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 Daha gelişmiş durumlarda, aynı **DataAdapter'ın** farklı tablolara farklı eşlemelerle yüklemeyi desteklemesini istediğinize karar verebilirsiniz. Bunu yapmak için ek **DataTableMapping** nesneleri eklemeniz yeterlidir.  
  
 **Dolgu** yöntemi bir **DataSet** ve **DataTableMapping** adı örneği geçirildiğinde, bu ada sahip bir eşleme varsa kullanılır; aksi takdirde, bu ada sahip bir **DataTable** kullanılır.  
  
 Aşağıdaki örnekler, **Müşterilerin** adı ve **BizTalkSchema**bir **DataTable** adı ile **DataTableMapping** oluşturun. Örnek daha sonra SELECT deyimi tarafından döndürülen satırları **BizTalkSchema** **DataTable**ile eşler.  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> Bir sütun eşleme için bir kaynak sütun adı sağlanmaz veya tablo eşlemesi için bir kaynak tablo adı sağlanmazsa, varsayılan adlar otomatik olarak oluşturulur. Sütun eşleme için kaynak sütun sağlanmışsa, sütun eşleme **kaynağına SourceColumn1**ile başlayarak **Kaynak Sütun** *U, N'nin* artımlı varsayılan adı verilir. Tablo eşleme için kaynak tablo adı sağlanmışsa, tablo eşlemi **SourceTable** *N'nin*artımlı varsayılan adı verilir, **SourceTable1**ile başlayarak.  
  
> [!NOTE]
> Bir sütun eşleme için **SourceColumn** *N'nin* adlandırma kuralından veya tablo eşlemesi için **SourceTable** *N'den* kaçınmanızı öneririz, çünkü sağladığınız **ad, ColumnMappingCollection'daki** varolan varsayılan sütun eşleme adı veya **DataTableMappingCollection'daki**tablo eşleme adı ile çakışabilir. Sağlanan ad zaten varsa, bir özel durum atılır.  
  
## <a name="handling-multiple-result-sets"></a>Birden Çok Sonuç Kümesini Işleme  
 **SelectCommand'ınız** birden çok tablo döndürürse, **Fill,** belirtilen tablo adı ile başlayan ve **TableName** *N*formunda devam eden **DataSet**tabloları için artımlı değerlere sahip tablo adlarını otomatik olarak oluşturur Tablo **Adı1**ile başlar. Otomatik olarak oluşturulan tablo adını **DataSet'teki**tablo için belirtilmiş olmasını istediğiniz bir ada eşleştirmek için tablo eşlemelerini kullanabilirsiniz. Örneğin, müşteriler **ve** **siparişler**olmak üzere iki tablo döndüren bir **SelectCommand** için aşağıdaki çağrıyı **Doldur'a**verir.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 **DataSet'te**iki tablo oluşturulur: **Müşteriler** ve **Müşteriler1.** İkinci tablonun Müşteriler yerine **Siparişler** olarak adlandırılmasını sağlamak için tablo eşlemelerini **kullanabilirsiniz1.** Bunu yapmak için, Aşağıdaki örnekte gösterildiği **gibi, Müşteriler1'in** kaynak tablosunu **DataSet** tablo **Siparişleri**ile eşlendirin.  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
