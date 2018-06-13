---
title: Yuva başına dinleme
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f85b63b151bcc20db635f56ec1dfec8df6c92241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395784"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="c27e4-102">Yuva başına dinleme</span><span class="sxs-lookup"><span data-stu-id="c27e4-102">Listening with Sockets</span></span>
<span data-ttu-id="c27e4-103">Dinleyici veya server yuva ağ üzerinde bir bağlantı noktası açın ve bu bağlantı noktasına bağlanmak bir istemci için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="c27e4-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="c27e4-104">Diğer ağ adres ailesi ve protokolleri mevcut olmasına karşın, bu örnek bir TCP/IP ağı için uzak hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c27e4-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="c27e4-105">TCP/IP'yi hizmetinin benzersiz adresini, ana bilgisayarın IP adresi hizmet için bir uç nokta oluşturmak için hizmet bağlantı noktası numarasını birleştirerek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c27e4-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="c27e4-106"><xref:System.Net.Dns> Sınıfı yerel ağ aygıtı tarafından desteklenen ağ adresleri ilgili bilgi döndüren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c27e4-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="c27e4-107">Yerel ağ aygıtı birden fazla ağ adresi olduğunda ya da yerel sistem birden fazla ağ aygıtı destekliyorsa **Dns** sınıfı, tüm ağ adresleri hakkında bilgi döndürür ve uygulama uygun seçmeniz gerekir hizmet adresi.</span><span class="sxs-lookup"><span data-stu-id="c27e4-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="c27e4-108">Internet Atanmış Numaralar Yetkilisi (IANA) (daha fazla bilgi için bkz: www.iana.org/assignments/port-numbers) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c27e4-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="c27e4-109">Diğer Hizmetleri bağlantı noktası numaraları aralığını 1.024 65. 535'ı için kayıt yaptırdınız.</span><span class="sxs-lookup"><span data-stu-id="c27e4-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="c27e4-110">Aşağıdaki örnekte bir <xref:System.Net.IPEndPoint> tarafından döndürülen ilk IP adresi birleştiren bir sunucu için **Dns** bir bağlantı noktası numarası ile ana bilgisayar için seçilen kayıtlı bağlantı noktası numaraları aralığında.</span><span class="sxs-lookup"><span data-stu-id="c27e4-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="c27e4-111">Yerel uç nokta belirlendikten sonra <xref:System.Net.Sockets.Socket> Bu uç nokta kullanarak ile ilişkilendirilmelidir <xref:System.Net.Sockets.Socket.Bind%2A> yöntemi ve kümesi kullanan uç noktasını dinlemek üzere <xref:System.Net.Sockets.Socket.Listen%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c27e4-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="c27e4-112">**Bağlama** bir özel durum döndürürse belirli adresi ve bağlantı noktası bileşimi zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="c27e4-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="c27e4-113">Aşağıdaki örnek, ilişkilendirme gösterir bir **yuva** ile bir **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="c27e4-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
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
  
 <span data-ttu-id="c27e4-114">**Dinleme** yöntemi için kaç tane bekleyen bağlantılar belirten tek bir parametre alan **yuva** sunucu meşgul hatası bağlanan istemciye döndürülmeden önce izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c27e4-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="c27e4-115">Bu durumda, sunucu meşgul yanıtı istemci numarası 101 döndürülmeden önce en fazla 100 istemci bağlantısı kuyruğuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c27e4-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c27e4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c27e4-116">See Also</span></span>  
 [<span data-ttu-id="c27e4-117">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c27e4-117">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="c27e4-118">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c27e4-118">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="c27e4-119">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c27e4-119">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="c27e4-120">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c27e4-120">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="c27e4-121">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="c27e4-121">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
