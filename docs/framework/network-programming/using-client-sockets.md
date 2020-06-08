---
title: İstemci Yuvaları Kullanma
description: Bu örnek, .NET Framework bir yuva kullanarak uzak bir hizmete TCP/IP bağlantısı oluşturmayı gösterir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: 1dc02d0b3651d5766d1d30752566217d8417af0c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502008"
---
# <a name="using-client-sockets"></a><span data-ttu-id="b53c8-103">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b53c8-103">Using Client Sockets</span></span>
<span data-ttu-id="b53c8-104">Bir konuşmayı bir ile başlatmak için önce <xref:System.Net.Sockets.Socket> uygulamanız ile uzak cihaz arasında bir veri kanalı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b53c8-104">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="b53c8-105">Diğer ağ adresi aileleri ve protokolleri var olsa da bu örnek, uzak bir hizmete TCP/IP bağlantısının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b53c8-105">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="b53c8-106">TCP/IP bir hizmeti benzersiz bir şekilde tanımlamak için bir ağ adresi ve bir hizmet bağlantı noktası numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="b53c8-106">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="b53c8-107">Ağ adresi ağ üzerinde belirli bir cihazı tanımlar; bağlantı noktası numarası, bu cihazdaki Bağlanılacak belirli hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b53c8-107">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="b53c8-108">Ağ adresi ve hizmet bağlantı noktası birleşimine, sınıfı tarafından .NET Framework temsil edilen bir uç nokta denir <xref:System.Net.EndPoint> .</span><span class="sxs-lookup"><span data-stu-id="b53c8-108">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="b53c8-109">Her desteklenen adres ailesi için **uç nokta** alt öğesi tanımlanmıştır; IP adresi ailesi için sınıfı <xref:System.Net.IPEndPoint> .</span><span class="sxs-lookup"><span data-stu-id="b53c8-109">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="b53c8-110"><xref:System.Net.Dns>Sınıfı, TCP/IP Internet hizmetlerini kullanan uygulamalara etki alanı ad hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b53c8-110">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="b53c8-111"><xref:System.Net.Dns.Resolve%2A>Yöntemi, BIR DNS sunucusunu, Kullanıcı dostu bir etki alanı adını (örneğin, "Host.contoso.com") sayısal bir Internet adresine (192.168.1.1 gibi) eşlemek üzere sorgular.</span><span class="sxs-lookup"><span data-stu-id="b53c8-111">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="b53c8-112">**Resolve** <xref:System.Net.IPHostEntry> , istenen ad için adreslerin ve diğer adların bir listesini içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="b53c8-112">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="b53c8-113">Çoğu durumda, dizide döndürülen ilk adresi kullanabilirsiniz <xref:System.Net.IPHostEntry.AddressList%2A> .</span><span class="sxs-lookup"><span data-stu-id="b53c8-113">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="b53c8-114">Aşağıdaki kod, <xref:System.Net.IPAddress> sunucu Host.contoso.com için IP adresini içeren bir IP adresi alır.</span><span class="sxs-lookup"><span data-stu-id="b53c8-114">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="b53c8-115">Internet atanmış numaralar yetkilisi (IANA) ortak hizmetler için bağlantı noktası numaralarını tanımlar (daha fazla bilgi için bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="b53c8-115">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="b53c8-116">Diğer hizmetler 1.024 ile 65.535 arasında kayıt bağlantı noktası numaraları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b53c8-116">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="b53c8-117">Aşağıdaki kod, bir bağlantı için uzak uç nokta oluşturmak üzere host.contoso.com IP adresini bir bağlantı noktası numarasıyla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b53c8-117">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="b53c8-118">Uzak cihazın adresini belirledikten ve bağlantı için kullanılacak bir bağlantı noktası seçtikten sonra uygulama, uzak cihazla bağlantı kurmayı deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="b53c8-118">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="b53c8-119">Aşağıdaki örnek, uzak bir cihaza bağlanmak ve oluşturulan tüm özel durumları yakalayan mevcut bir **IPEndPoint** kullanır.</span><span class="sxs-lookup"><span data-stu-id="b53c8-119">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b53c8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b53c8-120">See also</span></span>

- [<span data-ttu-id="b53c8-121">Zaman Uyumlu İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="b53c8-121">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="b53c8-122">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="b53c8-122">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="b53c8-123">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b53c8-123">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="b53c8-124">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="b53c8-124">Sockets</span></span>](sockets.md)
