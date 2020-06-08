---
title: Zaman Uyumlu İstemci Yuvası Kullanma
description: Bu örnekte, ağ işlemi tamamlanırken uygulama programını askıya alarak .NET Framework zaman uyumlu bir istemci yuvası gösterilmektedir.
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
ms.openlocfilehash: ef682af33c10cf06ffc398c22e4a7dc1adf8290e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502073"
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="feb7f-103">Zaman Uyumlu İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="feb7f-103">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="feb7f-104">Ağ işlemi tamamlanırken, zaman uyumlu bir istemci yuvası uygulama programını askıya alır.</span><span class="sxs-lookup"><span data-stu-id="feb7f-104">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="feb7f-105">Zaman uyumlu yuvalar, ağ işlemleri için yoğun olarak kullanılan uygulamalar için uygun değildir, ancak diğer uygulamalar için ağ hizmetlerine basit erişimi etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="feb7f-105">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="feb7f-106">Veri göndermek için, <xref:System.Net.Sockets.Socket> sınıfın Send-Data yöntemlerinden birine bir bayt dizisi geçirin ( <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.SendTo%2A> ).</span><span class="sxs-lookup"><span data-stu-id="feb7f-106">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="feb7f-107">Aşağıdaki örnek, özelliğini kullanarak bir dizeyi bir bayt dizisi arabelleğine kodluyor <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> ve sonra **Send** metodunu kullanarak arabelleği ağ cihazına iletir.</span><span class="sxs-lookup"><span data-stu-id="feb7f-107">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="feb7f-108">**Send** yöntemi, ağ cihazına gönderilen bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="feb7f-108">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="feb7f-109">**Send** yöntemi arabellekteki baytları kaldırır ve ağ cihazına gönderilmek üzere ağ arabirimiyle sıralar.</span><span class="sxs-lookup"><span data-stu-id="feb7f-109">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="feb7f-110">Ağ arabirimi, verileri hemen gönderemeyebilir, ancak bağlantı, normal şekilde yöntemle kapandığı sürece, bu işlemi sonunda gönderir <xref:System.Net.Sockets.Socket.Shutdown%2A> .</span><span class="sxs-lookup"><span data-stu-id="feb7f-110">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="feb7f-111">Bir ağ aygıtından veri almak için, **yuva** sınıfının Receive-Data yöntemlerinden birine bir arabellek geçirin ( <xref:System.Net.Sockets.Socket.Receive%2A> ve <xref:System.Net.Sockets.Socket.ReceiveFrom%2A> ).</span><span class="sxs-lookup"><span data-stu-id="feb7f-111">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="feb7f-112">Zaman uyumlu yuvalar, ağdan bayt alınana veya yuva kapatılıncaya kadar uygulamayı askıya alır.</span><span class="sxs-lookup"><span data-stu-id="feb7f-112">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="feb7f-113">Aşağıdaki örnek, ağdan verileri alır ve sonra konsolunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="feb7f-113">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="feb7f-114">Örnek, ağdan gelen verilerin ASCII kodlamalı metin olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="feb7f-114">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="feb7f-115">**Receive** yöntemi ağdan alınan bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="feb7f-115">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="feb7f-116">Yuva artık gerekli olmadığında, <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemini çağırarak ve sonra **Close** metodunu çağırarak onu serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="feb7f-116">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="feb7f-117">Aşağıdaki örnek bir **yuva**yayınlar.</span><span class="sxs-lookup"><span data-stu-id="feb7f-117">The following example releases a **Socket**.</span></span> <span data-ttu-id="feb7f-118"><xref:System.Net.Sockets.SocketShutdown>Sabit listesi, yuvanın gönderme, alma için veya her ikisi için de kapatılıp kapatılmayacağını belirten sabitleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="feb7f-118">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="feb7f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feb7f-119">See also</span></span>

- [<span data-ttu-id="feb7f-120">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="feb7f-120">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="feb7f-121">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="feb7f-121">Listening with Sockets</span></span>](listening-with-sockets.md)
- [<span data-ttu-id="feb7f-122">Zaman Uyumlu İstemci Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="feb7f-122">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
