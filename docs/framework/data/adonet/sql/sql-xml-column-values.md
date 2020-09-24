---
title: SQL XML Sütun Değerleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: cd55e2263d4b71fe62910ac918e331ebe37833eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177286"
---
# <a name="sql-xml-column-values"></a>SQL XML Sütun Değerleri

SQL Server `xml` veri türünü destekler ve geliştiriciler, sınıfının standart davranışını kullanarak bu tür dahil sonuç kümelerini alabilir <xref:System.Data.SqlClient.SqlCommand> . Bir `xml` sütun, herhangi bir sütun alındığı gibi ( <xref:System.Data.SqlClient.SqlDataReader> Örneğin, bir) alınabilir, ancak SÜTUNUN içeriğiyle XML olarak çalışmak istiyorsanız, ' yi kullanmanız gerekir <xref:System.Xml.XmlReader> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki konsol uygulaması, her biri bir sütun içeren iki satırı, `xml` **AdventureWorks** veritabanındaki **Sales. Store** tablosundan bir <xref:System.Data.SqlClient.SqlDataReader> örneğe seçer. Her satır için, sütunun değeri, `xml` yöntemi kullanılarak okundu <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> <xref:System.Data.SqlClient.SqlDataReader> . Değer bir içinde depolanır <xref:System.Xml.XmlReader> . <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> <xref:System.Data.IDataRecord.GetValue%2A> İçeriği bir değişkene ayarlamak istiyorsanız yöntemi yerine kullanmanız gerektiğini unutmayın <xref:System.Data.SqlTypes.SqlXml> ; <xref:System.Data.IDataRecord.GetValue%2A> `xml` sütunun değerini bir dize olarak döndürür.  
  
> [!NOTE]
> SQL Server yüklediğinizde **AdventureWorks** örnek veritabanı varsayılan olarak yüklenmez. SQL Server kurulumunu çalıştırarak yükleyebilirsiniz.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlTypes.SqlXml>
- [SQL Server'da XML Verileri](xml-data-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
