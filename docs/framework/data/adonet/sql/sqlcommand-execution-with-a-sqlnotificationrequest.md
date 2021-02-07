---
description: 'Daha fazla bilgi edinin: bir SqlNotificationRequest ile SqlCommand yürütme'
title: Bir SqlNotificationRequest ile SqlCommand Yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: d3e82022794aa67d4bd20223cac852097f2be9dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767056"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="0ee0e-103">Bir SqlNotificationRequest ile SqlCommand Yürütme</span><span class="sxs-lookup"><span data-stu-id="0ee0e-103">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="0ee0e-104">Bir, <xref:System.Data.SqlClient.SqlCommand> sunucudan alındıktan sonra veriler değiştiğinde bildirim oluşturmak üzere yapılandırılabilir ve sorgu yeniden yürütülürse sonuç kümesi farklı olur.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-104">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="0ee0e-105">Bu, sunucuda özel bildirim kuyruklarını kullanmak istediğiniz veya canlı nesneleri sürdürmek istemediğiniz senaryolar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-105">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="0ee0e-106">Bildirim Isteği oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="0ee0e-106">Creating the Notification Request</span></span>

<span data-ttu-id="0ee0e-107">Bir nesneyi <xref:System.Data.Sql.SqlNotificationRequest> bir nesnesine bağlayarak bildirim isteği oluşturmak için kullanabilirsiniz `SqlCommand` .</span><span class="sxs-lookup"><span data-stu-id="0ee0e-107">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="0ee0e-108">İstek oluşturulduktan sonra nesneye artık gerek kalmaz `SqlNotificationRequest` .</span><span class="sxs-lookup"><span data-stu-id="0ee0e-108">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="0ee0e-109">Kuyruğu herhangi bir bildirim için sorgulayabilir ve uygun şekilde yanıt verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-109">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="0ee0e-110">Uygulama kapatılsa ve daha sonra yeniden başlatıldığından bile bildirimler oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-110">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="0ee0e-111">İlişkili bildirime sahip komut yürütüldüğünde, özgün sonuç kümesinde yapılan değişiklikler bildirim isteğinde yapılandırılan SQL Server kuyruğuna bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-111">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="0ee0e-112">SQL Server kuyruğunu yoklayın ve iletinin uygulamanıza özgü olduğunu nasıl yorumlayacağınız.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-112">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="0ee0e-113">Uygulamanın, sıranın yoklanması ve iletinin içeriğine göre yeniden davranmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-113">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="0ee0e-114">İle SQL Server bildirim istekleri kullanırken <xref:System.Data.SqlClient.SqlDependency> , varsayılan hizmet adını kullanmak yerine kendi sıra adınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-114">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="0ee0e-115">İçin yeni bir istemci tarafı güvenlik öğesi yok <xref:System.Data.Sql.SqlNotificationRequest> .</span><span class="sxs-lookup"><span data-stu-id="0ee0e-115">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="0ee0e-116">Bu, öncelikli olarak bir sunucu özelliğidir ve sunucu, kullanıcıların bir bildirim istemesi için gereken özel ayrıcalıklar oluşturmuştur.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-116">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="0ee0e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ee0e-117">Example</span></span>

<span data-ttu-id="0ee0e-118">Aşağıdaki kod parçası, oluşturma ve ile ilişkilendirme işlemlerinin nasıl yapılacağını gösterir <xref:System.Data.Sql.SqlNotificationRequest> <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="0ee0e-118">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
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
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="0ee0e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ee0e-119">See also</span></span>

- [<span data-ttu-id="0ee0e-120">SQL Server'da Sorgu Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="0ee0e-120">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="0ee0e-121">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ee0e-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
