---
title: Bağlantı Kurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 4606ecb370b7e85cf5ebd92754471f5253321251
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149667"
---
# <a name="establishing-the-connection"></a>Bağlantı Kurma
Microsoft SQL Server'a bağlanmak <xref:System.Data.SqlClient.SqlConnection> için SQL Server için .NET Framework Data Provider nesnesini kullanın. Bir OLE DB veri kaynağına <xref:System.Data.OleDb.OleDbConnection> bağlanmak için OLE DB için .NET Framework Data Provider nesnesini kullanın. Bir ODBC veri kaynağına bağlanmak <xref:System.Data.Odbc.OdbcConnection> için ODBC için .NET Framework Data Provider nesnesini kullanın. Bir Oracle veri kaynağına bağlanmak <xref:System.Data.OracleClient.OracleConnection> için Oracle için .NET Framework Data Provider nesnesini kullanın. Bağlantı dizelerini güvenli bir şekilde depolamak ve almak için [bağlantı bilgilerini koruma'ya](protecting-connection-information.md)bakın.  
  
## <a name="closing-connections"></a>Bağlantıları Kapatma  
 Bağlantıyı kullanmayı bitirdiğinizde bağlantıyı her zaman kapatmanızı öneririz, böylece bağlantı havuza döndürülebilir. Visual `Using` Basic veya C#'daki blok, işlenmemiş bir özel durum durumunda bile kod bloktan çıktığında bağlantıyı otomatik olarak ortadan kaldırır. Daha fazla bilgi için [Ekstre'yi kullanma](../../../csharp/language-reference/keywords/using-statement.md) ve [İfade](../../../visual-basic/language-reference/statements/using-statement.md) kullanma'ya bakın.  
  
 Ayrıca, kullanmakta `Close` `Dispose` olduğunuz sağlayıcı için bağlantı nesnesinin veya yöntemlerini de kullanabilirsiniz. Açıkça kapatılmayan bağlantılar eklenmeyebilir veya havuza döndürülebilir. Örneğin, kapsam dışına çıkmış ancak açıkça kapatılmamış bir bağlantı yalnızca en büyük havuz boyutuna ulaşılmışsa ve bağlantı hala geçerliyse bağlantı havuzuna döndürülür. Daha fazla bilgi için Bkz. [OLE DB, ODBC ve Oracle Connection Pooling.](ole-db-odbc-and-oracle-connection-pooling.md)  
  
> [!NOTE]
> Bağlantı, `Close` **DataReader** **Connection**veya `Dispose` sınıfınızın yöntemindeki başka bir yönetilen `Finalize` nesneyi aramayın veya bağlantıda aramayın. Sonlandırıcıda, yalnızca sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınız yönetilmeyen kaynaklara sahip değilse, sınıf `Finalize` tanımınıza bir yöntem eklemeyin. Daha fazla bilgi için [Çöp Toplama'ya](../../../standard/garbage-collection/index.md)bakın.  
  
> [!NOTE]
> Bağlantı bağlantı havuzundan getirilen veya bağlantı havuzuna döndürüldüğünde oturum açma ve oturum açma olayları sunucuda yükseltilmez, çünkü bağlantı bağlantı havuzuna döndürüldüğünde aslında kapalı değildir. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md)adresine bakın.  
  
## <a name="connecting-to-sql-server"></a>SQL Server'a bağlanma  
 SQL Server için .NET Framework Data Provider, OLE DB (ADO) bağlantı dize biçimine benzer bir bağlantı dize biçimini destekler. Geçerli dize biçimi adları ve <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> değerleri <xref:System.Data.SqlClient.SqlConnection> için nesnenin özelliğine bakın. <xref:System.Data.SqlClient.SqlConnectionStringBuilder> Çalışma zamanında sözdizimi olarak geçerli bağlantı dizeleri oluşturmak için sınıfı da kullanabilirsiniz. Daha fazla bilgi için [Bağlantı Dize Oluşturucuları'na](connection-string-builders.md)bakın.  
  
 Aşağıdaki kod örneği, bir SQL Server veritabanına bağlantı oluşturmanın ve nasıl açılacağını gösterir.  
  
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
  
### <a name="integrated-security-and-aspnet"></a>Entegre Güvenlik ve ASP.NET  
 SQL Server tümleşik güvenliği (güvenilir bağlantılar olarak da bilinir), bağlantı dizesinde bir kullanıcı kimliği ve parola açığa çıkarmadığı ve bağlantının kimliğini doğrulamak için önerilen yöntem olduğundan, SQL Server'a bağlanırken koruma sağlamaya yardımcı olur. Tümleşik güvenlik, yürütme işleminin geçerli güvenlik kimliğini veya belirtecisini kullanır. Masaüstü uygulamaları için bu, genellikle şu anda oturum açmış olan kullanıcının kimliğidir.  
  
 ASP.NET uygulamalarının güvenlik kimliği birkaç farklı seçenekten birine ayarlanabilir. Bir ASP.NET uygulamasının SQL Server'a bağlanırken kullandığı güvenlik kimliğini daha iyi anlamak için, [ASP.NET Kimliğe Bürünme](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [kimlik doğrulama ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))ve Windows [Tümleşik Güvenlik Kullanarak SQL Server'a Nasıl](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100))Erişilir'e bakın.  
  
## <a name="connecting-to-an-ole-db-data-source"></a>OLE DB Veri Kaynağına Bağlanma  
 OLE DB için .NET Framework Data Provider, **OLE** DB (SQL Server için OLE DB Sağlayıcısı) kullanılarak ortaya çıkarılan veri kaynaklarına Bağlantı sağlar.  
  
 OLE DB için .NET Framework Data Provider için bağlantı dize biçimi, aşağıdaki istisnalar dışında ADO'da kullanılan bağlantı dize biçimiyle aynıdır:  
  
- **Sağlayıcı** anahtar sözcüğü gereklidir.  
  
- **URL,** **Uzak Sağlayıcı**ve **Uzak Sunucu** anahtar kelimeleri desteklenmez.  
  
 OLE DB bağlantı dizeleri hakkında daha <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> fazla bilgi için konuya bakın. Ayrıca çalışma zamanında <xref:System.Data.OleDb.OleDbConnectionStringBuilder> bağlantı dizeleri oluşturmak için kullanabilirsiniz.  
  
> [!NOTE]
> **OleDbConnection** nesnesi, ole DB sağlayıcısına özgü dinamik özellikleri ayarlamayı veya alma özelliğini desteklemez. Yalnızca OLE DB sağlayıcısının bağlantı dizesinde geçirilebilen özellikler desteklenir.  
  
 Aşağıdaki kod örneği, Bir OLE DB veri kaynağına nasıl bağlantı oluşturulup açılacağını gösterir.  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a>Evrensel Veri Bağlantısı Dosyalarını Kullanmayın  
 Evrensel Veri Bağlantısı (UDL) dosyasında bir **OleDbConnection** bağlantısı için bağlantı bilgileri sağlamak mümkündür; ancak bunu yapmaktan kaçınmalısınız. UDL dosyaları şifrelenmez ve bağlantı dize bilgilerini açık metinde açığa çıkarır. UDL dosyası uygulamanız için harici bir dosya tabanlı kaynak olduğundan, .NET Framework kullanılarak güvenli hale alınamaz.  
  
## <a name="connecting-to-an-odbc-data-source"></a>ODBC Veri Kaynağına Bağlanma  
 ODBC için .NET Framework Data Provider, **OdbcConnection** nesnesini kullanarak ODBC kullanılarak açığa çıkarılan veri kaynaklarına bağlantı sağlar.  
  
 ODBC için .NET Framework Data Provider için bağlantı dizesi biçimi, ODBC bağlantı dizesi biçimiyle mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır. Ayrıca bir ODBC veri kaynağı adı (DSN) da sağlayabilirsiniz. **OdbcConnection** hakkında daha fazla ayrıntı <xref:System.Data.Odbc.OdbcConnection>için bkz.  
  
 Aşağıdaki kod örneği, bir ODBC veri kaynağına nasıl bağlantı oluşturulup açılacağını gösterir.  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a>Bir Oracle Veri Kaynağına Bağlanma  
 Oracle için .NET Framework Data Provider, **OracleConnection** nesnesini kullanarak Oracle veri kaynaklarına bağlantı sağlar.  
  
 Oracle için .NET Framework Data Provider için bağlantı dizesi biçimi, Oracle için OLE DB Sağlayıcısı (MSDAORA) bağlantı dize biçimini mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır. **OracleConnection**hakkında daha fazla ayrıntı <xref:System.Data.OracleClient.OracleConnection>için bkz.  
  
 Aşağıdaki kod örneği, oracle veri kaynağına nasıl bağlantı oluşturulup açılacağı gösteriş verilmiştir.  
  
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

- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [Bağlantı Dizeleri](connection-strings.md)
- [OLE DB, ODBC ve Oracle Bağlantı Havuzu](ole-db-odbc-and-oracle-connection-pooling.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
