---
title: DataTable’a Sütun Ekleme
description: DataTable, tablonun Columns özelliği tarafından başvurulan DataColumn nesnelerini içerir. ADO.NET içindeki bir tabloya sütun eklemek için bu örnek kodu kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286953"
---
# <a name="adding-columns-to-a-datatable"></a>DataTable’a Sütun Ekleme
<xref:System.Data.DataTable> <xref:System.Data.DataColumn> , Tablonun **Columns** özelliği tarafından başvurulan nesnelerin bir koleksiyonunu içerir. Bu sütun koleksiyonu, tüm kısıtlamalarla birlikte, tablonun şemasını veya yapısını tanımlar.  
  
 **DataColumn** oluşturucusunu kullanarak veya tablosunun **Columns** özelliğinin **Add** metodunu çağırarak bir tablo içinde **DataColumn** nesneleri oluşturun <xref:System.Data.DataColumnCollection> . **Add** yöntemi, Isteğe bağlı **ColumnName**, **DataType**ve **Expression** bağımsız değişkenlerini kabul eder ve koleksiyonun bir üyesi olarak yeni bir **DataColumn** oluşturur. Ayrıca, var olan bir **DataColumn** nesnesini kabul eder ve koleksiyona ekler ve Isteniyorsa eklenen **DataColumn** öğesine bir başvuru döndürür. **DataTable** nesneleri herhangi bir veri kaynağına özgü olmadığından, bir **DataColumn**veri türü belirtirken .NET Framework türleri kullanılır.  
  
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
  
 Örnekte, **CustId** sütununun özelliklerinin **DBNull** değerlerine izin vermeyeceğini ve değerlerin benzersiz olduğunu kısıtlamak olduğuna dikkat edin. Ancak, tablosunun birincil anahtar sütunu olarak **CustId** sütununu tanımlarsanız, **AllowDBNull** özelliği otomatik olarak **false** olarak ayarlanır ve **Unique** özelliği otomatik olarak **doğru**olarak ayarlanır. Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](defining-primary-keys.md).  
  
> [!CAUTION]
> Bir sütun için bir sütun adı sağlanmazsa, sütuna, **DataColumnCollection**'a eklendiğinde "Sütun1"*ile başlayan, sütun için* artımlı bir varsayılan ad verilir. Sağladığınız ad, **DataColumnCollection**içinde varolan bir varsayılan sütun adıyla çakışabileceğinden, bir sütun adı belirttiğinizde "sütun*N*" adlandırma kuralına engel olmasını öneririz. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
 <xref:System.Xml.Linq.XElement> <xref:System.Data.DataColumn.DataType%2A> İçindeki bir ' ı olarak kullanıyorsanız, <xref:System.Data.DataColumn> <xref:System.Data.DataTable> verileri okurken XML serileştirme çalışmaz. Örneğin, <xref:System.Xml.XmlDocument> yöntemini kullanarak bir yazarsanız `DataTable.WriteXml` , XML 'e Serileştirmeden sonra içinde ek bir üst düğüm vardır <xref:System.Xml.Linq.XElement> . Bu sorunu geçici olarak çözmek için <xref:System.Data.SqlTypes.SqlXml> yerine türünü kullanın <xref:System.Xml.Linq.XElement> . `ReadXml`ve `WriteXml` ile düzgün çalışır <xref:System.Data.SqlTypes.SqlXml> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [DataTable Şema Tanımı](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
