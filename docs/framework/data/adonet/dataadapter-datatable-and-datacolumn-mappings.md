---
title: DataAdapter DataTable ve DataColumn Eşlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: a9c81c8554c0fb393c10ed69f84c8b2d936ec1e6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040123"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable ve DataColumn Eşlemeleri
Bir **DataAdapter** , **TableMappings** özelliğinde sıfır veya daha fazla <xref:System.Data.Common.DataTableMapping> nesne koleksiyonu içerir. Bir **DataTableMapping** , bir sorgudan veri kaynağına göre döndürülen veriler ile bir <xref:System.Data.DataTable>ana eşleme sağlar. **DataTableMapping** adı DataTable 'ın **Fill** metoduna **DataTable** adının yerine **geçirilebilir.** Aşağıdaki örnek, **yazarlar** tablosu Için **authorsmapping** adlı bir **DataTableMapping** oluşturur.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 Bir **DataTableMapping** , veritabanından farklı bir **DataTable** içindeki sütun adlarını kullanmanıza olanak sağlar. **DataAdapter** , tablo güncellendiği zaman sütunları eşleştirmek için eşlemeyi kullanır.  
  
 **DataAdapter**'ın **Fill** veya **Update** metodunu çağırırken bir **TableName** veya bir **DataTableMapping** adı belirtmezseniz, **DataAdapter** , "Table" adlı bir **DataTableMapping** öğesine bakar. Bu **DataTableMapping** yoksa, **DataTable** 'ın **TableName** tablosu "Table" olur. "Tablo" adıyla bir **DataTableMapping** oluşturarak varsayılan bir **DataTableMapping** belirtebilirsiniz.  
  
 Aşağıdaki kod örneği bir **DataTableMapping** oluşturur (<xref:System.Data.Common> ad alanından) ve "Table" olarak adlandırarak belirtilen **DataAdapter** için varsayılan eşleme yapar. Örnek daha sonra, sorgu sonucu ( **Northwind** veritabanının **Customers** tablosu) içindeki ilk tablodaki sütunları, <xref:System.Data.DataSet>**Northwind Customers** tablosunda daha kolay bir Kullanıcı adı kümesine eşler. Eşlenmemiş sütunlarda, veri kaynağındaki sütunun adı kullanılır.  
  
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
  
 Daha gelişmiş durumlarda, aynı **DataAdapter** 'ın farklı eşlemelere sahip farklı tabloları yüklemeyi desteklemesini tercih edebilirsiniz. Bunu yapmak için, ek **DataTableMapping** nesneleri eklemeniz yeterlidir.  
  
 **Fill** yöntemine bir **veri kümesi** ve bir ölçü adı geçirildiğinde, bu ada **sahip bir eşleme** varsa kullanılır; Aksi takdirde, bu adı taşıyan bir **DataTable** kullanılır.  
  
 Aşağıdaki örneklerde, **Müşteri** adı ve **BizTalkSchema** **DataTable** adı ile bir **DataTableMapping** oluşturulur. Örnek daha sonra SELECT ifadesinin döndürdüğü satırları **BizTalkSchema** **DataTable**' a eşler.  
  
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
> Bir sütun eşlemesi için bir kaynak sütun adı sağlanmamışsa veya tablo eşlemesi için kaynak tablo adı sağlanmadığında, varsayılan adlar otomatik olarak oluşturulur. Bir sütun eşlemesi için kaynak sütun sağlanmazsa, sütun eşlemesine **SourceColumn1**ile başlayan bir **SourceColumn** *N* artımlı varsayılan adı verilir. Tablo eşlemesi için kaynak tablo adı sağlanmadığında tablo eşlemesine, **SourceTable1**ile başlayan bir **SourceTable** *N*artımlı varsayılan adı verilir.  
  
> [!NOTE]
> Sağladığınız ad, var olan bir varsayılan sütun eşleme adı ile çakışabileceğinden, bir sütun eşlemesi için **SourceColumn** *n* adlandırma kuralını veya tablo eşlemesi için **SourceTable** *n* 'yi kullanmaktan kaçınmanızı öneririz. **DataTableMappingCollection**Içindeki ColumnMappingCollection veya tablo eşleme adı. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
## <a name="handling-multiple-result-sets"></a>Birden çok sonuç kümesini işleme  
 **SelectCommand** uygulamanız birden çok tablo döndürürse, **Fill** , belirtilen tablo adından başlayarak ve **TableName** biçiminde devam ederek, **veri kümesindeki**tablolar için artımlı değerler içeren tablo adlarını otomatik olarak oluşturur **TableName1**Ile başlayan *N*. Otomatik olarak üretilen tablo adını, **veri kümesindeki**tablo için belirtilen bir adla eşlemek için tablo eşlemelerini kullanabilirsiniz. Örneğin, iki tablo, **Müşteri** ve **sipariş**döndüren bir **SelectCommand** için, aşağıdaki çağrıyı **dolduracak**şekilde verin.  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 **Veri kümesinde**iki tablo oluşturulur: **Customers** ve **Customers1**. Tablo eşlemelerini, ikinci tablonun **Customers1**yerine **siparişler** olarak adlandırılmış olduğundan emin olmak için kullanabilirsiniz. Bunu yapmak için, **Customers1** kaynak tablosunu aşağıdaki örnekte gösterildiği gibi **veri kümesi** tablo **siparişleriyle**eşleyin.  
  
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
