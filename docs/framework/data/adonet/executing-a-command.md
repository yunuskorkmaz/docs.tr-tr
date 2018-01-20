---
title: "Bir komutu yürütme"
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
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c4879c49a410dfb40999f3163d8b23158cb71f0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="executing-a-command"></a>Bir komutu yürütme
.NET Framework ile dahil her .NET Framework veri sağlayıcısı devraldığı kendi komut nesnesi sahip <xref:System.Data.Common.DbCommand>. OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbCommand> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlCommand> nesne ODBC için .NET Framework veri sağlayıcısı içeren bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcı içeren bir <xref:System.Data.OracleClient.OracleCommand> nesnesi. Komutlar yürütülürken bu nesneleri çıkarır yöntemlerin her biri komut türüne göre ve dönüş değeri, aşağıdaki tabloda açıklandığı gibi istenen.  
  
|Komut|Dönüş Değeri|  
|-------------|------------------|  
|`ExecuteReader`|Döndürür bir `DataReader` nesne.|  
|`ExecuteScalar`|Tek bir sayı değerini döndürür.|  
|`ExecuteNonQuery`|Herhangi bir satır döndürmeyen bir komut yürütür.|  
|`ExecuteXMLReader`|Döndürür bir <xref:System.Xml.XmlReader>. İçin kullanılabilir bir `SqlCommand` yalnızca nesne.|  
  
 Her kesin türü belirtilmiş komut nesnesi de destekleyen bir <xref:System.Data.CommandType> belirten bir komut dizesi nasıl yorumlanacağını, aşağıdaki tabloda açıklandığı gibi numaralandırması.  
  
|CommandType|Açıklama|  
|-----------------|-----------------|  
|`Text`|Veri kaynağında yürütülecek deyimleri tanımlayan bir SQL komutu.|  
|`StoredProcedure`|Saklı yordam adı. Kullanabileceğiniz `Parameters` giriş ve çıkış parametreleri erişme ve dönüş değerleri, bağımsız olarak bir komut özelliğinin `Execute` yöntemi çağrılır. Kullanırken `ExecuteReader`, dönüş değerleri ve çıktı parametreleri kadar erişilemeyecek `DataReader` kapalı.|  
|`TableDirect`|Bir tablonun adı.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl oluşturulduğunu gösteren bir <xref:System.Data.SqlClient.SqlCommand> özelliklerini ayarlayarak bir saklı yordamı yürütmek için nesne. A <xref:System.Data.SqlClient.SqlParameter> nesne saklı yordamı için giriş parametresi belirtmek için kullanılır. Komutu kullanılarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi ve çıktısını <xref:System.Data.SqlClient.SqlDataReader> konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Sorun giderme komutları  
 SQL Server için .NET Framework veri sağlayıcısı başarısız komutu yürütmeleri için zaman zaman ortaya çıkan sorunları algılamak etkinleştirmek için performans sayaçlarını ekler. Daha fazla bilgi için bkz: [performans sayaçları](../../../../docs/framework/data/adonet/performance-counters.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataReader ile çalışma](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
