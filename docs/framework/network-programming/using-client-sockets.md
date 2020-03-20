---
title: İstemci Yuvaları Kullanma
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
ms.openlocfilehash: fe2ad55c3f60347369c0e92bc834d81d98f3870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046952"
---
# <a name="using-client-sockets"></a><span data-ttu-id="c6dce-102">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6dce-102">Using Client Sockets</span></span>
<span data-ttu-id="c6dce-103">Bir <xref:System.Net.Sockets.Socket>üzerinden bir konuşma başlatamadan önce, uygulamanız ve uzak aygıt arasında bir veri borusu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6dce-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="c6dce-104">Diğer ağ adresi aileleri ve protokolleri olsa da, bu örnek, uzak bir hizmete nasıl TCP/IP bağlantısı oluşturulacak larını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6dce-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="c6dce-105">TCP/IP, bir hizmeti benzersiz olarak tanımlamak için bir ağ adresi ve hizmet bağlantı noktası numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6dce-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="c6dce-106">Ağ adresi ağdaki belirli bir aygıtı tanımlar; bağlantı noktası numarası, bağlanılabilmek için o aygıttaki belirli hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6dce-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="c6dce-107">Ağ adresi ve hizmet bağlantı noktasının birleşimi, <xref:System.Net.EndPoint> sınıf tarafından .NET Framework'de temsil edilen bir bitiş noktası olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c6dce-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="c6dce-108">Desteklenen her adres ailesi için **EndPoint** soyundan gelen bir aile tanımlanır; IP adresi ailesi için <xref:System.Net.IPEndPoint>sınıf.</span><span class="sxs-lookup"><span data-stu-id="c6dce-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="c6dce-109">Sınıf, <xref:System.Net.Dns> TCP/IP Internet hizmetlerini kullanan uygulamalara etki alanı adı hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6dce-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="c6dce-110">Yöntem, <xref:System.Net.Dns.Resolve%2A> kullanıcı dostu bir etki alanı adını ("host.contoso.com" gibi) sayısal bir Internet adresiyle (192.168.1.1 gibi) eşlemek için Bir DNS sunucusunu sorgular.</span><span class="sxs-lookup"><span data-stu-id="c6dce-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="c6dce-111">**Çözümle,** istenen ada ait adresler ve diğer adların listesini içeren bir <xref:System.Net.IPHostEntry> sürüc döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6dce-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="c6dce-112">Çoğu durumda, <xref:System.Net.IPHostEntry.AddressList%2A> dizide döndürülen ilk adresi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6dce-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="c6dce-113">Aşağıdaki kod, <xref:System.Net.IPAddress> sunucu host.contoso.com için IP adresini içeren bir kod alır.</span><span class="sxs-lookup"><span data-stu-id="c6dce-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="c6dce-114">Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar (daha fazla bilgi için [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri'ne](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)bakın).</span><span class="sxs-lookup"><span data-stu-id="c6dce-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="c6dce-115">Diğer hizmetler, 1.024 ile 65.535 aralığında kayıtlı bağlantı noktası numaralarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c6dce-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="c6dce-116">Aşağıdaki kod, bağlantı için uzak bir bitiş noktası oluşturmak için host.contoso.com ip adresini bir bağlantı noktası numarasıyla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c6dce-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="c6dce-117">Uzak aygıtın adresini belirledikten ve bağlantı için kullanılacak bir bağlantı noktası seçtikten sonra, uygulama uzak aygıtla bağlantı kurmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c6dce-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="c6dce-118">Aşağıdaki örnek, uzak bir aygıta bağlanmak için varolan bir **IPEndPoint** kullanır ve atılan tüm özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="c6dce-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6dce-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6dce-119">See also</span></span>

- [<span data-ttu-id="c6dce-120">Zaman Uyumlu İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6dce-120">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="c6dce-121">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c6dce-121">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="c6dce-122">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6dce-122">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="c6dce-123">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="c6dce-123">Sockets</span></span>](sockets.md)
