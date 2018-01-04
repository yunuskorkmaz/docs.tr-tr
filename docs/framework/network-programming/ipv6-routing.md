---
title: "IPv6 yönlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c7bfb79c5ab5406793a27f653b7e6a1abf2b2859
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ipv6-routing"></a><span data-ttu-id="ecfba-102">IPv6 yönlendirme</span><span class="sxs-lookup"><span data-stu-id="ecfba-102">IPv6 Routing</span></span>
<span data-ttu-id="ecfba-103">Bir esnek yönlendirme IPv6 yararı mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="ecfba-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="ecfba-104">Hangi IPv4 ağ kimlikleri, olan ve ayrılmış, büyük yönlendirme tablolar yöntemi nedeniyle Internet omurgalarında yönlendirici tarafından saklanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecfba-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="ecfba-105">Bu yönlendiriciler, potansiyel olarak Internet'te herhangi bir düğüme yönlendirilmiş paketlerini iletmek için tüm yolları bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecfba-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="ecfba-106">Birleşik adreslerine kendi yeteneğiyle IPv6 esnek adresleme sağlar ve yönlendirme tablolarını boyutunu büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="ecfba-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="ecfba-107">Bu yeni adresleme mimarisinde Ara yönlendiriciler yalnızca kısmının yerel ağlarındaki iletilerini uygun şekilde iletmek için izlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecfba-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="ecfba-108">Komşu bulma</span><span class="sxs-lookup"><span data-stu-id="ecfba-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="ecfba-109">Komşu Bulma tarafından sağlanan özelliklerden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ecfba-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="ecfba-110">Yönlendirici bulma.</span><span class="sxs-lookup"><span data-stu-id="ecfba-110">Router discovery.</span></span> <span data-ttu-id="ecfba-111">Bu ana yerel yönlendirici tanımlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ecfba-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="ecfba-112">Çözümleme adres.</span><span class="sxs-lookup"><span data-stu-id="ecfba-112">Address resolution.</span></span> <span data-ttu-id="ecfba-113">Bu, karşılık gelen bir sonraki atlama adresi (Adres Çözümleme Protokolü'nü [ARP] yerine) için bir bağlantı katmanı adresi çözümlemek düğümleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecfba-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="ecfba-114">Otomatik yapılandırma adresi.</span><span class="sxs-lookup"><span data-stu-id="ecfba-114">Address auto-configuration.</span></span> <span data-ttu-id="ecfba-115">Bu ana otomatik olarak site-yerel ve genel adresleri yapılandır olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ecfba-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="ecfba-116">Komşu Bulma IPv6 için Internet Denetim İletisi protokolünü kullanan içerir (Icmpv6) ileti:</span><span class="sxs-lookup"><span data-stu-id="ecfba-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="ecfba-117">Yönlendirici Tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="ecfba-117">Router advertisement.</span></span> <span data-ttu-id="ecfba-118">Sözde düzenli aralıklarla veya yanıt yönlendirici bağlantısı olarak yönlendirici tarafından gönderilen.</span><span class="sxs-lookup"><span data-stu-id="ecfba-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="ecfba-119">IPv6 yönlendiricileri yönlendirici bildirileri kullanılabilirliklerini, adres öneklerini ve diğer parametreleri bildirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ecfba-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="ecfba-120">Yönlendirici Bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="ecfba-120">Router solicitation.</span></span> <span data-ttu-id="ecfba-121">Bağlantıyı yönlendiriciler bir yönlendirici hemen gönder istemek için ana bilgisayar tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ecfba-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="ecfba-122">Komşu bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="ecfba-122">Neighbor solicitation.</span></span> <span data-ttu-id="ecfba-123">Adres çözümlemesi için düğümleri tarafından gönderilen yinelenen adres algılama veya komşu hala erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="ecfba-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="ecfba-124">Komşu tanıtım.</span><span class="sxs-lookup"><span data-stu-id="ecfba-124">Neighbor advertisement.</span></span> <span data-ttu-id="ecfba-125">Komşu İsteği için yanıt vermesi veya Komşuları bağlantı katmanı adres değişikliği bildirmek için düğümleri tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ecfba-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="ecfba-126">Yeniden yönlendir.</span><span class="sxs-lookup"><span data-stu-id="ecfba-126">Redirect.</span></span> <span data-ttu-id="ecfba-127">Belirli bir hedefe gönderen bir düğüm için daha iyi bir sonraki atlama adresini belirtmek için yönlendiriciler tarafından gönderilen.</span><span class="sxs-lookup"><span data-stu-id="ecfba-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecfba-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecfba-128">See Also</span></span>  
 [<span data-ttu-id="ecfba-129">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="ecfba-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="ecfba-130">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="ecfba-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
