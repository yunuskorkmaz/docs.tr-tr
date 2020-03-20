---
title: SQL Server için Sağlayıcı İstatistikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 5e37a04ff731a99664d636e0d4175f99214c2646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174517"
---
# <a name="provider-statistics-for-sql-server"></a>SQL Server için Sağlayıcı İstatistikleri
.NET Framework sürüm 2.0 ile başlayarak, SQL Server için .NET Framework Data Provider çalışma zamanı istatistiklerini destekler. Oluşturulan geçerli bir bağlantı <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> nesnesi sonra <xref:System.Data.SqlClient.SqlConnection> nesnenin `True` özelliğini ayarlayarak istatistikleri etkinleştirmeniz gerekir. İstatistikler etkinleştirildikten sonra, <xref:System.Collections.IDictionary> <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> <xref:System.Data.SqlClient.SqlConnection> nesnenin yöntemi yle bir başvuru alarak bunları "zaman içinde anlık görüntü" olarak gözden geçirebilirsiniz. Listeyi ad/değer çifti sözlük girişleri kümesi olarak sıralarsınız. Bu ad/değer çiftleri sırasız. İstediğiniz zaman, sayaçları <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> sıfırlamak <xref:System.Data.SqlClient.SqlConnection> için nesnenin yöntemini arayabilirsiniz. İstatistik toplama etkinleştirilemediyse, bir özel durum oluşturulmadı. Ayrıca, önce <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> çağrılmadan <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> çağrılırsa, alınan değerler her giriş için başlangıç değerleridir. İstatistikleri etkinleştiriseniz, uygulamanızı bir süre çalıştırır ve istatistikleri devre dışı bıraktığınızda, alınan değerler toplanan değerleri istatistiklerin devre dışı bırakıldığı noktaya kadar yansıtır. Toplanan tüm istatistiksel değerler bağlantı başına ayrı ayrıdır.  
  
## <a name="statistical-values-available"></a>Mevcut İstatistiksel Değerler  
 Şu anda Microsoft SQL Server sağlayıcısından 18 farklı öğe mevcuttur. Kullanılabilir öğelerin sayısı, '' tarafından <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>döndürülen <xref:System.Collections.IDictionary> arabirim referansının **Count** özelliği üzerinden erişilebilir. Sağlayıcı istatistikleri için tüm sayaçlar, 64 <xref:System.Int64> bit genişliğinde olan ortak dil çalışma zamanı türünü (C# ve Visual Basic'te**uzun)** kullanır. **int64** tarafından tanımlanan int64 veri türünün maksimum **değeri. MaxValue** alanı, ((2^63)-1)). Sayaçların değerleri bu maksimum değere ulaştığında, artık doğru olarak kabul edilmemelidir. Bu **int64 anlamına gelir. MaxValue**-1((2^63)-2) herhangi bir istatistik için etkili bir şekilde en büyük geçerli değerdir.  
  
> [!NOTE]
> Döndürülen istatistiklerin sayısı, adları ve sırası gelecekte değişebileceğinden, sağlayıcı istatistiklerini döndürmek için sözlük kullanılır. Uygulamalar sözlükte bulunan belirli bir değere dayanmamalı, bunun yerine değerin var olup olmadığını ve buna göre dallanıp dallanmadığını kontrol etmelidir.  
  
 Aşağıdaki tabloda mevcut istatistiksel değerler açıklanmaktadır. Tek tek değerlerin anahtar adlarının Microsoft .NET Framework'ün bölgesel sürümlerinde yerelleştirilmediğini unutmayın.  
  
|Anahtar Adı|Açıklama|  
|--------------|-----------------|  
|`BuffersReceived`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra sağlayıcı tarafından SQL Server'dan alınan tabular veri akışı (TDS) paketlerinin sayısını verir.|  
|`BuffersSent`|İstatistikler etkinleştirildikten sonra sağlayıcı tarafından SQL Server'a gönderilen TDS paketlerinin sayısını verir. Büyük komutlar birden çok arabellek gerektirebilir. Örneğin, sunucuya büyük bir komut gönderilirse ve altı `ServerRoundtrips` paket gerektiriyorsa, `BuffersSent` bir komut uğruyla artımlanır ve altı ile artımlanır.|  
|`BytesReceived`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra sağlayıcı tarafından SQL Server'dan alınan TDS paketlerindeki bayt veri sayısını verir.|  
|`BytesSent`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra TDS paketlerinde SQL Server'a gönderilen veri baytlarının sayısını verir.|  
|`ConnectionTime`|İstatistikler etkinleştirildikten sonra bağlantının açıldığı süre (milisaniye cinsinden) (bağlantıyı açmadan önce istatistikler etkinleştirilmişse toplam bağlantı süresi).|  
|`CursorOpens`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra imleç bağlantı üzerinden kaç kez açık olduğunu verir.<br /><br /> SELECT deyimleri tarafından döndürülen salt/forward sonuçlarının imleç olarak kabul edilmeyeceğini ve bu nedenle bu sayacı etkilemediğini unutmayın.|  
|`ExecutionTime`|İstatistikler etkinleştirildikten sonra sağlayıcının işlemek için harcadığı kümülatif süreyi (milisaniye cinsinden) sunucudan gelen yanıtları beklerken harcanan süre ve sağlayıcının kendi içinde kodu yürütmek için harcanan süre de dahil olmak üzere döndürür.<br /><br /> Zamanlama kodu içeren sınıflar şunlardır:<br /><br /> Sqlconnection<br /><br /> Sqlcommand<br /><br /> Sqldatareader<br /><br /> Sqldataadapter<br /><br /> Sqltransaction<br /><br /> Sqlcommandbuilder<br /><br /> Performans açısından kritik üyeleri mümkün olduğunca küçük tutmak için aşağıdaki üyelere zaman landırılmaz:<br /><br /> Sqldatareader<br /><br /> bu[] işleci (tüm aşırı yüklemeler)<br /><br /> GetBoolean<br /><br /> Getchar<br /><br /> GetDateTime<br /><br /> GetOncimal<br /><br /> Getdouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> Getordinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> SqlByte'ı Alın<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> SqlInt16'yı alın<br /><br /> SqlInt32'yi alın<br /><br /> SqlInt64'i alın<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> ısdbnull|  
|`IduCount`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen INSERT, DELETE ve UPDATE deyimlerinin toplam sayısını verir.|  
|`IduRows`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen INSERT, DELETE ve UPDATE deyimlerinden etkilenen toplam satır sayısını verir.|  
|`NetworkServerTime`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra sağlayıcının sunucudan gelen yanıtları beklemek için harcadığı kümülatif süreyi (milisaniye cinsinden) döndürür.|  
|`PreparedExecs`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen hazırlanan komutların sayısını döndürür.|  
|`Prepares`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden hazırlanan deyim sayısını verir.|  
|`SelectCount`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen SELECT deyimlerinin sayısını verir. Bu imleçlerden satır almak için GETIR deyimleri içerir ve SELECT deyimleri için <xref:System.Data.SqlClient.SqlDataReader> sayı bir sonuna ulaşıldığında güncelleştirilir.|  
|`SelectRows`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra seçilen satır sayısını döndürür. Bu sayaç, SQL deyimleri tarafından oluşturulan tüm satırları, hatta arayan tarafından gerçekten tüketilemeyen satırları yansıtır. Örneğin, tüm sonuç kümesini okumadan önce bir veri okuyucuyu kapatmak sayımı etkilemez. Bu, imleçlerden FETCH deyimleri aracılığıyla alınan satırları içerir.|  
|`ServerRoundtrips`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantının komutları sunucuya kaç kez gönderdiğini ve yanıtını geri aldığı sayısını döndürür.|  
|`SumResultSets`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra kullanılan sonuç kümelerinin sayısını verir. Örneğin, bu istemciye döndürülen herhangi bir sonuç kümesini içerir. İmleçler için, her getirme veya engelleme işlemi bağımsız bir sonuç kümesi olarak kabul edilir.|  
|`Transactions`|Uygulama sağlayıcıyı kullanmaya başladıktan ve geri almalar da dahil olmak üzere istatistikleri etkinleştirdikten sonra başlatılan kullanıcı hareketleri sayısını döndürür. Otomatik commit ile çalışan bir bağlantı varsa, her komut bir işlem olarak kabul edilir.<br /><br /> Bu sayaç, işlemin kaydedilip işlenmediğine veya daha sonra geri alınıp alınmayacağına bakılmaksızın, BEGIN TRAN deyimi yürütülür yürütülür çalıştırılmaz hareket sayısını da yukarıya doğru şarampole bırakır.|  
|`UnpreparedExecs`|Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen hazırlıksız deyimlerin sayısını verir.|  
  
### <a name="retrieving-a-value"></a>Bir Değer Alma  
 Aşağıdaki konsol uygulaması, bir bağlantıdaki istatistikleri nasıl etkinleştireceklerini, dört ayrı istatistik değerini nasıl alsüreceğini ve bunları konsol penceresine nasıl yazarak yazacaklarını gösterir.  
  
> [!NOTE]
> Aşağıdaki örnek, SQL Server ile birlikte verilen örnek **AdventureWorks** veritabanını kullanır. Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklenmiş ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesini ortamınız için gerektiği gibi değiştirin.  
  
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
  
### <a name="retrieving-all-values"></a>Tüm Değerleri Alma  
 Aşağıdaki konsol uygulaması, bir bağlantıdaki istatistikleri nasıl etkinleştireceklerini, kullanılabilir tüm istatistik değerlerini sayısallaştırıcıyı kullanarak nasıl alsüreceğini ve konsol penceresine nasıl yazarak yazacaklarını gösterir.  
  
> [!NOTE]
> Aşağıdaki örnek, SQL Server ile birlikte verilen örnek **AdventureWorks** veritabanını kullanır. Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklenmiş ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesini ortamınız için gerektiği gibi değiştirin.  
  
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
