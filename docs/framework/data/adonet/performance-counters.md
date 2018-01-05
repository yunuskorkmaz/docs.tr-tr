---
title: "ADO.NET performans sayaçları"
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
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fe3005b3dbfa1a2f0018dd7b6049ab65d68b8e40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="performance-counters-in-adonet"></a>ADO.NET performans sayaçları
ADO.NET 2.0 sunulan her ikisi de desteği içeren performans sayaçları için Genişletilmiş Destek <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient>. <xref:System.Data.SqlClient> ADO.NET önceki sürümlerinde kullanılabilen performans sayaçlarının kullanım ve bu konuda tartışılan yeni performans sayaçları ile değiştirilir. ADO.NET performans sayaçları, uygulamanız ve kullandığı bağlantı kaynaklarını durumunu izlemek için kullanabilirsiniz. Performans sayaçlarını Windows Performans İzleyicisi'ni kullanarak izlenebilir veya program aracılığıyla kullanılarak erişilebilir <xref:System.Diagnostics.PerformanceCounter> sınıfını <xref:System.Diagnostics> ad alanı.  
  
## <a name="available-performance-counters"></a>Kullanılabilir performans sayaçları  
 Şu anda kullanılabilir 14 farklı performans sayaçları için <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient> aşağıdaki tabloda açıklandığı gibi. Ayrı ayrı sayaç adları bölgesel Microsoft .NET Framework sürümleri arasında yerelleştirilmiş değil olduğunu unutmayın.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Saniye başına veritabanı sunucusuna yapılan bağlantı sayısı.|  
|`HardDisconnectsPerSecond`|Veritabanı sunucusuna yapılan saniye başına sayısı keser.|  
|`NumberOfActiveConnectionPoolGroups`|Etkin olan benzersiz bağlantı havuzu gruplarını sayısı. Bu sayaç, uygulama etki alanında bulunan benzersiz bağlantı dizesi sayısı tarafından denetlenir.|  
|`NumberOfActiveConnectionPools`|Bağlantı havuzu toplam sayısı.|  
|`NumberOfActiveConnections`|Şu anda kullanımda olan etkin bağlantı sayısı. **Not:** bu performans sayacı varsayılan olarak etkin değildir. Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Bağlantı havuzu için kullanılabilir bağlantı sayısı. **Not:** bu performans sayacı varsayılan olarak etkin değildir. Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Ayıklama için işaretlenmiş benzersiz bağlantı havuzu gruplarını sayısı. Bu sayaç, uygulama etki alanında bulunan benzersiz bağlantı dizesi sayısı tarafından denetlenir.|  
|`NumberOfInactiveConnectionPools`|Son Etkinlik uygulanmamış ve çıkarılması için bekleyen etkin olmayan bağlantı havuzu sayısı.|  
|`NumberOfNonPooledConnections`|Havuza etkin bağlantı sayısı.|  
|`NumberOfPooledConnections`|Bağlantı altyapı havuzu tarafından yönetilen etkin bağlantı sayısı.|  
|`NumberOfReclaimedConnections`|Çöp toplama iadesi bağlantı sayısını nerede `Close` veya `Dispose` uygulama tarafından çağrılmadı. Açıkça kapatma veya bağlantılarını atma performans hurts.|  
|`NumberOfStasisConnections`|Şu anda bir eylem ve bu nedenle kullanılamaz uygulamanız tarafından kullanılmak üzere tamamlanmasını bekleyen bağlantılarının sayısı.|  
|`SoftConnectsPerSecond`|Bağlantı havuzundan çekilen etkin bağlantı sayısı. **Not:** bu performans sayacı varsayılan olarak etkin değildir. Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Bağlantı havuzu döndürülen etkin bağlantı sayısı. **Not:** bu performans sayacı varsayılan olarak etkin değildir. Bu performans sayacı etkinleştirmek için bkz: [etkinleştirme-varsayılan olarak kapalı sayaçları](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Bağlantı havuzu grupları ve bağlantı havuzu  
 Windows kimlik doğrulaması (tümleşik güvenlik) kullanırken, her ikisi de izlemelisiniz `NumberOfActiveConnectionPoolGroups` ve `NumberOfActiveConnectionPools` performans sayaçları. Benzersiz bağlantı dizeleri bağlantı havuzu grupları eşlenen nedenidir. Tümleşik güvenlik kullanıldığında, bağlantı havuzu bağlantı dizeleri için eşleme ve ayrıca Windows kimliklerini için ayrı havuzlar oluşturabilirsiniz. Örneğin, Gamze ve Julie, her aynı AppDomain içinde hem de bağlantı dizesi kullanıyorsanız `"Data Source=MySqlServer;Integrated Security=true"`, bağlantı dizesi için bir bağlantı havuzu grup oluşturulur ve iki ek havuzları oluşturulur, Gamze için diğeri için Julie. John ve Martha özdeş bir SQL Server oturumu ile bir bağlantı dizesi kullanırsanız, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, yalnızca tek bir havuz için oluşturulduktan sonra **lowPrivUser** kimliği.  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>Varsayılan olarak kapalı sayaçları etkinleştirme  
 Performans sayaçlarını `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, ve `SoftConnectsPerSecond` varsayılan olarak kapalıdır. Aşağıdaki bilgiler, bunları etkinleştirmek için uygulamanın yapılandırma dosyasına ekleyin:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Performans sayacı değerlerini alma  
 Aşağıdaki konsol uygulaması uygulamanızda performans sayacı değerlerini almak nasıl gösterir. Bağlantılar açık ve tüm ADO.NET performans sayaçları için döndürülecek bilgi etkin olması gerekir.  
  
> [!NOTE]
>  Bu örnek, örnek kullanır **AdventureWorks** ile birlikte gelen veritabanı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]. Örnek kodda sağlanan bağlantı dizeleri veritabanı yüklenir ve bir örnek adı SqlExpress ile yerel bilgisayardaki kullanılabilir olduğunu ve bağlantı dizeleri sağlanan eşleştiğinden SQL Server oturumları oluşturduğunuzu varsayalım. Yalnızca Windows kimlik doğrulaması izin veren varsayılan güvenlik ayarlarını kullanarak sunucunuzu yapılandırdıysanız, SQL Server oturumları etkinleştirmeniz gerekebilir. Bağlantı dizeleri ortamınıza uygun gerektiği gibi değiştirin.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [OLE DB, ODBC ve Oracle Bağlantı Havuzu](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [ASP.NET için performans sayaçları](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [Çalışma Zamanı Profili Oluşturma](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [Performans eşiklerini izlemeye giriş](http://msdn.microsoft.com/en-us/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
