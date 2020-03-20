---
title: Performans Sayaçları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: b68787980a8b64d9ee90ed8d834fab2c5c69006b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149342"
---
# <a name="performance-counters-in-adonet"></a>ADO.NET'da Performans Sayaçları
ADO.NET 2.0 hem de <xref:System.Data.SqlClient> <xref:System.Data.OracleClient>destek içeren performans sayaçları için genişletilmiş destek tanıttı. ADO.NET <xref:System.Data.SqlClient> önceki sürümlerinde bulunan performans sayaçları küçümsüldü ve bu konuda tartışılan yeni performans sayaçları ile değiştirildi. Uygulamanızın durumunu ve kullandığı bağlantı kaynaklarını izlemek için ADO.NET performans sayaçlarını kullanabilirsiniz. Performans sayaçları Windows Performance Monitor kullanılarak izlenebilir veya <xref:System.Diagnostics.PerformanceCounter> <xref:System.Diagnostics> ad alanındaki sınıf kullanılarak programlı olarak erişilebilir.  
  
## <a name="available-performance-counters"></a>Mevcut Performans Sayaçları  
 Şu anda 14 farklı performans <xref:System.Data.SqlClient> <xref:System.Data.OracleClient> sayacı için kullanılabilir ve aşağıdaki tabloda açıklandığı gibi vardır. Tek tek sayaçların adlarının Microsoft .NET Framework'ün bölgesel sürümlerinde yerelleştirilmediğini unutmayın.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Bir veritabanı sunucusuna yapılan saniyede bağlantı sayısı.|  
|`HardDisconnectsPerSecond`|Bir veritabanı sunucusuna yapılan saniyede bağlantı kesme sayısı.|  
|`NumberOfActiveConnectionPoolGroups`|Etkin olan benzersiz bağlantı havuzu gruplarının sayısı. Bu sayaç, AppDomain'de bulunan benzersiz bağlantı dizelerinin sayısı tarafından denetlenir.|  
|`NumberOfActiveConnectionPools`|Toplam bağlantı havuzu sayısı.|  
|`NumberOfActiveConnections`|Şu anda kullanılmakta olan etkin bağlantı sayısı. **Not:**  Bu performans sayacı varsayılan olarak etkinleştirilir. Bu performans sayacını etkinleştirmek için, [Varsayılan Olmayan Sayaçları Etkinleştirme'ye](#ActivatingOffByDefault)bakın.|  
|`NumberOfFreeConnections`|Bağlantı havuzlarında kullanılabilecek bağlantı sayısı. **Not:**  Bu performans sayacı varsayılan olarak etkinleştirilir. Bu performans sayacını etkinleştirmek için, [Varsayılan Olmayan Sayaçları Etkinleştirme'ye](#ActivatingOffByDefault)bakın.|  
|`NumberOfInactiveConnectionPoolGroups`|Budama için işaretlenmiş benzersiz bağlantı havuzu gruplarının sayısı. Bu sayaç, AppDomain'de bulunan benzersiz bağlantı dizelerinin sayısı tarafından denetlenir.|  
|`NumberOfInactiveConnectionPools`|Son herhangi bir etkinlik olmayan ve imha edilmeyi bekleyen etkin olmayan bağlantı havuzlarının sayısı.|  
|`NumberOfNonPooledConnections`|Havuza alınmayan etkin bağlantı sayısı.|  
|`NumberOfPooledConnections`|Bağlantı havuzu altyapısı tarafından yönetilen etkin bağlantı sayısı.|  
|`NumberOfReclaimedConnections`|Uygulama tarafından çağrılmayan `Close` veya `Dispose` çağrılmayan çöp toplama yoluyla geri alınan bağlantı sayısı. Bağlantıları açıkça kapatmamak veya atmamaperformansa zarar verir.|  
|`NumberOfStasisConnections`|Şu anda bir eylemin tamamlanmasını bekleyen ve bu nedenle uygulamanız tarafından kullanılamayan bağlantı sayısı.|  
|`SoftConnectsPerSecond`|Bağlantı havuzundan çekilen etkin bağlantı sayısı. **Not:**  Bu performans sayacı varsayılan olarak etkinleştirilir. Bu performans sayacını etkinleştirmek için, [Varsayılan Olmayan Sayaçları Etkinleştirme'ye](#ActivatingOffByDefault)bakın.|  
|`SoftDisconnectsPerSecond`|Bağlantı havuzuna döndürülen etkin bağlantı sayısı. **Not:**  Bu performans sayacı varsayılan olarak etkinleştirilir. Bu performans sayacını etkinleştirmek için, [Varsayılan Olmayan Sayaçları Etkinleştirme'ye](#ActivatingOffByDefault)bakın.|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Bağlantı Havuzu Grupları ve Bağlantı Havuzları  
 Windows Kimlik Doğrulama (tümleşik güvenlik) `NumberOfActiveConnectionPoolGroups` kullanırken, hem performans sayaçlarını hem `NumberOfActiveConnectionPools` de performans sayaçlarını izlemeniz gerekir. Bunun nedeni, bağlantı havuzu gruplarının benzersiz bağlantı dizeleri ile eşleşiş olmasıdır. Tümleşik güvenlik kullanıldığında, bağlantı havuzları bağlantı dizeleri eşlenir ve ayrıca tek tek Windows kimlikleri için ayrı havuzlar oluşturur. Örneğin, Her biri aynı AppDomain içinde olan Fred ve `"Data Source=MySqlServer;Integrated Security=true"`Julie her ikisi de bağlantı dizesini kullanırsa, bağlantı dizesi için bir bağlantı havuzu grubu oluşturulur ve biri Fred ve diğeri Julie için olmak üzere iki ek havuz oluşturulur. John ve Martha aynı SQL Server giriş ile `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`bir bağlantı dizesi kullanırsanız, o zaman sadece tek bir havuz **lowPrivUser** kimliği için oluşturulur.  
  
<a name="ActivatingOffByDefault"></a>
### <a name="activating-off-by-default-counters"></a>Varsayılan Olmayan Sayaçları Etkinleştirme  
 Performans sayaçları `NumberOfFreeConnections` `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, `SoftConnectsPerSecond` , ve varsayılan olarak kapalıdır. Bunları etkinleştirmek için uygulamanın yapılandırma dosyasına aşağıdaki bilgileri ekleyin:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Performans Sayacı Değerlerini Alma  
 Aşağıdaki konsol uygulaması, uygulamanızda performans sayacı değerlerinin nasıl alındığını gösterir. Tüm ADO.NET performans sayaçları için bilgilerin döndürülmesi için bağlantıların açık ve etkin olması gerekir.  
  
> [!NOTE]
> Bu örnek, SQL Server ile birlikte verilen örnek **AdventureWorks** veritabanını kullanır. Örnek kodda sağlanan bağlantı dizeleri veritabanının yüklü olduğunu ve sqlexpress örneği adı ile yerel bilgisayarda kullanılabildiğini ve bağlantı dizelerinde sağlananlarla eşleşen SQL Server girişleri oluşturduğunuzu varsayar. Sunucunuz yalnızca Windows Kimlik Doğrulamasına izin veren varsayılan güvenlik ayarları kullanılarak yapılandırılırsa, SQL Server oturumlarını etkinleştirmeniz gerekebilir. Bağlantı dizelerini ortamınıza uyacak şekilde gerektiği gibi değiştirin.  
  
### <a name="example"></a>Örnek  
  
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

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [OLE DB, ODBC ve Oracle Bağlantı Havuzu](ole-db-odbc-and-oracle-connection-pooling.md)
- [ASP.NET için Performans Sayaçları](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))
- [Çalışma Zamanı Profili Oluşturma](../../debug-trace-profile/runtime-profiling.md)
- [Performans Eşiklerinin İzlenmesine Giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
