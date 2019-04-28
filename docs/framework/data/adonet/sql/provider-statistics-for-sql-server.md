---
title: SQL Server için Sağlayıcı İstatistikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: b2b63719149c21eba493b3d8f2fc65309515bb0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646018"
---
# <a name="provider-statistics-for-sql-server"></a>SQL Server için Sağlayıcı İstatistikleri
SQL Server için .NET Framework veri sağlayıcısı, .NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı istatistikleri destekler. Ayarlayarak istatistikleri etkinleştirmelisiniz <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> nesnesini `True` sonra oluşturulmuş geçerli bir bağlantı nesnesi. İstatistikleri etkinleştirildikten sonra bunları "snapshot" zamanlı olarak alarak inceleyebilirsiniz bir <xref:System.Collections.IDictionary> aracılığıyla başvuru <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> yöntemi <xref:System.Data.SqlClient.SqlConnection> nesne. Listede bir ad/değer çifti dictionary girişlerinin kümesi olarak sıralar. Bu ad/değer çiftleri düzenlenmemiş olan. Herhangi bir zamanda çağırabilirsiniz <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> yöntemi <xref:System.Data.SqlClient.SqlConnection> sayaçları sıfırlamak için nesne. İstatistiği toplama etkin değil, bir özel durum oluşturulmaz. Ayrıca, varsa <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> olmadan adlı <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> önce çağrılmış, alınan her giriş için başlangıç değerlerini değerlerdir. İstatistikleri etkinleştirirseniz, bir süre için uygulamanızı çalıştırın ve istatistikleri devre dışı bırakmak, alınan değerlerin nereden istatistikleri devre dışı noktaya kadar toplanan değerleri yansıtır. Toplanan tüm istatistiksel bir bağlantı başına temelinde değerlerdir.  
  
## <a name="statistical-values-available"></a>İstatistiksel değerler var  
 Şu anda 18 farklı öğeler Microsoft SQL Server sağlayıcıdan kullanılabilir vardır. Kullanılabilir öğe sayısını erişilebilir **sayısı** özelliği <xref:System.Collections.IDictionary> arabirim tarafından döndürülen başvuru <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Ortak dil çalışma zamanı kullanan tüm sayaçları için sağlayıcı istatistikleri <xref:System.Int64> türü (**uzun** C# ve Visual Basic'te), 64 bit genişliğinde olan. En büyük değerini **Int64** veri türü tarafından tanımlandığı gibi **Int64. MaxValue** alan, ((2^63)-1.)). Sayaç değerlerini bu maksimum değeri ulaştığında, bunlar artık doğru kabul edilmelidir. Diğer bir deyişle **Int64. MaxValue**-1((2^63)-2) olan etkili bir şekilde herhangi bir istatistik için geçerli en büyük değer.  
  
> [!NOTE]
>  Bir sözlük sayısı, adları ve döndürülen istatistikleri sırasını gelecekte değişebilir olduğundan sağlayıcı istatistikleri döndürmek için kullanılır. Uygulamaları sözlükte bulunan belirli bir değerin dayanarak doğrulamamalısınız, ancak bunun yerine, değeri vardır ve buna göre dal denetlemeniz gerekir.  
  
 Aşağıdaki tabloda kullanılabilir geçerli istatistiksel değerleri açıklanmaktadır. Anahtar adları için ayrı ayrı değerlerin bölgesel Microsoft .NET Framework sürümleri arasında yerelleştirilmedi unutmayın.  
  
|Anahtar adı|Açıklama|  
|--------------|-----------------|  
|`BuffersReceived`|Tablo veri akışı (TDS) paketleri uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra SQL Server sağlayıcıdan alınan döndürür.|  
|`BuffersSent`|İstatistikleri etkinleştirdikten sonra SQL Server için sağlayıcı tarafından gönderilen TDS paketlerin sayısını döndürür. Büyük komutları birden fazla arabellek gerektirebilir. Örneğin, büyük bir komut sunucuya gönderilir ve altı paketleri gerektiriyorsa `ServerRoundtrips` bir artırılır ve `BuffersSent` altı artırılır.|  
|`BytesReceived`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra SQL Server sağlayıcıdan alınan TDS paketlerinde veri bayt sayısını döndürür.|  
|`BytesSent`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra SQL Server TDS paketlerinde gönderilen verilerin bayt sayısını döndürür.|  
|`ConnectionTime`|Bağlantı olduğu süreyi (milisaniye cinsinden) istatistikleri etkinleştirdikten sonra açılan (toplam bağlantı süresi istatistikleri bağlantı açmadan önce etkinleştirildiyse).|  
|`CursorOpens`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bir imleç bağlantı açıktı sayısını döndürür.<br /><br /> SELECT deyimleri tarafından döndürülen sonuçlar yalnızca/ileri-salt okunur imleçler dikkate alınmaz ve bu nedenle bu sayaç etkilemez unutmayın.|  
|`ExecutionTime`|Sağlayıcı istatistikleri etkinleştirdikten sonra işleme harcanan, sağlayıcısındaki kodu yürütürken harcanan süre yanı sıra sunucu yanıtları için beklerken geçen süre dahil olmak üzere süresi (milisaniye cinsinden) miktarı döndürür.<br /><br /> Zamanlama kodunu içeren sınıfları şunlardır:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Performans açısından kritik üyeleri olabildiğince küçük tutmak için aşağıdaki üyeleri zamanlanır değil:<br /><br /> SqlDataReader<br /><br /> Bu [] işleci (tüm aşırı yüklemeler)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDbNull|  
|`IduCount`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen deyimleri ekleme, silme ve güncelleştirme toplam sayısını döndürür.|  
|`IduRows`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen ekleme, silme ve güncelleştirme deyimlerin etkilediği satırları toplam sayısını döndürür.|  
|`NetworkServerTime`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra sağlayıcı'nın sunucudan yanıt bekleyen geçen süre (milisaniye cinsinden) miktarı döndürür.|  
|`PreparedExecs`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen hazırlanmış komutlarını sayısını döndürür.|  
|`Prepares`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden hazırlanmış deyimleri sayısını döndürür.|  
|`SelectCount`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen SELECT deyimleri sayısını döndürür. Bu satırları cursor'dan alınacak getirme deyimleri içerir ve SELECT deyimleri için sayısı güncelleştirilir, sonuna bir <xref:System.Data.SqlClient.SqlDataReader> ulaşıldı.|  
|`SelectRows`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra seçilen satır sayısını döndürür. Bu sayaç, aslında çağıran tarafından tüketilmeyen olanlar bile SQL deyimleri tarafından oluşturulan tüm satırları yansıtır. Örneğin, sonuç kümesinin tamamı okumadan önce bir veri okuyucu kapatma sayısı etkilemediğini. Bu, imleç getirme deyimleri üzerinden alınan satırları içerir.|  
|`ServerRoundtrips`|Komutlar ve sunucuya gönderilen ve uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bir yanıtı geri alındı bağlantı sayısını döndürür.|  
|`SumResultSets`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra döndürür, sonuç sayısını ayarlar kullanılır. Örneğin bu istemciye döndürülen herhangi bir sonuç kümesi içerir. İşaretçiler için bağımsız bir sonuç kümesi her getirme veya blok getirme işlemi olarak değerlendirilir.|  
|`Transactions`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikler, geri alma işlemleri dahil olmak üzere etkinleştirilmiş bir kez başlatılan kullanıcı işlemi sayısını döndürür. Bir bağlantı üzerinde otomatik tamamlama ile çalışıyorsa, her komut bir işlem olarak kabul edilir.<br /><br /> Bu sayaç, mi hareket kaydedilmiş veya daha sonra geri bağımsız olarak BAŞLAYAN TRAN deyim yürütülmeden hemen sonra işlem sayısını artırır.|  
|`UnpreparedExecs`|Uygulama sağlayıcısı kullanmaya başladı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen hazırlıksız deyimleri sayısını döndürür.|  
  
### <a name="retrieving-a-value"></a>Bir değer alma  
 Aşağıdaki konsol uygulamasında nasıl bir bağlantı istatistiklerle etkinleştirme, dört tekil istatistik değerleri almak ve konsol penceresine yazılmasına yarar gösterir.  
  
> [!NOTE]
>  Aşağıdaki örnek, örnek kullanır **AdventureWorks** veritabanını SQL Server'a dahildir. Örnek kodda sağlanan bağlantı dizesi, veritabanı yüklenir ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Tüm değerleri alma  
 Aşağıdaki konsol uygulamasında, bir bağlantı istatistiklerle etkinleştirme, numaralandırıcı kullanarak tüm kullanılabilen istatistik değerleri almak ve bunları konsola yazma işlemi gösterilmektedir.  
  
> [!NOTE]
>  Aşağıdaki örnek, örnek kullanır **AdventureWorks** veritabanını SQL Server'a dahildir. Örnek kodda sağlanan bağlantı dizesi, veritabanı yüklenir ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
