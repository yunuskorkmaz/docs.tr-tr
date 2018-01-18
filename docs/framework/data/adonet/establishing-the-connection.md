---
title: "Bağlantı oluşturma"
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
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5fa47254f97d48dccd13644e2547eaac4ca787bd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="establishing-the-connection"></a>Bağlantı oluşturma
Microsoft SQL Server veritabanına bağlanırken kullanacağı <xref:System.Data.SqlClient.SqlConnection> SQL Server için .NET Framework veri sağlayıcısı nesnesi. Bir OLE DB veri kaynağına bağlanırken kullanacağı <xref:System.Data.OleDb.OleDbConnection> OLE DB için .NET Framework veri sağlayıcısı nesnesi. Bir ODBC veri kaynağına bağlanmak için kullanmak <xref:System.Data.Odbc.OdbcConnection> ODBC için .NET Framework veri sağlayıcısı nesnesi. Bir Oracle veri kaynağına bağlanırken kullanacağı <xref:System.Data.OracleClient.OracleConnection> Oracle için .NET Framework veri sağlayıcısı nesnesi. Güvenli bir şekilde depolamak ve bağlantı dizeleri alma için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="closing-connections"></a>Bağlantı Kapatma  
 Böylece bağlantı havuza geri döndürülebilir, kullanarak bitirdiğinizde, her zaman bağlantı kapatmanızı öneririz. `Using` Visual Basic'te engellemek veya C# otomatik olarak siler bağlantısını kodu işlenmeyen bir özel durum durumunda bile blok çıktığında. Bkz: [deyimiyle](~/docs/csharp/language-reference/keywords/using-statement.md) ve [kullanarak deyimi](~/docs/visual-basic/language-reference/statements/using-statement.md) daha fazla bilgi için.  
  
 Aynı zamanda `Close` veya `Dispose` kullanmakta olduğunuz sağlayıcı için bağlantı nesnesi yöntemleri. Açıkça kapatılmamış bağlantıları eklenemez veya havuza geri döner. Örneğin, kapsam dışı geçti, ancak, değil açıkça kapatıldı bağlantı yalnızca bağlantı havuzu maksimum havuz boyutuna ulaştı ve bağlantı hala geçerli ise döndürülür. Daha fazla bilgi için bkz: [OLE DB, ODBC ve Oracle bağlantı havuzu](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).  
  
> [!NOTE]
>  Çağırmayın `Close` veya `Dispose` üzerinde bir **bağlantı**, **DataReader**, veya diğer yönetilen nesne içinde `Finalize` sınıfınızın yöntemi. Bir Sonlandırıcı, yalnızca sınıfınız doğrudan sahibi yönetilmeyen kaynakları serbest bırakmak. Sınıfınıza yönetilmeyen kaynakları sahip olmadığından, içermeyen bir `Finalize` Sınıf tanımınız yöntemi. Daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
> [!NOTE]
>  Bir bağlantı öğesinden alınan ya da bağlantı havuza geri döner bağlantı havuzu döndürüldüğünde bağlantı gerçekte kapalı olduğundan oturum açma ve kapatma olayları sunucuda oluşturulmaz. Daha fazla bilgi için bkz: [SQL Server bağlantı havuzu (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="connecting-to-sql-server"></a>SQL Server'a bağlanma  
 SQL Server için .NET Framework veri sağlayıcısı için OLE DB (ADO) bağlantı dizesi biçimi benzer bir bağlantı dizesi biçimi destekler. Geçerli bir dize biçim adları ve değerleri için bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> nesnesi. Aynı zamanda <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında sözdizimsel olarak geçerli bir bağlantı dizesi oluşturmak için sınıfı. Daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
 Aşağıdaki kod örneğinde, oluşturmak ve SQL Server veritabanına bir bağlantı açmak gösterilmiştir.  
  
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
  
### <a name="integrated-security-and-aspnet"></a>Tümleşik güvenliği ve ASP.NET  
 SQL Server'ın tümleşik güvenlik (güvenilen bağlantılar olarak da bilinir) olarak SQL Server'a bağlanırken koruma sağlamaya yardımcı olur. bir kullanıcı kimliği ve parola bağlantı dizesindeki kullanıma sunmuyor ve bir bağlantı kimlik doğrulaması için önerilen yöntemdir. Tümleşik güvenlik geçerli güvenlik kimliği veya yürütülen işlemin belirtecini kullanır. Masaüstü uygulamaları için bu genellikle şu anda oturum açmış kullanıcının kimliğini olur.  
  
 ASP.NET uygulamaları için güvenlik kimlik birkaç farklı seçenekler için ayarlanabilir. Bir ASP.NET uygulaması SQL Server'a bağlanırken kullandığı güvenlik kimliği daha iyi anlamak için bkz: [ASP.NET kimliğe bürünme](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET kimlik doğrulaması](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), ve [nasıl yapılır: erişim SQL Sunucu kullanarak Windows tümleşik güvenliği](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).  
  
## <a name="connecting-to-an-ole-db-data-source"></a>Bir OLE DB veri kaynağına bağlanma  
 OLE DB için .NET Framework veri sağlayıcısı (aracılığıyla SQLOLEDB, OLE DB sağlayıcısı için SQL Server), OLE DB kullanılarak kullanıma sunulan veri kaynaklarına bağlantısı sağlayan kullanarak **OleDbConnection** nesnesi.  
  
 OLE DB için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi aşağıdaki istisnalar ADO içinde kullanılan bağlantı dizesi biçimi aynıdır:  
  
-   **Sağlayıcı** anahtar sözcüğü gereklidir.  
  
-   **URL**, **uzak sağlayıcıya**, ve **uzak sunucu** anahtar sözcükleri desteklenmez.  
  
 OLE DB bağlantı dizeleri hakkında daha fazla bilgi için bkz: <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> konu. Aynı zamanda <xref:System.Data.OleDb.OleDbConnectionStringBuilder> bağlantı dizeleri çalışma zamanında oluşturmak için.  
  
> [!NOTE]
>  **OleDbConnection** nesne ayarlama veya dinamik özellikleri için bir OLE DB sağlayıcısı belirli alınırken desteklemez. OLE DB Sağlayıcısı bağlantı dizesinde aktarılabilecek özellikler desteklenir.  
  
 Aşağıdaki kod örneğinde nasıl oluşturulacağı ve bir OLE DB veri kaynağı bir bağlantı açmak gösterilmektedir.  
  
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
 Bağlantı bilgilerini sağlamak olası bir **OleDbConnection** evrensel veri bağlantısı (UDL) dosyasında; Bununla birlikte, kaçının Bunun yapılması. UDL dosyaları şifrelenmez ve düz metin bağlantı dizesi bilgilerini kullanıma sunar. Dış dosya tabanlı kaynak uygulamanıza UDL dosyası olduğu için .NET Framework kullanılarak korunamıyor.  
  
## <a name="connecting-to-an-odbc-data-source"></a>Bir ODBC veri kaynağına bağlanma  
 ODBC için .NET Framework veri sağlayıcısı ODBC kullanarak kullanıma sunulan veri kaynaklarına bağlantısı sağlayan **OdbcConnection** nesnesi.  
  
 ODBC için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi ODBC bağlantı dizesi biçimi mümkün olduğunca yakın eşleşecek şekilde tasarlanmıştır. ODBC veri kaynağı adı (DSN) de sağlayabilir. Daha fazla bilgi için **OdbcConnection** , bkz: <xref:System.Data.Odbc.OdbcConnection>.  
  
 Aşağıdaki kod örneğinde, oluşturmak ve ODBC veri kaynağını bir bağlantı açmak gösterilmiştir.  
  
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
 Oracle için .NET Framework veri sağlayıcısı kullanarak Oracle veri kaynaklarına bağlantısı sağlayan **OracleConnection** nesnesi.  
  
 Oracle için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi OLE DB sağlayıcısı Oracle (MSDAORA) bağlantı dizesi biçimi için mümkün olduğunca yakın eşleşecek şekilde tasarlanmıştır. Daha fazla bilgi için **OracleConnection**, bkz: <xref:System.Data.OracleClient.OracleConnection>.  
  
 Aşağıdaki kod örneğinde, oluşturmak ve Oracle veri kaynağını bir bağlantı açmak gösterilmiştir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)  
 [OLE DB, ODBC ve Oracle Bağlantı Havuzu](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
