---
title: DataTable Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 272976d3c581d3e8a5860ba5cf3f9695ca370d8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112391"
---
# <a name="creating-a-datatable"></a>DataTable Oluşturma
A <xref:System.Data.DataTable>, bellek içi ilişkisel verileri bir tablo temsil eden olabilir oluşturulan ve bağımsız olarak kullanılan veya diğer .NET Framework nesneleri tarafından en yaygın bir üyesi olarak kullanılabilir bir <xref:System.Data.DataSet>.  
  
 Oluşturabileceğiniz bir **DataTable** uygun kullanarak nesne **DataTable** Oluşturucusu. Kendisine ekleyebilirsiniz **veri kümesi** kullanarak **Ekle** eklemek üzere yöntemi **DataTable** nesnenin **tabloları** koleksiyonu.  
  
 Oluşturabilirsiniz **DataTable** içindeki nesneleri bir **veri kümesi** kullanarak **dolgu** veya **FillSchema** yöntemlerinin  **DataAdapter** nesnesi veya bir önceden tanımlanmış veya çıkarsanan XML şeması kullanarak **ReadXml**, **ReadXmlSchema**, veya **InferXmlSchema** yöntemlerinin **veri kümesi**. Ekledikten sonra dikkat bir **DataTable** üyesi olarak **tabloları** bir koleksiyonunu **veri kümesi**, diğer bir tablolarıkoleksiyonunaeklenemiyor**Veri kümesi**.  
  
 İlk oluşturduğunuzda bir **DataTable**, (diğer bir deyişle, bir yapı) bir şema yok. Tablo şemasını tanımlamak için oluşturma ekleyin ve gerekir <xref:System.Data.DataColumn> nesneleri için **sütunları** tablo koleksiyonu. Ayrıca tablosu için birincil anahtar sütunu tanımlamak ve oluşturma ve ekleme **kısıtlaması** nesneleri için **kısıtlamaları** tablo koleksiyonu. İçin şemayı tanımladıktan sonra bir **DataTable**, ekleyerek tabloya veri satırı ekleyebilirsiniz **DataRow** nesneleri için **satırları** tablo koleksiyonu.  
  
 İçin bir değer sağlamanız gerekmez <xref:System.Data.DataTable.TableName%2A> oluşturduğunuzda özelliği bir **DataTable**; özelliği başka bir zaman belirtebilirsiniz ya da bölmeyi boş bırakabilirsiniz. Ancak, bir tablo olmadan eklediğinizde bir **TableName** değerini bir **veri kümesi**, tablonun tablosunun bir artımlı varsayılan adı verilir*N*Table0 için "Tablo" ile başlayan.  
  
> [!NOTE]
>  Kaçınmanızı öneririz "tablo*N*" sağladığınız olduğunda adlandırma kuralı bir **TableName** sağladığınız ad mevcut bir varsayılan tablo adı ile çakışıyor çünkü değer **veri kümesi** . Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
 Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** nesnesi ve "Müşteri" adı atar  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Aşağıdaki örnek, bir örneğini oluşturur. bir **DataTable** ekleyerek **tabloları** koleksiyonunu bir **veri kümesi**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [DataAdapter’dan bir DataSet Doldurma](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [XML’den DataSet Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
