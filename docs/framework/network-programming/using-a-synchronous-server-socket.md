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
ms.openlocfilehash: cbc02c755ceefa8f31439f121a98978b82f33fa2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047029"
---
# <a name="using-a-synchronous-server-socket"></a><span data-ttu-id="446cd-102">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="446cd-102">Using a Synchronous Server Socket</span></span>
<span data-ttu-id="446cd-103">Zaman uyumlu sunucu yuvaları, yuvada bir bağlantı isteği alınana kadar uygulamanın yürütülmesini askıya alır.</span><span class="sxs-lookup"><span data-stu-id="446cd-103">Synchronous server sockets suspend the execution of the application until a connection request is received on the socket.</span></span> <span data-ttu-id="446cd-104">Zaman uyumlu sunucu yuvaları, ağ uygulamalarında yoğun olarak kullanılan uygulamalar için uygun değildir, ancak basit ağ uygulamaları için uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="446cd-104">Synchronous server sockets are not suitable for applications that make heavy use of the network in their operation, but they can be suitable for simple network applications.</span></span>  
  
 <span data-ttu-id="446cd-105">Bir uç <xref:System.Net.Sockets.Socket> noktayı <xref:System.Net.Sockets.Socket.Bind%2A> ve <xref:System.Net.Sockets.Socket.Listen%2A> yöntemlerini kullanarak bir uç noktada dinlemek üzere ayarlandıktan sonra, <xref:System.Net.Sockets.Socket.Accept%2A> yöntemi kullanılarak gelen bağlantı isteklerini kabul etmeye hazırlıdır.</span><span class="sxs-lookup"><span data-stu-id="446cd-105">After a <xref:System.Net.Sockets.Socket> is set to listen on an endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> and <xref:System.Net.Sockets.Socket.Listen%2A> methods, it is ready to accept incoming connection requests using the <xref:System.Net.Sockets.Socket.Accept%2A> method.</span></span> <span data-ttu-id="446cd-106">**Accept** yöntemi çağrıldığında bir bağlantı isteği alınana kadar uygulama askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="446cd-106">The application is suspended until a connection request is received when the **Accept** method is called.</span></span>  
  
 <span data-ttu-id="446cd-107">Bir bağlantı isteği alındığında, **kabul et** , bağlanılan istemciyle ilişkili yeni bir **yuva** örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="446cd-107">When a connection request is received, **Accept** returns a new **Socket** instance that is associated with the connecting client.</span></span> <span data-ttu-id="446cd-108">Aşağıdaki örnek, istemciden gelen verileri okur, konsolunda görüntüler ve verileri istemciye geri yankılar.</span><span class="sxs-lookup"><span data-stu-id="446cd-108">The following example reads data from the client, displays it on the console, and echoes the data back to the client.</span></span> <span data-ttu-id="446cd-109">**Yuva** herhangi bir ileti Protokolü belirtmez, bu nedenle "\<EOF >" dizesi ileti verilerinin sonunu işaretler.</span><span class="sxs-lookup"><span data-stu-id="446cd-109">The **Socket** does not specify any messaging protocol, so the string "\<EOF>" marks the end of the message data.</span></span> <span data-ttu-id="446cd-110">Adlandırılmış`listener` bir **yuvanın** başlatıldığını ve bir uç noktaya bağlandığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="446cd-110">It assumes that a **Socket** named `listener` has been initialized and bound to an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="446cd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="446cd-111">See also</span></span>

- [<span data-ttu-id="446cd-112">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="446cd-112">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="446cd-113">Zaman Uyumlu Sunucu Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="446cd-113">Synchronous Server Socket Example</span></span>](synchronous-server-socket-example.md)
- [<span data-ttu-id="446cd-114">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="446cd-114">Listening with Sockets</span></span>](listening-with-sockets.md)
