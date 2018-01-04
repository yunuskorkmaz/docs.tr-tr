---
title: "DataAdapter DataTable ve DataColumn eşlemeleri"
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
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3df07f8b7bf71d658e9073a8aeb3d51dee087544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable ve DataColumn eşlemeleri
A **DataAdapter** sıfır veya daha fazla koleksiyonu içeren <xref:System.Data.Common.DataTableMapping> nesnelerini kendi **TableMappings** özelliği. A **DataTableMapping** bir veri kaynağına karşı sorgu sağlayıcıdan döndürülen verileri arasında ana bir eşleme sağlar ve bir <xref:System.Data.DataTable>. **DataTableMapping** adı yerine geçirilebilir **DataTable** için ad **doldurun** yöntemi **DataAdapter**. Aşağıdaki örnekte bir **DataTableMapping** adlı **AuthorsMapping** için **yazarlar** tablo.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** sütun adları kullanmanıza olanak sağlayan bir **DataTable** , veritabanındaki kullanılanlardan farklı. **DataAdapter** eşleme tablosu güncelleştirildiğinde sütunlarla eşleşmesi için kullanır.  
  
 Belirtmezseniz, bir **TableName** veya **DataTableMapping** ad çağrılırken **doldurun** veya **güncelleştirme** yöntemi  **DataAdapter**, **DataAdapter** arar bir **DataTableMapping** "Tablo" adlı. Bu, **DataTableMapping** yok, **TableName** , **DataTable** "Tablo". Varsayılan belirtebilirsiniz **DataTableMapping** oluşturarak bir **DataTableMapping** "Tablo" adı.  
  
 Aşağıdaki kod örneği oluşturur bir **DataTableMapping** (gelen <xref:System.Data.Common> ad alanı) için belirtilen varsayılan eşleme yapar **DataAdapter** "Tablo" adlandırma tarafından. Örnek sorgu sonucundaki ilk tablodaki sütunların sonra eşlemeleri ( **müşteriler** tablosu **Northwind** veritabanı) daha kullanıcı dostu adlarında kümesine **Northwind müşterileri**  tablosundaki <xref:System.Data.DataSet>. Eşlenmemiş sütunlar için veri kaynağından sütunun adı kullanılır.  
  
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
  
 Daha gelişmiş durumlarda aynı istediğiniz karar verebilir **DataAdapter** farklı eşlemeleri farklı tablolarla yüklenirken desteklemek için. Bunu yapmak için sadece olarak ek ekleyin **DataTableMapping** nesneleri.  
  
 Zaman **doldurun** yöntemi örneği geçirilen bir **DataSet** ve **DataTableMapping** adı, bu adı taşıyan bir eşleme varsa, kullanılan Aksi takdirde bir  **DataTable** ile adı kullanılır.  
  
 Aşağıdaki örnekler oluşturma bir **DataTableMapping** adıyla **müşteriler** ve **DataTable** adını **BizTalkSchema**. Örnek ardından SELECT deyimi tarafından döndürülen satır eşler **BizTalkSchema** **DataTable**.  
  
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
>  Sütun eşlemesi için bir kaynak sütun adı belirtilmedi veya bir kaynak tablo adı için bir tablo eşlemesi belirtilmedi, varsayılan adlarını otomatik olarak oluşturulur. Hiç kaynak sütunu için sütun eşleme sağlanırsa, sütun eşlemesi bir artımlı varsayılan adı verilen **SourceColumn** *N* başlayarak **SourceColumn1**. Kaynak tablo adı için bir tablo eşleme sağlanırsa, tablo eşlemesi bir artımlı varsayılan adı verilen **SourceTable** *N*sürümünden itibaren **SourceTable1**.  
  
> [!NOTE]
>  Adlandırma kuralı kaçınmanızı öneririz **SourceColumn** *N* bir sütun eşlemesi için veya **SourceTable** *N* bir tablo için Sağladığınız ad mevcut bir varsayılan sütun eşlemesi adı ile çakışıyor olabilir çünkü eşleme **ColumnMappingCollection** veya Tablo eşleme adını **DataTableMappingCollection** . Sağlanan adı zaten varsa, bir özel durum.  
  
## <a name="handling-multiple-result-sets"></a>Birden çok sonuç kümesi işleme  
 Varsa, **SelectCommand** birden çok tablo döndüren **doldurun** artımlı değerlerle tablo adları tablolar için otomatik olarak oluşturur **DataSet**sürümünden itibaren Belirtilen tablo adı ve devam etmeden biçiminde **TableName** *N*sürümünden itibaren **TableName1**. Tablo için belirtilen istediğiniz bir adla otomatik olarak oluşturulan tablo adını eşleştirmek için Tablo eşlemeleri kullanabilirsiniz **DataSet**. Örneğin, bir **SelectCommand** iki tablo döndüren **müşteriler** ve **siparişleri**, aşağıdaki çağrıyı sorun **doldurun**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 İki tablo oluşturulan **DataSet**: **müşteriler** ve **Customers1**. Tablo eşlemeleri ikinci tablo adlandırdığınız emin olmak için kullanabileceğiniz **siparişleri** yerine **Customers1**. Bunu yapmak için kaynak tablosu eşleyin **Customers1** için **DataSet** tablo **siparişleri**, aşağıdaki örnekte gösterildiği gibi.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
