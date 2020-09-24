---
title: Komut Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: d7d290c1c149f9eab2449c25e8d32f2568eb0277
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156465"
---
# <a name="executing-a-command"></a>Komut Yürütme

.NET Framework eklenen her .NET Framework veri sağlayıcısının, öğesinden devralan kendi komut nesnesi vardır <xref:System.Data.Common.DbCommand> . OLE DB için .NET Framework Veri Sağlayıcısı bir nesne içerir, Veri Sağlayıcısı .NET Framework SQL Server bir nesne içerir, ODBC için .NET Framework veri sağlayıcısı bir nesne içerir <xref:System.Data.OleDb.OleDbCommand> <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.Odbc.OdbcCommand> ve Oracle için .NET Framework veri sağlayıcısı bir <xref:System.Data.OracleClient.OracleCommand> nesnesi içerir. Bu nesnelerin her biri, aşağıdaki tabloda açıklandığı gibi komut türüne ve istenen dönüş değerine göre komutları yürütmek için yöntemler sunar.  
  
|Komut|Dönüş Değeri|  
|-------------|------------------|  
|`ExecuteReader`|Döndürür bir `DataReader` nesne.|  
|`ExecuteScalar`|Tek bir skaler değer döndürür.|  
|`ExecuteNonQuery`|Herhangi bir satır döndürmeyen bir komutu yürütür.|  
|`ExecuteXMLReader`|Döndürür <xref:System.Xml.XmlReader> . Yalnızca bir nesne için kullanılabilir `SqlCommand` .|  
  
 Kesin belirlenmiş her komut nesnesi ayrıca <xref:System.Data.CommandType> , aşağıdaki tabloda açıklandığı gibi bir komut dizesinin nasıl yorumlandığını belirten bir sabit listesini destekler.  
  
|CommandType|Açıklama|  
|-----------------|-----------------|  
|`Text`|Veri kaynağında yürütülecek deyimleri tanımlayan bir SQL komutu.|  
|`StoredProcedure`|Saklı yordamın adı. `Parameters`Giriş ve çıkış parametrelerine erişmek için bir komutun özelliğini kullanabilir ve hangi yöntemin çağrıldığı bağımsız olarak değerleri döndürebilirsiniz `Execute` . Kullanırken `ExecuteReader` , dönüş değerleri ve çıkış parametreleri kapatılana kadar erişilebilir olmayacaktır `DataReader` .|  
|`TableDirect`|Bir tablonun adı.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneğinde, <xref:System.Data.SqlClient.SqlCommand> özelliklerini ayarlayarak bir saklı yordamı yürütmek için nasıl bir nesne oluşturacağınız gösterilmektedir. Bir <xref:System.Data.SqlClient.SqlParameter> nesnesi, saklı yordama giriş parametresini belirtmek için kullanılır. Komut yöntemi kullanılarak yürütülür <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> ve ' dan alınan çıktı <xref:System.Data.SqlClient.SqlDataReader> konsol penceresinde görüntülenir.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Sorun giderme komutları  

 SQL Server için .NET Framework Veri Sağlayıcısı, başarısız olan komut yürütmeleri ile ilgili aralıklı sorunları algılamanıza olanak tanımak için performans sayaçlarını ekler. Daha fazla bilgi için bkz. [performans sayaçları](performance-counters.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar ve Parametreler](commands-and-parameters.md)
- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
