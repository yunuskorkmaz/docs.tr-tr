---
title: SqlDependency ile Değişiklikleri Algılama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 3719188064388b00c756dd037d4a475ca6debd13
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782427"
---
# <a name="detecting-changes-with-sqldependency"></a>SqlDependency ile Değişiklikleri Algılama

Sorgu sonuçlarının başlangıçta alınanlardan farklı olduğunu <xref:System.Data.SqlClient.SqlCommand> algılamak için bir nesnesiileilişkilendirilebilir.<xref:System.Data.SqlClient.SqlDependency> Ayrıca `OnChange` olaya bir temsilci atayabilirsiniz, bu da bir ilişkili komutun sonuçları değiştiğinde harekete geçirsiniz. Komutu yürütmeden önce komutunu <xref:System.Data.SqlClient.SqlDependency> komutuyla ilişkilendirmeniz gerekir. `HasChanges` Özelliği<xref:System.Data.SqlClient.SqlDependency> , verilerin ilk alınmasından sonra sorgu sonuçlarının değişip değişmediğini tespit etmek için de kullanılabilir.

## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri

Bağımlılık altyapısı, belirli bir komut <xref:System.Data.SqlClient.SqlConnection> için temeldeki verilerin değiştiği <xref:System.Data.SqlClient.SqlDependency.Start%2A> bildirimleri almak için çağrıldığında açılan bir öğesine bağımlıdır. Bir istemcinin çağrıyı `SqlDependency.Start` başlatma yeteneği, <xref:System.Data.SqlClient.SqlClientPermission> ve kod erişimi güvenlik özniteliklerinin kullanımı ile denetlenir. Daha fazla bilgi için bkz. [sorgu bildirimlerini](enabling-query-notifications.md) ve [kod erişimi güvenliğini etkinleştirme ve ADO.net](../code-access-security.md).

### <a name="example"></a>Örnek

Aşağıdaki adımlarda, bir bağımlılık bildirme, komut yürütme ve sonuç kümesi değiştiğinde bildirim alma işlemleri gösterilmektedir:

1. Sunucusuyla bir `SqlDependency` bağlantı başlatın.

2. Sunucusuna <xref:System.Data.SqlClient.SqlConnection> bağlanmak <xref:System.Data.SqlClient.SqlCommand> için ve nesneleri oluşturun ve bir Transact-SQL ifadesini tanımlayın.

3. Yeni `SqlDependency` bir nesne oluşturun veya var olanı kullanın ve `SqlCommand` nesneye bağlayın. Bu, dahili olarak bir <xref:System.Data.Sql.SqlNotificationRequest> nesnesi oluşturur ve bunu gerektiğinde komut nesnesine bağlar. Bu bildirim isteği, bu `SqlDependency` nesneyi benzersiz bir şekilde tanımlayan bir iç tanımlayıcı içeriyor. Ayrıca, zaten etkin değilse istemci dinleyicisini başlatır.

4. Bir olay işleyicisini `OnChange` `SqlDependency` nesnenin olayına abone olma.

5. `Execute` Nesnesinin yöntemlerinden`SqlCommand` herhangi birini kullanarak komutu yürütün. Komut, bildirim nesnesine bağlandığı için, sunucu bir bildirim oluşturması gerektiğini algılar ve sıra bilgileri, bağımlılıklar kuyruğuna işaret eder.

6. `SqlDependency` Sunucu bağlantısını durdurun.

Herhangi bir Kullanıcı daha sonra temel alınan verileri değiştirirse, Microsoft SQL Server böyle bir değişiklik için bekleyen bir bildirim olduğunu algılar ve oluşturulan temel `SqlConnection` aracılığıyla istemciye işlenmiş ve iletilen bir bildirim gönderir. çağırarak `SqlDependency.Start`. İstemci dinleyicisi, geçersiz kılma iletisini alır. İstemci dinleyicisi daha sonra ilişkili `SqlDependency` nesneyi bulur ve `OnChange` olayı tetikler.

Aşağıdaki kod parçası, örnek bir uygulama oluşturmak için kullandığınız tasarım modelini gösterir.

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
        ' Maintain the refernce in a class member.
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

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](query-notifications-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
