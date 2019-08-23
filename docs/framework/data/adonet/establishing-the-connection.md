---
title: Bağlantı Kurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: b4a61306cd9b61f84eff16ffaac302317b6dfe44
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959186"
---
# <a name="establishing-the-connection"></a>Bağlantı Kurma
Microsoft SQL Server bağlanmak için, SQL Server için .NET Framework <xref:System.Data.SqlClient.SqlConnection> veri sağlayıcısı nesnesini kullanın. Bir OLE DB veri kaynağına bağlanmak için, OLE DB için .NET Framework <xref:System.Data.OleDb.OleDbConnection> veri sağlayıcısı nesnesini kullanın. ODBC veri kaynağına bağlanmak için, ODBC için .NET Framework veri sağlayıcısı <xref:System.Data.Odbc.OdbcConnection> nesnesini kullanın. Oracle veri kaynağına bağlanmak için, Oracle için .NET Framework veri sağlayıcısı <xref:System.Data.OracleClient.OracleConnection> nesnesini kullanın. Bağlantı dizelerini güvenli bir şekilde depolamak ve almak için bkz. [bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Bağlantıları kapatma  
 Bağlantıyı kullanarak her zaman bağlantıyı kapatmanızı öneririz, böylece bağlantı havuza geri döndürülebilecek. İşlenmemiş bir özel durum söz C# konusu olduğunda bile, kod bloktan çıktığında Visual Basic veya bağlantı otomatik olarak ortadan kaldırır. `Using` Daha fazla bilgi için bkz. [using deyimleri](../../../csharp/language-reference/keywords/using-statement.md) ve [using deyimleri](../../../visual-basic/language-reference/statements/using-statement.md) .  
  
 Ayrıca, `Close` kullanmakta olduğunuz sağlayıcı için `Dispose` bağlantı nesnesinin veya yöntemlerini de kullanabilirsiniz. Açıkça kapatılmayan bağlantılar, havuza eklenmeyebilir veya havuza döndürülemez. Örneğin, kapsam dışına çıkan ancak açıkça kapatılmayan bir bağlantı yalnızca en büyük havuz boyutuna ulaşılmışsa ve bağlantı hala geçerliyse bağlantı havuzuna döndürülür. Daha fazla bilgi için bkz. [OLE DB, ODBC ve Oracle bağlantı havuzu](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
> Sınıfınızın `Finalize` yönteminde veya `Close` `Dispose` bir **bağlantı**, bir **DataReader**veya başka bir yönetilen nesne çağırmayın. Sonlandırıcıda yalnızca, sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınız hiçbir yönetilmeyen kaynağa sahip değilse, sınıf tanımınıza bir `Finalize` Yöntem eklemeyin. Daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> Bağlantı, bağlantı havuzuna döndürüldüğünden bağlantı, gerçekten kapanmadığı için, bağlantı havuzundan bir bağlantı getirilirken ya da geri döndürülene kadar sunucuda oturum açma ve oturum kapatma olayları oluşturulmaz. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>SQL Server bağlanılıyor  
 SQL Server için .NET Framework Veri Sağlayıcısı, OLE DB (ADO) bağlantı dizesi biçimine benzer bir bağlantı dizesi biçimini destekler. Geçerli dize biçimi adları ve değerleri için, bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> . <xref:System.Data.SqlClient.SqlConnection> nesnesinin özelliği. Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında sözdizimi geçerli bağlantı dizeleri oluşturmak için sınıfını da kullanabilirsiniz. Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Aşağıdaki kod örneği, bir SQL Server veritabanına bağlantı oluşturmayı ve açmayı gösterir.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### <a name="integrated-security-and-aspnet"></a>Tümleşik güvenlik ve ASP.NET  
 SQL Server tümleşik güvenlik (güvenilen bağlantı olarak da bilinir), bağlantı dizesinde kullanıcı KIMLIĞI ve parola sunmaz ve bir bağlantının kimlik doğrulaması için önerilen yöntem olduğundan, SQL Server bağlanırken koruma sağlamaya yardımcı olur. Tümleşik güvenlik, yürütme işleminin geçerli güvenlik kimliğini veya belirtecini kullanır. Masaüstü uygulamaları için bu genellikle şu anda oturum açmış olan kullanıcının kimliğidir.  
  
 ASP.NET uygulamaları için güvenlik kimliği, birkaç farklı seçenekten birine ayarlanabilir. Bir ASP.NET uygulamasının SQL Server bağlanırken kullandığı güvenlik kimliğini daha iyi anlamak için bkz. [ASP.NET Kimliğe bürünme](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))ve [nasıl yapılır: Windows tümleşik güvenliği](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100))kullanarak SQL Server erişin.  
  
## <a name="connecting-to-an-ole-db-data-source"></a>OLE DB veri kaynağına bağlanma  
 OLE DB için .NET Framework Veri Sağlayıcısı, **OleDbConnection** nesnesi kullanılarak OLE DB (örneğin, OLE DB Için SQL Server sağlayıcısı) kullanılarak sunulan veri kaynaklarına bağlantı sağlar.  
  
 OLE DB için .NET Framework Veri Sağlayıcısı bağlantı dizesi biçimi, aşağıdaki özel durumlarla birlikte ADO 'da kullanılan bağlantı dizesi biçimiyle aynıdır:  
  
- **Sağlayıcı** anahtar sözcüğü gereklidir.  
  
- **URL**, **uzak sağlayıcı**ve **uzak sunucu** anahtar sözcükleri desteklenmez.  
  
 OLE DB bağlantı dizeleri hakkında daha fazla bilgi için konusuna bakın <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> . Ayrıca, <xref:System.Data.OleDb.OleDbConnectionStringBuilder> çalışma zamanında bağlantı dizeleri oluşturmak için öğesini de kullanabilirsiniz.  
  
> [!NOTE]
> **OleDbConnection** nesnesi bir OLE DB sağlayıcısına özgü dinamik özellikleri ayarlamayı veya almayı desteklemiyor. Yalnızca OLE DB sağlayıcısı için bağlantı dizesinde geçirilebilecek özellikler desteklenir.  
  
 Aşağıdaki kod örneği, bir OLE DB veri kaynağına bağlantı oluşturmayı ve açmayı gösterir.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="do-not-use-universal-data-link-files"></a>Evrensel veri bağlantısı dosyalarını kullanma  
 Bir evrensel veri bağlantısı (UDL) dosyasında bir **OleDbConnection** için bağlantı bilgilerini sağlamak mümkündür; Ancak bunu yapmaktan kaçınmalısınız. UDL dosyaları şifrelenmez ve bağlantı dizesi bilgilerini şifresiz metin olarak kullanıma sunar. Bir UDL dosyası uygulamanıza yönelik dış dosya tabanlı bir kaynak olduğundan .NET Framework kullanılarak güvenliği alınamaz.  
  
## <a name="connecting-to-an-odbc-data-source"></a>ODBC veri kaynağına bağlanma  
 ODBC için .NET Framework Veri Sağlayıcısı, **OdbcConnection** NESNESI kullanılarak ODBC kullanılarak sunulan veri kaynaklarına bağlantı sağlar.  
  
 ODBC için .NET Framework Veri Sağlayıcısı için bağlantı dizesi biçimi, ODBC bağlantı dizesi biçimiyle mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır. Ayrıca bir ODBC veri kaynağı adı (DSN) sağlayabilirsiniz. **OdbcConnection** hakkında daha fazla ayrıntı için bkz <xref:System.Data.Odbc.OdbcConnection>.  
  
 Aşağıdaki kod örneği, bir ODBC veri kaynağı ile bağlantı oluşturmayı ve açmayı gösterir.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## <a name="connecting-to-an-oracle-data-source"></a>Oracle veri kaynağına bağlanma  
 Oracle için .NET Framework Veri Sağlayıcısı, **OracleConnection** nesnesini kullanarak Oracle veri kaynaklarına bağlantı sağlar.  
  
 Oracle için .NET Framework Veri Sağlayıcısı bağlantı dizesi biçimi, Oracle (MSDAORA) bağlantı dizesi biçimi için OLE DB sağlayıcısı tarafından mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır. **OracleConnection**hakkında daha fazla ayrıntı için bkz <xref:System.Data.OracleClient.OracleConnection>.  
  
 Aşağıdaki kod örneği, bir Oracle veri kaynağına bir bağlantının nasıl oluşturulduğunu ve açılacağını gösterir.  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)
- [OLE DB, ODBC ve Oracle Bağlantı Havuzu](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
