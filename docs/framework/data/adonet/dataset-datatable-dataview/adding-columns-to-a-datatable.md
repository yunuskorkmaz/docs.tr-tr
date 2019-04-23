---
title: DataTable’a Sütun Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 2e7008f6693d7d76520a7ff6ae9172e28e4990c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207012"
---
# <a name="adding-columns-to-a-datatable"></a>DataTable’a Sütun Ekleme
A <xref:System.Data.DataTable> koleksiyonunu içeren <xref:System.Data.DataColumn> nesneler tarafından başvurulan **sütunları** tablonun özelliği. Bu sütunlar, kısıtlamalar, birlikte koleksiyonu, şema veya tablonun yapısını tanımlar.  
  
 Oluşturduğunuz **DataColumn** kullanarak bir tablo içindeki nesneleri **DataColumn** Oluşturucusu veya çağırarak **Ekle** yöntemi **sütunları**özelliği olan, tablodaki bir <xref:System.Data.DataColumnCollection>. **Ekle** yöntemi kabul isteğe bağlı **ColumnName**, **DataType**, ve **ifade** bağımsız değişkenleri ve yeni bir oluşturur  **DataColumn** koleksiyonunun bir üyesi olarak. Ayrıca var olan bir kabul **DataColumn** nesne koleksiyonuna ekler ve eklenen bir başvuru döndürür **DataColumn** istenmesi halinde. Çünkü **DataTable** nesneler herhangi bir veri kaynağına özgü değildir, .NET Framework türleri veri türü belirtmek için kullanılan bir **DataColumn**.  
  
 Aşağıdaki örnek, dört sütun ekler. bir **DataTable**.  
  
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
  
 Örnekte, dikkat özelliklerini **CustId** sütun izin ayarlanmış **DBNull** değerleri ve değerlerinin benzersiz sınırlamak için. Ancak, tanımlarsanız **CustId** sütun tablonun birincil anahtar sütunu olarak **AllowDBNull** özelliği otomatik olarak ayarlanır **false** ve **Benzersiz** özelliği otomatik olarak ayarlanır **true**. Daha fazla bilgi için [birincil anahtarlar tanımlama](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Bir sütun için bir sütun adı sağlanmazsa, sütun sütununun bir artımlı varsayılan ad verilir*N* "Column1" ile başlayarak, ne zaman eklenir **DataColumnCollection**. Adlandırma kuralı kaçınmanızı öneririz "sütun*N*" adı sağlamanız için ne zaman bir sütun adı sağlayın mevcut bir varsayılan sütun adıyla çakışıyor olabilir **DataColumnCollection**. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
 Kullanıyorsanız <xref:System.Xml.Linq.XElement> olarak <xref:System.Data.DataColumn.DataType%2A> , bir <xref:System.Data.DataColumn> içinde <xref:System.Data.DataTable>, XML serileştirme verilerinde okuduğunuzda çalışmaz. Örneğin, yazma, bir <xref:System.Xml.XmlDocument> kullanarak `DataTable.WriteXml` yöntem, bir ek üst düğümünde yoktur XML serileştirme <xref:System.Xml.Linq.XElement>. Bu sorunu geçici olarak çözmek için kullanın <xref:System.Data.SqlTypes.SqlXml> türü yerine <xref:System.Xml.Linq.XElement>. `ReadXml` ve `WriteXml` ile düzgün çalışmak <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [DataTable Şema Tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
