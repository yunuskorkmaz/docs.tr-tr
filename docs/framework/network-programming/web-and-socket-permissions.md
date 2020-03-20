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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046861"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="2dffe-102">Web ve Yuva İzinleri</span><span class="sxs-lookup"><span data-stu-id="2dffe-102">Web and Socket Permissions</span></span>
<span data-ttu-id="2dffe-103"><xref:System.Net> Ad alanını kullanan uygulamalar için Internet güvenliği <xref:System.Net.WebPermission> <xref:System.Net.SocketPermission> ve sınıflar tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2dffe-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="2dffe-104">**WebPermission** sınıfı, bir uygulamanın URI'den veri isteme veya Bir URI'yi Internet'e sunma hakkını denetler.</span><span class="sxs-lookup"><span data-stu-id="2dffe-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="2dffe-105">**SocketPermission** sınıfı, bir uygulamanın yerel <xref:System.Net.Sockets.Socket> bir bağlantı noktasında veri kabul etmek veya yuvanın ana bilgisayar, bağlantı noktası numarası ve taşıma protokolüne dayalı olarak başka bir adreste taşıma protokolü kullanarak uzak aygıtlarla iletişim kurmak için bir uygulamanın kullanma hakkını denetler.</span><span class="sxs-lookup"><span data-stu-id="2dffe-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="2dffe-106">Hangi izin sınıfını kullandığınız uygulama türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2dffe-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="2dffe-107">Kullanan <xref:System.Net.WebRequest> uygulamalar ve onun soyundan gelenler izinleri yönetmek için **WebPermission** sınıfını kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dffe-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="2dffe-108">Soket düzeyinde erişim kullanan uygulamalar, izinleri yönetmek için **SocketPermission** sınıfını kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dffe-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="2dffe-109">**WebPermission** ve **SocketPermission** iki izin tanımlar: kabul edin ve bağlanın.</span><span class="sxs-lookup"><span data-stu-id="2dffe-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="2dffe-110">Kabul kabul edin, başvuruya başka bir taraftan gelen bir bağlantıyı yanıtlama hakkı verir.</span><span class="sxs-lookup"><span data-stu-id="2dffe-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="2dffe-111">Connect, uygulamaya başka bir tarafa bağlantı kurma hakkı verir.</span><span class="sxs-lookup"><span data-stu-id="2dffe-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="2dffe-112">**SocketPermission** örnekleri için, bir uygulamanın yerel bir aktarım adresinde gelen bağlantıları kabul edebileceği anlamına gelir; bağlantı, bir uygulamanın bazı uzak (veya yerel) aktarım adresine bağlanabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2dffe-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="2dffe-113">**WebPermission** örnekleri için, bir uygulamanın **WebPermission** tarafından kontrol edilen URI'yi dünyaya dışa aktarabileceği anlamına gelir; bağlanmak, bir uygulamanın o URI'ye (uzak veya yerel olsun) erişebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2dffe-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dffe-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dffe-114">See also</span></span>

- [<span data-ttu-id="2dffe-115">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="2dffe-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="2dffe-116">Ağ Programlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="2dffe-116">Security in Network Programming</span></span>](security-in-network-programming.md)
