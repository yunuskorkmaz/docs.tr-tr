---
title: 'Nasıl Yapılır: Yuva Oluşturma'
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
ms.openlocfilehash: e71e7e235048361580c65bdb551919fe3038130b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180832"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="1b063-102">Nasıl Yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b063-102">How to: Create a Socket</span></span>
<span data-ttu-id="1b063-103">Uzak aygıtlarla iletişim kurmak için bir soket kullanabilmek için önce, soketin protokol ve ağ adresi bilgileriyle başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b063-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="1b063-104">Sınıfın oluşturucusu, yuvanın <xref:System.Net.Sockets.Socket> bağlantı yapmak için kullandığı adres ailesini, yuva türünü ve protokol türünü belirten parametrelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1b063-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b063-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b063-105">Example</span></span>  
 <span data-ttu-id="1b063-106">Aşağıdaki örnek, Internet gibi TCP/IP tabanlı bir ağda iletişim kurmak için kullanılabilecek bir Soket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b063-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="1b063-107">TCP yerine UDP kullanmak için, aşağıdaki örnekte olduğu gibi protokol türünü değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1b063-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="1b063-108">Numaralandırma, <xref:System.Net.Sockets.AddressFamily> **soket** sınıfı tarafından ağ adreslerini çözmek için kullanılan standart adres ailelerini belirtir (örneğin, **AddressFamily.InterNetwork** üyesi IP sürüm 4 adres ailesini belirtir).</span><span class="sxs-lookup"><span data-stu-id="1b063-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="1b063-109">Numaralandırma <xref:System.Net.Sockets.SocketType> soket türünü belirtir (örneğin, **SocketType.Stream** üyesi akış denetimi ile veri göndermek ve almak için standart bir soket gösterir).</span><span class="sxs-lookup"><span data-stu-id="1b063-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="1b063-110">Numaralandırma, <xref:System.Net.Sockets.ProtocolType> **Soket** üzerinde iletişim kurarken kullanılacak ağ protokolünü belirtir (örneğin, **ProtocolType.Tcp** soketin TCP kullandığını gösterir; **ProtocolType.Udp** soketin UDP kullandığını gösterir).</span><span class="sxs-lookup"><span data-stu-id="1b063-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="1b063-111">Bir **Soket** oluşturulduktan sonra, uzak bir uç noktaya bağlantı başlatabilir veya uzak aygıtlardan bağlantı alabilir.</span><span class="sxs-lookup"><span data-stu-id="1b063-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b063-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b063-112">See also</span></span>

- [<span data-ttu-id="1b063-113">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1b063-113">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="1b063-114">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="1b063-114">Listening with Sockets</span></span>](listening-with-sockets.md)
