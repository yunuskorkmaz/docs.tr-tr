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
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="4c007-102">Zaman Uyumlu İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="4c007-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="4c007-103">Ağ işlemi tamamlarken eşzamanlı istemci soketi uygulama programını askıya atanır.</span><span class="sxs-lookup"><span data-stu-id="4c007-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="4c007-104">Senkron soketler, ağları n için yoğun olarak kullanan uygulamalar için uygun değildir, ancak diğer uygulamalar için ağ hizmetlerine basit erişim sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="4c007-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="4c007-105">Veri göndermek için, sınıfın veri gönderme <xref:System.Net.Sockets.Socket> yöntemlerinden birine bir bayt dizisi geçirin (<xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.SendTo%2A>).</span><span class="sxs-lookup"><span data-stu-id="4c007-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="4c007-106">Aşağıdaki örnek özelliği kullanarak <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> bir bayt dizi arabelleği içine bir dize kodlar ve sonra **Gönder** yöntemini kullanarak ağ aygıtına arabellek iletir.</span><span class="sxs-lookup"><span data-stu-id="4c007-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="4c007-107">**Gönder** yöntemi, ağ aygıtına gönderilen bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c007-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="4c007-108">**Gönder** yöntemi arabellekten baytları kaldırır ve ağ aygıtına gönderilmek üzere ağ arabirimiyle sıralar.</span><span class="sxs-lookup"><span data-stu-id="4c007-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="4c007-109">Ağ arabirimi verileri hemen göndermeyebilir, ancak bağlantı <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemle normal olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="4c007-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="4c007-110">Bir ağ aygıtından veri almak için, bir arabellek **soket** sınıfının<xref:System.Net.Sockets.Socket.Receive%2A> alma <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>veri yöntemlerinden birine geçirin ( ve ).</span><span class="sxs-lookup"><span data-stu-id="4c007-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="4c007-111">Senkron soketler, ağdan baytlar alınana veya soket kapanana kadar uygulamayı askıya alacaktır.</span><span class="sxs-lookup"><span data-stu-id="4c007-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="4c007-112">Aşağıdaki örnek ağdan veri alır ve konsolda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4c007-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="4c007-113">Örnek, ağdan gelen verilerin ASCII kodlanmış bir metin olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="4c007-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="4c007-114">**Alma** yöntemi ağdan alınan bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c007-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="4c007-115">Sokete artık ihtiyaç duyulmadığında, <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi arayarak ve ardından **Kapat** yöntemini arayarak soketi serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c007-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="4c007-116">Aşağıdaki örnekte bir **Soket**serbest.</span><span class="sxs-lookup"><span data-stu-id="4c007-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="4c007-117">Numaralandırma, <xref:System.Net.Sockets.SocketShutdown> soketin göndermek, almak için mi yoksa her ikisi için mi kapatılması gerektiğini belirten sabitleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4c007-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c007-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c007-118">See also</span></span>

- [<span data-ttu-id="4c007-119">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="4c007-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="4c007-120">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="4c007-120">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="4c007-121">Zaman Uyumlu İstemci Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="4c007-121">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
