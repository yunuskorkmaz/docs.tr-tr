---
title: DataTable Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: b56d2f8cd46f3184f1001c8bd6a70dbfc4968968
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937025"
---
# <a name="creating-a-datatable"></a>DataTable Oluşturma
Bir <xref:System.Data.DataTable>bellek içi ilişkisel veri tablosunu temsil eden bir tablosu, bağımsız olarak oluşturulup kullanılabilir veya diğer .NET Framework nesneleri tarafından, genellikle bir <xref:System.Data.DataSet>üyesi olarak kullanılabilir.  
  
 Uygun **DataTable** oluşturucusunu kullanarak bir **DataTable** nesnesi oluşturabilirsiniz. Bunu **DataTable** nesnesinin **Tables** koleksiyonuna eklemek Için **Add** metodunu kullanarak **veri kümesine** ekleyebilirsiniz.  
  
 Ayrıca, **DataAdapter** nesnesinin **Fill** veya **FillSchema** yöntemlerini kullanarak, ya da **ReadXml**, ReadXmlSchema kullanarak önceden tanımlanmış veya Çıkarsanan xml şemasından **DataTable** nesneleri de oluşturabilirsiniz.ya da **veri kümesinin** **InferXmlSchema** yöntemleri. Bir **veri kümesinin** **Tables** koleksiyonunun bir üyesi olarak bir **DataTable** ekledikten sonra, bunu başka bir **veri kümesinin**tablo koleksiyonuna ekleyemediğini unutmayın.  
  
 İlk olarak bir **DataTable**oluşturduğunuzda, bir şeması (yani bir yapı) yoktur. Tablonun şemasını tanımlamak için, nesneleri oluşturmanız ve tablonun <xref:System.Data.DataColumn> **Columns** koleksiyonuna eklemeniz gerekir. Ayrıca tablo için bir birincil anahtar sütunu tanımlayabilir ve tablonun **kısıtlamalar** koleksiyonuna **kısıtlama** nesneleri oluşturabilir ve ekleyebilirsiniz. Bir **DataTable**şemasını tanımladıktan sonra, tablodaki **satır** koleksiyonuna **DataRow** nesneleri ekleyerek tabloya veri satırları ekleyebilirsiniz.  
  
 <xref:System.Data.DataTable.TableName%2A> **DataTable**oluştururken özellik için bir değer sağlamanız gerekmez; özelliği başka bir zaman belirtebilir veya boş bırakabilirsiniz. Ancak, bir **veri kümesine** **TableName** değeri olmayan bir tablo eklediğinizde, tabloya TABLE0 için "Table" Ile başlayarak, tablo*N*artımlı varsayılan adı verilir.  
  
> [!NOTE]
> Bir **TableName** değeri belirttiğinizde "tablo*N*" adlandırma kuralını önlemenize önerilir, çünkü sağladığınız ad **veri kümesindeki**mevcut bir varsayılan tablo adıyla çakışabilir. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
 Aşağıdaki örnek, bir **DataTable** nesnesinin örneğini oluşturur ve "Customers" adına atar.  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Aşağıdaki örnek, bir **veri kümesinin** **Tables** koleksiyonuna ekleyerek bir **DataTable** örneği oluşturur.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
