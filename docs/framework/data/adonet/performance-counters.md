---
title: Performans Sayaçları
description: Windows performans Izleyicisi 'ni veya programlama kullanarak uygulama durumunuzu ve bağlantı kaynaklarını izlemek için ADO.NET performans sayaçlarını kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 4f645a51996078f8dd80b6c455c420633db36155
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164609"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="87020-103">ADO.NET 'de performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="87020-103">Performance Counters in ADO.NET</span></span>

<span data-ttu-id="87020-104">ADO.NET 2,0, ve için desteği içeren performans sayaçları için genişletilmiş destek sunmuştur <xref:System.Data.SqlClient> <xref:System.Data.OracleClient> .</span><span class="sxs-lookup"><span data-stu-id="87020-104">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="87020-105"><xref:System.Data.SqlClient>Önceki ADO.net sürümlerinde bulunan performans sayaçları kullanımdan kaldırılmıştır ve bu konuda ele alınan yeni performans sayaçlarıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="87020-105">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="87020-106">Uygulamanızın durumunu ve kullandığı bağlantı kaynaklarını izlemek için ADO.NET performans sayaçlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87020-106">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="87020-107">Performans sayaçları, Windows performans Izleyicisi kullanılarak izlenebilir veya <xref:System.Diagnostics.PerformanceCounter> ad alanındaki sınıfı kullanılarak programlı bir şekilde erişilebilir <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="87020-107">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="87020-108">Kullanılabilir performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="87020-108">Available Performance Counters</span></span>  

 <span data-ttu-id="87020-109">Şu anda, için <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient> Aşağıdaki tabloda açıklandığı gibi 14 farklı performans sayacı mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="87020-109">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="87020-110">Bireysel sayaçların adlarının Microsoft .NET çerçevesinin bölgesel sürümlerinde yerelleştirilmemiş olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="87020-110">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="87020-111">Performans sayacı</span><span class="sxs-lookup"><span data-stu-id="87020-111">Performance counter</span></span>|<span data-ttu-id="87020-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87020-112">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="87020-113">Bir veritabanı sunucusuna yapılan saniye başına bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-113">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="87020-114">Bir veritabanı sunucusuna yapılan saniye başına bağlantı kesilen bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-114">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="87020-115">Etkin olan benzersiz bağlantı havuzu grupları sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-115">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="87020-116">Bu sayaç, AppDomain 'de bulunan benzersiz bağlantı dizeleri sayısına göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="87020-116">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="87020-117">Bağlantı havuzlarının toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-117">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="87020-118">Şu anda kullanımda olan etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-118">The number of active connections that are currently in use.</span></span> <span data-ttu-id="87020-119">**Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="87020-119">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="87020-120">Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="87020-120">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="87020-121">Bağlantı havuzlarında kullanılabilecek bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-121">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="87020-122">**Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="87020-122">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="87020-123">Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="87020-123">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="87020-124">Ayıklama için işaretlenen benzersiz bağlantı havuzu grupları sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-124">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="87020-125">Bu sayaç, AppDomain 'de bulunan benzersiz bağlantı dizeleri sayısına göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="87020-125">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="87020-126">En son etkinliği olmayan ve aktiften çıkarılmayı bekleyen etkin olmayan bağlantı havuzu sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-126">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="87020-127">Havuza alınmamış etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-127">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="87020-128">Bağlantı havuzu altyapısı tarafından yönetilmekte olan etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-128">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="87020-129">`Close`Ya da `Dispose` uygulama tarafından çağrılmayan çöp toplama aracılığıyla geri kazanılan bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-129">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="87020-130">Bağlantı kesilmesi performansını açıkça kapatma veya atma.</span><span class="sxs-lookup"><span data-stu-id="87020-130">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="87020-131">Şu anda bir eylemin tamamlanmasını bekleyen ve bu nedenle uygulamanız tarafından kullanılamayan bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-131">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="87020-132">Bağlantı havuzundan çekilen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-132">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="87020-133">**Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="87020-133">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="87020-134">Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="87020-134">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="87020-135">Bağlantı havuzuna döndürülen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="87020-135">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="87020-136">**Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="87020-136">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="87020-137">Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="87020-137">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="87020-138">Bağlantı havuzu grupları ve bağlantı havuzları</span><span class="sxs-lookup"><span data-stu-id="87020-138">Connection Pool Groups and Connection Pools</span></span>  

 <span data-ttu-id="87020-139">Windows kimlik doğrulaması (tümleşik güvenlik) kullanırken hem hem de `NumberOfActiveConnectionPoolGroups` performans sayaçlarını izlemeniz gerekir `NumberOfActiveConnectionPools` .</span><span class="sxs-lookup"><span data-stu-id="87020-139">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="87020-140">Bunun nedeni, bağlantı havuzu gruplarının benzersiz bağlantı dizeleriyle eşlenme nedenidir.</span><span class="sxs-lookup"><span data-stu-id="87020-140">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="87020-141">Tümleşik güvenlik kullanıldığında, bağlantı havuzları bağlantı dizelerine eşlenir ve ayrıca ayrı Windows kimlikleri için ayrı havuzlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87020-141">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="87020-142">Örneğin, her ikisi de aynı AppDomain içinde olan Fred ve Julie ise, bağlantı `"Data Source=MySqlServer;Integrated Security=true"` dizesi için bir bağlantı havuzu grubu oluşturulur ve biri Fred ve Julie için bir tane olmak üzere iki ek havuz oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="87020-142">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="87020-143">John ve Martha aynı SQL Server oturum açma işlemiyle bir bağlantı dizesi kullanıyorsa, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"` **Lowprıkullanıcı** kimliği için yalnızca tek bir havuz oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="87020-143">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>

### <a name="activating-off-by-default-counters"></a><span data-ttu-id="87020-144">Varsayılan olarak devre dışı sayaçları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="87020-144">Activating Off-By-Default Counters</span></span>  

 <span data-ttu-id="87020-145">Performans sayaçları,,, `NumberOfFreeConnections` `NumberOfActiveConnections` `SoftDisconnectsPerSecond` ve `SoftConnectsPerSecond` Varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="87020-145">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="87020-146">Aşağıdaki bilgileri etkinleştirmek için uygulamanın yapılandırma dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="87020-146">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="87020-147">Performans sayacı değerlerini alma</span><span class="sxs-lookup"><span data-stu-id="87020-147">Retrieving Performance Counter Values</span></span>  

 <span data-ttu-id="87020-148">Aşağıdaki konsol uygulaması, uygulamanızda performans sayacı değerlerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87020-148">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="87020-149">Tüm ADO.NET performans sayaçlarıyla ilgili bilgilerin döndürülmesi için bağlantıların açık ve etkin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87020-149">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87020-150">Bu örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="87020-150">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="87020-151">Örnek kodda sağlanan bağlantı dizeleri, veritabanının bir örnek adı SqlExpress olan yerel bilgisayarda yüklü ve kullanılabilir olduğunu ve bağlantı dizelerinde sağlananlarla eşleşen SQL Server oturum açma işlemleri oluşturduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="87020-151">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="87020-152">Sunucunuz yalnızca Windows kimlik doğrulamasına izin veren varsayılan güvenlik ayarları kullanılarak yapılandırılmışsa SQL Server oturum açma işlemlerini etkinleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="87020-152">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="87020-153">Bağlantı dizelerini ortamınıza uyacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="87020-153">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="87020-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="87020-154">Example</span></span>  
  
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
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
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
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="87020-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87020-155">See also</span></span>

- [<span data-ttu-id="87020-156">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="87020-156">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="87020-157">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="87020-157">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="87020-158">[ASP.NET için performans sayaçları](/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="87020-158">[Performance Counters for ASP.NET](/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="87020-159">Çalışma Zamanı Profili Oluşturma</span><span class="sxs-lookup"><span data-stu-id="87020-159">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="87020-160">[Performans eşiklerini Izlemeye giriş](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="87020-160">[Introduction to Monitoring Performance Thresholds](/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="87020-161">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="87020-161">ADO.NET Overview</span></span>](ado-net-overview.md)
