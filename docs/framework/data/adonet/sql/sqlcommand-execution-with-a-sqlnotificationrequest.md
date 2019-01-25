---
title: Bir SqlNotificationRequest ile SqlCommand yürütme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 1380d06b54980456080d9891013d0d8de6b4110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664102"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Bir SqlNotificationRequest ile SqlCommand yürütme
A <xref:System.Data.SqlClient.SqlCommand> sunucudan alınan sonra sonuç kümesi sorguyu tekrar yürütüldü, farklı veri değişikliği olduğunda bir bildirim oluşturmak için yapılandırılabilir. Bu, özel bir bildirim sırası sunucusunda veya canlı tutmak istemediğiniz kullanmak istediğiniz senaryolar için kullanışlıdır.  
  
## <a name="creating-the-notification-request"></a>Bildirim isteği oluşturma  
 Kullanabileceğiniz bir <xref:System.Data.Sql.SqlNotificationRequest> bildirim isteği için bağlama oluşturmak için nesne bir `SqlCommand` nesne. İstek oluşturulduktan sonra artık ihtiyacınız `SqlNotificationRequest` nesne. Sıra herhangi bir bildirim için sorgu ve uygun şekilde yanıt verin. Uygulamayı kapatın ve daha sonra yeniden bile bildirimleri oluşabilir.  
  
 İlişkili bildirim komutu yürütüldüğünde, özgün sonucu herhangi bir değişiklik bildirimi istekte yapılandırılmış SQL Server kuyruğa ileti gönderme tetikleyiciyi ayarlayın.  
  
 SQL Server sıra yoklamak ve iletinin nasıl uygulamanıza özeldir. Uygulama sıra yoklamak üzere sorumludur ve tepki iletinin içeriğine göre.  
  
> [!NOTE]
>  SQL Server bildirim istekleriyle kullanırken <xref:System.Data.SqlClient.SqlDependency>, varsayılan hizmet adını kullanmak yerine kendi kuyruk adı oluşturun.  
  
 İçin yeni bir istemci tarafı güvenlik öğesi yok <xref:System.Data.Sql.SqlNotificationRequest>. Bu birincil bir sunucu özelliğidir ve sunucunun kullanıcı bir bildirim isteği için gereken özel ayrıcalıklar oluşturdu.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod parçası nasıl oluşturulacağını gösterir. bir <xref:System.Data.Sql.SqlNotificationRequest> ve bunu bir <xref:System.Data.SqlClient.SqlCommand>.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [SQL Server'da Sorgu Bildirimleri](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
