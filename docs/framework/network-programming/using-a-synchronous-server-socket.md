---
title: Zaman uyumlu Server yuva kullanma
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4f04255edf9533612dd6b0733331fb18587ff3f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-synchronous-server-socket"></a>Zaman uyumlu Server yuva kullanma
Bir bağlantı isteği yuvada alınana kadar zaman uyumlu server yuva uygulamanın yürütülmesini askıya alın. Zaman uyumlu server yuva ağ kullanımına ağırlık kendi işleminde uygulamalar için uygun değildir, ancak bunlar Basit Ağ uygulamaları için uygun olabilir.  
  
 Sonra bir <xref:System.Net.Sockets.Socket> kullanarak bir uç noktası dinleyecek şekilde ayarlanmıştır <xref:System.Net.Sockets.Socket.Bind%2A> ve <xref:System.Net.Sockets.Socket.Listen%2A> yöntemleri, gelen bağlantı istekleri kullanarak kabul etmeye hazır <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi. Bir bağlantı isteği alınana kadar uygulama askıya alınmış durumda olduğunda **kabul** yöntemi çağrılır.  
  
 Bir bağlantı isteği alındığında **kabul** yeni döndürür **yuva** bağlanan istemciyle ilişkili olan örneği. Aşağıdaki örnek istemciden gelen verileri okur, konsolda görüntüler ve istemciye geri verileri görüntülemektedir. **Yuva** herhangi bir Mesajlaşma protokolünü böylece belirtmiyor dizesi "\<EOF >" iletisi verilerini sonunu işaretler. Varsayılmaktadır bir **yuva** adlı `listener` başlatılmadı ve bir uç noktasına bağlı.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman Uyumsuz Sunucu Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Zaman Uyumlu Sunucu Yuvası Örneği](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 [Yuvalarla Dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
