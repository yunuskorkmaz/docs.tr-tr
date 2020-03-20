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
ms.openlocfilehash: cf8316ede6888b99a8b0c87cfa3426b33be18b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180736"
---
# <a name="listening-with-sockets"></a>Yuvalarla Dinleme
Dinleyici veya sunucu soketleri ağda bir bağlantı noktası açar ve istemcinin bu bağlantı noktasına bağlanmasını bekler. Diğer ağ adresi aileleri ve protokolleri olsa da, bu örnek, bir TCP/IP ağı için uzaktan hizmetin nasıl oluşturulup oluşturulabildiğini gösterir.  
  
 Bir TCP/IP hizmetinin benzersiz adresi, hizmet için bir uç nokta oluşturmak için ana bilgisayar ın IP adresi ile hizmetin bağlantı noktası numarası nın birleştirilmesiyle tanımlanır. Sınıf, <xref:System.Net.Dns> yerel ağ aygıtı tarafından desteklenen ağ adresleri hakkında bilgi döndüren yöntemler sağlar. Yerel ağ aygıtında birden fazla ağ adresi varsa veya yerel sistem birden fazla ağ aygıtını destekliyorsa, **Dns** sınıfı tüm ağ adresleri hakkında bilgi verir ve uygulama nın hizmet için uygun adresi seçmesi gerekir. Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar; daha fazla bilgi için [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri'ne](https://www.iana.org/assignments/port-numbers)bakın. Diğer hizmetler, 1.024 ile 65.535 aralığında kayıtlı bağlantı noktası numaralarına sahip olabilir.  
  
 Aşağıdaki örnek, <xref:System.Net.IPEndPoint> **dns** tarafından ana bilgisayar için döndürülen ilk IP adresini kayıtlı bağlantı noktası numaraları aralığından seçilen bir bağlantı noktası numarasıyla birleştirerek bir sunucu için bir sunucu oluşturur.  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 Yerel bitiş noktası belirlendikten <xref:System.Net.Sockets.Socket> sonra, <xref:System.Net.Sockets.Socket.Bind%2A> yöntem kullanılarak bu uç nokta ile ilişkilendirilmeli ve <xref:System.Net.Sockets.Socket.Listen%2A> yöntemi kullanarak bitiş noktasını dinleyecek şekilde ayarlanmalıdır. **Bind,** belirli adres ve bağlantı noktası birleşimi zaten kullanılıyorsa bir özel durum oluşturur. Aşağıdaki örnek, bir **Soketi** **IPEndPoint**ile ilişkilendirme yi gösterir.  
  
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
  
 **Dinle** yöntemi, sunucu meşgul hatası bağlanan istemciye döndürülmeden önce **Soket'e** bekleyen kaç bağlantıya izin verildiğini belirten tek bir parametre alır. Bu durumda, sunucu meşgul yanıtı istemci numarası 101 döndürülmeden önce bağlantı kuyruğuna en fazla 100 istemci yerleştirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumlu Sunucu Yuvası Kullanma](using-a-synchronous-server-socket.md)
- [Zaman Uyumsuz Sunucu Yuvası Kullanma](using-an-asynchronous-server-socket.md)
- [İstemci Yuvaları Kullanma](using-client-sockets.md)
- [Nasıl Yapılır: Yuva Oluşturma](how-to-create-a-socket.md)
- [Yuvalar](sockets.md)
