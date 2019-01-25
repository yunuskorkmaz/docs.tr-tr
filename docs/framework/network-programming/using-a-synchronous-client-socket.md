---
title: Zaman uyumlu istemci yuvası kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: a368048f83540bf5bb9cd43a0a88c40641eb7e94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621712"
---
# <a name="using-a-synchronous-client-socket"></a>Zaman uyumlu istemci yuvası kullanma
Ağ işlemi tamamlanırken bir zaman uyumlu istemci yuvası uygulama programı askıya alır. Eşzamanlı yuva kendi işlemleri için ağ ağır olarak kullanan uygulamalar için uygun değildir, ancak bunlar diğer uygulamalar için Ağ Hizmetleri için basit erişim sağlar.  
  
 Veri göndermek için bir bayt dizisi birine geçmesi <xref:System.Net.Sockets.Socket> sınıfın veri gönderme yöntemleri (<xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.SendTo%2A>). Aşağıdaki örnek bir dizeyi bir bayt dizisi kullanarak arabellek kodlar <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> özelliği ve ardından ağ aygıtıyla arabellek iletir **Gönder** yöntemi. **Gönder** yöntem ağ cihazına gönderilen bayt sayısını döndürür.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Gönder** yöntemi arabellekteki bayt kaldırır ve ağ cihazına gönderilmek üzere ağ arabirimi ile kuyruğa. Ağ arabirimi verileri hemen göndermek, ancak bu bağlantı normalde ile kapalı olduğu sürece bu sonuç olarak, gönderecek <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi.  
  
 Bir ağ aygıtından veri almak, bir arabellek birine geçmesi **yuva** sınıfın alma veri yöntemleri (<xref:System.Net.Sockets.Socket.Receive%2A> ve <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>). Bayt ağdan veya yuva kapatılana kadar alınana kadar eşzamanlı yuva uygulama askıya alırız. Aşağıdaki örnek, ağ üzerinden veri aldığı ve daha sonra konsolda görüntüler. Örneğin, ağdan gelen verileri ASCII kodlamalı metin olduğunu varsayar. **Alma** yöntemi ağdan alınan bayt sayısını döndürür.  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 Yuva artık gerekli değilse, bunu çağırarak serbest bırakmanız <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi ve ardından arama **Kapat** yöntemi. Aşağıdaki örnek sürümleri bir **yuva**. <xref:System.Net.Sockets.SocketShutdown> Yuvaya gönderme, alma veya her ikisi için de kapatılıp kapatılmayacağını belirtir sabitleri sabit listesi tanımlar.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Zaman Uyumsuz İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [Yuvalarla Dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
- [Zaman Uyumlu İstemci Yuvası Örneği](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
