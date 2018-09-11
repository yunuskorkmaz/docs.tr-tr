---
title: SqlDependency ile değişiklikleri algılama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 63d6a17e5aaf3e5d39ed0eda288e75c071be4d73
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268360"
---
# <a name="detecting-changes-with-sqldependency"></a>SqlDependency ile değişiklikleri algılama
A <xref:System.Data.SqlClient.SqlDependency> nesne ilişkili bir <xref:System.Data.SqlClient.SqlCommand> sorgu sonuçları başlangıçta alınan farklı algılamak için. Bir temsilciye de atayabilirsiniz `OnChange` olay sonuçları için ilişkili bir komut değiştirdiğinizde, ateşlenir. İlişkilendirmeniz gerekir <xref:System.Data.SqlClient.SqlDependency> komutu yürütmeden önce komutu. `HasChanges` Özelliği <xref:System.Data.SqlClient.SqlDependency> veri ilk alındıktan sonra sorgu sonuçları değiştirdiyseniz belirlemek için de kullanılabilir.  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Bağımlılık altyapı dayanan bir <xref:System.Data.SqlClient.SqlConnection> ne zaman açıldığı <xref:System.Data.SqlClient.SqlDependency.Start%2A> belirli bir komut için temel alınan veriler değişmiştir bildirimleri almak için çağrılır. Çağrı başlatmak bir istemci `SqlDependency.Start` kullanımının denetlenir <xref:System.Data.SqlClient.SqlClientPermission> ve kod erişimi güvenlik öznitelikleri. Daha fazla bilgi için [sorgu bildirimleri etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) ve [kod erişimi güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki adımlar, bir bağımlılık bildirin, komut yürütme işlemini göstermektedir ve değişiklikleri sonuç kümesi bir bildirim alırsınız:  
  
1.  Başlatan bir `SqlDependency` sunucu bağlantısı.  
  
2.  Oluşturma <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> nesneleri sunucuya bağlanın ve Transact-SQL deyimini tanımlayın.  
  
3.  Yeni bir `SqlDependency` nesnesi veya var olanı kullanın ve öğeyi `SqlCommand` nesne. Dahili olarak, bu oluşturur bir <xref:System.Data.Sql.SqlNotificationRequest> nesne ve gerektiğinde komut nesnesine bağlar. Bu bildirim isteği bu benzersiz olarak tanımlayan bir iç tanımlayıcı içeren `SqlDependency` nesne. Zaten etkin değilse, ayrıca istemci dinleyicisini başlatır.  
  
4.  Bir olay işleyicisi abone `OnChange` olayı `SqlDependency` nesne.  
  
5.  Herhangi bir komutu yürütme `Execute` yöntemlerinin `SqlCommand` nesne. Komut bildirim nesneye bağlı olduğundan, sunucunun bir bildirim oluşturmalısınız ve kuyruk bilgileri bağımlılıkları kuyruğa işaret edecek tanır.  
  
6.  Durdur `SqlDependency` sunucu bağlantısı.  
  
 Microsoft SQL Server herhangi bir kullanıcı daha sonra temel alınan verileri değişirse, bu tür bir değişiklik için bekleyen bir bildirim ve arka plandaki aracılığıyla istemciye işlenen ve iletilen bir bildirim gönderir algılar `SqlConnection` oluşturulmuş çağırarak `SqlDependency.Start`. İstemci dinleyici geçersiz kılma iletiyi alır. İstemci dinleyici ardından ilişkili bulur `SqlDependency` nesne ve ateşlenir `OnChange` olay.  
  
 Aşağıdaki kod parçası, örnek bir uygulama oluşturmak için kullanacağınız tasarım desenini gösterir.  
  
```vb  
Sub Initialization()  
    ' Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName)  
End Sub  
  
Sub SomeMethod()   
    ' Assume connection is an open SqlConnection.  
    ' Create a new SqlCommand object.  
    Using command As New SqlCommand( _  
      "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", _  
      connection)  
  
        ' Create a dependency and associate it with the SqlCommand.  
        Dim dependency As New SqlDependency(command)  
        ' Maintain the refence in a class member.  
        ' Subscribe to the SqlDependency event.  
        AddHandler dependency.OnChange, AddressOf OnDependencyChange  
  
        ' Execute the command.  
        Using reader = command.ExecuteReader()  
            ' Process the DataReader.  
        End Using  
    End Using  
End Sub   
  
' Handler method  
Sub OnDependencyChange(ByVal sender As Object, _  
    ByVal e As SqlNotificationEventArgs)   
    ' Handle the event (for example, invalidate this cache entry).  
End Sub  
  
Sub Termination()  
    ' Release the dependency  
    SqlDependency.Stop(connectionString, queueName)  
End Sub  
```  
  
```csharp  
void Initialization()  
{  
    // Create a dependency connection.  
    SqlDependency.Start(connectionString, queueName);  
}  
  
void SomeMethod()  
{  
    // Assume connection is an open SqlConnection.  
  
    // Create a new SqlCommand object.  
    using (SqlCommand command=new SqlCommand(  
        "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers",   
        connection))  
    {  
  
        // Create a dependency and associate it with the SqlCommand.  
        SqlDependency dependency=new SqlDependency(command);  
        // Maintain the reference in a class member.  
  
        // Subscribe to the SqlDependency event.  
        dependency.OnChange+=new  
           OnChangeEventHandler(OnDependencyChange);  
  
        // Execute the command.  
        using (SqlDataReader reader = command.ExecuteReader())  
        {  
            // Process the DataReader.  
        }  
    }  
}  
  
// Handler method  
void OnDependencyChange(object sender,   
   SqlNotificationEventArgs e )  
{  
  // Handle the event (for example, invalidate this cache entry).  
}  
  
void Termination()  
{  
    // Release the dependency.  
    SqlDependency.Stop(connectionString, queueName);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server'da Sorgu Bildirimleri](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
