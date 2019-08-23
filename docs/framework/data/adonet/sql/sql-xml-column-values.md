---
title: SQL XML Sütun Değerleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 29e9ac5b95b62ef2a4467bf41484c3740d550abd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964956"
---
# <a name="sql-xml-column-values"></a>SQL XML Sütun Değerleri
SQL Server `xml` veri türünü destekler ve geliştiriciler, <xref:System.Data.SqlClient.SqlCommand> sınıfının standart davranışını kullanarak bu tür dahil sonuç kümelerini alabilir. Bir sütun, herhangi bir sütun alındığı gibi (örneğin, bir <xref:System.Data.SqlClient.SqlDataReader>) alınabilir <xref:System.Xml.XmlReader>, ancak sütunun içeriğiyle XML olarak çalışmak istiyorsanız, ' yi kullanmanız gerekir. `xml`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması, her biri bir `xml` sütun içeren iki satırı, **AdventureWorks** veritabanındaki <xref:System.Data.SqlClient.SqlDataReader> **Sales. Store** tablosundan bir örneğe seçer. Her satır için, `xml` sütunun değeri, <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yöntemi <xref:System.Data.SqlClient.SqlDataReader>kullanılarak okundu. Değer bir <xref:System.Xml.XmlReader>içinde depolanır. İçeriği bir <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> <xref:System.Data.IDataRecord.GetValue%2A> değişkeneayarlamakistiyorsanızyöntemiyerine<xref:System.Data.SqlTypes.SqlXml> kullanmanız gerektiğini unutmayın; sütunundeğerini`xml` bir dize olarak döndürür. <xref:System.Data.IDataRecord.GetValue%2A>  
  
> [!NOTE]
> SQL Server yüklediğinizde **AdventureWorks** örnek veritabanı varsayılan olarak yüklenmez. SQL Server kurulumunu çalıştırarak yükleyebilirsiniz.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlTypes.SqlXml>
- [SQL Server'da XML Verileri](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
