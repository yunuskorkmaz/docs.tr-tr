---
title: İstemci yuvaları kullanma
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 458e67861bfd40b69f7a6f756ddee8be433e9e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395953"
---
# <a name="using-client-sockets"></a><span data-ttu-id="9f611-102">İstemci yuvaları kullanma</span><span class="sxs-lookup"><span data-stu-id="9f611-102">Using Client Sockets</span></span>
<span data-ttu-id="9f611-103">Konuşma aracılığıyla başlatmadan önce bir <xref:System.Net.Sockets.Socket>, uygulamanızı ve uzak aygıt veri kanalı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f611-103">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="9f611-104">Diğer ağ adres ailesi ve protokolleri mevcut olmasına karşın, bu örnek uzak bir hizmet için TCP/IP'yi bağlantısının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f611-104">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="9f611-105">TCP/IP'yi hizmet benzersiz şekilde tanımlamak için bir ağ adresi ve bir hizmet bağlantı noktası numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f611-105">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="9f611-106">Ağ adresi ağdaki belirli bir aygıt tanımlar; bağlantı noktası numarasını hizmete bağlanmak için bu cihazda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f611-106">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="9f611-107">Ağ adresi ve hizmet bağlantı noktası bileşimi .NET Framework tarafından temsil edilen bir uç nokta adı verilen <xref:System.Net.EndPoint> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9f611-107">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="9f611-108">Bir alt öğesi **EndPoint** için tanımlanan her desteklenen Adres ailesi; IP adresi ailesi için sınıf <xref:System.Net.IPEndPoint>.</span><span class="sxs-lookup"><span data-stu-id="9f611-108">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="9f611-109"><xref:System.Net.Dns> Sınıfı, TCP/IP'yi Internet Hizmetleri kullanan uygulamalar için etki alanı adı hizmetleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f611-109">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="9f611-110"><xref:System.Net.Dns.Resolve%2A> Yöntemi (örneğin, 192.168.1.1) sayısal bir Internet adresi için bir kolay kullanılan etki alanı adı (örneğin, "host.contoso.com") eşlemek için bir DNS sunucusu sorgular.</span><span class="sxs-lookup"><span data-stu-id="9f611-110">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="9f611-111">**Gidermek** döndüren bir <xref:System.Net.IPHostEntry> adresleri ve istenen ad için diğer adlar listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9f611-111">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="9f611-112">Çoğu durumda, döndürülen ilk adres kullanabilirsiniz <xref:System.Net.IPHostEntry.AddressList%2A> dizi.</span><span class="sxs-lookup"><span data-stu-id="9f611-112">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="9f611-113">Aşağıdaki kod alır bir <xref:System.Net.IPAddress> server host.contoso.com IP adresini içeren.</span><span class="sxs-lookup"><span data-stu-id="9f611-113">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="9f611-114">Internet Atanmış Numaralar Yetkilisi (IANA) (daha fazla bilgi için bkz: www.iana.org/assignments/port-numbers) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f611-114">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="9f611-115">Diğer Hizmetleri bağlantı noktası numaraları aralığını 1.024 65. 535'ı için kayıt yaptırdınız.</span><span class="sxs-lookup"><span data-stu-id="9f611-115">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="9f611-116">Aşağıdaki kod host.contoso.com IP adresini bir uzak uç nokta için bir bağlantı oluşturmak için bir bağlantı noktası numarası ile birleştirir.</span><span class="sxs-lookup"><span data-stu-id="9f611-116">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="9f611-117">Uzak aygıt adresi belirleme ve bağlantı için kullanılacak bağlantı noktasını seçme sonra uygulama uzak aygıt ile bağlantı kurmak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f611-117">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="9f611-118">Aşağıdaki örnek, var olan kullanır **IPEndPoint** uzak bir aygıta bağlanmayı ve oluşturulan tüm özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="9f611-118">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f611-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f611-119">See Also</span></span>  
 [<span data-ttu-id="9f611-120">Zaman Uyumlu İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="9f611-120">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [<span data-ttu-id="9f611-121">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="9f611-121">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="9f611-122">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f611-122">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="9f611-123">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="9f611-123">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
