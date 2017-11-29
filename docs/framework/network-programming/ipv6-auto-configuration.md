---
title: "IPv6 otomatik yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0332bca146041aa955ea000cfeee78d3f5287036
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="f8155-102">IPv6 otomatik yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f8155-102">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="f8155-103">IPv6 için önemli bir hedef düğümü Tak ve Kullan desteklemektir.</span><span class="sxs-lookup"><span data-stu-id="f8155-103">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="f8155-104">Diğer bir deyişle, bir IPv6 ağında bir düğüm takın ve insan müdahalesi otomatik olarak yapılandırılması mümkün olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8155-104">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="f8155-105">Otomatik yapılandırma türü</span><span class="sxs-lookup"><span data-stu-id="f8155-105">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="f8155-106">IPv6 otomatik yapılandırma aşağıdaki türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="f8155-106">IPv6 supports the following types of auto-configuration:</span></span>  
  
-   <span data-ttu-id="f8155-107">**Durum bilgisi olan otomatik yapılandırma**.</span><span class="sxs-lookup"><span data-stu-id="f8155-107">**Stateful auto-configuration**.</span></span> <span data-ttu-id="f8155-108">IPv6 için Dinamik Ana Bilgisayar Yapılandırma Protokolü gerektiğinden bu tür bir yapılandırma belirli bir düzeyde insan etkileşimi gerektirir (DHCPv6) sunucusu yükleme ve yönetim düğümü.</span><span class="sxs-lookup"><span data-stu-id="f8155-108">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="f8155-109">DHCPv6 sunucusu için yapılandırma bilgilerini sağlayan düğümleri listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="f8155-109">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="f8155-110">Ne kadar her adresi kullanılıyor ve ne zaman yeniden atama için kullanılabilir olabilir sunucuya bilmesi için de durum bilgisini tutar.</span><span class="sxs-lookup"><span data-stu-id="f8155-110">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
-   <span data-ttu-id="f8155-111">**Durum bilgisiz otomatik yapılandırmanın**.</span><span class="sxs-lookup"><span data-stu-id="f8155-111">**Stateless auto-configuration**.</span></span> <span data-ttu-id="f8155-112">Bu tür bir yapılandırma küçük kuruluşlar ve kişiler için uygundur.</span><span class="sxs-lookup"><span data-stu-id="f8155-112">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="f8155-113">Bu durumda, her konak, alınan yönlendirici reklam içeriğini adresinden belirler.</span><span class="sxs-lookup"><span data-stu-id="f8155-113">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="f8155-114">Adresin ağ kimliği bölümünü tanımlamak için IEEE EUI-64 standart kullanarak ana bilgisayar adresi bağlantıyı benzersizliğini varsaymak makul değildir.</span><span class="sxs-lookup"><span data-stu-id="f8155-114">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="f8155-115">Adres nasıl belirlendiğinden bağımsız olarak düğümü olası adresini yerel bağlantısını benzersiz olduğunu doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8155-115">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="f8155-116">Bu komşu isteği göndererek yapılır olası adresine ileti.</span><span class="sxs-lookup"><span data-stu-id="f8155-116">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="f8155-117">Düğüm herhangi bir yanıt alırsa, adresi zaten kullanılıyor ve başka bir adresini belirlemelidir bilir.</span><span class="sxs-lookup"><span data-stu-id="f8155-117">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="f8155-118">IPv6 Mobility</span><span class="sxs-lookup"><span data-stu-id="f8155-118">IPv6 Mobility</span></span>  
 <span data-ttu-id="f8155-119">Mobil aygıtların artışı yeni gereksinimi sunulan: bir aygıtı rasgele IPv6 Internet üzerindeki konumlara değiştirmek ve hala var olan bağlantıların sürdürmek kurabilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8155-119">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="f8155-120">Bu işlevsellik sağlamak için mobil bir düğüme, bu her zaman ulaşılabilen ev adresi atanır.</span><span class="sxs-lookup"><span data-stu-id="f8155-120">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="f8155-121">Mobil düğüm evde olduğunda giriş bağlantısı bağlanır ve ev adresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8155-121">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="f8155-122">Mobil düğüm giriş uzağa doğru olduğunda, genellikle bir yönlendirici olduğundan, bir ev Aracısı iletileri mobil düğümü ve hangi bağlanıyor düğümler arasında aktarır.</span><span class="sxs-lookup"><span data-stu-id="f8155-122">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8155-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8155-123">See Also</span></span>  
 [<span data-ttu-id="f8155-124">Internet Protokolü sürüm 6</span><span class="sxs-lookup"><span data-stu-id="f8155-124">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="f8155-125">Yuva</span><span class="sxs-lookup"><span data-stu-id="f8155-125">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
