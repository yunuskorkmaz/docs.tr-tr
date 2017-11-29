---
title: "DataTable tablosuna sütun ekleme"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6107c21ed04c9c39d69c5c784244d8f6bf9560e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="adding-columns-to-a-datatable"></a>DataTable tablosuna sütun ekleme
A <xref:System.Data.DataTable> bir koleksiyonu içerir <xref:System.Data.DataColumn> tarafından başvurulan nesneler **sütunları** tablosunun özelliği. Tüm kısıtlamaları birlikte sütun bu koleksiyonu şema veya tablo yapısını tanımlar.  
  
 Oluşturduğunuz **DataColumn** kullanarak bir tablo içindeki nesneleri **DataColumn** oluşturucusu, veya çağırarak **Ekle** yöntemi **sütunları**özelliği olan tablonun bir <xref:System.Data.DataColumnCollection>. **Ekle** yöntemi kabul isteğe bağlı **ColumnName**, **DataType**, ve **ifade** bağımsız değişkenleri ve yeni bir  **DataColumn** koleksiyonunun bir üyesi olarak. Ayrıca varolan bir kabul **DataColumn** nesne ve koleksiyona ekler ve eklenen bir başvuru döndürür **DataColumn** istediyseniz. Çünkü **DataTable** nesneleri herhangi bir veri kaynağı için belirli olmayan, .NET Framework türleri veri türünü belirtmek için kullanılan bir **DataColumn**.  
  
 Dört sütun aşağıdaki örnek, bir **DataTable**.  
  
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
  
 Örnekte, dikkat özelliklerini **CustId** sütun izin ayarlandığında **DBNull** değerleri ve benzersiz olması için değerleri sınırlamak için. Ancak, tanımlarsanız **CustId** sütunu tablonun birincil anahtar sütunu olarak **AllowDBNull** özelliği otomatik olarak ayarlanacak **false** ve **Benzersiz** özelliği otomatik olarak ayarlanacak **doğru**. Daha fazla bilgi için bkz: [tanımlama birincil anahtarlar](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Bir sütun adı için bir sütun sağlanmazsa, sütun sütunun bir artımlı varsayılan adı verilen*N* "Column1" ile başlayarak, ne zaman eklenir **DataColumnCollection**. Adlandırma kuralı kaçınmanızı öneririz "sütun*N*" adı sağladığınız çünkü ne zaman bir sütun adı sağlayın mevcut bir varsayılan sütun adıyla çakışıyor olabilir **DataColumnCollection**. Sağlanan adı zaten varsa, özel durum oluşur.  
  
 Kullanıyorsanız <xref:System.Xml.Linq.XElement> olarak <xref:System.Data.DataColumn.DataType%2A> , bir <xref:System.Data.DataColumn> içinde <xref:System.Data.DataTable>, XML serileştirme verileri okurken çalışmaz. Örneğin, yazarsanız bir <xref:System.Xml.XmlDocument> kullanarak `DataTable.WriteXml` bir ek üst düğüm XML serileştirme sırasında yöntemi <xref:System.Xml.Linq.XElement>. Bu sorunu geçici olarak çözmek için kullanmak <xref:System.Data.SqlTypes.SqlXml> yerine tür <xref:System.Xml.Linq.XElement>. `ReadXml`ve `WriteXml` düzgün şekilde iş <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [DataTable şema tanımı](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
