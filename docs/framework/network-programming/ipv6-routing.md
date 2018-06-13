---
title: IPv6 yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c3e2662eb444c70d2376a05e44ac84f472f27384
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397812"
---
# <a name="ipv6-routing"></a><span data-ttu-id="e89b2-102">IPv6 yönlendirme</span><span class="sxs-lookup"><span data-stu-id="e89b2-102">IPv6 Routing</span></span>
<span data-ttu-id="e89b2-103">Bir esnek yönlendirme IPv6 yararı mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="e89b2-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="e89b2-104">Hangi IPv4 ağ kimlikleri, olan ve ayrılmış, büyük yönlendirme tablolar yöntemi nedeniyle Internet omurgalarında yönlendirici tarafından saklanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e89b2-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="e89b2-105">Bu yönlendiriciler, potansiyel olarak Internet'te herhangi bir düğüme yönlendirilmiş paketlerini iletmek için tüm yolları bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e89b2-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="e89b2-106">Birleşik adreslerine kendi yeteneğiyle IPv6 esnek adresleme sağlar ve yönlendirme tablolarını boyutunu büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="e89b2-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="e89b2-107">Bu yeni adresleme mimarisinde Ara yönlendiriciler yalnızca kısmının yerel ağlarındaki iletilerini uygun şekilde iletmek için izlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e89b2-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="e89b2-108">Komşu bulma</span><span class="sxs-lookup"><span data-stu-id="e89b2-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="e89b2-109">Komşu Bulma tarafından sağlanan özelliklerden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e89b2-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="e89b2-110">Yönlendirici bulma.</span><span class="sxs-lookup"><span data-stu-id="e89b2-110">Router discovery.</span></span> <span data-ttu-id="e89b2-111">Bu ana yerel yönlendirici tanımlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e89b2-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="e89b2-112">Çözümleme adres.</span><span class="sxs-lookup"><span data-stu-id="e89b2-112">Address resolution.</span></span> <span data-ttu-id="e89b2-113">Bu, karşılık gelen bir sonraki atlama adresi (Adres Çözümleme Protokolü'nü [ARP] yerine) için bir bağlantı katmanı adresi çözümlemek düğümleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e89b2-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="e89b2-114">Otomatik yapılandırma adresi.</span><span class="sxs-lookup"><span data-stu-id="e89b2-114">Address auto-configuration.</span></span> <span data-ttu-id="e89b2-115">Bu ana otomatik olarak site-yerel ve genel adresleri yapılandır olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e89b2-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="e89b2-116">Komşu Bulma IPv6 için Internet Denetim İletisi protokolünü kullanan içerir (Icmpv6) ileti:</span><span class="sxs-lookup"><span data-stu-id="e89b2-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="e89b2-117">Yönlendirici Tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="e89b2-117">Router advertisement.</span></span> <span data-ttu-id="e89b2-118">Sözde düzenli aralıklarla veya yanıt yönlendirici bağlantısı olarak yönlendirici tarafından gönderilen.</span><span class="sxs-lookup"><span data-stu-id="e89b2-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="e89b2-119">IPv6 yönlendiricileri yönlendirici bildirileri kullanılabilirliklerini, adres öneklerini ve diğer parametreleri bildirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e89b2-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="e89b2-120">Yönlendirici Bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="e89b2-120">Router solicitation.</span></span> <span data-ttu-id="e89b2-121">Bağlantıyı yönlendiriciler bir yönlendirici hemen gönder istemek için ana bilgisayar tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e89b2-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="e89b2-122">Komşu bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="e89b2-122">Neighbor solicitation.</span></span> <span data-ttu-id="e89b2-123">Adres çözümlemesi için düğümleri tarafından gönderilen yinelenen adres algılama veya komşu hala erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e89b2-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="e89b2-124">Komşu tanıtım.</span><span class="sxs-lookup"><span data-stu-id="e89b2-124">Neighbor advertisement.</span></span> <span data-ttu-id="e89b2-125">Komşu İsteği için yanıt vermesi veya Komşuları bağlantı katmanı adres değişikliği bildirmek için düğümleri tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e89b2-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="e89b2-126">Yeniden yönlendir.</span><span class="sxs-lookup"><span data-stu-id="e89b2-126">Redirect.</span></span> <span data-ttu-id="e89b2-127">Belirli bir hedefe gönderen bir düğüm için daha iyi bir sonraki atlama adresini belirtmek için yönlendiriciler tarafından gönderilen.</span><span class="sxs-lookup"><span data-stu-id="e89b2-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89b2-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e89b2-128">See Also</span></span>  
 [<span data-ttu-id="e89b2-129">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="e89b2-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="e89b2-130">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="e89b2-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
