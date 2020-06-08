---
title: Zaman Uyumlu Sunucu Yuvası Kullanma
description: Bu örnekte, yuvada bir bağlantı isteği alınana kadar uygulamayı askıya alan .NET Framework zaman uyumlu bir sunucu yuvası gösterilmektedir.
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
ms.openlocfilehash: 9e7d32595f554b32ecc72bbb1f1a469ad5935467
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502060"
---
# <a name="using-a-synchronous-server-socket"></a>Zaman Uyumlu Sunucu Yuvası Kullanma
Zaman uyumlu sunucu yuvaları, yuvada bir bağlantı isteği alınana kadar uygulamanın yürütülmesini askıya alır. Zaman uyumlu sunucu yuvaları, ağ uygulamalarında yoğun olarak kullanılan uygulamalar için uygun değildir, ancak basit ağ uygulamaları için uygun olabilir.  
  
 Bir <xref:System.Net.Sockets.Socket> uç noktayı ve yöntemlerini kullanarak bir uç noktada dinlemek üzere ayarlandıktan sonra <xref:System.Net.Sockets.Socket.Bind%2A> <xref:System.Net.Sockets.Socket.Listen%2A> , yöntemi kullanılarak gelen bağlantı isteklerini kabul etmeye hazırlıdır <xref:System.Net.Sockets.Socket.Accept%2A> . **Accept** yöntemi çağrıldığında bir bağlantı isteği alınana kadar uygulama askıya alınır.  
  
 Bir bağlantı isteği alındığında, **kabul et** , bağlanılan istemciyle ilişkili yeni bir **yuva** örneği döndürür. Aşağıdaki örnek, istemciden gelen verileri okur, konsolunda görüntüler ve verileri istemciye geri yankılar. **Yuva** herhangi bir mesajlaşma Protokolü belirtmez, bu nedenle " \<EOF> " dizesi ileti verilerinin sonunu işaretler. Adlandırılmış bir **yuvanın** `listener` başlatıldığını ve bir uç noktaya bağlandığını varsayar.  
  
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

- [Zaman Uyumsuz Sunucu Yuvası Kullanma](using-an-asynchronous-server-socket.md)
- [Zaman Uyumlu Sunucu Yuvası Örneği](synchronous-server-socket-example.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
