---
title: İstemci yuvaları kullanma
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 458e67861bfd40b69f7a6f756ddee8be433e9e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395953"
---
# <a name="using-client-sockets"></a>İstemci yuvaları kullanma
Konuşma aracılığıyla başlatmadan önce bir <xref:System.Net.Sockets.Socket>, uygulamanızı ve uzak aygıt veri kanalı oluşturmanız gerekir. Diğer ağ adres ailesi ve protokolleri mevcut olmasına karşın, bu örnek uzak bir hizmet için TCP/IP'yi bağlantısının nasıl oluşturulacağını gösterir.  
  
 TCP/IP'yi hizmet benzersiz şekilde tanımlamak için bir ağ adresi ve bir hizmet bağlantı noktası numarası kullanır. Ağ adresi ağdaki belirli bir aygıt tanımlar; bağlantı noktası numarasını hizmete bağlanmak için bu cihazda tanımlar. Ağ adresi ve hizmet bağlantı noktası bileşimi .NET Framework tarafından temsil edilen bir uç nokta adı verilen <xref:System.Net.EndPoint> sınıfı. Bir alt öğesi **EndPoint** için tanımlanan her desteklenen Adres ailesi; IP adresi ailesi için sınıf <xref:System.Net.IPEndPoint>.  
  
 <xref:System.Net.Dns> Sınıfı, TCP/IP'yi Internet Hizmetleri kullanan uygulamalar için etki alanı adı hizmetleri sağlar. <xref:System.Net.Dns.Resolve%2A> Yöntemi (örneğin, 192.168.1.1) sayısal bir Internet adresi için bir kolay kullanılan etki alanı adı (örneğin, "host.contoso.com") eşlemek için bir DNS sunucusu sorgular. **Gidermek** döndüren bir <xref:System.Net.IPHostEntry> adresleri ve istenen ad için diğer adlar listesini içerir. Çoğu durumda, döndürülen ilk adres kullanabilirsiniz <xref:System.Net.IPHostEntry.AddressList%2A> dizi. Aşağıdaki kod alır bir <xref:System.Net.IPAddress> server host.contoso.com IP adresini içeren.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Atanmış Numaralar Yetkilisi (IANA) (daha fazla bilgi için bkz: www.iana.org/assignments/port-numbers) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar. Diğer Hizmetleri bağlantı noktası numaraları aralığını 1.024 65. 535'ı için kayıt yaptırdınız. Aşağıdaki kod host.contoso.com IP adresini bir uzak uç nokta için bir bağlantı oluşturmak için bir bağlantı noktası numarası ile birleştirir.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Uzak aygıt adresi belirleme ve bağlantı için kullanılacak bağlantı noktasını seçme sonra uygulama uzak aygıt ile bağlantı kurmak deneyebilirsiniz. Aşağıdaki örnek, var olan kullanır **IPEndPoint** uzak bir aygıta bağlanmayı ve oluşturulan tüm özel durumları yakalar.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman Uyumlu İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [Zaman Uyumsuz İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Nasıl Yapılır: Yuva Oluşturma](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
