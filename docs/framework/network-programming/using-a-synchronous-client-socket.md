---
title: Zaman Uyumlu İstemci Yuvası Kullanma
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
ms.openlocfilehash: fdecd18dc5975cd469e49de0eb0b55081e738cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047068"
---
# <a name="using-a-synchronous-client-socket"></a>Zaman Uyumlu İstemci Yuvası Kullanma
Ağ işlemi tamamlarken eşzamanlı istemci soketi uygulama programını askıya atanır. Senkron soketler, ağları n için yoğun olarak kullanan uygulamalar için uygun değildir, ancak diğer uygulamalar için ağ hizmetlerine basit erişim sağlayabilir.  
  
 Veri göndermek için, sınıfın veri gönderme <xref:System.Net.Sockets.Socket> yöntemlerinden birine bir bayt dizisi geçirin (<xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.SendTo%2A>). Aşağıdaki örnek özelliği kullanarak <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> bir bayt dizi arabelleği içine bir dize kodlar ve sonra **Gönder** yöntemini kullanarak ağ aygıtına arabellek iletir. **Gönder** yöntemi, ağ aygıtına gönderilen bayt sayısını döndürür.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Gönder** yöntemi arabellekten baytları kaldırır ve ağ aygıtına gönderilmek üzere ağ arabirimiyle sıralar. Ağ arabirimi verileri hemen göndermeyebilir, ancak bağlantı <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemle normal olarak kapatılır.  
  
 Bir ağ aygıtından veri almak için, bir arabellek **soket** sınıfının<xref:System.Net.Sockets.Socket.Receive%2A> alma <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>veri yöntemlerinden birine geçirin ( ve ). Senkron soketler, ağdan baytlar alınana veya soket kapanana kadar uygulamayı askıya alacaktır. Aşağıdaki örnek ağdan veri alır ve konsolda görüntüler. Örnek, ağdan gelen verilerin ASCII kodlanmış bir metin olduğunu varsayar. **Alma** yöntemi ağdan alınan bayt sayısını döndürür.  
  
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
  
 Sokete artık ihtiyaç duyulmadığında, <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi arayarak ve ardından **Kapat** yöntemini arayarak soketi serbest bırakmanız gerekir. Aşağıdaki örnekte bir **Soket**serbest. Numaralandırma, <xref:System.Net.Sockets.SocketShutdown> soketin göndermek, almak için mi yoksa her ikisi için mi kapatılması gerektiğini belirten sabitleri tanımlar.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumsuz İstemci Yuvası Kullanma](using-an-asynchronous-client-socket.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
- [Zaman Uyumlu İstemci Yuvası Örneği](synchronous-client-socket-example.md)
