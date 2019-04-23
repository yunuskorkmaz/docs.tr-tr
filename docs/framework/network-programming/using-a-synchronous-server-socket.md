---
title: Zaman Uyumlu Sunucu Yuvası Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
ms.openlocfilehash: 43e1d54d4e74b49fdf1a8997d1cc89492c9412bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117258"
---
# <a name="using-a-synchronous-server-socket"></a>Zaman Uyumlu Sunucu Yuvası Kullanma
Yuva bağlantısı isteği alınana kadar zaman uyumlu sunucu yuva uygulamanın yürütülmesini askıya alın. Zaman uyumlu sunucu yuva ağ kullanımı yoğun uygulamalar, işlemi için uygun değildir, ancak Basit Ağ uygulamaları için uygun olabilir.  
  
 Sonra bir <xref:System.Net.Sockets.Socket> kullanarak bir uç noktası dinleyecek şekilde ayarlanır <xref:System.Net.Sockets.Socket.Bind%2A> ve <xref:System.Net.Sockets.Socket.Listen%2A> yöntemleri, gelen bağlantı isteklerini kullanarak kabul etmeye hazır <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi. Bir bağlantı isteği alınana kadar uygulamanın askıya olduğunda **kabul** yöntemi çağrılır.  
  
 Bir bağlantı isteği alındığında **kabul** yeni bir **yuva** bağlanan istemcinin ile ilişkili olan örneği. Aşağıdaki örnek istemciden gelen verileri okur, konsolda görüntüler ve istemcisine verileri görüntülemektedir. **Yuva** herhangi bir Mesajlaşma protokolü, bu nedenle belirtmiyor dize "\<EOF >" ileti verileri sonunu işaretler. Olduğunu varsayar bir **yuva** adlı `listener` başlatılır ve bir uç noktasına bağlı.  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumsuz Sunucu Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [Zaman Uyumlu Sunucu Yuvası Örneği](../../../docs/framework/network-programming/synchronous-server-socket-example.md)
- [Yuvalarla Dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
