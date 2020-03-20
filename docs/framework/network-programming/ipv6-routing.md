---
title: IPv6 Yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047783"
---
# <a name="ipv6-routing"></a><span data-ttu-id="61611-102">IPv6 Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="61611-102">IPv6 Routing</span></span>
<span data-ttu-id="61611-103">Esnek yönlendirme mekanizması IPv6'nın bir avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="61611-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="61611-104">IPv4 ağ iD'lerinin ayrılma ve ayrılma biçimi nedeniyle, büyük yönlendirme tablolarının Internet omurgasında bulunan yönlendiriciler tarafından korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61611-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="61611-105">Bu yönlendiriciler, Internet'teki herhangi bir düğüme yönlendirilmiş olabilecek paketleri iletmek için tüm yolları bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="61611-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="61611-106">Adresleri toplama yeteneği yle IPv6 esnek adresleme sağlar ve yönlendirme tablolarının boyutunu büyük ölçüde azaltır.</span><span class="sxs-lookup"><span data-stu-id="61611-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="61611-107">Bu yeni adresleme mimarisinde, ara yönlendiriciler iletileri uygun şekilde iletmek için yalnızca ağlarının yerel bölümünü izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="61611-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="61611-108">Komşu Bulma</span><span class="sxs-lookup"><span data-stu-id="61611-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="61611-109">Komşu Bulma tarafından sağlanan özelliklerden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="61611-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="61611-110">Yönlendirici keşfi.</span><span class="sxs-lookup"><span data-stu-id="61611-110">Router discovery.</span></span> <span data-ttu-id="61611-111">Bu, ana bilgisayarların yerel yönlendiricileri tanımlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="61611-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="61611-112">Adres çözünürlüğü.</span><span class="sxs-lookup"><span data-stu-id="61611-112">Address resolution.</span></span> <span data-ttu-id="61611-113">Bu, düğümlerin karşılık gelen bir sonraki atlama adresi (Adres Çözümleme Protokolü [ARP] yerine bir bağlantı katmanı adresi çözmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="61611-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="61611-114">Adres otomatik yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="61611-114">Address auto-configuration.</span></span> <span data-ttu-id="61611-115">Bu, ana bilgisayarların site yerel ve genel adreslerini otomatik olarak yapılandırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="61611-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="61611-116">Komşu Bulma, IPv6 (ICMPv6) iletileri için:</span><span class="sxs-lookup"><span data-stu-id="61611-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="61611-117">Yönlendirici reklam.</span><span class="sxs-lookup"><span data-stu-id="61611-117">Router advertisement.</span></span> <span data-ttu-id="61611-118">Bir yönlendirici tarafından sözde periyodik olarak veya yönlendirici talebine yanıt olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="61611-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="61611-119">IPv6 yönlendiricileri kullanılabilirliklerini, adres öneklerini ve diğer parametreleri bildirmek için yönlendirici reklamları kullanır.</span><span class="sxs-lookup"><span data-stu-id="61611-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="61611-120">Yönlendirici talebi.</span><span class="sxs-lookup"><span data-stu-id="61611-120">Router solicitation.</span></span> <span data-ttu-id="61611-121">Bağlantıdaki yönlendiricilerin hemen bir yönlendirici reklamı göndermesini istemek için bir ana bilgisayar tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="61611-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="61611-122">Komşu talebi.</span><span class="sxs-lookup"><span data-stu-id="61611-122">Neighbor solicitation.</span></span> <span data-ttu-id="61611-123">Adres çözümlemesi, yinelenen adres algılamaveya komşunun hala ulaşılabilir olduğunu doğrulamak için düğümler tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="61611-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="61611-124">Komşu reklamı.</span><span class="sxs-lookup"><span data-stu-id="61611-124">Neighbor advertisement.</span></span> <span data-ttu-id="61611-125">Bir komşu talebine yanıt vermek veya bağlantı katmanı adresindeki bir değişikliği komşuları bilgilendirmek için düğümler tarafından gönderilir.</span><span class="sxs-lookup"><span data-stu-id="61611-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="61611-126">Yönlendirme.</span><span class="sxs-lookup"><span data-stu-id="61611-126">Redirect.</span></span> <span data-ttu-id="61611-127">Yönlendiriciler tarafından, gönderen düğüm için belirli bir hedefe daha iyi bir sonraki atlama adresini belirtmek için gönderilir.</span><span class="sxs-lookup"><span data-stu-id="61611-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61611-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61611-128">See also</span></span>

- [<span data-ttu-id="61611-129">İnternet Protokolü Sürüm 6</span><span class="sxs-lookup"><span data-stu-id="61611-129">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="61611-130">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="61611-130">Sockets</span></span>](sockets.md)
