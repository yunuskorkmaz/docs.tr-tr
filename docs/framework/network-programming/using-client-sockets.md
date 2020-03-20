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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046952"
---
# <a name="using-client-sockets"></a>İstemci Yuvaları Kullanma
Bir <xref:System.Net.Sockets.Socket>üzerinden bir konuşma başlatamadan önce, uygulamanız ve uzak aygıt arasında bir veri borusu oluşturmanız gerekir. Diğer ağ adresi aileleri ve protokolleri olsa da, bu örnek, uzak bir hizmete nasıl TCP/IP bağlantısı oluşturulacak larını gösterir.  
  
 TCP/IP, bir hizmeti benzersiz olarak tanımlamak için bir ağ adresi ve hizmet bağlantı noktası numarası kullanır. Ağ adresi ağdaki belirli bir aygıtı tanımlar; bağlantı noktası numarası, bağlanılabilmek için o aygıttaki belirli hizmeti tanımlar. Ağ adresi ve hizmet bağlantı noktasının birleşimi, <xref:System.Net.EndPoint> sınıf tarafından .NET Framework'de temsil edilen bir bitiş noktası olarak adlandırılır. Desteklenen her adres ailesi için **EndPoint** soyundan gelen bir aile tanımlanır; IP adresi ailesi için <xref:System.Net.IPEndPoint>sınıf.  
  
 Sınıf, <xref:System.Net.Dns> TCP/IP Internet hizmetlerini kullanan uygulamalara etki alanı adı hizmetleri sağlar. Yöntem, <xref:System.Net.Dns.Resolve%2A> kullanıcı dostu bir etki alanı adını ("host.contoso.com" gibi) sayısal bir Internet adresiyle (192.168.1.1 gibi) eşlemek için Bir DNS sunucusunu sorgular. **Çözümle,** istenen ada ait adresler ve diğer adların listesini içeren bir <xref:System.Net.IPHostEntry> sürüc döndürür. Çoğu durumda, <xref:System.Net.IPHostEntry.AddressList%2A> dizide döndürülen ilk adresi kullanabilirsiniz. Aşağıdaki kod, <xref:System.Net.IPAddress> sunucu host.contoso.com için IP adresini içeren bir kod alır.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar (daha fazla bilgi için [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri'ne](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)bakın). Diğer hizmetler, 1.024 ile 65.535 aralığında kayıtlı bağlantı noktası numaralarına sahip olabilir. Aşağıdaki kod, bağlantı için uzak bir bitiş noktası oluşturmak için host.contoso.com ip adresini bir bağlantı noktası numarasıyla birleştirir.  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 Uzak aygıtın adresini belirledikten ve bağlantı için kullanılacak bir bağlantı noktası seçtikten sonra, uygulama uzak aygıtla bağlantı kurmaya çalışabilir. Aşağıdaki örnek, uzak bir aygıta bağlanmak için varolan bir **IPEndPoint** kullanır ve atılan tüm özel durumları yakalar.  
  
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
- [Nasıl Yapılır: Yuva Oluşturma](how-to-create-a-socket.md)
- [Yuvalar](sockets.md)
