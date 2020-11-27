---
title: 'Nasıl yapılır: Yuva Oluşturma'
description: Uzak cihazlarla iletişim kurmak için bir yuva başlatmayı öğrenin. Adres ailesini, yuva türünü ve protokol türünü belirtmek için yuva sınıfını kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 9746b814188a4dc92463399542a6044501d0da12
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287403"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="8394a-104">Nasıl yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8394a-104">How to: Create a Socket</span></span>

<span data-ttu-id="8394a-105">Uzak cihazlarla iletişim kurmak üzere bir yuva kullanabilmeniz için, yuva protokol ve ağ adresi bilgileriyle başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8394a-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="8394a-106">Sınıfına yönelik oluşturucunun, <xref:System.Net.Sockets.Socket> bağlantı kurmak için yuvanın kullandığı adres ailesini, yuva türünü ve protokol türünü belirten parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8394a-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8394a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8394a-107">Example</span></span>  

 <span data-ttu-id="8394a-108">Aşağıdaki örnek, Internet gibi TCP/IP tabanlı bir ağda iletişim kurmak için kullanılabilecek bir yuva oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8394a-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="8394a-109">TCP yerine UDP kullanmak için, aşağıdaki örnekte olduğu gibi protokol türünü değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8394a-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="8394a-110"><xref:System.Net.Sockets.AddressFamily>Sabit listesi, ağ adreslerini çözümlemek Için **yuva** sınıfı tarafından kullanılan standart adres aileleri belirtir (örneğin, **AddressFamily. ıNTERNETWORK** üyesi, IP sürüm 4 adres ailesini belirtir).</span><span class="sxs-lookup"><span data-stu-id="8394a-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="8394a-111"><xref:System.Net.Sockets.SocketType>Numaralandırma, yuva türünü belirtir (örneğin, **SocketType. Stream** üyesi, akış denetimiyle veri gönderme ve alma için standart bir yuva gösterir).</span><span class="sxs-lookup"><span data-stu-id="8394a-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="8394a-112"><xref:System.Net.Sockets.ProtocolType>Sabit listesi, **yuvada** iletişim kurulurken kullanılacak ağ protokolünü belirtir (örneğin, **ProtocolType. TCP** , yuvanın TCP kullandığını gösterir; **ProtocolType. UDP** , yuvanın UDP kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8394a-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="8394a-113">Bir **yuva** oluşturulduktan sonra, uzak bir uç noktaya bağlantı başlatabilir veya uzak cihazlardan gelen bağlantıları alabilir.</span><span class="sxs-lookup"><span data-stu-id="8394a-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8394a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8394a-114">See also</span></span>

- [<span data-ttu-id="8394a-115">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8394a-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="8394a-116">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="8394a-116">Listening with Sockets</span></span>](listening-with-sockets.md)
