---
description: 'Hakkında daha fazla bilgi edinin: bağlantı kurma'
title: Bağlantı Kurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: e7f8c837476a678f003eb0477934bb8bd08fd896
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724342"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="9a4b0-103">Bağlantı Kurma</span><span class="sxs-lookup"><span data-stu-id="9a4b0-103">Establishing the Connection</span></span>

<span data-ttu-id="9a4b0-104">Microsoft SQL Server bağlanmak için, <xref:System.Data.SqlClient.SqlConnection> SQL Server için .NET Framework veri sağlayıcısı nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-104">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="9a4b0-105">Bir OLE DB veri kaynağına bağlanmak için, <xref:System.Data.OleDb.OleDbConnection> OLE DB için .NET Framework veri sağlayıcısı nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-105">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="9a4b0-106">ODBC veri kaynağına bağlanmak için, <xref:System.Data.Odbc.OdbcConnection> ODBC için .NET Framework veri sağlayıcısı nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-106">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="9a4b0-107">Oracle veri kaynağına bağlanmak için, <xref:System.Data.OracleClient.OracleConnection> Oracle için .NET Framework veri sağlayıcısı nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-107">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="9a4b0-108">Bağlantı dizelerini güvenli bir şekilde depolamak ve almak için bkz. [bağlantı bilgilerini koruma](protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9a4b0-108">For securely storing and retrieving connection strings, see [Protecting Connection Information](protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="9a4b0-109">Bağlantıları kapatma</span><span class="sxs-lookup"><span data-stu-id="9a4b0-109">Closing Connections</span></span>  

 <span data-ttu-id="9a4b0-110">Bağlantıyı kullanarak her zaman bağlantıyı kapatmanızı öneririz, böylece bağlantı havuza geri döndürülebilecek.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-110">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="9a4b0-111">`Using`Visual Basic veya C# ' deki blok, işlenmemiş bir özel durum söz konusu olduğunda bile kod bloğundan çıktığında otomatik olarak bağlantıyı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-111">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="9a4b0-112">Daha fazla bilgi için bkz. [using deyimleri](../../../csharp/language-reference/keywords/using-statement.md) ve [using deyimleri](../../../visual-basic/language-reference/statements/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="9a4b0-112">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) and [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="9a4b0-113">Ayrıca, `Close` `Dispose` kullanmakta olduğunuz sağlayıcı için bağlantı nesnesinin veya yöntemlerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-113">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="9a4b0-114">Açıkça kapatılmayan bağlantılar, havuza eklenmeyebilir veya havuza döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-114">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="9a4b0-115">Örneğin, kapsam dışına çıkan ancak açıkça kapatılmayan bir bağlantı yalnızca en büyük havuz boyutuna ulaşılmışsa ve bağlantı hala geçerliyse bağlantı havuzuna döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-115">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="9a4b0-116">Daha fazla bilgi için bkz. [OLE DB, ODBC ve Oracle bağlantı havuzu](ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="9a4b0-116">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a4b0-117">`Close` `Dispose` Sınıfınızın yönteminde veya bir **bağlantı**, bir **DataReader** veya başka bir yönetilen nesne çağırmayın `Finalize` .</span><span class="sxs-lookup"><span data-stu-id="9a4b0-117">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="9a4b0-118">Sonlandırıcıda yalnızca, sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-118">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="9a4b0-119">Sınıfınız hiçbir yönetilmeyen kaynağa sahip değilse, `Finalize` sınıf tanımınıza bir yöntem eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-119">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="9a4b0-120">Daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="9a4b0-120">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a4b0-121">Bağlantı, bağlantı havuzuna döndürüldüğünden bağlantı, gerçekten kapanmadığı için, bağlantı havuzundan bir bağlantı getirilirken ya da geri döndürülene kadar sunucuda oturum açma ve oturum kapatma olayları oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-121">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="9a4b0-122">Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="9a4b0-122">For more information, see [SQL Server Connection Pooling (ADO.NET)](sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="9a4b0-123">SQL Server bağlanılıyor</span><span class="sxs-lookup"><span data-stu-id="9a4b0-123">Connecting to SQL Server</span></span>  

 <span data-ttu-id="9a4b0-124">SQL Server için .NET Framework Veri Sağlayıcısı, OLE DB (ADO) bağlantı dizesi biçimine benzer bir bağlantı dizesi biçimini destekler.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-124">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="9a4b0-125">Geçerli dize biçimi adları ve değerleri için, bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> <xref:System.Data.SqlClient.SqlConnection> . nesnesinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-125">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="9a4b0-126">Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında sözdizimi geçerli bağlantı dizeleri oluşturmak için sınıfını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-126">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="9a4b0-127">Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="9a4b0-127">For more information, see [Connection String Builders](connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="9a4b0-128">Aşağıdaki kod örneği, bir SQL Server veritabanına bağlantı oluşturmayı ve açmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-128">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="9a4b0-129">Tümleşik güvenlik ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9a4b0-129">Integrated Security and ASP.NET</span></span>  

 <span data-ttu-id="9a4b0-130">SQL Server tümleşik güvenlik (güvenilen bağlantı olarak da bilinir), bağlantı dizesinde kullanıcı KIMLIĞI ve parola sunmaz ve bir bağlantının kimlik doğrulaması için önerilen yöntem olduğundan, SQL Server bağlanırken koruma sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-130">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="9a4b0-131">Tümleşik güvenlik, yürütme işleminin geçerli güvenlik kimliğini veya belirtecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-131">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="9a4b0-132">Masaüstü uygulamaları için bu genellikle şu anda oturum açmış olan kullanıcının kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-132">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="9a4b0-133">ASP.NET uygulamaları için güvenlik kimliği, birkaç farklı seçenekten birine ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-133">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="9a4b0-134">Bir ASP.NET uygulamasının SQL Server bağlanırken kullandığı güvenlik kimliğini daha iyi anlamak için, bkz. [ASP.NET Kimliğe bürünme](/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](/previous-versions/aspnet/eeyk640h(v=vs.100))ve [nasıl yapılır: Windows tümleşik güvenliği kullanarak SQL Server erişme](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9a4b0-134">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](/previous-versions/aspnet/xh507fc5(v=vs.100)), [ASP.NET Authentication](/previous-versions/aspnet/eeyk640h(v=vs.100)), and [How to: Access SQL Server Using Windows Integrated Security](/previous-versions/aspnet/bsz5788z(v=vs.100)).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="9a4b0-135">OLE DB veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="9a4b0-135">Connecting to an OLE DB Data Source</span></span>  

 <span data-ttu-id="9a4b0-136">OLE DB için .NET Framework Veri Sağlayıcısı, **OleDbConnection** nesnesi kullanılarak OLE DB (örneğin, OLE DB Için SQL Server sağlayıcısı) kullanılarak sunulan veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-136">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="9a4b0-137">OLE DB için .NET Framework Veri Sağlayıcısı bağlantı dizesi biçimi, aşağıdaki özel durumlarla birlikte ADO 'da kullanılan bağlantı dizesi biçimiyle aynıdır:</span><span class="sxs-lookup"><span data-stu-id="9a4b0-137">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
- <span data-ttu-id="9a4b0-138">**Sağlayıcı** anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-138">The **Provider** keyword is required.</span></span>  
  
- <span data-ttu-id="9a4b0-139">**URL**, **uzak sağlayıcı** ve **uzak sunucu** anahtar sözcükleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-139">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="9a4b0-140">OLE DB bağlantı dizeleri hakkında daha fazla bilgi için konusuna bakın <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> .</span><span class="sxs-lookup"><span data-stu-id="9a4b0-140">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="9a4b0-141">Ayrıca, <xref:System.Data.OleDb.OleDbConnectionStringBuilder> çalışma zamanında bağlantı dizeleri oluşturmak için öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-141">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a4b0-142">**OleDbConnection** nesnesi bir OLE DB sağlayıcısına özgü dinamik özellikleri ayarlamayı veya almayı desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-142">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="9a4b0-143">Yalnızca OLE DB sağlayıcısı için bağlantı dizesinde geçirilebilecek özellikler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-143">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="9a4b0-144">Aşağıdaki kod örneği, bir OLE DB veri kaynağına bağlantı oluşturmayı ve açmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-144">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="9a4b0-145">Evrensel veri bağlantısı dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="9a4b0-145">Do Not Use Universal Data Link Files</span></span>  

 <span data-ttu-id="9a4b0-146">Bir evrensel veri bağlantısı (UDL) dosyasında bir **OleDbConnection** için bağlantı bilgilerini sağlamak mümkündür; Ancak bunu yapmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-146">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="9a4b0-147">UDL dosyaları şifrelenmez ve bağlantı dizesi bilgilerini şifresiz metin olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-147">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="9a4b0-148">Bir UDL dosyası uygulamanıza yönelik dış dosya tabanlı bir kaynak olduğundan .NET Framework kullanılarak güvenliği alınamaz.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-148">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="9a4b0-149">ODBC veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="9a4b0-149">Connecting to an ODBC Data Source</span></span>  

 <span data-ttu-id="9a4b0-150">ODBC için .NET Framework Veri Sağlayıcısı, **OdbcConnection** NESNESI kullanılarak ODBC kullanılarak sunulan veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-150">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="9a4b0-151">ODBC için .NET Framework Veri Sağlayıcısı için bağlantı dizesi biçimi, ODBC bağlantı dizesi biçimiyle mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-151">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="9a4b0-152">Ayrıca bir ODBC veri kaynağı adı (DSN) sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-152">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="9a4b0-153">**OdbcConnection** hakkında daha fazla ayrıntı için bkz <xref:System.Data.Odbc.OdbcConnection> ..</span><span class="sxs-lookup"><span data-stu-id="9a4b0-153">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="9a4b0-154">Aşağıdaki kod örneği, bir ODBC veri kaynağı ile bağlantı oluşturmayı ve açmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-154">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="9a4b0-155">Oracle veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="9a4b0-155">Connecting to an Oracle Data Source</span></span>  

 <span data-ttu-id="9a4b0-156">Oracle için .NET Framework Veri Sağlayıcısı, **OracleConnection** nesnesini kullanarak Oracle veri kaynaklarına bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-156">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="9a4b0-157">Oracle için .NET Framework Veri Sağlayıcısı bağlantı dizesi biçimi, Oracle (MSDAORA) bağlantı dizesi biçimi için OLE DB sağlayıcısı tarafından mümkün olduğunca yakından eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-157">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="9a4b0-158">**OracleConnection** hakkında daha fazla ayrıntı için bkz <xref:System.Data.OracleClient.OracleConnection> ..</span><span class="sxs-lookup"><span data-stu-id="9a4b0-158">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="9a4b0-159">Aşağıdaki kod örneği, bir Oracle veri kaynağına bir bağlantının nasıl oluşturulduğunu ve açılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-159">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a4b0-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a4b0-160">See also</span></span>

- [<span data-ttu-id="9a4b0-161">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="9a4b0-161">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="9a4b0-162">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="9a4b0-162">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="9a4b0-163">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="9a4b0-163">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- [<span data-ttu-id="9a4b0-164">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9a4b0-164">ADO.NET Overview</span></span>](ado-net-overview.md)
