---
title: Bir SqlNotificationRequest ile SqlCommand yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 83450e6ace33e89ddd263a1514f74f4d4e231cf7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798579"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="2eda7-102">Bir SqlNotificationRequest ile SqlCommand yürütme</span><span class="sxs-lookup"><span data-stu-id="2eda7-102">SqlCommand Execution with a SqlNotificationRequest</span></span>
<span data-ttu-id="2eda7-103">A <xref:System.Data.SqlClient.SqlCommand> sunucudan alınan sonra sonuç kümesi sorguyu tekrar yürütüldü, farklı veri değişikliği olduğunda bir bildirim oluşturmak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2eda7-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="2eda7-104">Bu, özel bir bildirim sırası sunucusunda veya canlı tutmak istemediğiniz kullanmak istediğiniz senaryolar için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="2eda7-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>  
  
## <a name="creating-the-notification-request"></a><span data-ttu-id="2eda7-105">Bildirim isteği oluşturma</span><span class="sxs-lookup"><span data-stu-id="2eda7-105">Creating the Notification Request</span></span>  
 <span data-ttu-id="2eda7-106">Kullanabileceğiniz bir <xref:System.Data.Sql.SqlNotificationRequest> bildirim isteği için bağlama oluşturmak için nesne bir `SqlCommand` nesne.</span><span class="sxs-lookup"><span data-stu-id="2eda7-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="2eda7-107">İstek oluşturulduktan sonra artık ihtiyacınız `SqlNotificationRequest` nesne.</span><span class="sxs-lookup"><span data-stu-id="2eda7-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="2eda7-108">Sıra herhangi bir bildirim için sorgu ve uygun şekilde yanıt verin.</span><span class="sxs-lookup"><span data-stu-id="2eda7-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="2eda7-109">Uygulamayı kapatın ve daha sonra yeniden bile bildirimleri oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="2eda7-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>  
  
 <span data-ttu-id="2eda7-110">İlişkili bildirim komutu yürütüldüğünde, özgün sonucu herhangi bir değişiklik bildirimi istekte yapılandırılmış SQL Server kuyruğa ileti gönderme tetikleyiciyi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2eda7-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>  
  
 <span data-ttu-id="2eda7-111">SQL Server sıra yoklamak ve iletinin nasıl uygulamanıza özeldir.</span><span class="sxs-lookup"><span data-stu-id="2eda7-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="2eda7-112">Uygulama sıra yoklamak üzere sorumludur ve tepki iletinin içeriğine göre.</span><span class="sxs-lookup"><span data-stu-id="2eda7-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2eda7-113">SQL Server bildirim istekleriyle kullanırken <xref:System.Data.SqlClient.SqlDependency>, varsayılan hizmet adını kullanmak yerine kendi kuyruk adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2eda7-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>  
  
 <span data-ttu-id="2eda7-114">İçin yeni bir istemci tarafı güvenlik öğesi yok <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="2eda7-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="2eda7-115">Bu birincil bir sunucu özelliğidir ve sunucunun kullanıcı bir bildirim isteği için gereken özel ayrıcalıklar oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="2eda7-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>  
  
### <a name="example"></a><span data-ttu-id="2eda7-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="2eda7-116">Example</span></span>  
 <span data-ttu-id="2eda7-117">Aşağıdaki kod parçası nasıl oluşturulacağını gösterir. bir <xref:System.Data.Sql.SqlNotificationRequest> ve bunu bir <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="2eda7-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>  
  
```vb  
' Assume connection is an open SqlConnection.  
' Create a new SqlCommand object.  
Dim command As New SqlCommand( _  
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)  
  
' Create a SqlNotificationRequest object.  
Dim notficationRequest As New SqlNotificationRequest()  
notficationRequest.id = "NotificationID"  
notficationRequest.Service = "mySSBQueue"  
  
' Associate the notification request with the command.  
command.Notification = notficationRequest  
' Execute the command.  
command.ExecuteReader()  
' Process the DataReader.  
' You can use Transact-SQL syntax to periodically poll the   
' SQL Server queue to see if you have a new message.  
```  
  
```csharp  
// Assume connection is an open SqlConnection.  
// Create a new SqlCommand object.  
SqlCommand command=new SqlCommand(  
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);  
  
// Create a SqlNotificationRequest object.  
SqlNotificationRequest notficationRequest=new SqlNotificationRequest();  
notficationRequest.id="NotificationID";  
notficationRequest.Service="mySSBQueue";  
  
// Associate the notification request with the command.  
command.Notification=notficationRequest;  
// Execute the command.  
command.ExecuteReader();  
// Process the DataReader.  
// You can use Transact-SQL syntax to periodically poll the   
// SQL Server queue to see if you have a new message.  
```  
  
## <a name="see-also"></a><span data-ttu-id="2eda7-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2eda7-118">See Also</span></span>  
 [<span data-ttu-id="2eda7-119">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="2eda7-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="2eda7-120">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="2eda7-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
