---
title: 'Nasıl yapılır: Yuva Oluşturma'
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
ms.openlocfilehash: 54706293784d77e535cac582c99b1dd21a12e380
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048379"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="7ed33-102">Nasıl yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7ed33-102">How to: Create a Socket</span></span>
<span data-ttu-id="7ed33-103">Uzak cihazlarla iletişim kurmak üzere bir yuva kullanabilmeniz için, yuva protokol ve ağ adresi bilgileriyle başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ed33-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="7ed33-104"><xref:System.Net.Sockets.Socket> Sınıfına yönelik oluşturucunun, bağlantı kurmak için yuvanın kullandığı adres ailesini, yuva türünü ve protokol türünü belirten parametreleri vardır.</span><span class="sxs-lookup"><span data-stu-id="7ed33-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ed33-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ed33-105">Example</span></span>  
 <span data-ttu-id="7ed33-106">Aşağıdaki örnek, Internet gibi TCP/IP tabanlı bir ağda iletişim kurmak için kullanılabilecek bir yuva oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7ed33-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="7ed33-107">TCP yerine UDP kullanmak için, aşağıdaki örnekte olduğu gibi protokol türünü değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7ed33-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="7ed33-108">Sabit listesi, ağ adreslerini çözümlemek için **yuva** sınıfı tarafından kullanılan standart adres aileleri belirtir (örneğin, **AddressFamily. InterNetwork** üyesi, IP sürüm 4 adres ailesini belirtir). <xref:System.Net.Sockets.AddressFamily></span><span class="sxs-lookup"><span data-stu-id="7ed33-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="7ed33-109">Numaralandırma, yuva türünü belirtir (örneğin, **SocketType. Stream** üyesi, akış denetimiyle veri gönderme ve alma için standart bir yuva gösterir). <xref:System.Net.Sockets.SocketType></span><span class="sxs-lookup"><span data-stu-id="7ed33-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="7ed33-110">Sabit listesi, **yuvada** iletişim kurulurken kullanılacak ağ protokolünü belirtir (örneğin, **ProtocolType. TCP** , yuvanın TCP kullandığını gösterir; <xref:System.Net.Sockets.ProtocolType> **ProtocolType. UDP** , yuvanın UDP kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ed33-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="7ed33-111">Bir **yuva** oluşturulduktan sonra, uzak bir uç noktaya bağlantı başlatabilir veya uzak cihazlardan gelen bağlantıları alabilir.</span><span class="sxs-lookup"><span data-stu-id="7ed33-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed33-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ed33-112">See also</span></span>

- [<span data-ttu-id="7ed33-113">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7ed33-113">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="7ed33-114">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="7ed33-114">Listening with Sockets</span></span>](listening-with-sockets.md)
