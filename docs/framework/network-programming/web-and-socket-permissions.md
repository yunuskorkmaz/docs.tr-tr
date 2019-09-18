---
title: Web ve Yuva İzinleri
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: d1b993acbf20eac244e596075c3f826bba3211a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046861"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="48573-102">Web ve Yuva İzinleri</span><span class="sxs-lookup"><span data-stu-id="48573-102">Web and Socket Permissions</span></span>
<span data-ttu-id="48573-103"><xref:System.Net> Ad alanını kullanan uygulamalar için Internet güvenliği, <xref:System.Net.WebPermission> ve <xref:System.Net.SocketPermission> sınıfları tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="48573-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="48573-104">**WebPermission** sınıfı bir URI 'den veri istemek veya bir URI 'yi Internet 'e sağlamak için bir uygulamanın hakkını denetler.</span><span class="sxs-lookup"><span data-stu-id="48573-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="48573-105">**SocketPermission** sınıfı, bir uygulamanın, bir <xref:System.Net.Sockets.Socket> yerel bağlantı noktasındaki verileri kabul etmek veya başka bir adreste bir aktarım protokolü kullanarak uzak cihazlara iletişim kurmak için, ' ın ana bilgisayar, bağlantı noktası numarası ve aktarım protokolüne bağlı olarak kullanılması hakkını denetler yuvasının.</span><span class="sxs-lookup"><span data-stu-id="48573-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="48573-106">Kullandığınız izin sınıfı, uygulama türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="48573-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="48573-107">Ve alt öğeleri kullanan uygulamaların, izinleri yönetmek için **WebPermission** sınıfını kullanması gerekir. <xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="48573-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="48573-108">Yuva düzeyi erişim kullanan uygulamaların, izinleri yönetmek için **SocketPermission** sınıfını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48573-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="48573-109">**WebPermission** ve **SocketPermission** iki izin tanımlar: Accept ve Connect.</span><span class="sxs-lookup"><span data-stu-id="48573-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="48573-110">Accept, uygulamayı başka bir taraftan gelen bir bağlantıyı yanıtlamak için hak verir.</span><span class="sxs-lookup"><span data-stu-id="48573-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="48573-111">Connect, uygulamaya başka bir tarafa bağlantı başlatma hakkı verir.</span><span class="sxs-lookup"><span data-stu-id="48573-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="48573-112">**SocketPermission** örnekleri için kabul et, bir uygulamanın yerel bir aktarım adresinde gelen bağlantıları kabul edebileceği anlamına gelir; Connect, bir uygulamanın bir uzak (veya yerel) aktarım adresine bağlanabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="48573-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="48573-113">**WebPermission** örnekleri için kabul et, bir uygulamanın **WebPermission** tarafından denetlenen URI 'yi dünyaya dışa verebileceği anlamına gelir; bağlantı, bir uygulamanın bu URI 'ye erişebileceği anlamına gelir (uzak veya yerel olsun).</span><span class="sxs-lookup"><span data-stu-id="48573-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48573-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48573-114">See also</span></span>

- [<span data-ttu-id="48573-115">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="48573-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="48573-116">Ağ Programlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="48573-116">Security in Network Programming</span></span>](security-in-network-programming.md)
