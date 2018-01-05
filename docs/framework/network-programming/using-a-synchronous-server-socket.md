---
title: Zaman uyumlu Server yuva kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 03f6dc6ea517aba410430fea69113b64dccc6ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="fc36a-102">Zaman uyumlu Server yuva kullanma</span><span class="sxs-lookup"><span data-stu-id="fc36a-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="fc36a-103">Bir bağlantı isteği yuvada alınana kadar zaman uyumlu server yuva uygulamanın yürütülmesini askıya alın.</span><span class="sxs-lookup"><span data-stu-id="fc36a-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="fc36a-104">Zaman uyumlu server yuva ağ kullanımına ağırlık kendi işleminde uygulamalar için uygun değildir, ancak bunlar Basit Ağ uygulamaları için uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc36a-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="fc36a-105">Sonra bir <xref:System.Net.Sockets.Socket> kullanarak bir uç noktası dinleyecek şekilde ayarlanmıştır <xref:System.Net.Sockets.Socket.Bind%2A> ve <xref:System.Net.Sockets.Socket.Listen%2A> yöntemleri, gelen bağlantı istekleri kullanarak kabul etmeye hazır <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fc36a-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="fc36a-106">Bir bağlantı isteği alınana kadar uygulama askıya alınmış durumda olduğunda **kabul** yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fc36a-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="fc36a-107">Bir bağlantı isteği alındığında **kabul** yeni döndürür **yuva** bağlanan istemciyle ilişkili olan örneği.</span><span class="sxs-lookup"><span data-stu-id="fc36a-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="fc36a-108">Aşağıdaki örnek istemciden gelen verileri okur, konsolda görüntüler ve istemciye geri verileri görüntülemektedir.</span><span class="sxs-lookup"><span data-stu-id="fc36a-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="fc36a-109">**Yuva** herhangi bir Mesajlaşma protokolünü böylece belirtmiyor dizesi "\<EOF >" iletisi verilerini sonunu işaretler.</span><span class="sxs-lookup"><span data-stu-id="fc36a-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="fc36a-110">Varsayılmaktadır bir **yuva** adlı `listener` başlatılmadı ve bir uç noktasına bağlı.</span><span class="sxs-lookup"><span data-stu-id="fc36a-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc36a-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc36a-111">See Also</span></span>  
 [<span data-ttu-id="fc36a-112">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="fc36a-112">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="fc36a-113">Zaman Uyumlu Sunucu Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="fc36a-113">Synchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 [<span data-ttu-id="fc36a-114">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="fc36a-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
