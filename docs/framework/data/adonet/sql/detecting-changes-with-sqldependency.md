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
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="75242-102">SqlDependency ile Değişiklikleri Algılama</span><span class="sxs-lookup"><span data-stu-id="75242-102">Detecting Changes with SqlDependency</span></span>

<span data-ttu-id="75242-103">Sorgu sonuçlarının başlangıçta alınanlardan farklı olduğunu <xref:System.Data.SqlClient.SqlCommand> algılamak için bir nesnesiileilişkilendirilebilir.<xref:System.Data.SqlClient.SqlDependency></span><span class="sxs-lookup"><span data-stu-id="75242-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="75242-104">Ayrıca `OnChange` olaya bir temsilci atayabilirsiniz, bu da bir ilişkili komutun sonuçları değiştiğinde harekete geçirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75242-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="75242-105">Komutu yürütmeden önce komutunu <xref:System.Data.SqlClient.SqlDependency> komutuyla ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="75242-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="75242-106">`HasChanges` Özelliği<xref:System.Data.SqlClient.SqlDependency> , verilerin ilk alınmasından sonra sorgu sonuçlarının değişip değişmediğini tespit etmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75242-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="75242-107">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="75242-107">Security Considerations</span></span>

<span data-ttu-id="75242-108">Bağımlılık altyapısı, belirli bir komut <xref:System.Data.SqlClient.SqlConnection> için temeldeki verilerin değiştiği <xref:System.Data.SqlClient.SqlDependency.Start%2A> bildirimleri almak için çağrıldığında açılan bir öğesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="75242-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="75242-109">Bir istemcinin çağrıyı `SqlDependency.Start` başlatma yeteneği, <xref:System.Data.SqlClient.SqlClientPermission> ve kod erişimi güvenlik özniteliklerinin kullanımı ile denetlenir.</span><span class="sxs-lookup"><span data-stu-id="75242-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="75242-110">Daha fazla bilgi için bkz. [sorgu bildirimlerini](enabling-query-notifications.md) ve [kod erişimi güvenliğini etkinleştirme ve ADO.net](../code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="75242-110">For more information, see [Enabling Query Notifications](enabling-query-notifications.md) and [Code Access Security and ADO.NET](../code-access-security.md).</span></span>

### <a name="example"></a><span data-ttu-id="75242-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="75242-111">Example</span></span>

<span data-ttu-id="75242-112">Aşağıdaki adımlarda, bir bağımlılık bildirme, komut yürütme ve sonuç kümesi değiştiğinde bildirim alma işlemleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="75242-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>

1. <span data-ttu-id="75242-113">Sunucusuyla bir `SqlDependency` bağlantı başlatın.</span><span class="sxs-lookup"><span data-stu-id="75242-113">Initiate a `SqlDependency` connection to the server.</span></span>

2. <span data-ttu-id="75242-114">Sunucusuna <xref:System.Data.SqlClient.SqlConnection> bağlanmak <xref:System.Data.SqlClient.SqlCommand> için ve nesneleri oluşturun ve bir Transact-SQL ifadesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="75242-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>

3. <span data-ttu-id="75242-115">Yeni `SqlDependency` bir nesne oluşturun veya var olanı kullanın ve `SqlCommand` nesneye bağlayın.</span><span class="sxs-lookup"><span data-stu-id="75242-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="75242-116">Bu, dahili olarak bir <xref:System.Data.Sql.SqlNotificationRequest> nesnesi oluşturur ve bunu gerektiğinde komut nesnesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="75242-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="75242-117">Bu bildirim isteği, bu `SqlDependency` nesneyi benzersiz bir şekilde tanımlayan bir iç tanımlayıcı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="75242-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="75242-118">Ayrıca, zaten etkin değilse istemci dinleyicisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="75242-118">It also starts the client listener if it is not already active.</span></span>

4. <span data-ttu-id="75242-119">Bir olay işleyicisini `OnChange` `SqlDependency` nesnenin olayına abone olma.</span><span class="sxs-lookup"><span data-stu-id="75242-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>

5. <span data-ttu-id="75242-120">`Execute` Nesnesinin yöntemlerinden`SqlCommand` herhangi birini kullanarak komutu yürütün.</span><span class="sxs-lookup"><span data-stu-id="75242-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="75242-121">Komut, bildirim nesnesine bağlandığı için, sunucu bir bildirim oluşturması gerektiğini algılar ve sıra bilgileri, bağımlılıklar kuyruğuna işaret eder.</span><span class="sxs-lookup"><span data-stu-id="75242-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>

6. <span data-ttu-id="75242-122">`SqlDependency` Sunucu bağlantısını durdurun.</span><span class="sxs-lookup"><span data-stu-id="75242-122">Stop the `SqlDependency` connection to the server.</span></span>

<span data-ttu-id="75242-123">Herhangi bir Kullanıcı daha sonra temel alınan verileri değiştirirse, Microsoft SQL Server böyle bir değişiklik için bekleyen bir bildirim olduğunu algılar ve oluşturulan temel `SqlConnection` aracılığıyla istemciye işlenmiş ve iletilen bir bildirim gönderir. çağırarak `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="75242-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="75242-124">İstemci dinleyicisi, geçersiz kılma iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="75242-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="75242-125">İstemci dinleyicisi daha sonra ilişkili `SqlDependency` nesneyi bulur ve `OnChange` olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="75242-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>

<span data-ttu-id="75242-126">Aşağıdaki kod parçası, örnek bir uygulama oluşturmak için kullandığınız tasarım modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="75242-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="75242-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75242-127">See also</span></span>

- [<span data-ttu-id="75242-128">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="75242-128">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="75242-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="75242-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
