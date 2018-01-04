---
title: "SQL Server için sağlayıcı istatistikleri"
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
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 87f3dfbb3af6e638207d68540217f7134b95c354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="provider-statistics-for-sql-server"></a>SQL Server için sağlayıcı istatistikleri
.NET Framework sürüm 2.0 ile başlayarak, SQL Server için .NET Framework veri sağlayıcısı çalışma zamanı istatistikleri destekler. Ayarlayarak istatistikleri etkinleştirmelisiniz <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> nesnesine `True` oluşturulan geçerli bir bağlantı nesnesi sonra. İstatistikleri etkinleştirildikten sonra bunları "anlık görüntü olarak zaman içinde" alarak gözden geçirebilirsiniz bir <xref:System.Collections.IDictionary> aracılığıyla başvuru <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> yöntemi <xref:System.Data.SqlClient.SqlConnection> nesnesi. Ad/değer çifti dictionary girişlerinin bir dizi listesini numaralandırır. Bu ad/değer çiftleri sırasız şunlardır. Herhangi bir zamanda çağırabilirsiniz <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> yöntemi <xref:System.Data.SqlClient.SqlConnection> sayaçları sıfırlamak için nesne. Toplama istatistiği etkin değil, bir özel durum oluşturulmaz. Ayrıca, varsa <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> olmadan adlı <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ilk çağrılmış alınan her giriş için başlangıç değerlerini değerlerdir. İstatistikleri etkinleştirirseniz, bir süre için uygulamanızı çalıştırın ve istatistikleri devre dışı bırakmak, alınan değerleri nerede istatistikleri devre dışı bırakılan noktaya kadar toplanan değerleri yansıtır. Toplanan tüm istatistiksel bir bağlantı başına temelinde değerlerdir.  
  
## <a name="statistical-values-available"></a>İstatistiksel kullanılabilir değerler  
 Şu anda 18 farklı öğeler Microsoft SQL Server sağlayıcıdan kullanılabilir yok. Kullanılabilir öğelerin sayısı üzerinden erişilen **sayısı** özelliği <xref:System.Collections.IDictionary> arabirim tarafından döndürülen başvuru <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Tüm sayaçları sağlayıcı istatistikler için ortak dil çalışma zamanı kullanmak <xref:System.Int64> türü (**uzun** C# ve Visual Basic), 64 bit uzunluğunda olduğunu. En büyük değerini **Int64** tarafından tanımlanan veri türü, **Int64. MaxValue** alan, ((2^63)-1.)). Sayaç değerlerini bu en büyük değer ulaştığında, bunlar artık doğru dikkate alınmalıdır. Bunun anlamı **Int64. MaxValue**-1((2^63)-2) olan etkili bir şekilde tüm istatistiği için geçerli en büyük değer.  
  
> [!NOTE]
>  Bir sözlük sayısı, adları ve döndürülen istatistikleri sırasını gelecekte değişebilir çünkü sağlayıcı istatistikleri döndürmek için kullanılır. Uygulamaları sözlükte bulunan belirli bir değerin güvenmemelisiniz, ancak bunun yerine değeri vardır ve buna göre dal denetlemelisiniz.  
  
 Aşağıdaki tabloda kullanılabilir geçerli istatistiksel değerleri açıklanmaktadır. Bölgesel Microsoft .NET Framework sürümleri arasında değerlerini ayrı ayrı anahtar adları yerelleştirilmiş değil unutmayın.  
  
|Anahtar adı|Açıklama|  
|--------------|-----------------|  
|`BuffersReceived`|Tablo veri akışı (TDS) paketleri uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra sağlayıcının SQL Server tarafından alınan döndürür.|  
|`BuffersSent`|İstatistikleri etkinleştirdikten sonra SQL Server'a sağlayıcı tarafından gönderilen TDS paketlerin sayısını döndürür. Büyük komutları birden çok arabellek gerektirebilir. Örneğin, büyük bir komut sunucuya gönderilir ve altı paketleri gerektiriyorsa `ServerRoundtrips` bir artırılır ve `BuffersSent` altı tarafından artırılır.|  
|`BytesReceived`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra SQL Server'ın sağlayıcısı tarafından alınan TDS paketlerde veri baytlarının miktarını döndürür.|  
|`BytesSent`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra SQL Server'a TDS paketlerinde gönderilen veri baytı sayısı sayısını döndürür.|  
|`ConnectionTime`|Bağlantı kaldırıldı süre (milisaniye olarak) miktarını istatistikleri etkinleştirdikten sonra açılan (toplam bağlantı süresi istatistikleri bağlantı açmadan önce etkinleştirilmişse).|  
|`CursorOpens`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bir imleç bağlantı üzerinden açık sayısını döndürür.<br /><br /> SELECT deyimleri tarafından döndürülen yalnızca/ileri-salt okunur sonuçları imleçler dikkate alınmaz ve bu nedenle bu sayaç etkilemez unutmayın.|  
|`ExecutionTime`|Toplam süreyi (milisaniye cinsinden) sağlayıcı istatistikleri etkinleştirildikten sonra işleme harcanan, saatin yanı sıra, sunucunun yanıt beklerken harcanan süre dahil olmak üzere sağlayıcı kod çalıştırırken harcadığı döndürür.<br /><br /> Zamanlama kod dahil sınıfları şunlardır:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Performans açısından kritik üyeleri olabildiğince küçük tutmak için aşağıdaki üyeleri zamanlanır değil:<br /><br /> SqlDataReader<br /><br /> Bu [] işleci (tüm aşırı)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> Getınt16<br /><br /> Getınt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDbNull|  
|`IduCount`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen ekleme, silme ve güncelleştirme deyimleri toplam sayısını döndürür.|  
|`IduRows`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen ekleme, silme ve güncelleştirme deyimleri tarafından etkilenen satırların toplam sayısını döndürür.|  
|`NetworkServerTime`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra sağlayıcının'ın sunucudan yanıt beklerken harcanan süre (milisaniye cinsinden) toplu miktarını döndürür.|  
|`PreparedExecs`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen hazırlıklı komutlarını sayısını döndürür.|  
|`Prepares`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden prepared deyimleri sayısını döndürür.|  
|`SelectCount`|SELECT deyimi sonra uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkin olduğundan bağlantı üzerinden yürütülen sayısını döndürür. Bu imleçler satır almak için FETCH deyimleri içerir ve SELECT deyimi için sayısı güncelleştirilir zaman sonuna bir <xref:System.Data.SqlClient.SqlDataReader> ulaşıldı.|  
|`SelectRows`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra seçilen satır sayısını döndürür. Bu sayaç, aslında çağıran tarafından tüketilmeyen olanlar bile SQL deyimleri tarafından oluşturulan tüm satırları yansıtır. Örneğin, tüm sonuç kümesini okumadan önce bir veri okuyucu kapatma sayısı onaydan etkilenmez. Bu, imleçler FETCH deyimlerinin üzerinden alınan satırları içerir.|  
|`ServerRoundtrips`|Bağlantının komutları ve sunucuya gönderilen ve uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bir yanıtı geri alındı sayısını döndürür.|  
|`SumResultSets`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra sonuç sayısını ayarlar veya döndürür kullanıldı. Bu istemciye döndürülen herhangi bir sonuç kümesi örneğin içerir. İmleçler için her getirme veya blok getirme işlemi bağımsız sonuç kümesi olarak kabul edilir.|  
|`Transactions`|Uygulama sağlayıcısını kullanarak başlatıldığından ve istatistikler, geri alma dahil olmak üzere etkinleştirilmiş bir kez başlatılan kullanıcı işlemleri sayısını döndürür. Bağlantı otomatik tamamlama üzerinde çalışıyorsa, her komutun bir işlem olarak kabul edilir.<br /><br /> Olup işlem yürütülmeli veya geri daha sonra bağımsız olarak başlamak TRAN deyimine yürütüldükten hemen sonra Bu sayaç işlem sayısını artırır.|  
|`UnpreparedExecs`|Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen hazırlıksız deyimleri sayısını döndürür.|  
  
### <a name="retrieving-a-value"></a>Bir değer alma  
 Aşağıdaki konsol uygulaması, bir bağlantı istatistiklerle etkinleştirmek, dört tekil istatistik değerleri almak ve konsol penceresine yazamadı gösterilmektedir.  
  
> [!NOTE]
>  Aşağıdaki örnek, örnek kullanır **AdventureWorks** ile birlikte gelen veritabanı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Örnek kodda sağlanan bağlantı dizesi veritabanına yüklenir ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.  
  
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
 Aşağıdaki konsol uygulaması, bir bağlantı istatistiklerle etkinleştirmek, numaralandırıcı kullanarak tüm kullanılabilir istatistik değerleri almak ve konsol penceresine yazma gösterilmektedir.  
  
> [!NOTE]
>  Aşağıdaki örnek, örnek kullanır **AdventureWorks** ile birlikte gelen veritabanı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. Örnek kodda sağlanan bağlantı dizesi veritabanına yüklenir ve yerel bilgisayarda kullanılabilir olduğunu varsayar. Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server ve ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
