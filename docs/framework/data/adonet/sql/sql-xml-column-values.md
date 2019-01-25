---
title: SQL XML sütun değerleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 1cd6962a02a50ecd9f9b634148eeb38ad0a45e05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664050"
---
# <a name="sql-xml-column-values"></a>SQL XML sütun değerleri
SQL Server'ı destekleyen `xml` veri türü ve geliştiriciler, standart davranışını kullanarak bu türü içeren sonuç kümelerini alabilir <xref:System.Data.SqlClient.SqlCommand> sınıfı. Bir `xml` sütun alınabilir, yalnızca herhangi bir sütun getirildiği (içine bir <xref:System.Data.SqlClient.SqlDataReader>, örneğin) ancak içeriği sütunun XML olarak çalışmak istiyorsanız, kullanmanız gerekir bir <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulamasında içeren her iki satır seçer bir `xml` sütun, gelen **Sales.Store** tablosundaki **AdventureWorks** veritabanını bir <xref:System.Data.SqlClient.SqlDataReader> örneği. Her satırın değerini `xml` sütun kullanılarak okunur <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yöntemi <xref:System.Data.SqlClient.SqlDataReader>. Bir değeri depolanan bir <xref:System.Xml.XmlReader>. Kullanmanız gereken Not <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yerine <xref:System.Data.IDataRecord.GetValue%2A> içeriği ayarlamak isterseniz yöntemi bir <xref:System.Data.SqlTypes.SqlXml> değişkeni; <xref:System.Data.IDataRecord.GetValue%2A> değerini döndürür `xml` dize olarak sütun.  
  
> [!NOTE]
>  **AdventureWorks** örnek veritabanı, SQL Server'ı yüklediğinizde varsayılan olarak yüklenmedi. SQL Server Kurulumu çalıştırarak yükleyebilirsiniz.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Data.SqlTypes.SqlXml>
- [SQL Server'da XML Verileri](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
