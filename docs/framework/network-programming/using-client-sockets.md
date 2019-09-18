---
title: İstemci Yuvaları Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046952"
---
# <a name="using-client-sockets"></a>İstemci Yuvaları Kullanma
Bir konuşmayı bir <xref:System.Net.Sockets.Socket>ile başlatmak için önce uygulamanız ile uzak cihaz arasında bir veri kanalı oluşturmanız gerekir. Diğer ağ adresi aileleri ve protokolleri var olsa da bu örnek, uzak bir hizmete TCP/IP bağlantısının nasıl oluşturulacağını gösterir.  
  
 TCP/IP bir hizmeti benzersiz bir şekilde tanımlamak için bir ağ adresi ve bir hizmet bağlantı noktası numarası kullanır. Ağ adresi ağ üzerinde belirli bir cihazı tanımlar; bağlantı noktası numarası, bu cihazdaki Bağlanılacak belirli hizmeti tanımlar. Ağ adresi ve hizmet bağlantı noktası birleşimine, <xref:System.Net.EndPoint> sınıfı tarafından .NET Framework temsil edilen bir uç nokta denir. Her desteklenen adres ailesi için **uç nokta** alt öğesi tanımlanmıştır; IP adresi ailesi için sınıfı <xref:System.Net.IPEndPoint>.  
  
 Sınıfı <xref:System.Net.Dns> , TCP/IP Internet hizmetlerini kullanan uygulamalara etki alanı ad hizmetleri sağlar. Yöntemi <xref:System.Net.Dns.Resolve%2A> , bir DNS sunucusunu, Kullanıcı dostu bir etki alanı adını (örneğin, "Host.contoso.com") sayısal bir Internet adresine (192.168.1.1 gibi) eşlemek üzere sorgular. **Resolve** , istenen <xref:System.Net.IPHostEntry> ad için adreslerin ve diğer adların bir listesini içeren bir döndürür. Çoğu durumda, <xref:System.Net.IPHostEntry.AddressList%2A> dizide döndürülen ilk adresi kullanabilirsiniz. Aşağıdaki kod, sunucu Host.contoso.com <xref:System.Net.IPAddress> için IP adresini içeren bir IP adresi alır.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet atanmış numaralar yetkilisi (IANA) ortak hizmetler için bağlantı noktası numaralarını tanımlar (daha fazla bilgi için bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Diğer hizmetler 1.024 ile 65.535 arasında kayıt bağlantı noktası numaraları içerebilir. Aşağıdaki kod, bir bağlantı için uzak uç nokta oluşturmak üzere host.contoso.com IP adresini bir bağlantı noktası numarasıyla birleştirir.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Uzak cihazın adresini belirledikten ve bağlantı için kullanılacak bir bağlantı noktası seçtikten sonra uygulama, uzak cihazla bağlantı kurmayı deneyebilir. Aşağıdaki örnek, uzak bir cihaza bağlanmak ve oluşturulan tüm özel durumları yakalayan mevcut bir **IPEndPoint** kullanır.  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumlu İstemci Yuvası Kullanma](using-a-synchronous-client-socket.md)
- [Zaman Uyumsuz İstemci Yuvası Kullanma](using-an-asynchronous-client-socket.md)
- [Nasıl yapılır: Yuva oluşturma](how-to-create-a-socket.md)
- [Yuvalar](sockets.md)
