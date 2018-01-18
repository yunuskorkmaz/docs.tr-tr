---
title: "DataTable oluşturma"
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 94fa5507d71fef557baadc6ee8979efeee4acf40
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-datatable"></a>DataTable oluşturma
A <xref:System.Data.DataTable>, bellek içi ilişkisel veriyi, bir tablo temsil eden olabilir oluşturulan ve bağımsız olarak kullanılan ya da diğer .NET Framework nesneleri tarafından yaygın bir üyesi olarak kullanılabilir bir <xref:System.Data.DataSet>.  
  
 Oluşturabileceğiniz bir **DataTable** uygun kullanarak nesne **DataTable** Oluşturucusu. Ona ekleyebilirsiniz **DataSet** kullanarak **Ekle** eklemek için yöntemi **DataTable** nesnenin **tabloları** koleksiyonu.  
  
 Oluşturabilirsiniz **DataTable** içindeki nesneleri bir **DataSet** kullanarak **doldurun** veya **FillSchema** yöntemleri  **DataAdapter** nesnesi veya önceden tanımlanmış veya oluşturulursa XML şeması kullanarak bir **ReadXml**, **ReadXmlSchema**, veya **InferXmlSchema** yöntemlerinin **DataSet**. Ekledikten sonra unutmayın bir **DataTable** bir üyesi olarak **tabloları** bir koleksiyonunu **DataSet**, diğer tablolarıkoleksiyonunaeklenemez**DataSet**.  
  
 İlk oluşturduğunuzda bir **DataTable**, bir şema (diğer bir deyişle, bir yapı) yok. Tablonun şeması tanımlamak için Oluştur ekleyin ve gerekir <xref:System.Data.DataColumn> nesneleri **sütunları** tablo koleksiyonu. Ayrıca tablosu için birincil anahtar sütunu tanımlayın ve oluşturun ve eklemek **kısıtlaması** nesneleri **kısıtlamaları** tablo koleksiyonu. İçin şemayı tanımladıktan sonra bir **DataTable**, ekleyerek tabloya veri satırı ekleyebilirsiniz **DataRow** nesneleri **satırları** tablo koleksiyonu.  
  
 İçin bir değer sağlamanız gerekmez <xref:System.Data.DataTable.TableName%2A> oluşturduğunuzda özelliği bir **DataTable**; başka bir zamanda özelliği belirtebilirsiniz veya boş bırakabilirsiniz. Ancak, olmayan bir tablo eklediğinizde bir **TableName** değeri bir **DataSet**, tabloyu tablonun artımlı varsayılan adı verilen*N*Table0 için "Tablo" ile başlayan.  
  
> [!NOTE]
>  Kaçınmanızı öneririz "tablo*N*" sağladığınız zaman adlandırma bir **TableName** değer sağladığınız ad içinde varolan bir varsayılan tablo adı ile çakışıyor olabilir çünkü **veri kümesi** . Sağlanan adı zaten varsa, özel durum oluşur.  
  
 Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** nesnesi ve "Müşteri" adı atar  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** ekleyerek **tabloları** koleksiyonu bir **DataSet**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [DataAdapter’dan bir DataSet Doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
