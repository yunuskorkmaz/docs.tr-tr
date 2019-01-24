---
title: Bağlantı kurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 6e3a88f7b34c64480d69df1a06a113e392d8fe53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619389"
---
# <a name="establishing-the-connection"></a>Bağlantı kurma
Microsoft SQL Server'a bağlanmak için <xref:System.Data.SqlClient.SqlConnection> SQL Server için .NET Framework veri sağlayıcısı nesnesi. Bir OLE DB veri kaynağına bağlanmak için <xref:System.Data.OleDb.OleDbConnection> nesnesini OLE DB için .NET Framework veri sağlayıcısı. Bir ODBC veri kaynağına bağlanmak için <xref:System.Data.Odbc.OdbcConnection> ODBC için .NET Framework veri sağlayıcısı nesnesi. Bir Oracle veri kaynağına bağlanmak için <xref:System.Data.OracleClient.OracleConnection> Oracle için .NET Framework veri sağlayıcısı nesnesi. Güvenli bir şekilde depolamak ve bağlantı dizelerini almak için bkz. [bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Bağlantı Kapatma  
 Böylece bağlantı havuzuna döndürülebilir kullanmayı bitirdiğiniz zaman, her zaman bağlantı kapatmanızı öneririz. `Using` Visual Basic'te engellemek ya da C# otomatik olarak atar bağlantısı kod bloğu, işlenmeyen bir özel durum durumunda bile çıktığında. Bkz: [using deyimi](~/docs/csharp/language-reference/keywords/using-statement.md) ve [Using deyimi](~/docs/visual-basic/language-reference/statements/using-statement.md) daha fazla bilgi için.  
  
 Ayrıca `Close` veya `Dispose` kullandığınız sağlayıcı için bağlantı nesnesi yöntemleri. Açıkça kapanmamış bağlantıları eklenemez veya havuza geri döner. Örneğin, bir bağlantı, kapsam dışına geçti, ancak bu değil açıkça kapatıldı yalnızca bağlantı havuzuna maksimum havuz boyutuna ulaştı ve bağlantı hala geçerli ise döndürülür. Daha fazla bilgi için [OLE DB, ODBC ve Oracle bağlantı havuzu](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  Çağırmayın `Close` veya `Dispose` üzerinde bir **bağlantı**, **DataReader**, ya da diğer yönetilen nesnelere `Finalize` sınıfınızın yöntemi. İçindeki bir sonlandırıcı yalnızca sınıfınıza doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınızın herhangi bir yönetilmeyen kaynağa sahip değilse içermeyen bir `Finalize` sınıf tanımına yöntemi. Daha fazla bilgi için [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Bağlantı için bağlantı havuzunu döndürüldüğünde gerçekten kapatılmamış çünkü bağlantı öğesinden alınan ya da bağlantı havuzu için döndürülen de sunucuda oturum açma ve kapatma olayları harekete Geçirilmemesi. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>SQL Server'a bağlanma  
 SQL Server için .NET Framework veri sağlayıcısı için OLE DB (ADO) bağlantı dizesi biçimi benzer bir bağlantı dizesi biçimi destekler. Geçerli dize biçimi adları ve değerleri için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> nesne. Ayrıca <xref:System.Data.SqlClient.SqlConnectionStringBuilder> sözdizimsel açıdan geçerli bağlantı dizeleri çalışma zamanında oluşturmak için sınıf. Daha fazla bilgi için [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Aşağıdaki kod örneği, oluşturmak ve bir SQL Server veritabanına bir bağlantı açmak gösterilmektedir.  
  
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
  
### <a name="integrated-security-and-aspnet"></a>Tümleşik Güvenlik'i ve ASP.NET  
 SQL Server'ın tümleşik güvenlik (güvenilen bağlantılar olarak da bilinir) olarak SQL Server'a bağlanırken koruma sağlamaya yardımcı olur, bir kullanıcı kimliği ve bağlantı dizesinde parola kullanıma sunmuyor ve bağlantı kimliğini doğrulamak için önerilen yöntemdir. Tümleşik güvenlik geçerli güvenlik kimliği ya da belirtecinde, yürütme işlemi kullanır. Masaüstü uygulamaları için bu genellikle şu anda oturum açmış kullanıcı kimliğidir.  
  
 ASP.NET uygulamaları için güvenlik kimlik birkaç farklı seçenekten birini için ayarlanabilir. Bir ASP.NET uygulamasını SQL Server'a bağlanırken kullandığı güvenlik kimlik daha iyi anlamak için bkz: [ASP.NET kimliğe bürünme](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET kimlik doğrulaması](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), ve [nasıl yapılır: Erişim SQL Server'ı kullanarak Windows tümleşik güvenliği](https://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Bir OLE DB veri kaynağına bağlanma  
 OLE DB için .NET Framework veri sağlayıcısı (aracılığıyla SQLOLEDB, OLE DB sağlayıcısı için SQL Server), OLE DB kullanılarak kullanıma sunulan veri kaynaklarına bağlantı sağlayan kullanarak **OleDbConnection** nesne.  
  
 OLE DB için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi aşağıdaki istisnalar, ADO kullanılan bağlantı dizesi biçimi aynıdır:  
  
-   **Sağlayıcısı** anahtar sözcüğü gereklidir.  
  
-   **URL**, **uzak sağlayıcıya**, ve **uzak sunucu** anahtar sözcükleri desteklenmez.  
  
 OLE DB bağlantı dizeleri hakkında daha fazla bilgi için bkz. <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> konu. Ayrıca <xref:System.Data.OleDb.OleDbConnectionStringBuilder> bağlantı dizeleri çalışma zamanında oluşturmak için.  
  
> [!NOTE]
>  **OleDbConnection** nesne ayarlama veya belirli bir OLE DB sağlayıcısı için dinamik özellikleri alınırken desteklemez. OLE DB Sağlayıcısı bağlantı dizesinde geçirilebilen özellikleri desteklenir.  
  
 Aşağıdaki kod örneği, oluşturmak ve bir OLE DB veri kaynağı bağlantısı açmak gösterilmektedir.  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a>Evrensel Veri Bağlantısı dosyalarını kullanmayın  
 İlgili bağlantı bilgilerini sağlamak olası bir **OleDbConnection** evrensel veri bağlantısı (UDL) dosyasında; Bununla birlikte, kaçının bunu. UDL dosyaları şifreli olmayan ve düz metin bağlantı dizesi bilgilerini kullanıma sunar. UDL dosyası uygulamanız için bir dış dosya tabanlı kaynak olduğundan, .NET Framework kullanarak korunamıyor.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Bir ODBC veri kaynağına bağlanma  
 ODBC için .NET Framework veri sağlayıcısı ODBC kullanarak kullanıma sunulan veri kaynaklarına bağlantı sağlayan **OdbcConnection** nesne.  
  
 ODBC için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi ODBC bağlantı dizesi biçimi mümkün olduğunca yakın eşleşecek şekilde tasarlanmıştır. Bir ODBC veri kaynağı adı (DSN) da sağlayabilir. Hakkında daha fazla ayrıntı için **OdbcConnection** , bkz: <xref:System.Data.Odbc.OdbcConnection>.  
  
 Aşağıdaki kod örneği, oluşturmak ve bir ODBC veri kaynağı için bir bağlantı açmak gösterilmektedir.  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a>Bir Oracle veri kaynağına bağlanma  
 Oracle için .NET Framework veri sağlayıcısı kullanarak Oracle veri kaynaklarına bağlantı sağlayan **OracleConnection** nesne.  
  
 Oracle için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi, OLE DB sağlayıcısı (MSDAORA) Oracle bağlantı dize biçimi için mümkün olduğunca yakın eşleşecek şekilde tasarlanmıştır. Hakkında daha fazla ayrıntı için **OracleConnection**, bkz: <xref:System.Data.OracleClient.OracleConnection>.  
  
 Aşağıdaki kod örneği, oluşturmak ve bir Oracle veri kaynağı bağlantısı açmak gösterilmektedir.  
  
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
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
