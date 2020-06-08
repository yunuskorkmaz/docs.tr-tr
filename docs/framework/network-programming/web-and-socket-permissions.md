---
title: Web ve Yuva İzinleri
description: WebPermission ve SocketPermission sınıflarının, .NET Framework System.Net ad alanını kullanmak için internet güvenliği nasıl sağladığını öğrenin.
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
ms.openlocfilehash: 08ae360e8097f7281631da2a3f9846994dfbf5b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501904"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="565af-103">Web ve Yuva İzinleri</span><span class="sxs-lookup"><span data-stu-id="565af-103">Web and Socket Permissions</span></span>
<span data-ttu-id="565af-104">Ad alanını kullanan uygulamalar için Internet güvenliği <xref:System.Net> , <xref:System.Net.WebPermission> ve sınıfları tarafından sağlanır <xref:System.Net.SocketPermission> .</span><span class="sxs-lookup"><span data-stu-id="565af-104">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="565af-105">**WebPermission** sınıfı bir URI 'den veri istemek veya bir URI 'yi Internet 'e sağlamak için bir uygulamanın hakkını denetler.</span><span class="sxs-lookup"><span data-stu-id="565af-105">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="565af-106">**SocketPermission** sınıfı, bir uygulamanın <xref:System.Net.Sockets.Socket> , bir yerel bağlantı noktasındaki verileri kabul etmek veya başka bir adreste bir aktarım protokolü kullanarak uzak cihazlara bağlantı kurmak için, yuvanın ana bilgisayar, bağlantı noktası numarası ve aktarım protokolüne bağlı olarak kullanılması hakkını denetler.</span><span class="sxs-lookup"><span data-stu-id="565af-106">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="565af-107">Kullandığınız izin sınıfı, uygulama türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="565af-107">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="565af-108"><xref:System.Net.WebRequest>Ve alt öğeleri kullanan uygulamaların, izinleri yönetmek Için **WebPermission** sınıfını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="565af-108">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="565af-109">Yuva düzeyi erişim kullanan uygulamaların, izinleri yönetmek için **SocketPermission** sınıfını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="565af-109">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="565af-110">**WebPermission** ve **SocketPermission** iki izin tanımlar: Accept ve Connect.</span><span class="sxs-lookup"><span data-stu-id="565af-110">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="565af-111">Accept, uygulamayı başka bir taraftan gelen bir bağlantıyı yanıtlamak için hak verir.</span><span class="sxs-lookup"><span data-stu-id="565af-111">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="565af-112">Connect, uygulamaya başka bir tarafa bağlantı başlatma hakkı verir.</span><span class="sxs-lookup"><span data-stu-id="565af-112">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="565af-113">**SocketPermission** örnekleri için kabul et, bir uygulamanın yerel bir aktarım adresinde gelen bağlantıları kabul edebileceği anlamına gelir; Connect, bir uygulamanın bir uzak (veya yerel) aktarım adresine bağlanabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="565af-113">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="565af-114">**WebPermission** örnekleri için kabul et, bir uygulamanın **WebPermission** tarafından denetlenen URI 'yi dünyaya dışa verebileceği anlamına gelir; bağlantı, bir uygulamanın bu URI 'ye erişebileceği anlamına gelir (uzak veya yerel olsun).</span><span class="sxs-lookup"><span data-stu-id="565af-114">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565af-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="565af-115">See also</span></span>

- [<span data-ttu-id="565af-116">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="565af-116">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="565af-117">Ağ Programlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="565af-117">Security in Network Programming</span></span>](security-in-network-programming.md)
