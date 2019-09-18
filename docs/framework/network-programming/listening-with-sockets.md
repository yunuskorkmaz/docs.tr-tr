---
title: Yuvalarla Dinleme
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
ms.openlocfilehash: 2eb1174c98cdd88cc519559011659a2a277219b0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047777"
---
# <a name="listening-with-sockets"></a>Yuvalarla Dinleme
Dinleyici veya sunucu Yuvaları ağ üzerinde bir bağlantı noktası açın ve bir istemcinin bu bağlantı noktasına bağlanmasını bekleyin. Diğer ağ adresi aileleri ve protokolleri var olsa da, bu örnek bir TCP/IP ağı için uzak hizmetin nasıl oluşturulacağını gösterir.  
  
 TCP/IP hizmetinin benzersiz adresi, hizmet için bir uç nokta oluşturmak üzere hizmetin bağlantı noktası numarasıyla ana bilgisayarın IP adresi birleştirilerek tanımlanır. <xref:System.Net.Dns> Sınıfı, yerel ağ aygıtı tarafından desteklenen ağ adresleri hakkında bilgi döndüren yöntemler sağlar. Yerel ağ cihazında birden fazla ağ adresi varsa veya yerel sistem birden fazla ağ cihazını destekliyorsa, **DNS** sınıfı tüm ağ adresleriyle ilgili bilgileri döndürür ve uygulamanın hizmet için uygun adresi seçmesi gerekir. Internet atanmış numaralar yetkilisi (IANA), ortak hizmetler için bağlantı noktası numaralarını tanımlar; daha fazla bilgi için bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/port-numbers). Diğer hizmetler 1.024 ile 65.535 arasında kayıt bağlantı noktası numaraları içerebilir.  
  
 Aşağıdaki örnek, ana bilgisayar <xref:System.Net.IPEndPoint> için **DNS** tarafından döndürülen ilk IP adresini, kayıtlı bağlantı noktası numaraları aralığından seçilen bir bağlantı noktası numarası ile birleştirerek bir sunucu için oluşturur.  
  
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
  
 Yerel uç nokta saptandıktan <xref:System.Net.Sockets.Socket> sonra, <xref:System.Net.Sockets.Socket.Bind%2A> yöntemi kullanılarak bu uç noktayla ilişkilendirilmelidir ve <xref:System.Net.Sockets.Socket.Listen%2A> yöntemi kullanılarak uç noktada dinlemek üzere ayarlanır. **Bağlama** , belirli bir adres ve bağlantı noktası birleşimi zaten kullanımda olduğunda bir özel durum oluşturur. Aşağıdaki örnek, bir **yuvayı** **ipendpoint**ile ilişkilendirdiğini gösterir.  
  
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
  
 **Dinleme** yöntemi, bağlantı istemcisine sunucu meşgul hatası döndürülmeden önce **yuva** için kaç tane bekleyen bağlantıya izin verileceğini belirten tek bir parametre alır. Bu durumda, 100 istemci 101 numarasına bir sunucu meşgul yanıtı döndürülmeden önce bağlantı kuyruğuna kadar istemci konur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumlu Sunucu Yuvası Kullanma](using-a-synchronous-server-socket.md)
- [Zaman Uyumsuz Sunucu Yuvası Kullanma](using-an-asynchronous-server-socket.md)
- [İstemci Yuvaları Kullanma](using-client-sockets.md)
- [Nasıl yapılır: Yuva oluşturma](how-to-create-a-socket.md)
- [Yuvalar](sockets.md)
