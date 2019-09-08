---
title: Bağlantı Kurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: c4e782b670bfc74a651ce38457c05d9acfcf0e8c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783900"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="c4647-102">Bağlantı Kurma</span><span class="sxs-lookup"><span data-stu-id="c4647-102">Establishing the Connection</span></span>
<span data-ttu-id="c4647-103">Microsoft SQL Server bağlanmak için, SQL Server için .NET Framework <xref:System.Data.SqlClient.SqlConnection> veri sağlayıcısı nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4647-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="c4647-104">Bir OLE DB veri kaynağına bağlanmak için, OLE DB için .NET Framework <xref:System.Data.OleDb.OleDbConnection> veri sağlayıcısı nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4647-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="c4647-105">ODBC veri kaynağına bağlanmak için, ODBC için .NET Framework veri sağlayıcısı <xref:System.Data.Odbc.OdbcConnection> nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4647-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="c4647-106">Oracle veri kaynağına bağlanmak için, Oracle için .NET Framework veri sağlayıcısı <xref:System.Data.OracleClient.OracleConnection> nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4647-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="c4647-107">Bağlantı dizelerini güvenli bir şekilde depolamak ve almak için bkz. [bağlantı bilgilerini koruma](protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="c4647-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="c4647-108">Bağlantıları kapatma</span><span class="sxs-lookup"><span data-stu-id="c4647-108">Closing Connections</span></span>  
 <span data-ttu-id="c4647-109">Bağlantıyı kullanarak her zaman bağlantıyı kapatmanızı öneririz, böylece bağlantı havuza geri döndürülebilecek.</span><span class="sxs-lookup"><span data-stu-id="c4647-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="c4647-110">İşlenmemiş bir özel durum söz C# konusu olduğunda bile, kod bloktan çıktığında Visual Basic veya bağlantı otomatik olarak ortadan kaldırır. `Using`</span><span class="sxs-lookup"><span data-stu-id="c4647-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="c4647-111">Daha fazla bilgi için bkz. [using deyimleri](../../../csharp/language-reference/keywords/using-statement.md) ve [using deyimleri](../../../visual-basic/language-reference/statements/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="c4647-111">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="c4647-112">Ayrıca, `Close` kullanmakta olduğunuz sağlayıcı için `Dispose` bağlantı nesnesinin veya yöntemlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4647-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="c4647-113">Açıkça kapatılmayan bağlantılar, havuza eklenmeyebilir veya havuza döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="c4647-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="c4647-114">Örneğin, kapsam dışına çıkan ancak açıkça kapatılmayan bir bağlantı yalnızca en büyük havuz boyutuna ulaşılmışsa ve bağlantı hala geçerliyse bağlantı havuzuna döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c4647-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="c4647-115">Daha fazla bilgi için bkz. [OLE DB, ODBC ve Oracle bağlantı havuzu](ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="c4647-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4647-116">Sınıfınızın `Finalize` yönteminde veya `Close` `Dispose` bir **bağlantı**, bir **DataReader**veya başka bir yönetilen nesne çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="c4647-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="c4647-117">Sonlandırıcıda yalnızca, sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="c4647-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="c4647-118">Sınıfınız hiçbir yönetilmeyen kaynağa sahip değilse, sınıf tanımınıza bir `Finalize` Yöntem eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="c4647-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="c4647-119">Daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="c4647-119">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4647-120">Bağlantı, bağlantı havuzuna döndürüldüğünden bağlantı, gerçekten kapanmadığı için, bağlantı havuzundan bir bağlantı getirilirken ya da geri döndürülene kadar sunucuda oturum açma ve oturum kapatma olayları oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="c4647-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="c4647-121">Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="c4647-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="c4647-122">SQL Server bağlanılıyor</span><span class="sxs-lookup"><span data-stu-id="c4647-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="c4647-123">SQL Server için .NET Framework Veri Sağlayıcısı, OLE DB (ADO) bağlantı dizesi biçimine benzer bir bağlantı dizesi biçimini destekler.</span><span class="sxs-lookup"><span data-stu-id="c4647-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="c4647-124">Geçerli dize biçimi adları ve değerleri için, bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> . <xref:System.Data.SqlClient.SqlConnection> nesnesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="c4647-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="c4647-125">Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında sözdizimi geçerli bağlantı dizeleri oluşturmak için sınıfını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4647-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="c4647-126">Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="c4647-126">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="c4647-127">Aşağıdaki kod örneği, bir SQL Server veritabanına bağlantı oluşturmayı ve açmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4647-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="c4647-128">Tümleşik güvenlik ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c4647-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="c4647-129">SQL Server tümleşik güvenlik (güvenilen bağlantı olarak da bilinir), bağlantı dizesinde kullanıcı KIMLIĞI ve parola sunmaz ve bir bağlantının kimlik doğrulaması için önerilen yöntem olduğundan, SQL Server bağlanırken koruma sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c4647-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="c4647-130">Tümleşik güvenlik, yürütme işleminin geçerli güvenlik kimliğini veya belirtecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4647-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="c4647-131">Masaüstü uygulamaları için bu genellikle şu anda oturum açmış olan kullanıcının kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="c4647-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="c4647-132">ASP.NET uygulamaları için güvenlik kimliği, birkaç farklı seçenekten birine ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c4647-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="c4647-133">Bir ASP.NET uygulamasının SQL Server bağlanırken kullandığı güvenlik kimliğini daha iyi anlamak için bkz. [ASP.NET Kimliğe bürünme](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100))ve [nasıl yapılır: Windows tümleşik güvenliği](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100))kullanarak SQL Server erişin.</span><span class="sxs-lookup"><span data-stu-id="c4647-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](https://docs.microsoft.com/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](https://docs.microsoft.com/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="c4647-134">OLE DB veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="c4647-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="c4647-135">OLE DB için .NET Framework Veri Sağlayıcısı, **OleDbConnection** nesnesi kullanılarak OLE DB (örneğin, OLE DB Için SQL Server sağlayıcısı) kullanılarak sunulan veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4647-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="c4647-136">OLE DB için .NET Framework Veri Sağlayıcısı bağlantı dizesi biçimi, aşağıdaki özel durumlarla birlikte ADO 'da kullanılan bağlantı dizesi biçimiyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="c4647-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="c4647-137">**Sağlayıcı** anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c4647-137">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="c4647-138">**URL**, **uzak sağlayıcı**ve **uzak sunucu** anahtar sözcükleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c4647-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="c4647-139">OLE DB bağlantı dizeleri hakkında daha fazla bilgi için konusuna bakın <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> .</span><span class="sxs-lookup"><span data-stu-id="c4647-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="c4647-140">Ayrıca, <xref:System.Data.OleDb.OleDbConnectionStringBuilder> çalışma zamanında bağlantı dizeleri oluşturmak için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4647-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4647-141">**OleDbConnection** nesnesi bir OLE DB sağlayıcısına özgü dinamik özellikleri ayarlamayı veya almayı desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="c4647-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="c4647-142">Yalnızca OLE DB sağlayıcısı için bağlantı dizesinde geçirilebilecek özellikler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c4647-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="c4647-143">Aşağıdaki kod örneği, bir OLE DB veri kaynağına bağlantı oluşturmayı ve açmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4647-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="c4647-144">Evrensel veri bağlantısı dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="c4647-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="c4647-145">Bir evrensel veri bağlantısı (UDL) dosyasında bir **OleDbConnection** için bağlantı bilgilerini sağlamak mümkündür; Ancak bunu yapmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="c4647-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="c4647-146">UDL dosyaları şifrelenmez ve bağlantı dizesi bilgilerini şifresiz metin olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="c4647-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="c4647-147">Bir UDL dosyası uygulamanıza yönelik dış dosya tabanlı bir kaynak olduğundan .NET Framework kullanılarak güvenliği alınamaz.</span><span class="sxs-lookup"><span data-stu-id="c4647-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="c4647-148">ODBC veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="c4647-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="c4647-149">ODBC için .NET Framework Veri Sağlayıcısı, **OdbcConnection** NESNESI kullanılarak ODBC kullanılarak sunulan veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4647-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="c4647-150">ODBC için .NET Framework Veri Sağlayıcısı için bağlantı dizesi biçimi, ODBC bağlantı dizesi biçimiyle mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4647-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="c4647-151">Ayrıca bir ODBC veri kaynağı adı (DSN) sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4647-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="c4647-152">**OdbcConnection** hakkında daha fazla ayrıntı için bkz <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="c4647-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="c4647-153">Aşağıdaki kod örneği, bir ODBC veri kaynağı ile bağlantı oluşturmayı ve açmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4647-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="c4647-154">Oracle veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="c4647-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="c4647-155">Oracle için .NET Framework Veri Sağlayıcısı, **OracleConnection** nesnesini kullanarak Oracle veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4647-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="c4647-156">Oracle için .NET Framework Veri Sağlayıcısı bağlantı dizesi biçimi, Oracle (MSDAORA) bağlantı dizesi biçimi için OLE DB sağlayıcısı tarafından mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4647-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="c4647-157">**OracleConnection**hakkında daha fazla ayrıntı için bkz <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="c4647-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="c4647-158">Aşağıdaki kod örneği, bir Oracle veri kaynağına bir bağlantının nasıl oluşturulduğunu ve açılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4647-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4647-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4647-159">See also</span></span>

- [<span data-ttu-id="c4647-160">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="c4647-160">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="c4647-161">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="c4647-161">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="c4647-162">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="c4647-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="c4647-163">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c4647-163">ADO.NET Overview</span></span>](ado-net-overview.md)
