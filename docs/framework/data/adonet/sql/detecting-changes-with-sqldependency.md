---
title: SqlDependency ile değişiklikleri algılama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
ms.openlocfilehash: 63d6a17e5aaf3e5d39ed0eda288e75c071be4d73
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508485"
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="efd92-102">SqlDependency ile değişiklikleri algılama</span><span class="sxs-lookup"><span data-stu-id="efd92-102">Detecting Changes with SqlDependency</span></span>
<span data-ttu-id="efd92-103">A <xref:System.Data.SqlClient.SqlDependency> nesne ilişkili bir <xref:System.Data.SqlClient.SqlCommand> sorgu sonuçları başlangıçta alınan farklı algılamak için.</span><span class="sxs-lookup"><span data-stu-id="efd92-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="efd92-104">Bir temsilciye de atayabilirsiniz `OnChange` olay sonuçları için ilişkili bir komut değiştirdiğinizde, ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="efd92-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="efd92-105">İlişkilendirmeniz gerekir <xref:System.Data.SqlClient.SqlDependency> komutu yürütmeden önce komutu.</span><span class="sxs-lookup"><span data-stu-id="efd92-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="efd92-106">`HasChanges` Özelliği <xref:System.Data.SqlClient.SqlDependency> veri ilk alındıktan sonra sorgu sonuçları değiştirdiyseniz belirlemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="efd92-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="efd92-107">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="efd92-107">Security Considerations</span></span>  
 <span data-ttu-id="efd92-108">Bağımlılık altyapı dayanan bir <xref:System.Data.SqlClient.SqlConnection> ne zaman açıldığı <xref:System.Data.SqlClient.SqlDependency.Start%2A> belirli bir komut için temel alınan veriler değişmiştir bildirimleri almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="efd92-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="efd92-109">Çağrı başlatmak bir istemci `SqlDependency.Start` kullanımının denetlenir <xref:System.Data.SqlClient.SqlClientPermission> ve kod erişimi güvenlik öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="efd92-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="efd92-110">Daha fazla bilgi için [sorgu bildirimleri etkinleştirme](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) ve [kod erişimi güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="efd92-110">For more information, see [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) and [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="efd92-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="efd92-111">Example</span></span>  
 <span data-ttu-id="efd92-112">Aşağıdaki adımlar, bir bağımlılık bildirin, komut yürütme işlemini göstermektedir ve değişiklikleri sonuç kümesi bir bildirim alırsınız:</span><span class="sxs-lookup"><span data-stu-id="efd92-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>  
  
1.  <span data-ttu-id="efd92-113">Başlatan bir `SqlDependency` sunucu bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="efd92-113">Initiate a `SqlDependency` connection to the server.</span></span>  
  
2.  <span data-ttu-id="efd92-114">Oluşturma <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> nesneleri sunucuya bağlanın ve Transact-SQL deyimini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="efd92-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="efd92-115">Yeni bir `SqlDependency` nesnesi veya var olanı kullanın ve öğeyi `SqlCommand` nesne.</span><span class="sxs-lookup"><span data-stu-id="efd92-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="efd92-116">Dahili olarak, bu oluşturur bir <xref:System.Data.Sql.SqlNotificationRequest> nesne ve gerektiğinde komut nesnesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="efd92-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="efd92-117">Bu bildirim isteği bu benzersiz olarak tanımlayan bir iç tanımlayıcı içeren `SqlDependency` nesne.</span><span class="sxs-lookup"><span data-stu-id="efd92-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="efd92-118">Zaten etkin değilse, ayrıca istemci dinleyicisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="efd92-118">It also starts the client listener if it is not already active.</span></span>  
  
4.  <span data-ttu-id="efd92-119">Bir olay işleyicisi abone `OnChange` olayı `SqlDependency` nesne.</span><span class="sxs-lookup"><span data-stu-id="efd92-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>  
  
5.  <span data-ttu-id="efd92-120">Herhangi bir komutu yürütme `Execute` yöntemlerinin `SqlCommand` nesne.</span><span class="sxs-lookup"><span data-stu-id="efd92-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="efd92-121">Komut bildirim nesneye bağlı olduğundan, sunucunun bir bildirim oluşturmalısınız ve kuyruk bilgileri bağımlılıkları kuyruğa işaret edecek tanır.</span><span class="sxs-lookup"><span data-stu-id="efd92-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>  
  
6.  <span data-ttu-id="efd92-122">Durdur `SqlDependency` sunucu bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="efd92-122">Stop the `SqlDependency` connection to the server.</span></span>  
  
 <span data-ttu-id="efd92-123">Microsoft SQL Server herhangi bir kullanıcı daha sonra temel alınan verileri değişirse, bu tür bir değişiklik için bekleyen bir bildirim ve arka plandaki aracılığıyla istemciye işlenen ve iletilen bir bildirim gönderir algılar `SqlConnection` oluşturulmuş çağırarak `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="efd92-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="efd92-124">İstemci dinleyici geçersiz kılma iletiyi alır.</span><span class="sxs-lookup"><span data-stu-id="efd92-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="efd92-125">İstemci dinleyici ardından ilişkili bulur `SqlDependency` nesne ve ateşlenir `OnChange` olay.</span><span class="sxs-lookup"><span data-stu-id="efd92-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>  
  
 <span data-ttu-id="efd92-126">Aşağıdaki kod parçası, örnek bir uygulama oluşturmak için kullanacağınız tasarım desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="efd92-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="efd92-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efd92-127">See Also</span></span>  
 [<span data-ttu-id="efd92-128">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="efd92-128">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="efd92-129">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="efd92-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
