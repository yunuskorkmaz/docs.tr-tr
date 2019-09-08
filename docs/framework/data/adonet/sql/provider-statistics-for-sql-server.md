---
title: SQL Server için Sağlayıcı İstatistikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: b6fa4207531e86cbde8657d0c47596f22c886f89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791876"
---
# <a name="provider-statistics-for-sql-server"></a>SQL Server için Sağlayıcı İstatistikleri
.NET Framework sürüm 2,0 ' den başlayarak, SQL Server için .NET Framework Veri Sağlayıcısı, çalışma zamanı istatistiklerini destekler. Geçerli bir Connection nesneniz oluşturulduktan <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> `True` sonra <xref:System.Data.SqlClient.SqlConnection> nesnesinin özelliğini ayarlayarak istatistikleri etkinleştirmeniz gerekir. İstatistikler etkinleştirildikten sonra, <xref:System.Collections.IDictionary> <xref:System.Data.SqlClient.SqlConnection> nesnenin <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> yöntemi aracılığıyla bir başvuru alarak bunları bir "anlık görüntü" olarak gözden geçirebilirsiniz. Liste/değer çifti sözlüğü girdileri kümesi olarak listeyi numaralandırın. Bu ad/değer çiftleri sırasız. İstediğiniz zaman, sayaçları sıfırlamak için <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> <xref:System.Data.SqlClient.SqlConnection> nesnesinin yöntemini çağırabilirsiniz. İstatistik toplama etkinleştirilmediyse, bir özel durum oluşturulmaz. Ayrıca <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> , ilki çağrılmadan <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> çağrılırsa, alınan değerler her girdinin başlangıç değerleridir. İstatistikleri etkinleştirir, uygulamanızı bir süre için çalıştırın ve sonra istatistikleri devre dışı bırakırsanız, alınan değerler istatistiklerin devre dışı bırakıldığı noktaya kadar toplanan değerleri yansıtır. Toplanan tüm istatistiksel değerler her bağlantı için yapılır.  
  
## <a name="statistical-values-available"></a>İstatistiksel değerler kullanılabilir  
 Şu anda Microsoft SQL Server sağlayıcısından 18 farklı öğe mevcuttur. Kullanılabilir öğelerin sayısına tarafından <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>döndürülen <xref:System.Collections.IDictionary> arabirim başvurusunun **Count** özelliği aracılığıyla erişilebilir. Sağlayıcı istatistikleri için tüm sayaçlar, ortak dil çalışma zamanı <xref:System.Int64> türünü (**Long** in C# and Visual Basic) kullanır, bu da 64 bit geniştir. Int64 tarafından tanımlanan en büyük **Int64** veri türü değeri **. MaxValue** alanı ((2 ^ 63)-1)). Sayaçların değerleri bu en büyük değere ulaştığında, artık doğru olarak değerlendirilmemelidir. Bu, söz konusu int64 anlamına gelir **. MaxValue**-1 ((2 ^ 63)-2), herhangi bir istatistiğin en büyük geçerli değeri etkin değildir.  
  
> [!NOTE]
> Döndürülen istatistiklerin sayısı, isimleri ve sırası gelecekte değiştirebileceğinden, sağlayıcı istatistiklerini döndürmek için bir sözlük kullanılır. Uygulamalar, sözlükte bulunan belirli bir değere güvenmemelidir, ancak bunun yerine değerin aynı ve uygun olup olmadığını kontrol etmelidir.  
  
 Aşağıdaki tabloda mevcut istatistiksel değerler açıklanmaktadır. Tek tek değerler için anahtar adlarının, Microsoft .NET çerçevesinin bölgesel sürümlerinde yerelleştirilmediğini unutmayın.  
  
|Anahtar adı|Açıklama|  
|--------------|-----------------|  
|`BuffersReceived`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra SQL Server sağlayıcı tarafından alınan tablo veri akışı (TDS) paketlerinin sayısını döndürür.|  
|`BuffersSent`|İstatistikler etkinleştirildikten sonra sağlayıcı tarafından SQL Server gönderilen TDS paketlerinin sayısını döndürür. Büyük komutlar, birden çok arabellek gerektirebilir. Örneğin, sunucuya büyük bir komut gönderiliyorsa ve altı paket gerektiriyorsa, `ServerRoundtrips` bunlardan biri ile artırılır ve `BuffersSent` altı ile artırılır.|  
|`BytesReceived`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirmişse, SQL Server sağlayıcı tarafından alınan TDS paketlerindeki veri bayt sayısını döndürür.|  
|`BytesSent`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra TDS paketlerindeki SQL Server gönderilen verilerin bayt sayısını döndürür.|  
|`ConnectionTime`|İstatistiklerin etkinleştirildikten sonra bağlantının açıldığı süre (milisaniye cinsinden) (bağlantı açılmadan önce istatistiklerin etkinleştirilmesi durumunda toplam bağlantı süresi).|  
|`CursorOpens`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bir imlecin bağlantı üzerinden kaç kez açık olduğunu döndürür.<br /><br /> SELECT deyimlerinin döndürdüğü salt okuma/iletme sonuçlarının işaretçiler kabul edilmediğini ve bu nedenle bu sayacı etkilemediğini unutmayın.|  
|`ExecutionTime`|Sağlayıcıdan alınan yanıtların yanı sıra sağlayıcının kendisindeki kodu çalıştırırken harcanan süre dahil olmak üzere, sağlayıcının, istatistikleri etkinleştirildikten sonra işlem harcadığı süreyi (milisaniye cinsinden) döndürür.<br /><br /> Zamanlama kodu içeren sınıflar şunlardır:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> Sýnýfý<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Performans açısından kritik üyeleri mümkün olduğunca küçük tutmak için aşağıdaki Üyeler zaman aşımına uğramaz:<br /><br /> Sýnýfý<br /><br /> This [] işleci (tüm aşırı yüklemeler)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> Getınt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklere etkinleştikten sonra bağlantı aracılığıyla yürütülen INSERT, DELETE ve UPDATE deyimlerinin toplam sayısını döndürür.|  
|`IduRows`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklere etkinleştikten sonra bağlantı aracılığıyla yürütülen INSERT, DELETE ve UPDATE deyimlerinin etkilediği toplam satır sayısını döndürür.|  
|`NetworkServerTime`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklerin etkinleştirildiğinden, sağlayıcının sunucudan yanıt bekletmeyi beklediği toplam süreyi (milisaniye cinsinden) döndürür.|  
|`PreparedExecs`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen hazırlanan komutların sayısını döndürür.|  
|`Prepares`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla hazırlanan deyimlerin sayısını döndürür.|  
|`SelectCount`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen SELECT deyimlerinin sayısını döndürür. Bu, imleçlerden satırları almak için Fetch deyimlerini içerir ve sonuna <xref:System.Data.SqlClient.SqlDataReader> ulaşıldığında SELECT deyimlerinin sayısı güncellenir.|  
|`SelectRows`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra seçilen satır sayısını döndürür. Bu sayaç, SQL deyimleri tarafından oluşturulan ve aslında çağıran tarafından tüketilmemiş olanlar dahil tüm satırları yansıtır. Örneğin, tüm sonuç kümesini okumadan önce bir veri okuyucuyu kapatmak sayıyı etkilemez. Bu, GETIRME deyimleri aracılığıyla imleçler aracılığıyla alınan satırları içerir.|  
|`ServerRoundtrips`|Bağlantının sunucuya gönderilme sayısını döndürür ve uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bir yanıt gönderir.|  
|`SumResultSets`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra kullanılan sonuç kümesi sayısını döndürür. Örneğin bu, istemciye döndürülen sonuç kümesini içerir. İmleçler için, her getirme veya engelleme getirme işlemi bağımsız bir sonuç kümesi olarak değerlendirilir.|  
|`Transactions`|Uygulama sağlayıcıyı kullanmaya başladıktan sonra başlatılan kullanıcı işlemleri sayısını döndürür ve geri alma dahil istatistikleri etkinleştirdi. Bir bağlantı otomatik işleme ile çalışıyorsa her komut bir işlem olarak kabul edilir.<br /><br /> Bu sayaç, işlemin daha sonra yapılıp yapılmayacağını veya geri döndürülüp döndürülmediğine bakılmaksızın BEGIN TRAN ifadesinin yürütüldüğü anda işlem sayısını artırır.|  
|`UnpreparedExecs`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen hazırlanmamış deyimlerin sayısını döndürür.|  
  
### <a name="retrieving-a-value"></a>Değer alma  
 Aşağıdaki konsol uygulaması, bir bağlantı üzerinde istatistiklerin nasıl etkinleştirileceğini, dört ayrı istatistiksel değerin nasıl alınacağını ve bunları konsol penceresine nasıl yazılacağını gösterir.  
  
> [!NOTE]
> Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır. Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklü olduğunu ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesini ortamınız için gereken şekilde değiştirin.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Tüm değerler alınıyor  
 Aşağıdaki konsol uygulaması, bir bağlantı üzerinde istatistiklerin nasıl etkinleştirileceğini, Numaralandırıcının kullanıldığı tüm kullanılabilir istatistik değerlerini almayı ve bunları konsol penceresine yazmayı gösterir.  
  
> [!NOTE]
> Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır. Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklü olduğunu ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesini ortamınız için gereken şekilde değiştirin.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
