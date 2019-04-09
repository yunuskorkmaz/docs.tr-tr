---
title: Komut Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: c3ed424aff3cd485a78d26a7f27bc5b1eac66448
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119749"
---
# <a name="executing-a-command"></a>Komut Yürütme
Devralınan kendi komut nesnesi .NET Framework ile birlikte dahil edilen her .NET Framework veri sağlayıcısı olan <xref:System.Data.Common.DbCommand>. OLE DB için .NET Framework Veri Sağlayıcısı'nı içeren bir <xref:System.Data.OleDb.OleDbCommand> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlCommand> nesnesi, ODBC için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcısı'nı içeren bir <xref:System.Data.OracleClient.OracleCommand> nesne. Komutları yürütmek bu nesneleri kullanıma sunan yöntemlerin her biri, komut türüne göre ve dönüş değeri, aşağıdaki tabloda açıklandığı gibi gerekli.  
  
|Komut|Dönüş Değeri|  
|-------------|------------------|  
|`ExecuteReader`|Döndürür bir `DataReader` nesne.|  
|`ExecuteScalar`|Tek bir sayı değerini döndürür.|  
|`ExecuteNonQuery`|Herhangi bir satır döndürmeyen bir komutu yürütür.|  
|`ExecuteXMLReader`|Döndürür bir <xref:System.Xml.XmlReader>. Kullanılabilir bir `SqlCommand` yalnızca nesne.|  
  
 Her bir türü kesin belirlenmiş komut nesnesi de destekleyen bir <xref:System.Data.CommandType> komut dizesi nasıl yorumlanacağını, aşağıdaki tabloda açıklandığı gibi belirten sabit listesi.  
  
|CommandType|Açıklama|  
|-----------------|-----------------|  
|`Text`|Veri kaynağında çalıştırılacak deyimleri tanımlayan bir SQL komutu.|  
|`StoredProcedure`|Saklı yordamın adı. Kullanabileceğiniz `Parameters` giriş ve çıkış parametrelerini erişme ve dönüş değerleri, bağımsız olarak bir komut özelliğini `Execute` yöntemi çağrılır. Kullanırken `ExecuteReader`çıkış parametresi ve dönüş değerleri kadar erişilemez `DataReader` kapatılır.|  
|`TableDirect`|Bir tablonun adı.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Data.SqlClient.SqlCommand> özelliklerini ayarlayarak bir saklı yordamı yürütmek için nesne. A <xref:System.Data.SqlClient.SqlParameter> nesne saklı yordam için giriş parametresi belirtmek için kullanılır. Kullanarak komutu yürütülmeden <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi ve çıktısını <xref:System.Data.SqlClient.SqlDataReader> konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Sorun giderme komutları  
 SQL Server için .NET Framework veri sağlayıcısı sağlamak başarısız komut yürütmeleriyle ilişkili aralıklı olarak ortaya çıkan sorunları algılamak performans sayaçları ekler. Daha fazla bilgi için [performans sayaçları](../../../../docs/framework/data/adonet/performance-counters.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
