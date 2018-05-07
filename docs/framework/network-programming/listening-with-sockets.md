---
title: Yuva başına dinleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f85b63b151bcc20db635f56ec1dfec8df6c92241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="listening-with-sockets"></a>Yuva başına dinleme
Dinleyici veya server yuva ağ üzerinde bir bağlantı noktası açın ve bu bağlantı noktasına bağlanmak bir istemci için bekleyin. Diğer ağ adres ailesi ve protokolleri mevcut olmasına karşın, bu örnek bir TCP/IP ağı için uzak hizmetin nasıl oluşturulacağını gösterir.  
  
 TCP/IP'yi hizmetinin benzersiz adresini, ana bilgisayarın IP adresi hizmet için bir uç nokta oluşturmak için hizmet bağlantı noktası numarasını birleştirerek tanımlanır. <xref:System.Net.Dns> Sınıfı yerel ağ aygıtı tarafından desteklenen ağ adresleri ilgili bilgi döndüren yöntemler sağlar. Yerel ağ aygıtı birden fazla ağ adresi olduğunda ya da yerel sistem birden fazla ağ aygıtı destekliyorsa **Dns** sınıfı, tüm ağ adresleri hakkında bilgi döndürür ve uygulama uygun seçmeniz gerekir hizmet adresi. Internet Atanmış Numaralar Yetkilisi (IANA) (daha fazla bilgi için bkz: www.iana.org/assignments/port-numbers) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar. Diğer Hizmetleri bağlantı noktası numaraları aralığını 1.024 65. 535'ı için kayıt yaptırdınız.  
  
 Aşağıdaki örnekte bir <xref:System.Net.IPEndPoint> tarafından döndürülen ilk IP adresi birleştiren bir sunucu için **Dns** bir bağlantı noktası numarası ile ana bilgisayar için seçilen kayıtlı bağlantı noktası numaraları aralığında.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Yerel uç nokta belirlendikten sonra <xref:System.Net.Sockets.Socket> Bu uç nokta kullanarak ile ilişkilendirilmelidir <xref:System.Net.Sockets.Socket.Bind%2A> yöntemi ve kümesi kullanan uç noktasını dinlemek üzere <xref:System.Net.Sockets.Socket.Listen%2A> yöntemi. **Bağlama** bir özel durum döndürürse belirli adresi ve bağlantı noktası bileşimi zaten kullanılıyor. Aşağıdaki örnek, ilişkilendirme gösterir bir **yuva** ile bir **IPEndPoint**.  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 **Dinleme** yöntemi için kaç tane bekleyen bağlantılar belirten tek bir parametre alan **yuva** sunucu meşgul hatası bağlanan istemciye döndürülmeden önce izin verilir. Bu durumda, sunucu meşgul yanıtı istemci numarası 101 döndürülmeden önce en fazla 100 istemci bağlantısı kuyruğuna yerleştirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman Uyumlu Sunucu Yuvası Kullanma](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [Zaman Uyumsuz Sunucu Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [İstemci Yuvaları Kullanma](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Nasıl Yapılır: Yuva Oluşturma](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
