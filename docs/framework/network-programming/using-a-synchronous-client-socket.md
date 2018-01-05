---
title: "Zaman uyumlu istemci yuvası kullanma"
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 03595539d825f26251a24fce33ede2552b79b38b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="f5fc4-102">Zaman uyumlu istemci yuvası kullanma</span><span class="sxs-lookup"><span data-stu-id="f5fc4-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="f5fc4-103">Ağ işlemi tamamlanırken bir zaman uyumlu istemci yuva uygulama programı askıya alır.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="f5fc4-104">Zaman uyumlu yuva ağ yoğun olarak kullanılır, işlem için uygulamalar için uygun değildir, ancak basit ağ hizmetlerine erişim için diğer uygulamalar için etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="f5fc4-105">Veri göndermek için bir bayt dizisi birine geçirmek <xref:System.Net.Sockets.Socket> sınıfının gönderme veri yöntemleri (<xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="f5fc4-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="f5fc4-106">Aşağıdaki örnekte bir dizeyi bir bayt dizisi kullanarak arabellek kodlar <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> özelliği ve kullanarak ağ aygıtı için arabellek iletir **Gönder** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="f5fc4-107">**Gönder** yöntemi ağ cihazına gönderilen bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="f5fc4-108">**Gönder** yöntemi arabellekteki bayt kaldırır ve bunları ağ cihazına gönderilmek üzere ağ arabirimine sahip sıralar.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="f5fc4-109">Ağ arabirimi verileri hemen göndermek, ancak bağlantı normalde ile kapalı olduğu sürece, sonuç olarak, göndereceğiniz <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="f5fc4-110">Bir ağ aygıtından veri almak için bir arabellek birine geçirmek **yuva** sınıfının aldığınız verilerinin yöntemleri (<xref:System.Net.Sockets.Socket.Receive%2A> ve <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span><span class="sxs-lookup"><span data-stu-id="f5fc4-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="f5fc4-111">Bayt ağdan veya yuva kapatılana kadar alınana kadar zaman uyumlu yuva uygulama askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="f5fc4-112">Aşağıdaki örnek veri ağdan alır ve konsolda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="f5fc4-113">Örneğin, ağdan gelen veriler ASCII kodlanmış metin olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="f5fc4-114">**Alma** yöntemi ağdan alınan bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="f5fc4-115">Yuva artık gerekli olmadığında çağırarak serbest bırakmanız <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi ve ardından çağırma **Kapat** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="f5fc4-116">Aşağıdaki örnek serbest bir **yuva**.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="f5fc4-117"><xref:System.Net.Sockets.SocketShutdown> Numaralandırma yuva gönderme, alma veya her ikisi için de kapatılıp kapatılmayacağını belirtmek sabitleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5fc4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5fc4-118">See Also</span></span>  
 [<span data-ttu-id="f5fc4-119">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="f5fc4-119">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="f5fc4-120">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="f5fc4-120">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [<span data-ttu-id="f5fc4-121">Zaman Uyumlu İstemci Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="f5fc4-121">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
