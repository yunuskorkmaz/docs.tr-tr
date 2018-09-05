---
title: Bağlantı kurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
ms.openlocfilehash: 29db884a88f5150cd93571ba8fa7bf72be2b8c69
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514574"
---
# <a name="establishing-the-connection"></a><span data-ttu-id="41172-102">Bağlantı kurma</span><span class="sxs-lookup"><span data-stu-id="41172-102">Establishing the Connection</span></span>
<span data-ttu-id="41172-103">Microsoft SQL Server'a bağlanmak için <xref:System.Data.SqlClient.SqlConnection> SQL Server için .NET Framework veri sağlayıcısı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="41172-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="41172-104">Bir OLE DB veri kaynağına bağlanmak için <xref:System.Data.OleDb.OleDbConnection> nesnesini OLE DB için .NET Framework veri sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="41172-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="41172-105">Bir ODBC veri kaynağına bağlanmak için <xref:System.Data.Odbc.OdbcConnection> ODBC için .NET Framework veri sağlayıcısı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="41172-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="41172-106">Bir Oracle veri kaynağına bağlanmak için <xref:System.Data.OracleClient.OracleConnection> Oracle için .NET Framework veri sağlayıcısı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="41172-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="41172-107">Güvenli bir şekilde depolamak ve bağlantı dizelerini almak için bkz. [bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="41172-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="41172-108">Bağlantı Kapatma</span><span class="sxs-lookup"><span data-stu-id="41172-108">Closing Connections</span></span>  
 <span data-ttu-id="41172-109">Böylece bağlantı havuzuna döndürülebilir kullanmayı bitirdiğiniz zaman, her zaman bağlantı kapatmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="41172-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="41172-110">`Using` Visual Basic'te engellemek ya da C# otomatik olarak atar bağlantısı kod bloğu, işlenmeyen bir özel durum durumunda bile çıktığında.</span><span class="sxs-lookup"><span data-stu-id="41172-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="41172-111">Bkz: [using deyimi](~/docs/csharp/language-reference/keywords/using-statement.md) ve [Using deyimi](~/docs/visual-basic/language-reference/statements/using-statement.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="41172-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="41172-112">Ayrıca `Close` veya `Dispose` kullandığınız sağlayıcı için bağlantı nesnesi yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="41172-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="41172-113">Açıkça kapanmamış bağlantıları eklenemez veya havuza geri döner.</span><span class="sxs-lookup"><span data-stu-id="41172-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="41172-114">Örneğin, bir bağlantı, kapsam dışına geçti, ancak bu değil açıkça kapatıldı yalnızca bağlantı havuzuna maksimum havuz boyutuna ulaştı ve bağlantı hala geçerli ise döndürülür.</span><span class="sxs-lookup"><span data-stu-id="41172-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="41172-115">Daha fazla bilgi için [OLE DB, ODBC ve Oracle bağlantı havuzu](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="41172-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41172-116">Çağırmayın `Close` veya `Dispose` üzerinde bir **bağlantı**, **DataReader**, ya da diğer yönetilen nesnelere `Finalize` sınıfınızın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41172-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="41172-117">İçindeki bir sonlandırıcı yalnızca sınıfınıza doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="41172-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="41172-118">Sınıfınızın herhangi bir yönetilmeyen kaynağa sahip değilse içermeyen bir `Finalize` sınıf tanımına yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41172-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="41172-119">Daha fazla bilgi için [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="41172-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41172-120">Bağlantı için bağlantı havuzunu döndürüldüğünde gerçekten kapatılmamış çünkü bağlantı öğesinden alınan ya da bağlantı havuzu için döndürülen de sunucuda oturum açma ve kapatma olayları harekete Geçirilmemesi.</span><span class="sxs-lookup"><span data-stu-id="41172-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="41172-121">Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="41172-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="41172-122">SQL Server'a bağlanma</span><span class="sxs-lookup"><span data-stu-id="41172-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="41172-123">SQL Server için .NET Framework veri sağlayıcısı için OLE DB (ADO) bağlantı dizesi biçimi benzer bir bağlantı dizesi biçimi destekler.</span><span class="sxs-lookup"><span data-stu-id="41172-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="41172-124">Geçerli dize biçimi adları ve değerleri için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> nesne.</span><span class="sxs-lookup"><span data-stu-id="41172-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="41172-125">Ayrıca <xref:System.Data.SqlClient.SqlConnectionStringBuilder> sözdizimsel açıdan geçerli bağlantı dizeleri çalışma zamanında oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="41172-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="41172-126">Daha fazla bilgi için [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="41172-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="41172-127">Aşağıdaki kod örneği, oluşturmak ve bir SQL Server veritabanına bir bağlantı açmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41172-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="41172-128">Tümleşik Güvenlik'i ve ASP.NET</span><span class="sxs-lookup"><span data-stu-id="41172-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="41172-129">SQL Server'ın tümleşik güvenlik (güvenilen bağlantılar olarak da bilinir) olarak SQL Server'a bağlanırken koruma sağlamaya yardımcı olur, bir kullanıcı kimliği ve bağlantı dizesinde parola kullanıma sunmuyor ve bağlantı kimliğini doğrulamak için önerilen yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="41172-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="41172-130">Tümleşik güvenlik geçerli güvenlik kimliği ya da belirtecinde, yürütme işlemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="41172-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="41172-131">Masaüstü uygulamaları için bu genellikle şu anda oturum açmış kullanıcı kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="41172-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="41172-132">ASP.NET uygulamaları için güvenlik kimlik birkaç farklı seçenekten birini için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="41172-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="41172-133">Bir ASP.NET uygulamasını SQL Server'a bağlanırken kullandığı güvenlik kimlik daha iyi anlamak için bkz: [ASP.NET kimliğe bürünme](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET kimlik doğrulaması](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), ve [nasıl yapılır: erişim SQL Sunucu kullanarak Windows tümleşik güvenliği](https://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span><span class="sxs-lookup"><span data-stu-id="41172-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET Authentication](https://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), and [How to: Access SQL Server Using Windows Integrated Security](https://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="41172-134">Bir OLE DB veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="41172-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="41172-135">OLE DB için .NET Framework veri sağlayıcısı (aracılığıyla SQLOLEDB, OLE DB sağlayıcısı için SQL Server), OLE DB kullanılarak kullanıma sunulan veri kaynaklarına bağlantı sağlayan kullanarak **OleDbConnection** nesne.</span><span class="sxs-lookup"><span data-stu-id="41172-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="41172-136">OLE DB için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi aşağıdaki istisnalar, ADO kullanılan bağlantı dizesi biçimi aynıdır:</span><span class="sxs-lookup"><span data-stu-id="41172-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="41172-137">**Sağlayıcısı** anahtar sözcüğü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="41172-137">The **Provider** keyword is required.</span></span>  
  
-   <span data-ttu-id="41172-138">**URL**, **uzak sağlayıcıya**, ve **uzak sunucu** anahtar sözcükleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="41172-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="41172-139">OLE DB bağlantı dizeleri hakkında daha fazla bilgi için bkz. <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> konu.</span><span class="sxs-lookup"><span data-stu-id="41172-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="41172-140">Ayrıca <xref:System.Data.OleDb.OleDbConnectionStringBuilder> bağlantı dizeleri çalışma zamanında oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="41172-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41172-141">**OleDbConnection** nesne ayarlama veya belirli bir OLE DB sağlayıcısı için dinamik özellikleri alınırken desteklemez.</span><span class="sxs-lookup"><span data-stu-id="41172-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="41172-142">OLE DB Sağlayıcısı bağlantı dizesinde geçirilebilen özellikleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="41172-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="41172-143">Aşağıdaki kod örneği, oluşturmak ve bir OLE DB veri kaynağı bağlantısı açmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41172-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="41172-144">Evrensel Veri Bağlantısı dosyalarını kullanmayın</span><span class="sxs-lookup"><span data-stu-id="41172-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="41172-145">İlgili bağlantı bilgilerini sağlamak olası bir **OleDbConnection** evrensel veri bağlantısı (UDL) dosyasında; Bununla birlikte, kaçının bunu.</span><span class="sxs-lookup"><span data-stu-id="41172-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="41172-146">UDL dosyaları şifreli olmayan ve düz metin bağlantı dizesi bilgilerini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="41172-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="41172-147">UDL dosyası uygulamanız için bir dış dosya tabanlı kaynak olduğundan, .NET Framework kullanarak korunamıyor.</span><span class="sxs-lookup"><span data-stu-id="41172-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="41172-148">Bir ODBC veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="41172-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="41172-149">ODBC için .NET Framework veri sağlayıcısı ODBC kullanarak kullanıma sunulan veri kaynaklarına bağlantı sağlayan **OdbcConnection** nesne.</span><span class="sxs-lookup"><span data-stu-id="41172-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="41172-150">ODBC için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi ODBC bağlantı dizesi biçimi mümkün olduğunca yakın eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="41172-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="41172-151">Bir ODBC veri kaynağı adı (DSN) da sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="41172-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="41172-152">Hakkında daha fazla ayrıntı için **OdbcConnection** , bkz: <xref:System.Data.Odbc.OdbcConnection>.</span><span class="sxs-lookup"><span data-stu-id="41172-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="41172-153">Aşağıdaki kod örneği, oluşturmak ve bir ODBC veri kaynağı için bir bağlantı açmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41172-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="41172-154">Bir Oracle veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="41172-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="41172-155">Oracle için .NET Framework veri sağlayıcısı kullanarak Oracle veri kaynaklarına bağlantı sağlayan **OracleConnection** nesne.</span><span class="sxs-lookup"><span data-stu-id="41172-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="41172-156">Oracle için .NET Framework veri sağlayıcısı için bağlantı dizesi biçimi, OLE DB sağlayıcısı (MSDAORA) Oracle bağlantı dize biçimi için mümkün olduğunca yakın eşleşecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="41172-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="41172-157">Hakkında daha fazla ayrıntı için **OracleConnection**, bkz: <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="41172-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="41172-158">Aşağıdaki kod örneği, oluşturmak ve bir Oracle veri kaynağı bağlantısı açmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41172-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41172-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41172-159">See Also</span></span>  
 [<span data-ttu-id="41172-160">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="41172-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="41172-161">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="41172-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="41172-162">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="41172-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="41172-163">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="41172-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
