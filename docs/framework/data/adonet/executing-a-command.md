---
title: Komut Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: f749ea37e1655f006e4de26e7cb279b778fe4faf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795115"
---
# <a name="executing-a-command"></a>Komut Yürütme
.NET Framework eklenen her .NET Framework veri sağlayıcısının, öğesinden <xref:System.Data.Common.DbCommand>devralan kendi komut nesnesi vardır. OLE DB için .NET Framework veri sağlayıcısı bir <xref:System.Data.OleDb.OleDbCommand> nesne içerir, veri sağlayıcısı için .NET Framework SQL Server bir <xref:System.Data.SqlClient.SqlCommand> nesnesi içerir, ODBC için .NET Framework veri sağlayıcısı bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleCommand> nesne içerir. Bu nesnelerin her biri, aşağıdaki tabloda açıklandığı gibi komut türüne ve istenen dönüş değerine göre komutları yürütmek için yöntemler sunar.  
  
|Komut|Dönüş Değeri|  
|-------------|------------------|  
|`ExecuteReader`|Döndürür bir `DataReader` nesne.|  
|`ExecuteScalar`|Tek bir skaler değer döndürür.|  
|`ExecuteNonQuery`|Herhangi bir satır döndürmeyen bir komutu yürütür.|  
|`ExecuteXMLReader`|<xref:System.Xml.XmlReader>Döndürür. Yalnızca bir `SqlCommand` nesne için kullanılabilir.|  
  
 Kesin belirlenmiş her komut nesnesi Ayrıca, aşağıdaki <xref:System.Data.CommandType> tabloda açıklandığı gibi bir komut dizesinin nasıl yorumlandığını belirten bir sabit listesini destekler.  
  
|CommandType|Açıklama|  
|-----------------|-----------------|  
|`Text`|Veri kaynağında yürütülecek deyimleri tanımlayan bir SQL komutu.|  
|`StoredProcedure`|Saklı yordamın adı. Giriş ve çıkış parametrelerine `Parameters` erişmek için bir komutun özelliğini kullanabilir ve hangi `Execute` yöntemin çağrıldığı bağımsız olarak değerleri döndürebilirsiniz. Kullanırken `ExecuteReader`, dönüş değerleri ve çıkış parametreleri kapatılana `DataReader` kadar erişilebilir olmayacaktır.|  
|`TableDirect`|Bir tablonun adı.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, özelliklerini ayarlayarak bir saklı yordamı <xref:System.Data.SqlClient.SqlCommand> yürütmek için nasıl bir nesne oluşturacağınız gösterilmektedir. Bir <xref:System.Data.SqlClient.SqlParameter> nesnesi, saklı yordama giriş parametresini belirtmek için kullanılır. Komut <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi kullanılarak yürütülür ve ' <xref:System.Data.SqlClient.SqlDataReader> dan alınan çıktı konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Sorun giderme komutları  
 SQL Server için .NET Framework Veri Sağlayıcısı, başarısız olan komut yürütmeleri ile ilgili aralıklı sorunları algılamanıza olanak tanımak için performans sayaçlarını ekler. Daha fazla bilgi için bkz. [performans sayaçları](performance-counters.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar ve Parametreler](commands-and-parameters.md)
- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
