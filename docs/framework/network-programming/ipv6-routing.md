---
description: 'Daha fazla bilgi edinin: IPv6 yönlendirme'
title: IPv6 Yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 75499a7380ab0ea7c38c83a6407a0c2a269b5fce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672042"
---
# <a name="ipv6-routing"></a><span data-ttu-id="b2f49-103">IPv6 Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="b2f49-103">IPv6 Routing</span></span>

<span data-ttu-id="b2f49-104">Esnek yönlendirme mekanizması IPv6 avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="b2f49-104">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="b2f49-105">IPv4 ağ kimliklerinin ayrıldığı ve ayrılma yöntemi nedeniyle, büyük yönlendirme tablolarının Internet 'te bulunan yönlendiriciler tarafından saklanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-105">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="b2f49-106">Bu yönlendiricilerin, Internet 'teki herhangi bir düğüme potansiyel olarak yönlendirilmiş paketleri iletmeniz için tüm yolları bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-106">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="b2f49-107">IPv6, adresleri toplama özelliği sayesinde esnek adresleme sağlar ve yönlendirme tablolarının boyutunu büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="b2f49-107">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="b2f49-108">Bu yeni adres mimaride, Ara yönlendiriciler iletileri uygun şekilde iletmek için ağın yalnızca yerel bölümünü takip etmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-108">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="b2f49-109">Komşu bulma</span><span class="sxs-lookup"><span data-stu-id="b2f49-109">Neighbor Discovery</span></span>  

 <span data-ttu-id="b2f49-110">Komşu bulma tarafından sunulan özelliklerden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b2f49-110">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="b2f49-111">Yönlendirici bulma.</span><span class="sxs-lookup"><span data-stu-id="b2f49-111">Router discovery.</span></span> <span data-ttu-id="b2f49-112">Bu, ana bilgisayarların yerel yönlendiricileri belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-112">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="b2f49-113">Adres çözümlemesi.</span><span class="sxs-lookup"><span data-stu-id="b2f49-113">Address resolution.</span></span> <span data-ttu-id="b2f49-114">Bu, düğümlerin ilgili bir sonraki atlama adresi (Adres Çözümleme Protokolü [ARP] için değiştirme) için bir bağlantı katmanı adresini çözümlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2f49-114">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="b2f49-115">Adres otomatik yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="b2f49-115">Address auto-configuration.</span></span> <span data-ttu-id="b2f49-116">Bu, ana bilgisayarların site yerel ve genel adreslerini otomatik olarak yapılandırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-116">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="b2f49-117">Komşu bulma şunları içeren IPv6 (Icmpv6) iletileri için Internet Denetim Iletisi protokolünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="b2f49-117">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="b2f49-118">Yönlendirici tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="b2f49-118">Router advertisement.</span></span> <span data-ttu-id="b2f49-119">Bir yönlendirici tarafından sözde dönemsel olarak veya yönlendirici yanıtına yanıt olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-119">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="b2f49-120">IPv6 yönlendiricileri, kullanılabilirlik, adres ön eklerini ve diğer parametreleri tanıtmak için yönlendirici tanıtımları kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2f49-120">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="b2f49-121">Yönlendirici bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="b2f49-121">Router solicitation.</span></span> <span data-ttu-id="b2f49-122">Bağlantı üzerindeki yönlendiricilerin yönlendirici tanıtımı anında göndermesini istemek için bir ana bilgisayar tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-122">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="b2f49-123">Komşu isteme.</span><span class="sxs-lookup"><span data-stu-id="b2f49-123">Neighbor solicitation.</span></span> <span data-ttu-id="b2f49-124">Adres çözümlemesi, yinelenen adres algılama veya bir komşunun hala erişilebilir olduğunu doğrulama için düğümler tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-124">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="b2f49-125">Komşu tanıtım.</span><span class="sxs-lookup"><span data-stu-id="b2f49-125">Neighbor advertisement.</span></span> <span data-ttu-id="b2f49-126">Bir komşu bağlantısına yanıt vermek veya bağlantı katmanı adresindeki bir değişikliğin komşularını bilgilendirmek için düğümler tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-126">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="b2f49-127">Meniz.</span><span class="sxs-lookup"><span data-stu-id="b2f49-127">Redirect.</span></span> <span data-ttu-id="b2f49-128">Gönderen düğüm için belirli bir hedefe daha iyi bir sonraki atlama adresi göstermek üzere yönlendiriciler tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b2f49-128">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f49-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2f49-129">See also</span></span>

- [<span data-ttu-id="b2f49-130">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="b2f49-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="b2f49-131">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="b2f49-131">Sockets</span></span>](sockets.md)
