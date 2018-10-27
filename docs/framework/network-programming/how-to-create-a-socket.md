---
title: 'Nasıl yapılır: Yuva oluşturma'
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
ms.openlocfilehash: 2c3bfb6435901ac8154bc801ae2a420b252d5849
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50046768"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="bda4f-102">Nasıl yapılır: Yuva oluşturma</span><span class="sxs-lookup"><span data-stu-id="bda4f-102">How to: Create a Socket</span></span>
<span data-ttu-id="bda4f-103">Yuvanın uzak cihazlarla iletişim kurmak için bir yuva kullanmadan önce protokolü ve ağ adresi bilgilerini başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bda4f-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="bda4f-104">Oluşturucusu <xref:System.Net.Sockets.Socket> sınıfı Adres ailesi, yuva türünü ve yuva bağlantı kurmak için kullandığı protokol türü parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="bda4f-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bda4f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bda4f-105">Example</span></span>  
 <span data-ttu-id="bda4f-106">Aşağıdaki örnek, Internet gibi IP tabanlı bir ağda iletişim kurmak için kullanılan bir yuva oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bda4f-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="bda4f-107">UDP, TCP yerine kullanmak için aşağıdaki örnekte olduğu gibi bir protokol türü değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bda4f-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="bda4f-108"><xref:System.Net.Sockets.AddressFamily> Numaralandırması tarafından kullanılan standart adres ailesi belirtir **yuva** ağ adreslerini çözümlemeye sınıfı (örneğin, **AddressFamily.InterNetwork** üye IP belirtir sürüm 4 Adres ailesi).</span><span class="sxs-lookup"><span data-stu-id="bda4f-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="bda4f-109"><xref:System.Net.Sockets.SocketType> Numaralandırma yuva türünü belirtir (örneğin, **SocketType.Stream** üye akış denetimi ile veri gönderme ve alma için standart bir yuva gösterir).</span><span class="sxs-lookup"><span data-stu-id="bda4f-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="bda4f-110"><xref:System.Net.Sockets.ProtocolType> Numaralandırma üzerinde iletişim kurarken kullanılacak ağ protokolü belirtir **yuva** (örneğin, **ProtocolType.Tcp** yuva TCP; kullandığını gösterir **ProtocolType.Udp** yuva UDP kullandığını gösterir).</span><span class="sxs-lookup"><span data-stu-id="bda4f-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="bda4f-111">Sonra bir **yuva** olan oluşturulmuş, uzak uç noktası için bir bağlantı başlatmak veya uzak bağlantıları alabilir.</span><span class="sxs-lookup"><span data-stu-id="bda4f-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda4f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bda4f-112">See Also</span></span>  
 [<span data-ttu-id="bda4f-113">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bda4f-113">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="bda4f-114">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="bda4f-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
