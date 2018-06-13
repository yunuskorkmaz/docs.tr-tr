---
title: ADO.NET performans sayaçları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 8696bf567d8f32fc3bc3f78e127631f488c551aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365122"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="48922-102">ADO.NET performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="48922-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="48922-103">ADO.NET 2.0 sunulan her ikisi de desteği içeren performans sayaçları için Genişletilmiş Destek <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="48922-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="48922-104"><xref:System.Data.SqlClient> ADO.NET önceki sürümlerinde kullanılabilen performans sayaçlarının kullanım ve bu konuda tartışılan yeni performans sayaçları ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="48922-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="48922-105">ADO.NET performans sayaçları, uygulamanız ve kullandığı bağlantı kaynaklarını durumunu izlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48922-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="48922-106">Performans sayaçlarını Windows Performans İzleyicisi'ni kullanarak izlenebilir veya program aracılığıyla kullanılarak erişilebilir <xref:System.Diagnostics.PerformanceCounter> sınıfını <xref:System.Diagnostics> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="48922-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="48922-107">Kullanılabilir performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="48922-107">Available Performance Counters</span></span>  
 <span data-ttu-id="48922-108">Şu anda kullanılabilir 14 farklı performans sayaçları için <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient> aşağıdaki tabloda açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="48922-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="48922-109">Ayrı ayrı sayaç adları bölgesel Microsoft .NET Framework sürümleri arasında yerelleştirilmiş değil olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="48922-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="48922-110">Performans sayacı</span><span class="sxs-lookup"><span data-stu-id="48922-110">Performance counter</span></span>|<span data-ttu-id="48922-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48922-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="48922-112">Saniye başına veritabanı sunucusuna yapılan bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="48922-113">Veritabanı sunucusuna yapılan saniye başına sayısı keser.</span><span class="sxs-lookup"><span data-stu-id="48922-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="48922-114">Etkin olan benzersiz bağlantı havuzu gruplarını sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="48922-115">Bu sayaç, uygulama etki alanında bulunan benzersiz bağlantı dizesi sayısı tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="48922-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="48922-116">Bağlantı havuzu toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="48922-117">Şu anda kullanımda olan etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="48922-118">**Not:** bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="48922-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="48922-119">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="48922-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="48922-120">Bağlantı havuzu için kullanılabilir bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="48922-121">**Not:** bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="48922-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="48922-122">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="48922-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="48922-123">Ayıklama için işaretlenmiş benzersiz bağlantı havuzu gruplarını sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="48922-124">Bu sayaç, uygulama etki alanında bulunan benzersiz bağlantı dizesi sayısı tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="48922-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="48922-125">Son Etkinlik uygulanmamış ve çıkarılması için bekleyen etkin olmayan bağlantı havuzu sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="48922-126">Havuza etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="48922-127">Bağlantı altyapı havuzu tarafından yönetilen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="48922-128">Çöp toplama iadesi bağlantı sayısını nerede `Close` veya `Dispose` uygulama tarafından çağrılmadı.</span><span class="sxs-lookup"><span data-stu-id="48922-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="48922-129">Açıkça kapatma veya bağlantılarını atma performans hurts.</span><span class="sxs-lookup"><span data-stu-id="48922-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="48922-130">Şu anda bir eylem ve bu nedenle kullanılamaz uygulamanız tarafından kullanılmak üzere tamamlanmasını bekleyen bağlantılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="48922-131">Bağlantı havuzundan çekilen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="48922-132">**Not:** bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="48922-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="48922-133">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="48922-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="48922-134">Bağlantı havuzu döndürülen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="48922-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="48922-135">**Not:** bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="48922-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="48922-136">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="48922-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="48922-137">Bağlantı havuzu grupları ve bağlantı havuzu</span><span class="sxs-lookup"><span data-stu-id="48922-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="48922-138">Windows kimlik doğrulaması (tümleşik güvenlik) kullanırken, her ikisi de izlemelisiniz `NumberOfActiveConnectionPoolGroups` ve `NumberOfActiveConnectionPools` performans sayaçları.</span><span class="sxs-lookup"><span data-stu-id="48922-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="48922-139">Benzersiz bağlantı dizeleri bağlantı havuzu grupları eşlenen nedenidir.</span><span class="sxs-lookup"><span data-stu-id="48922-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="48922-140">Tümleşik güvenlik kullanıldığında, bağlantı havuzu bağlantı dizeleri için eşleme ve ayrıca Windows kimliklerini için ayrı havuzlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48922-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="48922-141">Örneğin, Gamze ve Julie, her aynı AppDomain içinde hem de bağlantı dizesi kullanıyorsanız `"Data Source=MySqlServer;Integrated Security=true"`, bağlantı dizesi için bir bağlantı havuzu grup oluşturulur ve iki ek havuzları oluşturulur, Gamze için diğeri için Julie.</span><span class="sxs-lookup"><span data-stu-id="48922-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="48922-142">John ve Martha özdeş bir SQL Server oturumu ile bir bağlantı dizesi kullanırsanız, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, yalnızca tek bir havuz için oluşturulduktan sonra **lowPrivUser** kimliği.</span><span class="sxs-lookup"><span data-stu-id="48922-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="48922-143">Varsayılan olarak kapalı sayaçları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="48922-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="48922-144">Performans sayaçlarını `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, ve `SoftConnectsPerSecond` varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="48922-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="48922-145">Aşağıdaki bilgiler, bunları etkinleştirmek için uygulamanın yapılandırma dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="48922-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="48922-146">Performans sayacı değerlerini alma</span><span class="sxs-lookup"><span data-stu-id="48922-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="48922-147">Aşağıdaki konsol uygulaması uygulamanızda performans sayacı değerlerini almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="48922-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="48922-148">Bağlantılar açık ve tüm ADO.NET performans sayaçları için döndürülecek bilgi etkin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48922-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48922-149">Bu örnek, örnek kullanır **AdventureWorks** SQL Server'da bulunan veritabanı.</span><span class="sxs-lookup"><span data-stu-id="48922-149">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="48922-150">Örnek kodda sağlanan bağlantı dizeleri veritabanı yüklenir ve bir örnek adı SqlExpress ile yerel bilgisayardaki kullanılabilir olduğunu ve bağlantı dizeleri sağlanan eşleştiğinden SQL Server oturumları oluşturduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="48922-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="48922-151">Yalnızca Windows kimlik doğrulaması izin veren varsayılan güvenlik ayarlarını kullanarak sunucunuzu yapılandırdıysanız, SQL Server oturumları etkinleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="48922-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="48922-152">Bağlantı dizeleri ortamınıza uygun gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="48922-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="48922-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="48922-153">Example</span></span>  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.   
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.   
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\   
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's   
        'FriendlyName. Replace the line above that sets the instanceName with this:   
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's   
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
        //  "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="48922-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48922-154">See Also</span></span>  
 [<span data-ttu-id="48922-155">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="48922-155">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="48922-156">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="48922-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="48922-157">ASP.NET için performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="48922-157">Performance Counters for ASP.NET</span></span>](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [<span data-ttu-id="48922-158">Çalışma Zamanı Profili Oluşturma</span><span class="sxs-lookup"><span data-stu-id="48922-158">Runtime Profiling</span></span>](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [<span data-ttu-id="48922-159">Performans eşiklerini izlemeye giriş</span><span class="sxs-lookup"><span data-stu-id="48922-159">Introduction to Monitoring Performance Thresholds</span></span>](http://msdn.microsoft.com/library/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 [<span data-ttu-id="48922-160">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="48922-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
