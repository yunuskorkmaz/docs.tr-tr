---
title: SqlDependency ile Değişiklikleri Algılama
description: Sorgu sonuçlarının ADO.NET içinde ilk olarak alınanlardan farklı olduğunu algılamak için bir SqlDependency nesnesini SqlCommand ile ilişkilendirin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: b196d42477e1778c45df64b1390502645fdd649d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286474"
---
# <a name="detecting-changes-with-sqldependency"></a>SqlDependency ile Değişiklikleri Algılama

<xref:System.Data.SqlClient.SqlDependency> <xref:System.Data.SqlClient.SqlCommand> Sorgu sonuçlarının başlangıçta alınanlardan farklı olduğunu algılamak için bir nesnesi ile ilişkilendirilebilir. Ayrıca olaya bir temsilci atayabilirsiniz `OnChange` , bu da bir ilişkili komutun sonuçları değiştiğinde harekete geçirsiniz. <xref:System.Data.SqlClient.SqlDependency>Komutu yürütmeden önce komutunu komutuyla ilişkilendirmeniz gerekir. `HasChanges`Özelliği, <xref:System.Data.SqlClient.SqlDependency> verilerin ilk alınmasından sonra sorgu sonuçlarının değişip değişmediğini tespit etmek için de kullanılabilir.

## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler

Bağımlılık altyapısı, <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlDependency.Start%2A> belirli bir komut için temeldeki verilerin değiştiği bildirimleri almak için çağrıldığında açılan bir öğesine bağımlıdır. Bir istemcinin çağrıyı başlatma yeteneği, `SqlDependency.Start` <xref:System.Data.SqlClient.SqlClientPermission> ve kod erişimi güvenlik özniteliklerinin kullanımı ile denetlenir. Daha fazla bilgi için bkz. [sorgu bildirimlerini](enabling-query-notifications.md) ve [kod erişimi güvenliğini etkinleştirme ve ADO.net](../code-access-security.md).

### <a name="example"></a>Örnek

Aşağıdaki adımlarda, bir bağımlılık bildirme, komut yürütme ve sonuç kümesi değiştiğinde bildirim alma işlemleri gösterilmektedir:

1. Sunucusuyla bir `SqlDependency` bağlantı başlatın.

2. <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlCommand> Sunucusuna bağlanmak için ve nesneleri oluşturun ve bir Transact-SQL ifadesini tanımlayın.

3. Yeni bir `SqlDependency` nesne oluşturun veya var olanı kullanın ve `SqlCommand` nesneye bağlayın. Bu, dahili olarak bir <xref:System.Data.Sql.SqlNotificationRequest> nesnesi oluşturur ve bunu gerektiğinde komut nesnesine bağlar. Bu bildirim isteği, bu nesneyi benzersiz bir şekilde tanımlayan bir iç tanımlayıcı içeriyor `SqlDependency` . Ayrıca, zaten etkin değilse istemci dinleyicisini başlatır.

4. Bir olay işleyicisini `OnChange` nesnenin olayına abone olma `SqlDependency` .

5. Nesnesinin yöntemlerinden herhangi birini kullanarak komutu yürütün `Execute` `SqlCommand` . Komut, bildirim nesnesine bağlandığı için, sunucu bir bildirim oluşturması gerektiğini algılar ve sıra bilgileri, bağımlılıklar kuyruğuna işaret eder.

6. `SqlDependency`Sunucu bağlantısını durdurun.

Herhangi bir Kullanıcı daha sonra temel alınan verileri değiştirirse, Microsoft SQL Server böyle bir değişiklik için bekleyen bir bildirim olduğunu algılar ve tarafından oluşturulan temel aracılığıyla istemciye işlenmiş ve iletilen bir bildirim gönderir `SqlConnection` `SqlDependency.Start` . İstemci dinleyicisi, geçersiz kılma iletisini alır. İstemci dinleyicisi daha sonra ilişkili nesneyi bulur `SqlDependency` ve `OnChange` olayı tetikler.

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
