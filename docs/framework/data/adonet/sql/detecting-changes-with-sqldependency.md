---
title: "SqlDependency ile değişiklikleri algılama"
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
ms.assetid: e6a58316-f005-4477-92e1-45cc2eb8c5b4
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e105080b6ef3bdd6ce20ad8291c57fc9180980d7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="detecting-changes-with-sqldependency"></a><span data-ttu-id="d0f87-102">SqlDependency ile değişiklikleri algılama</span><span class="sxs-lookup"><span data-stu-id="d0f87-102">Detecting Changes with SqlDependency</span></span>
<span data-ttu-id="d0f87-103">A <xref:System.Data.SqlClient.SqlDependency> nesne ilişkilendirilebilir bir <xref:System.Data.SqlClient.SqlCommand> sorgu sonuçları ilk başta farklı algılamak için.</span><span class="sxs-lookup"><span data-stu-id="d0f87-103">A <xref:System.Data.SqlClient.SqlDependency> object can be associated with a <xref:System.Data.SqlClient.SqlCommand> in order to detect when query results differ from those originally retrieved.</span></span> <span data-ttu-id="d0f87-104">Ayrıca bir temsilci atayabilirsiniz `OnChange` sonuçları için ilişkili bir komut değiştirdiğinizde, ateşlenir olay.</span><span class="sxs-lookup"><span data-stu-id="d0f87-104">You can also assign a delegate to the `OnChange` event, which will fire when the results change for an associated command.</span></span> <span data-ttu-id="d0f87-105">İlişkilendirmeniz gerekir <xref:System.Data.SqlClient.SqlDependency> komutu yürütmeden önce komutu.</span><span class="sxs-lookup"><span data-stu-id="d0f87-105">You must associate the <xref:System.Data.SqlClient.SqlDependency> with the command before you execute the command.</span></span> <span data-ttu-id="d0f87-106">`HasChanges` Özelliği <xref:System.Data.SqlClient.SqlDependency> verileri ilk alındığından beri sorgu sonuçlarını değişip değişmediğini için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0f87-106">The `HasChanges` property of the <xref:System.Data.SqlClient.SqlDependency> can also be used to determine if the query results have changed since the data was first retrieved.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="d0f87-107">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="d0f87-107">Security Considerations</span></span>  
 <span data-ttu-id="d0f87-108">Bağımlılık altyapı dayanan bir <xref:System.Data.SqlClient.SqlConnection> , ne zaman açıldığında <xref:System.Data.SqlClient.SqlDependency.Start%2A> temel alınan veriler için verilen komut değişti bildirimleri almak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d0f87-108">The dependency infrastructure relies on a <xref:System.Data.SqlClient.SqlConnection> that is opened when <xref:System.Data.SqlClient.SqlDependency.Start%2A> is called in order to receive notifications that the underlying data has changed for a given command.</span></span> <span data-ttu-id="d0f87-109">Çağrısı başlatmak bir istemci özelliğini `SqlDependency.Start` kullanılarak denetlenir <xref:System.Data.SqlClient.SqlClientPermission> ve kod erişim güvenliği öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="d0f87-109">The ability for a client to initiate the call to `SqlDependency.Start` is controlled through the use of <xref:System.Data.SqlClient.SqlClientPermission> and code access security attributes.</span></span> <span data-ttu-id="d0f87-110">Daha fazla bilgi için bkz: [etkinleştirme sorgu bildirimleri](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) ve [kod erişim güvenliği ve ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="d0f87-110">For more information, see [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md) and [Code Access Security and ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0f87-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0f87-111">Example</span></span>  
 <span data-ttu-id="d0f87-112">Aşağıdaki adımları bir bağımlılık bildirmek için komut yürütme nasıl çalışılacağını ve değişiklikleri sonuç kümesi, bir bildirim alırsınız:</span><span class="sxs-lookup"><span data-stu-id="d0f87-112">The following steps illustrate how to declare a dependency, execute a command, and receive a notification when the result set changes:</span></span>  
  
1.  <span data-ttu-id="d0f87-113">Başlatma bir `SqlDependency` sunucu bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="d0f87-113">Initiate a `SqlDependency` connection to the server.</span></span>  
  
2.  <span data-ttu-id="d0f87-114">Oluşturma <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlCommand> sunucuya bağlanın ve bir Transact-SQL deyimi tanımlamak için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d0f87-114">Create <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to connect to the server and define a Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="d0f87-115">Yeni bir `SqlDependency` nesnesi veya mevcut bir kullanın ve onu bağladıktan `SqlCommand` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0f87-115">Create a new `SqlDependency` object, or use an existing one, and bind it to the `SqlCommand` object.</span></span> <span data-ttu-id="d0f87-116">Dahili olarak, bu oluşturur bir <xref:System.Data.Sql.SqlNotificationRequest> nesne ve gerektiği gibi komut nesnesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="d0f87-116">Internally, this creates a <xref:System.Data.Sql.SqlNotificationRequest> object and binds it to the command object as needed.</span></span> <span data-ttu-id="d0f87-117">Bu bildirim isteği bu benzersiz olarak tanımlayan bir iç tanımlayıcı içeren `SqlDependency` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0f87-117">This notification request contains an internal identifier that uniquely identifies this `SqlDependency` object.</span></span> <span data-ttu-id="d0f87-118">Zaten etkin değilse, aynı zamanda istemci dinleyicisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="d0f87-118">It also starts the client listener if it is not already active.</span></span>  
  
4.  <span data-ttu-id="d0f87-119">Bir olay işleyicisi abone `OnChange` olayı `SqlDependency` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0f87-119">Subscribe an event handler to the `OnChange` event of the `SqlDependency` object.</span></span>  
  
5.  <span data-ttu-id="d0f87-120">Herhangi birini kullanarak komutu yürütün `Execute` yöntemlerinin `SqlCommand` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0f87-120">Execute the command using any of the `Execute` methods of the `SqlCommand` object.</span></span> <span data-ttu-id="d0f87-121">Komut bildirim nesnesine bağlı olduğundan, sunucunun bir bildirim oluşturmalısınız ve sırası bilgilerini bağımlılıkları kuyruğuna işaret edecek tanır.</span><span class="sxs-lookup"><span data-stu-id="d0f87-121">Because the command is bound to the notification object, the server recognizes that it must generate a notification, and the queue information will point to the dependencies queue.</span></span>  
  
6.  <span data-ttu-id="d0f87-122">Durdur `SqlDependency` sunucu bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="d0f87-122">Stop the `SqlDependency` connection to the server.</span></span>  
  
 <span data-ttu-id="d0f87-123">Herhangi bir kullanıcı daha sonra temel alınan veriler değişirse, Microsoft SQL Server, bu tür bir değişiklik için bekleyen bir bildirim arka plandaki aracılığıyla istemciye işlenen ve iletilen bir bildirim gönderir algılar ve `SqlConnection` oluşturulmuş çağırarak `SqlDependency.Start`.</span><span class="sxs-lookup"><span data-stu-id="d0f87-123">If any user subsequently changes the underlying data, Microsoft SQL Server detects that there is a notification pending for such a change, and posts a notification that is processed and forwarded to the client through the underlying `SqlConnection` that was created by calling `SqlDependency.Start`.</span></span> <span data-ttu-id="d0f87-124">İstemci dinleyicisi geçersiz kılma iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="d0f87-124">The client listener receives the invalidation message.</span></span> <span data-ttu-id="d0f87-125">İstemci dinleyicisi ardından ilişkili bulur `SqlDependency` nesne ve ateşlenir `OnChange` olay.</span><span class="sxs-lookup"><span data-stu-id="d0f87-125">The client listener then locates the associated `SqlDependency` object and fires the `OnChange` event.</span></span>  
  
 <span data-ttu-id="d0f87-126">Aşağıdaki kod parçası, örnek bir uygulama oluşturmak için kullanacağınız tasarım deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0f87-126">The following code fragment shows the design pattern you would use to create a sample application.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0f87-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0f87-127">See Also</span></span>  
 [<span data-ttu-id="d0f87-128">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="d0f87-128">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="d0f87-129">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d0f87-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
