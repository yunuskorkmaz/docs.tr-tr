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
ms.openlocfilehash: b99720b9653b8454419acd35085bfe9a7ac4b5af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796792"
---
# <a name="using-client-sockets"></a>İstemci Yuvaları Kullanma
Bir konuşma aracılığıyla başlatabilmesi bir <xref:System.Net.Sockets.Socket>, uygulamanızı hem de uzak cihazı veri kanalı oluşturmanız gerekir. Diğer ağ adresi ailelerini ve protokolleri mevcut olmasına karşın, bu örnek bir uzak hizmete bir TCP/IP bağlantısı oluşturma işlemi gösterilmektedir.  
  
 TCP/IP'yi hizmet benzersiz olarak tanımlanabilmesi için bir ağ adresi ve bir hizmet bağlantı noktası numarası kullanır. Ağ adresi, ağdaki belirli bir aygıt tanımlar; bağlantı noktası numarası, hizmete bağlanmak için bu cihazda tanımlar. Ağ adresi ve hizmet bağlantı noktası birleşimi .NET Framework tarafından temsil edilen bir uç nokta adı verilen <xref:System.Net.EndPoint> sınıfı. Bir alt öğesi **uç nokta** için tanımlanan her desteklenen Adres ailesi; IP adresi ailesi için sınıf <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Sınıfı TCP/IP'yi Internet Hizmetleri kullanan uygulamalar için etki alanı adı hizmetleri sağlar. <xref:System.Net.Dns.Resolve%2A> Yöntemi (Örneğin 192.168.1.1) sayısal bir Internet adresi için bir kullanıcı dostu bir etki alanı adı (örneğin, "host.contoso.com") eşlemek için bir DNS sunucusunu sorgular. **Çözmek** döndürür bir <xref:System.Net.IPHostEntry> , adresleri ve istenen ad için diğer adlar listesini içerir. Çoğu durumda, döndürülen ilk adresi kullanabileceğinizi <xref:System.Net.IPHostEntry.AddressList%2A> dizisi. Aşağıdaki kod alır bir <xref:System.Net.IPAddress> sunucu host.contoso.com IP adresini içeren.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Ortak Hizmetleri için bağlantı noktası numaralarını Internet Atanmış Numaralar Yetkilisi (IANA) tanımlar (daha fazla bilgi için [hizmet adını ve Aktarım Protokolü bağlantı noktası numarasını kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Diğer hizmetler için 1024 65,535 aralığında bağlantı noktası numaralarını kayıtlı. Aşağıdaki kod host.contoso.com için IP adresi için bir bağlantı uzak uç noktası oluşturmak için bir bağlantı noktası numarası ile birleştirir.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Uzak cihaz adresi belirleme ve bağlantısı için kullanmak üzere bir bağlantı noktası seçme sonra uzak cihazla bağlantı kurmak uygulama deneyebilirsiniz. Aşağıdaki örnekte mevcut bir **IPEndPoint** uzak bir aygıta bağlanmayı ve oluşturulan özel durumları yakalar.  
  
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

- [Zaman Uyumlu İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)
- [Zaman Uyumsuz İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [Nasıl yapılır: Yuva oluşturun](../../../docs/framework/network-programming/how-to-create-a-socket.md)
- [Yuvalar](../../../docs/framework/network-programming/sockets.md)
