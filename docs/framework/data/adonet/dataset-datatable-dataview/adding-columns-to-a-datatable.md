---
title: DataTable’a Sütun Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 77bf117b8835623d768f8b8b0ec3e4195174cad7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043943"
---
# <a name="adding-columns-to-a-datatable"></a>DataTable’a Sütun Ekleme
, Tablonun **Columns** özelliği tarafından <xref:System.Data.DataColumn> başvurulan nesnelerin bir koleksiyonunu içerir.<xref:System.Data.DataTable> Bu sütun koleksiyonu, tüm kısıtlamalarla birlikte, tablonun şemasını veya yapısını tanımlar.  
  
 **DataColumn** oluşturucusunu kullanarak veya tablosunun **Columns** özelliğinin <xref:System.Data.DataColumnCollection> **Add** metodunu çağırarak bir tablo içinde **DataColumn** nesneleri oluşturun. **Add** yöntemi, Isteğe bağlı **ColumnName**, **DataType**ve **Expression** bağımsız değişkenlerini kabul eder ve koleksiyonun bir üyesi olarak yeni bir **DataColumn** oluşturur. Ayrıca, var olan bir **DataColumn** nesnesini kabul eder ve koleksiyona ekler ve Isteniyorsa eklenen **DataColumn** öğesine bir başvuru döndürür. **DataTable** nesneleri herhangi bir veri kaynağına özgü olmadığından, bir **DataColumn**veri türü belirtirken .NET Framework türleri kullanılır.  
  
 Aşağıdaki örnek, bir **DataTable**'a dört sütun ekler.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 Örnekte, **CustId** sütununun özelliklerinin **DBNull** değerlerine izin vermeyeceğini ve değerlerin benzersiz olduğunu kısıtlamak olduğuna dikkat edin. Ancak, tablosunun birincil anahtar sütunu olarak **CustId** sütununu tanımlarsanız, **AllowDBNull** özelliği otomatik olarak **false** olarak ayarlanır ve **Unique** özelliği otomatik olarak **doğru**olarak ayarlanır. Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
> Bir sütun için bir sütun adı sağlanmazsa, sütuna, **DataColumnCollection**'a eklendiğinde "Sütun1" ile başlayan, sütun için artımlı bir varsayılan ad verilir. Sağladığınız ad, **DataColumnCollection**içinde varolan bir varsayılan sütun adıyla çakışabileceğinden, bir sütun adı belirttiğinizde "sütun*N*" adlandırma kuralına engel olmasını öneririz. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
 <xref:System.Xml.Linq.XElement> İçindeki bir <xref:System.Data.DataColumn.DataType%2A> '<xref:System.Data.DataTable>ıolarak kullanıyorsanız, verileri okurken XML serileştirme çalışmaz. <xref:System.Data.DataColumn> Örneğin, <xref:System.Xml.XmlDocument> `DataTable.WriteXml` yöntemini kullanarak bir yazarsanız, XML 'e Serileştirmeden sonra içinde <xref:System.Xml.Linq.XElement>ek bir üst düğüm vardır. Bu sorunu geçici olarak çözmek için <xref:System.Data.SqlTypes.SqlXml> <xref:System.Xml.Linq.XElement>yerine türünü kullanın. `ReadXml`ve `WriteXml` ile<xref:System.Data.SqlTypes.SqlXml>düzgün çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
