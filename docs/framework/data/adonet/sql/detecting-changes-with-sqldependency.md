---
title: SqlDependency ile değişiklikleri algılama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: a25afbe0124f7870df886a1e26e0df2a0716b205
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="detecting-changes-with-sqldependency"></a>SqlDependency ile değişiklikleri algılama
A <xref:System.Data.SqlClient.SqlDependency> nesne ilişkilendirilebilir bir <xref:System.Data.SqlClient.SqlCommand> sorgu sonuçları ilk başta farklı algılamak için. Ayrıca bir temsilci atayabilirsiniz `OnChange` sonuçları için ilişkili bir komut değiştirdiğinizde, ateşlenir olay. İlişkilendirmeniz gerekir <xref:System.Data.SqlClient.SqlDependency> komutu yürütmeden önce komutu. `HasChanges` Özelliği <xref:System.Data.SqlClient.SqlDependency> verileri ilk alındığından beri sorgu sonuçlarını değişip değişmediğini için de kullanılabilir.  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Bağımlılık altyapı dayanan bir <xref:System.Data.SqlClient.SqlConnection> , ne zaman açıldığında <xref:System.Data.SqlClient.SqlDependency.Start%2A> temel alınan veriler için verilen komut değişti bildirimleri almak için çağrılır. Çağrısı başlatmak bir istemci özelliğini `SqlDependency.Start` kullanılarak denetlenir <xref:System.Data.SqlClient.SqlClientPermission> ve kod erişim güvenliği öznitelikleri. Daha fazla bilgi için bkz: [etkinleştirme sorgu bildirimleri](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) ve [kod erişim güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).  
  
### <a name="example"></a>Örnek  
 Aşağıdaki adımları bir bağımlılık bildirmek için komut yürütme nasıl çalışılacağını ve değişiklikleri sonuç kümesi, bir bildirim alırsınız:  
  
1.  Başlatma bir `SqlDependency` sunucu bağlantısı.  
  
2.  Oluşturma <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> sunucuya bağlanın ve bir Transact-SQL deyimi tanımlamak için nesneleri.  
  
3.  Yeni bir `SqlDependency` nesnesi veya mevcut bir kullanın ve onu bağladıktan `SqlCommand` nesnesi. Dahili olarak, bu oluşturur bir <xref:System.Data.Sql.SqlNotificationRequest> nesne ve gerektiği gibi komut nesnesine bağlar. Bu bildirim isteği bu benzersiz olarak tanımlayan bir iç tanımlayıcı içeren `SqlDependency` nesnesi. Zaten etkin değilse, aynı zamanda istemci dinleyicisini başlatır.  
  
4.  Bir olay işleyicisi abone `OnChange` olayı `SqlDependency` nesnesi.  
  
5.  Herhangi birini kullanarak komutu yürütün `Execute` yöntemlerinin `SqlCommand` nesnesi. Komut bildirim nesnesine bağlı olduğundan, sunucunun bir bildirim oluşturmalısınız ve sırası bilgilerini bağımlılıkları kuyruğuna işaret edecek tanır.  
  
6.  Durdur `SqlDependency` sunucu bağlantısı.  
  
 Herhangi bir kullanıcı daha sonra temel alınan veriler değişirse, Microsoft SQL Server, bu tür bir değişiklik için bekleyen bir bildirim arka plandaki aracılığıyla istemciye işlenen ve iletilen bir bildirim gönderir algılar ve `SqlConnection` oluşturulmuş çağırarak `SqlDependency.Start`. İstemci dinleyicisi geçersiz kılma iletisini alır. İstemci dinleyicisi ardından ilişkili bulur `SqlDependency` nesne ve ateşlenir `OnChange` olay.  
  
 Aşağıdaki kod parçası, örnek bir uygulama oluşturmak için kullanacağınız tasarım deseni gösterir.  
  
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
        // Maintain the refence in a class member.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
