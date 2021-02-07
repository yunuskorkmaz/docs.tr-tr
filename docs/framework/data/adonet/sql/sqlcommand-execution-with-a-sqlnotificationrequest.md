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
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Bir SqlNotificationRequest ile SqlCommand Yürütme

Bir, <xref:System.Data.SqlClient.SqlCommand> sunucudan alındıktan sonra veriler değiştiğinde bildirim oluşturmak üzere yapılandırılabilir ve sorgu yeniden yürütülürse sonuç kümesi farklı olur. Bu, sunucuda özel bildirim kuyruklarını kullanmak istediğiniz veya canlı nesneleri sürdürmek istemediğiniz senaryolar için yararlıdır.

## <a name="creating-the-notification-request"></a>Bildirim Isteği oluşturuluyor

Bir nesneyi <xref:System.Data.Sql.SqlNotificationRequest> bir nesnesine bağlayarak bildirim isteği oluşturmak için kullanabilirsiniz `SqlCommand` . İstek oluşturulduktan sonra nesneye artık gerek kalmaz `SqlNotificationRequest` . Kuyruğu herhangi bir bildirim için sorgulayabilir ve uygun şekilde yanıt verebilirsiniz. Uygulama kapatılsa ve daha sonra yeniden başlatıldığından bile bildirimler oluşabilir.

İlişkili bildirime sahip komut yürütüldüğünde, özgün sonuç kümesinde yapılan değişiklikler bildirim isteğinde yapılandırılan SQL Server kuyruğuna bir ileti gönderir.

SQL Server kuyruğunu yoklayın ve iletinin uygulamanıza özgü olduğunu nasıl yorumlayacağınız. Uygulamanın, sıranın yoklanması ve iletinin içeriğine göre yeniden davranmasından sorumludur.

> [!NOTE]
> İle SQL Server bildirim istekleri kullanırken <xref:System.Data.SqlClient.SqlDependency> , varsayılan hizmet adını kullanmak yerine kendi sıra adınızı oluşturun.

İçin yeni bir istemci tarafı güvenlik öğesi yok <xref:System.Data.Sql.SqlNotificationRequest> . Bu, öncelikli olarak bir sunucu özelliğidir ve sunucu, kullanıcıların bir bildirim istemesi için gereken özel ayrıcalıklar oluşturmuştur.

### <a name="example"></a>Örnek

Aşağıdaki kod parçası, oluşturma ve ile ilişkilendirme işlemlerinin nasıl yapılacağını gösterir <xref:System.Data.Sql.SqlNotificationRequest> <xref:System.Data.SqlClient.SqlCommand> .

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

## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server'da Sorgu Bildirimleri](query-notifications-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
