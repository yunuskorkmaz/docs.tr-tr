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
# <a name="establishing-the-connection"></a><span data-ttu-id="1c279-102">Bağlantı Kurma</span><span class="sxs-lookup"><span data-stu-id="1c279-102">Establishing the Connection</span></span>
<span data-ttu-id="1c279-103">Microsoft SQL Server'a bağlanmak <xref:System.Data.SqlClient.SqlConnection> için SQL Server için .NET Framework Data Provider nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c279-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="1c279-104">Bir OLE DB veri kaynağına <xref:System.Data.OleDb.OleDbConnection> bağlanmak için OLE DB için .NET Framework Data Provider nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c279-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="1c279-105">Bir ODBC veri kaynağına bağlanmak <xref:System.Data.Odbc.OdbcConnection> için ODBC için .NET Framework Data Provider nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c279-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="1c279-106">Bir Oracle veri kaynağına bağlanmak <xref:System.Data.OracleClient.OracleConnection> için Oracle için .NET Framework Data Provider nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c279-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="1c279-107">Bağlantı dizelerini güvenli bir şekilde depolamak ve almak için [bağlantı bilgilerini koruma'ya](protecting-connection-information.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="1c279-108">Bağlantıları Kapatma</span><span class="sxs-lookup"><span data-stu-id="1c279-108">Closing Connections</span></span>  
 <span data-ttu-id="1c279-109">Bağlantıyı kullanmayı bitirdiğinizde bağlantıyı her zaman kapatmanızı öneririz, böylece bağlantı havuza döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="1c279-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="1c279-110">Visual `Using` Basic veya C#'daki blok, işlenmemiş bir özel durum durumunda bile kod bloktan çıktığında bağlantıyı otomatik olarak ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1c279-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="1c279-111">Daha fazla bilgi için [Ekstre'yi kullanma](../../../csharp/language-reference/keywords/using-statement.md) ve [İfade](../../../visual-basic/language-reference/statements/using-statement.md) kullanma'ya bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-111">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="1c279-112">Ayrıca, kullanmakta `Close` `Dispose` olduğunuz sağlayıcı için bağlantı nesnesinin veya yöntemlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c279-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="1c279-113">Açıkça kapatılmayan bağlantılar eklenmeyebilir veya havuza döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="1c279-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="1c279-114">Örneğin, kapsam dışına çıkmış ancak açıkça kapatılmamış bir bağlantı yalnızca en büyük havuz boyutuna ulaşılmışsa ve bağlantı hala geçerliyse bağlantı havuzuna döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1c279-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="1c279-115">Daha fazla bilgi için Bkz. [OLE DB, ODBC ve Oracle Connection Pooling.](ole-db-odbc-and-oracle-connection-pooling.md)</span><span class="sxs-lookup"><span data-stu-id="1c279-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c279-116">Bağlantı, `Close` **DataReader** **Connection**veya `Dispose` sınıfınızın yöntemindeki başka bir yönetilen `Finalize` nesneyi aramayın veya bağlantıda aramayın.</span><span class="sxs-lookup"><span data-stu-id="1c279-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="1c279-117">Sonlandırıcıda, yalnızca sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="1c279-118">Sınıfınız yönetilmeyen kaynaklara sahip değilse, sınıf `Finalize` tanımınıza bir yöntem eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="1c279-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="1c279-119">Daha fazla bilgi için [Çöp Toplama'ya](../../../standard/garbage-collection/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-119">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c279-120">Bağlantı bağlantı havuzundan getirilen veya bağlantı havuzuna döndürüldüğünde oturum açma ve oturum açma olayları sunucuda yükseltilmez, çünkü bağlantı bağlantı havuzuna döndürüldüğünde aslında kapalı değildir.</span><span class="sxs-lookup"><span data-stu-id="1c279-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="1c279-121">Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md)adresine bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="1c279-122">SQL Server'a bağlanma</span><span class="sxs-lookup"><span data-stu-id="1c279-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="1c279-123">SQL Server için .NET Framework Data Provider, OLE DB (ADO) bağlantı dize biçimine benzer bir bağlantı dize biçimini destekler.</span><span class="sxs-lookup"><span data-stu-id="1c279-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="1c279-124">Geçerli dize biçimi adları ve <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> değerleri <xref:System.Data.SqlClient.SqlConnection> için nesnenin özelliğine bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="1c279-125"><xref:System.Data.SqlClient.SqlConnectionStringBuilder> Çalışma zamanında sözdizimi olarak geçerli bağlantı dizeleri oluşturmak için sınıfı da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c279-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="1c279-126">Daha fazla bilgi için [Bağlantı Dize Oluşturucuları'na](connection-string-builders.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-126">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="1c279-127">Aşağıdaki kod örneği, bir SQL Server veritabanına bağlantı oluşturmanın ve nasıl açılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c279-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="1c279-128">Entegre Güvenlik ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1c279-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="1c279-129">SQL Server tümleşik güvenliği (güvenilir bağlantılar olarak da bilinir), bağlantı dizesinde bir kullanıcı kimliği ve parola açığa çıkarmadığı ve bağlantının kimliğini doğrulamak için önerilen yöntem olduğundan, SQL Server'a bağlanırken koruma sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1c279-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="1c279-130">Tümleşik güvenlik, yürütme işleminin geçerli güvenlik kimliğini veya belirtecisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c279-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="1c279-131">Masaüstü uygulamaları için bu, genellikle şu anda oturum açmış olan kullanıcının kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="1c279-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="1c279-132">ASP.NET uygulamalarının güvenlik kimliği birkaç farklı seçenekten birine ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1c279-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="1c279-133">Bir ASP.NET uygulamasının SQL Server'a bağlanırken kullandığı güvenlik kimliğini daha iyi anlamak için, [ASP.NET Kimliğe Bürünme](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [kimlik doğrulama ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))ve Windows [Tümleşik Güvenlik Kullanarak SQL Server'a Nasıl](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100))Erişilir'e bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="1c279-134">OLE DB Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="1c279-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="1c279-135">OLE DB için .NET Framework Data Provider, **OLE** DB (SQL Server için OLE DB Sağlayıcısı) kullanılarak ortaya çıkarılan veri kaynaklarına Bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c279-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="1c279-136">OLE DB için .NET Framework Data Provider için bağlantı dize biçimi, aşağıdaki istisnalar dışında ADO'da kullanılan bağlantı dize biçimiyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="1c279-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="1c279-137">**Sağlayıcı** anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1c279-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="1c279-138">**URL,** **Uzak Sağlayıcı**ve **Uzak Sunucu** anahtar kelimeleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1c279-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="1c279-139">OLE DB bağlantı dizeleri hakkında daha <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> fazla bilgi için konuya bakın.</span><span class="sxs-lookup"><span data-stu-id="1c279-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="1c279-140">Ayrıca çalışma zamanında <xref:System.Data.OleDb.OleDbConnectionStringBuilder> bağlantı dizeleri oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c279-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c279-141">**OleDbConnection** nesnesi, ole DB sağlayıcısına özgü dinamik özellikleri ayarlamayı veya alma özelliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1c279-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="1c279-142">Yalnızca OLE DB sağlayıcısının bağlantı dizesinde geçirilebilen özellikler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1c279-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="1c279-143">Aşağıdaki kod örneği, Bir OLE DB veri kaynağına nasıl bağlantı oluşturulup açılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c279-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="1c279-144">Evrensel Veri Bağlantısı Dosyalarını Kullanmayın</span><span class="sxs-lookup"><span data-stu-id="1c279-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="1c279-145">Evrensel Veri Bağlantısı (UDL) dosyasında bir **OleDbConnection** bağlantısı için bağlantı bilgileri sağlamak mümkündür; ancak bunu yapmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1c279-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="1c279-146">UDL dosyaları şifrelenmez ve bağlantı dize bilgilerini açık metinde açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="1c279-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="1c279-147">UDL dosyası uygulamanız için harici bir dosya tabanlı kaynak olduğundan, .NET Framework kullanılarak güvenli hale alınamaz.</span><span class="sxs-lookup"><span data-stu-id="1c279-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="1c279-148">ODBC Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="1c279-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="1c279-149">ODBC için .NET Framework Data Provider, **OdbcConnection** nesnesini kullanarak ODBC kullanılarak açığa çıkarılan veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c279-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="1c279-150">ODBC için .NET Framework Data Provider için bağlantı dizesi biçimi, ODBC bağlantı dizesi biçimiyle mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c279-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="1c279-151">Ayrıca bir ODBC veri kaynağı adı (DSN) da sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c279-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="1c279-152">**OdbcConnection** hakkında daha fazla ayrıntı <xref:System.Data.Odbc.OdbcConnection>için bkz.</span><span class="sxs-lookup"><span data-stu-id="1c279-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="1c279-153">Aşağıdaki kod örneği, bir ODBC veri kaynağına nasıl bağlantı oluşturulup açılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c279-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="1c279-154">Bir Oracle Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="1c279-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="1c279-155">Oracle için .NET Framework Data Provider, **OracleConnection** nesnesini kullanarak Oracle veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c279-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="1c279-156">Oracle için .NET Framework Data Provider için bağlantı dizesi biçimi, Oracle için OLE DB Sağlayıcısı (MSDAORA) bağlantı dize biçimini mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c279-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="1c279-157">**OracleConnection**hakkında daha fazla ayrıntı <xref:System.Data.OracleClient.OracleConnection>için bkz.</span><span class="sxs-lookup"><span data-stu-id="1c279-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="1c279-158">Aşağıdaki kod örneği, oracle veri kaynağına nasıl bağlantı oluşturulup açılacağı gösteriş verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c279-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c279-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c279-159">See also</span></span>

- [<span data-ttu-id="1c279-160">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="1c279-160">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="1c279-161">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="1c279-161">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="1c279-162">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="1c279-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="1c279-163">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c279-163">ADO.NET Overview</span></span>](ado-net-overview.md)
