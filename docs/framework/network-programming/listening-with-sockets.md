---
title: Yuvalarla dinleme
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
ms.openlocfilehash: c518c3bea980e23367477bd1b9851630454b728b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075128"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="c1fd7-102">Yuvalarla dinleme</span><span class="sxs-lookup"><span data-stu-id="c1fd7-102">Listening with Sockets</span></span>
<span data-ttu-id="c1fd7-103">Dinleyici veya server yuva ağ üzerindeki bir bağlantı noktasını açın ve bu bağlantı noktasına bağlanmak bir istemci için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="c1fd7-104">Diğer ağ adresi ailelerini ve protokolleri mevcut olmasına karşın, bu örnek bir TCP/IP ağı için uzak bir hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="c1fd7-105">TCP/IP'yi hizmetinin benzersiz adresini, IP adresi ana bilgisayar hizmeti için bir uç nokta oluşturmak için hizmet bağlantı noktası numarasını birleştirerek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="c1fd7-106"><xref:System.Net.Dns> Sınıfı yerel ağ cihaz tarafından desteklenen ağ adresleri hakkında bilgi döndüren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="c1fd7-107">Yerel ağ cihaz birden fazla ağ adresi sahip olduğunda veya yerel sistemin birden fazla ağ aygıtı destekliyorsa **Dns** sınıfı, tüm ağ adresleri hakkında bilgileri döndürür ve uygulama uygun seçmeniz gerekir hizmet için adresi.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="c1fd7-108">Internet Atanmış Numaralar Yetkilisi (IANA) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar; Daha fazla bilgi için [hizmet adını ve Aktarım Protokolü bağlantı noktası numarasını kayıt defteri](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="c1fd7-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="c1fd7-109">Diğer hizmetler için 1024 65,535 aralığında bağlantı noktası numaralarını kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="c1fd7-110">Aşağıdaki örnek, oluşturur bir <xref:System.Net.IPEndPoint> tarafından döndürülen ilk IP adresini birleştirerek bir sunucu için **Dns** ana bilgisayar bağlantı noktası numarası için kayıtlı bir bağlantı noktası numaralarını aralıktan seçildi.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
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
  
 <span data-ttu-id="c1fd7-111">Yerel uç nokta belirlendikten sonra <xref:System.Net.Sockets.Socket> Bu uç noktayı kullanarak ile ilişkilendirilmelidir <xref:System.Net.Sockets.Socket.Bind%2A> yöntemi ve kullanarak uç noktası dinleyecek şekilde <xref:System.Net.Sockets.Socket.Listen%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="c1fd7-112">**Bağlama** bir özel durum oluşturur belirli adres ve bağlantı noktası zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="c1fd7-113">Aşağıdaki örnek, ilişkilendirme gösterir. bir **yuva** ile bir **IPEndPoint**.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
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
  
 <span data-ttu-id="c1fd7-114">**Dinleme** yöntemi kaç bekleyen bağlantılar belirten tek bir parametre alır **yuva** sunucu meşgul hatası bağlanan istemciye döndürülmeden önce izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="c1fd7-115">Bu durumda, bir sunucu meşgul yanıtı istemci sayıya 101 döndürülmeden önce en fazla 100 istemci bağlantı kuyruğuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1fd7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1fd7-116">See Also</span></span>  
 [<span data-ttu-id="c1fd7-117">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c1fd7-117">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="c1fd7-118">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c1fd7-118">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="c1fd7-119">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c1fd7-119">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="c1fd7-120">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1fd7-120">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="c1fd7-121">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="c1fd7-121">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
