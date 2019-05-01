---
title: ADO.NET performans sayaçları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: e7e7ba379f6f92f3ba8fba55f22c8eaec81ab1cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878351"
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="0387d-102">ADO.NET performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="0387d-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="0387d-103">ADO.NET 2.0 desteği her ikisini de içeren genişletilmiş destek performans sayaçları için sunulan <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="0387d-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="0387d-104"><xref:System.Data.SqlClient> ADO.NET önceki sürümlerinde kullanılabilen performans sayaçlarının kullanımdan kaldırıldı ve bu konuda açıklanan yeni performans sayaçları ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0387d-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="0387d-105">ADO.NET performans sayaçları, uygulamanızı ve kullandığı bağlantı kaynağının durumunu izlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0387d-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="0387d-106">Performans sayaçlarını Windows Performans İzleyicisi'ni kullanarak izlenebilir veya kullanılarak programlı olarak erişilebilir <xref:System.Diagnostics.PerformanceCounter> sınıfını <xref:System.Diagnostics> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0387d-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="0387d-107">Ulaşılabilir performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="0387d-107">Available Performance Counters</span></span>  
 <span data-ttu-id="0387d-108">Şu anda kullanılabilir 14 farklı performans sayaçları için <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient> aşağıdaki tabloda açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="0387d-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="0387d-109">Ayrı ayrı sayaç adları bölgesel Microsoft .NET Framework sürümleri arasında yerelleştirilmedi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0387d-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="0387d-110">Performans sayacı</span><span class="sxs-lookup"><span data-stu-id="0387d-110">Performance counter</span></span>|<span data-ttu-id="0387d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0387d-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="0387d-112">Saniye başına bir veritabanı sunucusuna yapılan bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="0387d-113">Veritabanı sunucusuna yapılan saniye başına sayısı keser.</span><span class="sxs-lookup"><span data-stu-id="0387d-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="0387d-114">Etkin olan benzersiz bir bağlantı havuzu grubu sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="0387d-115">Bu sayaç, uygulama etki alanında bulunan benzersiz bağlantı dizelerini sayısına göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="0387d-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="0387d-116">Bağlantı havuzları toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="0387d-117">Şu anda kullanımda olan etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="0387d-118">**Not:**  Bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="0387d-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="0387d-119">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme devre dışı varsayılan olarak sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="0387d-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="0387d-120">Bağlantı havuzları için kullanılabilir bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="0387d-121">**Not:**  Bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="0387d-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="0387d-122">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme devre dışı varsayılan olarak sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="0387d-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="0387d-123">Ayıklama için işaretlenmiş benzersiz bir bağlantı havuzu grubu sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="0387d-124">Bu sayaç, uygulama etki alanında bulunan benzersiz bağlantı dizelerini sayısına göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="0387d-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="0387d-125">Son Etkinlik uygulanmamış ve çıkarılması için bekleyen etkin olmayan bir bağlantı havuzu sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="0387d-126">Havuza etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="0387d-127">Bağlantı altyapı havuzu tarafından yönetilen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="0387d-128">Çöp toplama geri kazanıldıktan bağlantı sayısını burada `Close` veya `Dispose` uygulama tarafından çağrılmadı.</span><span class="sxs-lookup"><span data-stu-id="0387d-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="0387d-129">Açıkça kapatma veya bağlantılarını disposing performans gelmez.</span><span class="sxs-lookup"><span data-stu-id="0387d-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="0387d-130">Tamamlama eylemi ve bu nedenle kullanılamaz hale uygulamanız tarafından şu anda bekleyen bağlantılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="0387d-131">Bağlantı havuzundan çekilen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="0387d-132">**Not:**  Bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="0387d-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="0387d-133">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme devre dışı varsayılan olarak sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="0387d-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="0387d-134">Bağlantı havuzu için döndürülen etkin bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0387d-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="0387d-135">**Not:**  Bu performans sayacı varsayılan olarak etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="0387d-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="0387d-136">Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme devre dışı varsayılan olarak sayaçları](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="0387d-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="0387d-137">Bağlantı havuzu grupları ve bağlantı havuzu</span><span class="sxs-lookup"><span data-stu-id="0387d-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="0387d-138">Windows kimlik doğrulaması (tümleşik güvenlik) kullanırken, her ikisi de izlemeniz gereken `NumberOfActiveConnectionPoolGroups` ve `NumberOfActiveConnectionPools` performans sayaçları.</span><span class="sxs-lookup"><span data-stu-id="0387d-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="0387d-139">Benzersiz bağlantı dizelerini bağlantı havuzu grupları eşleştiren nedenidir.</span><span class="sxs-lookup"><span data-stu-id="0387d-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="0387d-140">Tümleşik güvenlik kullanıldığında, bağlantı havuzları eşlemek için bağlantı dizelerini ve ayrıca kimliklerini Windows için ayrı havuzlar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0387d-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="0387d-141">Örneğin, Gamze ve Julie, her aynı AppDomain içinde hem de bağlantı dizesi kullanıyorsanız `"Data Source=MySqlServer;Integrated Security=true"`, bağlantı dizesi için bir bağlantı havuzu grubu oluşturulur ve iki ek havuzları oluşturulur ve biri Fred ve diğeri Julie için.</span><span class="sxs-lookup"><span data-stu-id="0387d-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="0387d-142">John ve Martha özdeş bir SQL Server oturumu ile bir bağlantı dizesi kullanıyorsanız `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, yalnızca tek bir havuz için oluşturulduktan sonra **lowPrivUser** kimlik.</span><span class="sxs-lookup"><span data-stu-id="0387d-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="0387d-143">Kapalı-varsayılan olarak sayaçları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0387d-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="0387d-144">Performans sayaçlarını `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, ve `SoftConnectsPerSecond` varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="0387d-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="0387d-145">Bunları etkinleştirmek için uygulamanın yapılandırma dosyası için aşağıdaki bilgileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0387d-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="0387d-146">Performans sayacı değerlerini alma</span><span class="sxs-lookup"><span data-stu-id="0387d-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="0387d-147">Aşağıdaki konsol uygulamasında, uygulamanızdaki performans sayacı değerlerini alma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0387d-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="0387d-148">Bağlantılar açık ve tüm ADO.NET performans sayaçları için döndürülecek bilgi etkin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0387d-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0387d-149">Bu örnekte örnek **AdventureWorks** veritabanını SQL Server'a dahildir.</span><span class="sxs-lookup"><span data-stu-id="0387d-149">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="0387d-150">Örnek kodda sağlanan bağlantı dizeleri veritabanı yüklü ve bir örnek adı SqlExpress ile yerel bilgisayarda kullanılabilir durumda olduğunu ve bağlantı dizelerini sağlanan eşleşen bir SQL Server oturumları oluşturduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0387d-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="0387d-151">Sunucunuz yalnızca Windows kimlik doğrulamasına izin veren varsayılan güvenlik ayarları kullanılarak yapılandırıldıysa, SQL Server oturum açma bilgileri etkinleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0387d-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="0387d-152">Bağlantı dizelerini ortamınıza uygun gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0387d-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0387d-153">Örnek</span><span class="sxs-lookup"><span data-stu-id="0387d-153">Example</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="0387d-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0387d-154">See also</span></span>

- [<span data-ttu-id="0387d-155">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="0387d-155">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="0387d-156">OLE DB, ODBC ve Oracle Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="0387d-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="0387d-157">[ASP.NET için performans sayaçları](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0387d-157">[Performance Counters for ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="0387d-158">Çalışma Zamanı Profili Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0387d-158">Runtime Profiling</span></span>](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="0387d-159">[Performans eşiklerini izlemeye giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0387d-159">[Introduction to Monitoring Performance Thresholds](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="0387d-160">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0387d-160">ADO.NET Overview</span></span>](ado-net-overview.md)
