---
title: DataAdapter DataTable ve DataColumn eşlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 9f33ae085bef2b611d1ce95bed1b26f9101a10b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385232"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable ve DataColumn eşlemeleri
A **DataAdapter** sıfır veya daha fazla koleksiyonu içeren <xref:System.Data.Common.DataTableMapping> nesneler, **TableMappings** özelliği. A **DataTableMapping** verileri arasındaki ana eşlemeyi döndürülen bir veri kaynağında bir sorgudan sağlar ve bir <xref:System.Data.DataTable>. **DataTableMapping** adı yerine geçirilebilir **DataTable** için ad **dolgu** yöntemi **DataAdapter**. Aşağıdaki örnek, oluşturur bir **DataTableMapping** adlı **AuthorsMapping** için **yazarlar** tablo.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** sütun adları kullanmanızı sağlayan bir **DataTable** veritabanı farklı olan. **DataAdapter** sütunlarla tablo güncelleştirildiğinde eşleşmesi için eşleme kullanır.  
  
 Belirtmezseniz, bir **TableName** veya **DataTableMapping** ad çağrılırken **dolgu** veya **güncelleştirme** yöntemi  **DataAdapter**, **DataAdapter** arayan bir **DataTableMapping** "Tablo" adlı. Bu, **DataTableMapping** yok **TableName** , **DataTable** "Tablo". Varsayılan belirtebilirsiniz **DataTableMapping** oluşturarak bir **DataTableMapping** "Tablo" adı.  
  
 Aşağıdaki kod örneği oluşturur bir **DataTableMapping** (gelen <xref:System.Data.Common> ad alanı) için belirtilen varsayılan eşleme hale getirir **DataAdapter** "Tablo" adlandırma tarafından. Örnek sorgu sonucu Birinci tablodaki sütunların sonra eşler ( **müşteriler** tablosu **Northwind** veritabanı) daha kullanıcı dostu adlarında bir dizi **Northwind müşterileri**  tablosundaki <xref:System.Data.DataSet>. Eşlenmemiş sütunlar için veri kaynağından sütunun adı kullanılır.  
  
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
  
 Daha gelişmiş durumlarda, aynı istediğinize karar **DataAdapter** farklı eşlemeleri farklı tablolarla yüklemeyi destekleyecek kadar. Bunu yapmak için ek eklemeniz yeterlidir **DataTableMapping** nesneleri.  
  
 Zaman **dolgu** yönteme örneği bir **veri kümesi** ve **DataTableMapping** adı bu ada sahip bir eşleme varsa, aksi takdirde bir  **DataTable** ile adı kullanılır.  
  
 Aşağıdaki örnekler bir **DataTableMapping** adıyla **müşteriler** ve **DataTable** adını **BizTalkSchema**. Bu örnek için SELECT deyimi tarafından döndürülen satırlar sonra eşler **BizTalkSchema** **DataTable**.  
  
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
>  Sütun eşlemesi için bir kaynak sütun adı sağlanmazsa veya bir tablo eşleme için bir kaynak tablo adı sağlanmazsa, varsayılan adları otomatik olarak oluşturulur. Hiç kaynak sütunu için sütun eşlemesi sağlanırsa, sütun eşleme bir artımlı varsayılan adı verilen **SourceColumn** *N* başlayarak **SourceColumn1**. Kaynak tablo adı için bir tablo eşleme sağlanırsa, Tablo eşleme, bir artımlı varsayılan ad verilir **SourceTable** *N*ile başlayan **SourceTable1**.  
  
> [!NOTE]
>  Adlandırma kuralı kaçınmanızı öneririz **SourceColumn** *N* bir sütun eşlemesi için veya **SourceTable** *N* bir tablo için eşleme sağladığınız ad mevcut bir varsayılan sütun eşleme adı çakışıyor çünkü **ColumnMappingCollection** veya Tablo eşleme adını **DataTableMappingCollection** . Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
## <a name="handling-multiple-result-sets"></a>Birden çok sonuç kümesi işleme  
 Varsa, **SelectCommand** birden fazla tabloyu döndürür **doldurun** tabloları için artımlı değerlerle tablo adları otomatik olarak oluşturduğu **veri kümesi**ile başlayan Belirtilen tablo adı ve devam etmeden biçiminde **TableName** *N*ile başlayan **TableName1**. Tablo eşlemeleri için tabloda belirtilen bir adı otomatik olarak oluşturulan tablo adını eşleştirmek için kullanabileceğiniz **veri kümesi**. Örneğin, bir **SelectCommand** iki tablo döndüren **müşteriler** ve **siparişler**, aşağıdaki çağrısını sorun **dolgu**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 İki tablo oluşturulan **veri kümesi**: **müşteriler** ve **Customers1**. Tablo eşlemeleri ikinci tablo adı emin olmak için kullanabileceğiniz **siparişler** yerine **Customers1**. Bunu yapmak için kaynak tablosu harita **Customers1** için **veri kümesi** tablo **siparişler**, aşağıdaki örnekte gösterildiği gibi.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
