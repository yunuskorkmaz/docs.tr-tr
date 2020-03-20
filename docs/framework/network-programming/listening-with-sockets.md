---
title: Yuvalarla Dinleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: cf8316ede6888b99a8b0c87cfa3426b33be18b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180736"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="06ed7-102">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="06ed7-102">Listening with Sockets</span></span>
<span data-ttu-id="06ed7-103">Dinleyici veya sunucu soketleri ağda bir bağlantı noktası açar ve istemcinin bu bağlantı noktasına bağlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="06ed7-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="06ed7-104">Diğer ağ adresi aileleri ve protokolleri olsa da, bu örnek, bir TCP/IP ağı için uzaktan hizmetin nasıl oluşturulup oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ed7-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="06ed7-105">Bir TCP/IP hizmetinin benzersiz adresi, hizmet için bir uç nokta oluşturmak için ana bilgisayar ın IP adresi ile hizmetin bağlantı noktası numarası nın birleştirilmesiyle tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="06ed7-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="06ed7-106">Sınıf, <xref:System.Net.Dns> yerel ağ aygıtı tarafından desteklenen ağ adresleri hakkında bilgi döndüren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="06ed7-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="06ed7-107">Yerel ağ aygıtında birden fazla ağ adresi varsa veya yerel sistem birden fazla ağ aygıtını destekliyorsa, **Dns** sınıfı tüm ağ adresleri hakkında bilgi verir ve uygulama nın hizmet için uygun adresi seçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="06ed7-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="06ed7-108">Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar; daha fazla bilgi için [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri'ne](https://www.iana.org/assignments/port-numbers)bakın.</span><span class="sxs-lookup"><span data-stu-id="06ed7-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="06ed7-109">Diğer hizmetler, 1.024 ile 65.535 aralığında kayıtlı bağlantı noktası numaralarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="06ed7-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="06ed7-110">Aşağıdaki örnek, <xref:System.Net.IPEndPoint> **dns** tarafından ana bilgisayar için döndürülen ilk IP adresini kayıtlı bağlantı noktası numaraları aralığından seçilen bir bağlantı noktası numarasıyla birleştirerek bir sunucu için bir sunucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06ed7-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="06ed7-111">Yerel bitiş noktası belirlendikten <xref:System.Net.Sockets.Socket> sonra, <xref:System.Net.Sockets.Socket.Bind%2A> yöntem kullanılarak bu uç nokta ile ilişkilendirilmeli ve <xref:System.Net.Sockets.Socket.Listen%2A> yöntemi kullanarak bitiş noktasını dinleyecek şekilde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06ed7-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="06ed7-112">**Bind,** belirli adres ve bağlantı noktası birleşimi zaten kullanılıyorsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06ed7-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="06ed7-113">Aşağıdaki örnek, bir **Soketi** **IPEndPoint**ile ilişkilendirme yi gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ed7-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp)
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="06ed7-114">**Dinle** yöntemi, sunucu meşgul hatası bağlanan istemciye döndürülmeden önce **Soket'e** bekleyen kaç bağlantıya izin verildiğini belirten tek bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="06ed7-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="06ed7-115">Bu durumda, sunucu meşgul yanıtı istemci numarası 101 döndürülmeden önce bağlantı kuyruğuna en fazla 100 istemci yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="06ed7-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ed7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06ed7-116">See also</span></span>

- [<span data-ttu-id="06ed7-117">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="06ed7-117">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="06ed7-118">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="06ed7-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="06ed7-119">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="06ed7-119">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="06ed7-120">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="06ed7-120">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="06ed7-121">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="06ed7-121">Sockets</span></span>](sockets.md)
