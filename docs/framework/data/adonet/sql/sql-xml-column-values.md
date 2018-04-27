---
title: SQL XML sütun değerleri
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c4eecbe66df3224e6dc3f118be474f25712afe8a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="sql-xml-column-values"></a>SQL XML sütun değerleri
SQL Server destekler `xml` veri türü ve geliştiriciler, standart davranışını kullanarak bu türü içeren sonuç kümelerini alabilir <xref:System.Data.SqlClient.SqlCommand> sınıfı. Bir `xml` yalnızca herhangi bir sütun getirildiği sütun alınabilir (içine bir <xref:System.Data.SqlClient.SqlDataReader>, örneğin) ancak sütunun XML olarak içeriğini çalışmak isterseniz, kullanmanız gereken bir <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki konsol uygulaması her içeren iki satırları seçer bir `xml` sütun, gelen **Sales.Store** tablosundaki **AdventureWorks** için veritabanı bir <xref:System.Data.SqlClient.SqlDataReader> örneği. Değeri, her satır için `xml` sütun kullanarak okunur <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yöntemi <xref:System.Data.SqlClient.SqlDataReader>. Değer depolanan bir <xref:System.Xml.XmlReader>. Kullanmanız gereken Not <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> yerine <xref:System.Data.IDataRecord.GetValue%2A> içeriği hale getirmek istiyorsanız yöntemi bir <xref:System.Data.SqlTypes.SqlXml> değişkeni; <xref:System.Data.IDataRecord.GetValue%2A> değerini döndürür `xml` sütunu bir dize olarak.  
  
> [!NOTE]
>  **AdventureWorks** örnek veritabanını SQL Server'ı yüklediğinizde varsayılan olarak yüklenmedi. SQL Server Kurulumu çalıştırarak yükleyebilirsiniz.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.SqlTypes.SqlXml>  
 [SQL Server'da XML Verileri](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
